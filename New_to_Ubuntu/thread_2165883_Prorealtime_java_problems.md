---
title: "Prorealtime java problems"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by padnoter on 2013-08-06
Hi,

I'm using ubuntu 12.04 (3.2.0-51-generic)

I'm trying to run the "complete workstation 10.1" from [www.prorealtime.com]("http://www.prorealtime.com") (free to register & try)
I had been running it for years on various ubuntu installs up until about 2 weeks ago. Now it always fails (it still works under windows7 & I hate having to use that!)
It's a java app that downloads a .jnlp which then runs & downloads some .jars that finally start the app.

I have OpenJDK Java6 runtime & icedtea java plug-in installed - which as I said, did work for years.

Now during/after the .jar download phase I get this error;

[SIZE=1]net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize application. 
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:778)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:552)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:889)
Caused by: net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars. Description: error in opening zip file
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:485)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:204)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:323)
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:770)
    ... 2 more
Caused by: 
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars. Description: error in opening zip file
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:485)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:204)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:323)
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:770)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:552)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:889)[/SIZE]

They have a diagnostic page - that all passes ok.

I also tried the Java7 & IcedTea Java Web start, but no difference - although looking at the "java" processes it seems to still use java6 - even when "java -version" points to java7. 

The prorealtime "simplified workstation" still launches & works fine.

I've cleared the .icedtea/cache directory & killed java/javawc processes

I have searched the forum, but can't find anything recent about this problem.
Any help would be appreciated.

Thanks

---

### Post by craig10x on 2013-08-06
Perhaps you need the licensed version of Oracle Java...I use two java programs myself that simply don't run properly with the open source version, so perhaps that is also true with what you are trying to run...here's an easy way to get it (it is a deb package that not only installs the licensed version but also gives you updates in the software manager as well) see linked article...copy and paste one command in at a time, and let the terminal do it's thing, then when the license agreement comes up, pivot your arrow keys to the "OK" button and hit enter...
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

Worth a try :)
I use that deb installer myself and it works great...

---

### Post by padnoter on 2013-08-07
> **craig10x said:**
> Perhaps you need the licensed version of Oracle Java...I use two java programs myself that simply don't run properly with the open source version, so perhaps that is also true with what you are trying to run...here's an easy way to get it (it is a deb package that not only installs the licensed version but also gives you updates in the software manager as well) see linked article...copy and paste one command in at a time, and let the terminal do it's thing, then when the license agreement comes up, pivot your arrow keys to the "OK" button and hit enter...
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

Worth a try :)
I use that deb installer myself and it works great...


Hi craig10x,
Thanks - I followed that and upgraded java to the latest oracle 7_25.
It looks good (& matches the windows - that still works ok), but I still get the same problem.
The prorealtime "simplified workstation" downloads and runs fine.
The prorealtime "Complete workstation 10.1" fails to download fully & won't run.
Here is the 'fuller' error from java7;

[SIZE=1]application error:
launch file:

<jnlp spec="1.0+" codebase="https://www.prorealtime.com/">
  <information>
    <title>ProRealTime Complete</title>
    <vendor>ProRealTime</vendor>
    <homepage href="https://www.prorealtime.com"/>
    <description>ProRealTime - Complete workstation</description>
    <description kind="short">ProRealTime - Complete workstation</description>
    <icon href="https://www.prorealtime.com/en/images/logo.gif" kind="splash"/>
    <icon href="https://www.prorealtime.com/common/images/icon.png"/>
  </information>
  <security>
    <all-permissions/>
  </security>
  <resources>
    <property name="-Dsun.java2d.d3d" value="false"/>
    <property name="jnlp.packEnabled" value="true"/>
    <j2se version="1.6.0+" href="http://java.sun.com/products/autodl/j2se" max-heap-size="1024M" java-vm-args="-noverify"/>
    <jar href="**[https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar](https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar)**" main="true" download="eager"/>
    <jar href="https://www.prorealtime.com/java/proordersounds-0.9.jar" download="eager"/>
    <jar href="https://www.prorealtime.com/java/prtsounds-0.9.jar" download="eager"/>
    <jar href="https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815-en.jar" download="eager"/>
  </resources>
  <application-desc main-class="General.StartApplet">
    <argument>http://c.rt1.e.prorealtime.com/ProRealTimeNew/</argument>
    <argument>c50bd97989a4db6d83c11fe3ba08430664a23203b9370fb734863ec9cd461e6b</argument>
    <argument>lang=en_GB_ProRealTime|url_server=https://www.prorealtime.com|pingport=48557|port=48618|mainframetitle=ProRealTime Complete|ws_path=services|pkey=de2529f8e0b80e6933c1ab3e1c1f4c53adf5ed590547800685e45b43920bb61c|prt_key=8cdd03e1d94c87bed8f0d9eae402fde53065a0bb7d7311d7340a4ce242bfae8d|prttrading=t|sign=24bae1b9dd42d006c2003e8ff8dab3665d9ce0c068bb45f6ad1f85f10f747864</argument>
  </application-desc>
</jnlp>

exception:
com.sun.deploy.net.FailedDownloadException: **Unable to load resource: [https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar](https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar)**
    at com.sun.deploy.net.DownloadEngine.actionDownload(Unknown Source)
    at com.sun.deploy.net.DownloadEngine.downloadResource(Unknown Source)
    at com.sun.deploy.cache.ResourceProviderImpl.getResource(Unknown Source)
    at com.sun.deploy.cache.ResourceProviderImpl.getResource(Unknown Source)
    at com.sun.javaws.LaunchDownload$DownloadTask.call(Unknown Source)
    at java.util.concurrent.FutureTask$Sync.innerRun(FutureTask.java:334)
    at java.util.concurrent.FutureTask.run(FutureTask.java:166)
    at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1145)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:615)
    at java.lang.Thread.run(Thread.java:724)

wrapped exception:
**javax.net.ssl.SSLException: Connection has been shutdown: javax.net.ssl.SSLException: java.net.SocketException: Connection reset**
    at sun.security.ssl.SSLSocketImpl.checkEOF(SSLSocketImpl.java:1476)
    at sun.security.ssl.AppInputStream.available(AppInputStream.java:59)
    at java.io.BufferedInputStream.available(BufferedInputStream.java:399)
    at sun.net.[www.MeteredStream.available(MeteredStream.java:170)]("http://www.MeteredStream.available(MeteredStream.java:170)")
    at sun.net.[www.http.KeepAliveStream.close(KeepAliveStream.java:85)]("http://www.http.KeepAliveStream.close(KeepAliveStream.java:85)")
    at java.io.FilterInputStream.close(FilterInputStream.java:181)
    at sun.net.www.protocol.http.HttpURLConnection$HttpInputStream.close(HttpURLConnection.java:3122)
    at java.io.BufferedInputStream.close(BufferedInputStream.java:472)
    at com.sun.deploy.net.HttpDownloadHelper.download(Unknown Source)
    at com.sun.deploy.cache.Cache.downloadResourceToTempFile(Unknown Source)
    at com.sun.deploy.cache.Cache.downloadResourceToCache(Unknown Source)
    at com.sun.deploy.net.DownloadEngine.actionDownload(Unknown Source)
    at com.sun.deploy.net.DownloadEngine.downloadResource(Unknown Source)
    at com.sun.deploy.cache.ResourceProviderImpl.getResource(Unknown Source)
    at com.sun.deploy.cache.ResourceProviderImpl.getResource(Unknown Source)
    at com.sun.javaws.LaunchDownload$DownloadTask.call(Unknown Source)
    at java.util.concurrent.FutureTask$Sync.innerRun(FutureTask.java:334)
    at java.util.concurrent.FutureTask.run(FutureTask.java:166)
    at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1145)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:615)
    at java.lang.Thread.run(Thread.java:724)
Caused by: javax.net.ssl.SSLException: java.net.SocketException: Connection reset
    at sun.security.ssl.Alerts.getSSLException(Alerts.java:208)
    at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1886)
    at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1844)
    at sun.security.ssl.SSLSocketImpl.handleException(SSLSocketImpl.java:1808)
    at sun.security.ssl.SSLSocketImpl.handleException(SSLSocketImpl.java:1753)
    at sun.security.ssl.AppInputStream.read(AppInputStream.java:113)
    at java.io.BufferedInputStream.read1(BufferedInputStream.java:273)
    at java.io.BufferedInputStream.read(BufferedInputStream.java:334)
    at sun.net.[www.MeteredStream.read(MeteredStream.java:134)]("http://www.MeteredStream.read(MeteredStream.java:134)")
    at java.io.FilterInputStream.read(FilterInputStream.java:133)
    at sun.net.www.protocol.http.HttpURLConnection$HttpInputStream.read(HttpURLConnection.java:3052)
    at java.io.BufferedInputStream.fill(BufferedInputStream.java:235)
    at java.io.BufferedInputStream.read1(BufferedInputStream.java:275)
    at java.io.BufferedInputStream.read(BufferedInputStream.java:334)
    at java.util.zip.InflaterInputStream.fill(InflaterInputStream.java:238)
    at java.util.zip.InflaterInputStream.read(InflaterInputStream.java:158)
    at java.util.zip.GZIPInputStream.read(GZIPInputStream.java:116)
    at java.io.BufferedInputStream.fill(BufferedInputStream.java:235)
    at java.io.BufferedInputStream.read1(BufferedInputStream.java:275)
    at java.io.BufferedInputStream.read(BufferedInputStream.java:334)
    at java.io.BufferedInputStream.read1(BufferedInputStream.java:273)
    at java.io.BufferedInputStream.read(BufferedInputStream.java:334)
    at com.sun.java.util.jar.pack.NativeUnpack.readInputFn(NativeUnpack.java:124)
    at com.sun.java.util.jar.pack.NativeUnpack.start(Native Method)
    at com.sun.java.util.jar.pack.NativeUnpack.run(NativeUnpack.java:193)
    at com.sun.java.util.jar.pack.NativeUnpack.run(NativeUnpack.java:242)
    at com.sun.java.util.jar.pack.UnpackerImpl.unpack(UnpackerImpl.java:136)
    ... 13 more
Caused by: java.net.SocketException: Connection reset
    at java.net.SocketInputStream.read(SocketInputStream.java:189)
    at java.net.SocketInputStream.read(SocketInputStream.java:121)
    at sun.security.ssl.InputRecord.readFully(InputRecord.java:442)
    at sun.security.ssl.InputRecord.readV3Record(InputRecord.java:554)
    at sun.security.ssl.InputRecord.read(InputRecord.java:509)
    at sun.security.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:927)
    at sun.security.ssl.SSLSocketImpl.readDataRecord(SSLSocketImpl.java:884)
    at sun.security.ssl.AppInputStream.read(AppInputStream.java:102)
    ... 34 more

[/SIZE]- in case that helps anyone help me?

From what I can see the main file (9.1mb) fails to download completely every time on ubuntu/firefox (&chromium);
[https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar](https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar)
(see above in **bold**)

I've even tried pasting; [https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar](https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar) into a browser tab, and it stops after downloading about 1.8mb of the 9.1mb ??? :confused:

(It all works under windows on the same laptop & internet connection, and the file will download 9.1mb in a windows firefox browser tab too - so I think that rules out internet connection and/or prorealtime host).

Any ideas anyone?
Is there some limit for .jar files under firefox/ubuntu - some variable I can check/set/trace to see why it stops every time? Remember, it all worked on ubuntu up until about 2 weeks ago - & i've been fighting it ever since.

The .jnlp that is being executed is;

[SIZE=1]<?xml version="1.0" encoding="utf-8"?>
<jnlp spec="1.0+" codebase="https://www.prorealtime.com/">
    <information>
        <title>ProRealTime Complete</title>
        <vendor>ProRealTime</vendor>
        <homepage href="https://www.prorealtime.com" />
        <description>ProRealTime - Complete workstation</description>
        <description kind="short">ProRealTime - Complete workstation</description>
        <icon href="https://www.prorealtime.com/en/images/logo.gif" kind="splash" />
        <icon href="https://www.prorealtime.com/common/images/icon.png" />
    </information>

    <security>
        <all-permissions/>
    </security>

    <resources>
        <property name="-Dsun.java2d.d3d" value="false"/>
        <property name="jnlp.packEnabled" value="true" />
        <j2se version="1.6.0+" href="http://java.sun.com/products/autodl/j2se" max-heap-size="1024M" java-vm-args="-noverify"/>
        **<jar href="https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar" main="true" download="eager" />**
        <jar href="https://www.prorealtime.com/java/proordersounds-0.9.jar" download="eager" />
        <jar href="https://www.prorealtime.com/java/prtsounds-0.9.jar" download="eager" />
        <jar href="https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815-en.jar" download="eager" />
    </resources>

    <application-desc main-class="General.StartApplet">
        <argument>http://c.rt0.e.prorealtime.com/ProRealTimeNew/</argument>
        <argument>cf1867a6ea3e342de265ca2519f7ba67a890886f6d1abcf74c40bda2e9fad97a</argument>
        <argument>lang=en_GB_ProRealTime|url_server=https://www.prorealtime.com|pingport=48558|port=48619|mainframetitle=ProRealTime Complete|ws_path=services|pkey=4bcb80e8d15d0dc6d1d0c410a2310281e1b93c1c389542c95d514ce778ac744a|prt_key=a4b53bdb21b3a99e2d6c88f36e2ff0120e0134cc92e4028ba1b7ee4f4d4c425d|prttrading=t|sign=8d4b6d4fa1f53bf6ebf2fefcfee7eecbc4c298c5270f5b5ca6536453d0d9c7dd</argument>
    </application-desc>
</jnlp>
[/SIZE]
- not sure if i can edit this to help, but included for reference.

Any help/suggestions appreciated?
(I'm talking to prorealtime too... will update if they suggest anything)
Thanks

---

### Post by craig10x on 2013-08-07
Glad to hear the java update i gave you was successful...yeah i see you are still experiencing a problem...i hope someone who is more technically oriented will come along and be able to assist you...

---

### Post by padnoter on 2013-08-07
> **craig10x said:**
> Glad to hear the java update i gave you was successful...yeah i see you are still experiencing a problem...i hope someone who is more technically oriented will come along and be able to assist you...

yes it's a real pain.... even pointing firefox to download [https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar](https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar) - fails
(but works fine on windows schmindows :( )

any ideas anyone?

---

### Post by padnoter on 2013-08-10
If anyone else has a problem with this a solution that worked for me is here;

[http://ubuntuforums.org/showthread.php?t=2166416&p=12752402#post12752402](http://ubuntuforums.org/showthread.php?t=2166416&p=12752402#post12752402)

 					[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **The Cog** 					[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12752017#post12752017") 				
 				It's a long shot, but I wonder if there is a  problem with TCP window scaling. Try this to disabling scaling, then try  theo download again:
 	Code:
 	sudo sh -c 'echo 0 > /proc/sys/net/ipv4/tcp_window_scaling' 
You can re-enable scaling with 
 	Code:
 	sudo sh -c 'echo 1 > /proc/sys/net/ipv4/tcp_window_scaling'

---

