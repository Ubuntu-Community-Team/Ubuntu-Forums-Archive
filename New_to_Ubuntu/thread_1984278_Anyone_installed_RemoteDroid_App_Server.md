---
title: "Anyone installed RemoteDroid App Server?"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by mikee55 on 2012-05-21
FINISHED --2012-05-21 17:35:02--
Total wall clock time: 51s
Downloaded: 1 files, 60K in 0.7s (87.9 KB/s)
tuxusers@Tuxuser:~$ unzip RemoteDroidServer.zip
unzip:  cannot find or open RemoteDroidServer.zip, RemoteDroidServer.zip.zip or RemoteDroidServer.zip.ZIP.
tuxusers@Tuxuser:~$ cd RemoteDroidServer
bash: cd: RemoteDroidServer: No such file or directory
tuxusers@Tuxuser:~$ chmod +x RemoteDroidServer.jar
chmod: cannot access `RemoteDroidServer.jar': No such file or directory
tuxusers@Tuxuser:~$ java -jar RemoteDroidServer.jar
Error: Unable to access jarfile RemoteDroidServer.jar
tuxusers@Tuxuser:~$ wget RemoteDroidServer.zip [http://goo.gl/3weiT](http://goo.gl/3weiT)
--2012-05-21 17:44:53--  [http://remotedroidserver.zip/](http://remotedroidserver.zip/)
Resolving remotedroidserver.zip (remotedroidserver.zip)... 
failed: Name or service not known.
wget: unable to resolve host address `remotedroidserver.zip'
--2012-05-21 17:45:33--  [http://goo.gl/3weiT](http://goo.gl/3weiT)
Resolving goo.gl (goo.gl)... 173.194.41.128, 173.194.41.135, 173.194.41.133, ...
Connecting to goo.gl (goo.gl)|173.194.41.128|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.remotedroid.net/RemoteDroidServer_v1.5.zip](http://www.remotedroid.net/RemoteDroidServer_v1.5.zip) [following]
--2012-05-21 17:45:38--  [http://www.remotedroid.net/RemoteDroidServer_v1.5.zip](http://www.remotedroid.net/RemoteDroidServer_v1.5.zip)
Resolving [www.remotedroid.net](www.remotedroid.net) ([www.remotedroid.net](www.remotedroid.net))... 96.126.96.240
Connecting to [www.remotedroid.net](www.remotedroid.net) ([www.remotedroid.net)|96.126.96.240|:80](www.remotedroid.net)|96.126.96.240|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 61552 (60K) [application/zip]
Saving to: `3weiT.2'

100%[======================================>] 61,552       154K/s   in 0.4s    

2012-05-21 17:45:39 (154 KB/s) - `3weiT.2' saved [61552/61552]

FINISHED --2012-05-21 17:45:39--
Total wall clock time: 46s
Downloaded: 1 files, 60K in 0.4s (154 KB/s)
tuxusers@Tuxuser:~$ unzip RemoteDroidServer.zip
unzip:  cannot find or open RemoteDroidServer.zip, RemoteDroidServer.zip.zip or RemoteDroidServer.zip.ZIP.
tuxusers@Tuxuser:~$ cd RemoteDroidServer
bash: cd: RemoteDroidServer: No such file or directory
tuxusers@Tuxuser:~$ chmod +x RemoteDroidServer.jar
chmod: cannot access `RemoteDroidServer.jar': No such file or directory
tuxusers@Tuxuser:~$ java -jar RemoteDroidServer.jar
Error: Unable to access jarfile RemoteDroidServer.jar


I can't get this app to install in 12.04
[http://www.upubuntu.com/2011/12/use-your-android-powered-phone-tablet.html](http://www.upubuntu.com/2011/12/use-your-android-powered-phone-tablet.html)

Can you please help?
Thanks
Mike

---

### Post by Lisiano on 2012-05-21
The file is getting saved as 3weiT.2 so either unzip that, or add this option to wget 
```
-O RemoteDroidServer.zip
```
Note, wget considers anything given to it as a link, so if you tell it to download RemoteDroidServer.zip (Without -O ) it will think it's a link.

---

