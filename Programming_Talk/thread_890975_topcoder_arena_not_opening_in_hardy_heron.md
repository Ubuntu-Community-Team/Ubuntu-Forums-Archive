---
title: "topcoder arena not opening in hardy heron"
date: 2008-08-15
forum: Programming Talk
---

### Post by shankhs on 2008-08-15
I installed jre in my ubuntu 8.04 PC...
and the jre has installed fine as when i did
```
java -version
```
I got:
```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
```
but whenever I am trying to open the arena it says:
The application cannot be opened due to:

EXCEPTION:```

com.sun.deploy.net.FailedDownloadException: Unable to load resource: http://www.topcoder.com/contest/arena/ContestAppletProd.jnlp
at com.sun.deploy.net.DownloadEngine.actionDownload(DownloadEngine.java:961)
at com.sun.deploy.net.DownloadEngine.getCacheEntry(DownloadEngine.java:1059)
at com.sun.deploy.net.DownloadEngine.getResourceCacheEntry(DownloadEngine.java:1134)
at com.sun.deploy.net.DownloadEngine.getResourceCacheEntry(DownloadEngine.java:1068)
at com.sun.deploy.net.DownloadEngine.getResource(DownloadEngine.java:142)
at com.sun.deploy.net.DownloadEngine.getResource(DownloadEngine.java:127)
at com.sun.javaws.Launcher.updateFinalLaunchDesc(Launcher.java:245)
at com.sun.javaws.Launcher.prepareToLaunch(Launcher.java:127)
at com.sun.javaws.Launcher.launch(Launcher.java:95)
at com.sun.javaws.Main.launchApp(Main.java:300)
at com.sun.javaws.Main.continueInSecureThread(Main.java:210)
at com.sun.javaws.Main$1.run(Main.java:107)
at java.lang.Thread.run(Thread.java:619)
```
WRAPPED EXCEPTION:```

java.net.ConnectException: Connection timed out
at java.net.PlainSocketImpl.socketConnect(Native Method)
at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
at java.net.Socket.connect(Socket.java:519)
at java.net.Socket.connect(Socket.java:469)
at sun.net.NetworkClient.doConnect(NetworkClient.java:157)
at sun.net.www.http.HttpClient.openServer(HttpClient.java:394)
at sun.net.www.http.HttpClient.openServer(HttpClient.java:529)
at sun.net.www.http.HttpClient.<init>(HttpClient.java:233)
at sun.net.www.http.HttpClient.New(HttpClient.java:306)
at sun.net.www.http.HttpClient.New(HttpClient.java:323)
at sun.net.www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:788)
at sun.net.www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:729)
at sun.net.www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:654)
at com.sun.deploy.net.BasicHttpRequest.doRequest(BasicHttpRequest.java:178)
at com.sun.deploy.net.BasicHttpRequest.doRequest(BasicHttpRequest.java:106)
at com.sun.deploy.net.BasicHttpRequest.doGetRequest(BasicHttpRequest.java:71)
at com.sun.deploy.net.DownloadEngine.actionDownload(DownloadEngine.java:791)
at com.sun.deploy.net.DownloadEngine.getCacheEntry(DownloadEngine.java:1059)
at com.sun.deploy.net.DownloadEngine.getResourceCacheEntry(DownloadEngine.java:1134)
at com.sun.deploy.net.DownloadEngine.getResourceCacheEntry(DownloadEngine.java:1068)
at com.sun.deploy.net.DownloadEngine.getResource(DownloadEngine.java:142)
at com.sun.deploy.net.DownloadEngine.getResource(DownloadEngine.java:127)
at com.sun.javaws.Launcher.updateFinalLaunchDesc(Launcher.java:245)
at com.sun.javaws.Launcher.prepareToLaunch(Launcher.java:127)
at com.sun.javaws.Launcher.launch(Launcher.java:95)
at com.sun.javaws.Main.launchApp(Main.java:300)
at com.sun.javaws.Main.continueInSecureThread(Main.java:210)
at com.sun.javaws.Main$1.run(Main.java:107)
at java.lang.Thread.run(Thread.java:619)
```
PLZ help me!!!

---

### Post by catabriga on 2008-08-29
I'm having this same problem, and I haven't found a solution yet...

This problems happens with any jnpl, not just the topcoder arena, I tried running it with openjdk and java 32-bit (I'm using 64-bit ubuntu) and neither worked. However, the errors were different. With opendjdk I execute  the jnpl file and nothing happens. With the java 32-bit, I got the exact same error shanks is having.

So some help for us would be great.

---

### Post by shankhs on 2008-09-01
magically the problem solved i dont know how.

---

### Post by podapoda on 2009-02-05
Topcoder arena used to work fine for me until i installed IBM's java version for running Websphere. After that the arena stopped opening and when i execute the jnlp file, nothing happens!!. Someone please help.

---

### Post by zack1988 on 2009-06-22
hi all! Here is a guide i used to fix it

[http://pceasy4all.wordpress.com/2009/06/22/topcoderubuntu/](http://pceasy4all.wordpress.com/2009/06/22/topcoderubuntu/)

Hope it could help! bye

---

