---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-08-08
forum: Philippine Team
---

### Post by teerapon.sookhom on 2014-08-08
I found a problem with this. someone help me


root@indigoblue-desktop:/home/indigoblue# sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up sandboxgamemaker (2.7.1+dfsg-1) ...
Cleaned old data
--2014-08-08 11:39:08--  [http://sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip](http://sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip)
Resolving sandboxgamemaker.com (sandboxgamemaker.com)... 69.163.152.135
Connecting to sandboxgamemaker.com (sandboxgamemaker.com)|69.163.152.135|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip](http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip) [following]
--2014-08-08 11:39:10--  [http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip](http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip)
Resolving [www.sandboxgamemaker.com](www.sandboxgamemaker.com) ([www.sandboxgamemaker.com](www.sandboxgamemaker.com))... 69.163.152.135
Connecting to [www.sandboxgamemaker.com](www.sandboxgamemaker.com) ([www.sandboxgamemaker.com)|69.163.152.135|:80](www.sandboxgamemaker.com)|69.163.152.135|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2014-08-08 11:39:25 ERROR 404: Not Found.

dpkg: error processing sandboxgamemaker (--configure):
 subprocess installed post-installation script returned error exit status 8
Errors were encountered while processing:
 sandboxgamemaker
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ibjsb4 on 2014-08-08
Please post the output of
```
cat /etc/apt/sources.list
```
and
```
ls /etc/apt/sources.list.d/*.list
```

---

