#  Multiplatform SDK のインストール時にUnExpected Errorが発生する


# 問題

Windows 11 or 10 にて、Link-OS Multi-platform をインストールするとLAX エラーが発生し、インストールが中断する。

![Alt text](image.png)

![Alt text](image-1.png)


▽ 詳細エラーの内容（例）

    Flexeraayd$aaa: Windows DLL failed to load
    at Flexeraayd.af(Unknown Source)
    at Flexeraayd.aa(Unknown Source)
    at com.zerog.ia.installer.LifeCycleManager.init(Unknown Source)
    at com.zerog.ia.installer.LifeCycleManager.executeApplication(Unknown Source)
    at com.zerog.ia.installer.Main.main(Unknown Source)
    at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:104)
    at java.base/java.lang.reflect.Method.invoke(Method.java:578)
    at com.zerog.lax.LAX.launch(Unknown Source)
    at com.zerog.lax.LAX.main(Unknown Source)

a. 実施環境

    エディション      Windows 11 Pro
    バージョン         22H2
    インストール日  ‎2023/‎07/‎03
    OS ビルド          22621.1992
    エクスペリエンス            Windows Feature Experience Pack 1000.22644.1000.0
    
    C:\Program Files\Java\jdk-20\bin>java -version
    java version "20.0.1" 2023-04-18 ★
    Java(TM) SE Runtime Environment (build 20.0.1+9-29)
    Java HotSpot(TM) 64-Bit Server VM (build 20.0.1+9-29, mixed mode, sharing)

<br><br>

# 原因

SDKインストーラが最新のJava VM（20.0.x） に対応していない。

<br><br>

# 対処方法

1. java runtinme のバージョンを確認する。

        C:\Users\zebra>java -version
        'java' は、内部コマンドまたは外部コマンド、
        操作可能なプログラムまたはバッチ ファイルとして認識されていません。


1. java runtine が1.8.0_321以上の場合はJDK をアンインストールする。

1. "Java SE Development Kit 8u311" をインストールする。

    #### Java SE 8 Archive Downloads (JDK 8u211 and later)
    https://www.oracle.com/jp/java/technologies/javase/javase8u211-later-archive-downloads.html


1. Link-OS SDK をインストールする。

    #### LINK-OS MULTIPLATFORM SDK DOWNLOADS & SUPPORT
    https://www.zebra.com/us/en/support-downloads/printer-software/link-os-multiplatform-sdk.html

1. "Java SE Development Kit 8u311"  をアンインストールする。

1. 最新のJDKを再インストールする。

    #### JDK Development Kit 20.0.2 downloads
    https://www.oracle.com/java/technologies/downloads/

    <br><br>
