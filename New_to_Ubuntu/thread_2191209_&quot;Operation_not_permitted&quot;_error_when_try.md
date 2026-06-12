---
title: "&quot;Operation not permitted&quot; error when trying to extract files"
date: 2013-12-01
forum: New to Ubuntu
---

### Post by goghvv on 2013-12-01
Hi.
I'm new to ubuntu (just installed a fresh copy of Ubuntu today), and have very little experience with ubuntu and linux in general.
I'm trying to extract some files I downloaded from here:
[http://www.eclipse.org/kepler/](http://www.eclipse.org/kepler/)

For some reason, when I try to extract it I get this error saying:
"An error occurred while extracting files.
Error setting owner: operation not permitted."

this is my ubuntu version: 
Linux ubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Any help would be greatly appreciated.
thanks in advance.

---

### Post by The Cog on 2013-12-01
Eclipse is in the repositories. I would recommend that you use the software centre to install it, as it will have been packaged up to also fetch all the other bits and bobs that it depends on, and all the compatibility issues will have been sorted out. Installing downloads from a web site may not be so easy.

However, if you want to install your download, we need more info to work out what's going wrong. How are you trying to extract the download, and where to? If you are doing it by command line, please post the full command and error message for us to look at.

---

### Post by jdeca57 on 2013-12-01
Probably you don't have write permissions - and you need to extract with sudo. But of course I don't know what you downloaded, in what directory, and how you extracted the files... or was it part of an install?

---

### Post by goghvv on 2013-12-01
Thank you both for the help.
I just updated my Ubuntu (since it also didn't let me install anything - it couldn't find any package), and it fixed it.

It's nice to see such a great Ubuntu users community, hope to blend in.
Cheers.

---

### Post by jimmyh1972 on 2013-12-03
[COLOR=#000000]Probably you downloaded an .exe file for windows

linux uses diffrent packages called .deb

you can try sudo apt-get install eclipse

or to download a .deb package double click it and it will open software center to install it automatically[/COLOR]

---

### Post by jimmyh1972 on 2013-12-03
#linux ubuntu
because there are also rpm's but thats another story:-)

---

### Post by monkeybrain20122 on 2013-12-03
This is a file roller bug [https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1238266](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1238266)
Since a fix has been released for quite some times (I experienced this when saucy was released but it was fixed shortly afterwards) you should update you system 
```
sudo apt-get update
sudo apt-get upgrade
```

If it still does not work for some strange reason you can always use the command line. Say you download it to Downloads
```
cd Downloads 
tar -zxvf eclipse-standard-kepler-SR1-linux-gtk-x86_64.tar.gz
```

**DON'T USE SUDO**. you don't have to be root to run or extract eclipse

Eclipse doesn't need installation, just open the extracted folder and click the binary eclipse. You need to have java installed though.

---

### Post by monkeybrain20122 on 2013-12-03
> **The Cog said:**
> Eclipse is in the repositories. I would recommend that you use the software centre to install it, as it will have been packaged up to also fetch all the other bits and bobs that it depends on, and all the compatibility issues will have been sorted out. Installing downloads from a web site may not be so easy.


I wouldn't do that. The version in the repo is old and it installs a whole bunch of dependencies. It is a lot cleaner to just get it from eclipse and run it off your home.

---

