---
title: "Development server and IDE"
date: 2008-02-23
forum: Programming Talk
---

### Post by codeking on 2008-02-23
So, I've decided to start doing all my PHP on linux.  And with PHP comes a need for a development server.  And I don't want to install Ubuntu Server (It won't download, internet isn't working well).  Is there a simpler way to do this?  On windows I just had Apache set up with MySQL and PHP.  Is there a simple way to do that with Ubuntu?

Also, what PHP+HTML IDE do you recommend.  Built in FTP is a must, WYSIWYG preferred

---

### Post by cb951303 on 2008-02-23
```
sudo tasksel install lamp-server
```
that's all you need to do to install apache+mysql+php

Eventho it's not WYSIWYG, eclipse + pdt is very good. It has a FTP plug-in too ;)

---

### Post by slavik on 2008-02-24
there is also bluefish and aptana

---

### Post by lnostdal on 2008-02-24
about built in ftp .. 

i use curlftpfs(#1) for this; it's great..  you get to mount ftp-connections as a regular disk

say you're working on a website that is hosted on someserver.com .. it goes something like this:

```

cd ~
mkdir someserver.com
curlftpfs ftp://username:password@someserver.com/ someserver.com
cd someserver.com
ls

```

..note that this makes FTP "built into" all programs .. you can browse using nautilus .. you can open and edit files on the remote server using any program

another option, if the server supports it - is to use sshfs .. this is in my opinion much better than ftp because data (usernames/passwords etc.) is encrypted .. but not all hosts/servers support this of course


#1: i had a problem with curlftpfs [https://bugs.launchpad.net/ubuntu/gutsy/+source/curl/+bug/150277](https://bugs.launchpad.net/ubuntu/gutsy/+source/curl/+bug/150277) .. they have made a fix but i'm not sure it is up yet .. i have solved this "manually" - let me know if you encounter this problem and i can post a working (temporary) solution

---

### Post by cb951303 on 2008-02-24
BTW, the official FTP plug-in of eclipse is in the "Remote Systems" package which is accessible via eclipse update tool -> discovery site

---

### Post by xlinuks on 2008-02-24
For some time Sun is trying to make NetBeans an IDE for most langs, PHP is supported AFAIK. I only tested JSP and worked fine, not sure whether PHP works as fine as JSP.
Easy web site creation with NetBeans adding Web Components with Drag and Drop:
[http://java.sun.com/developer/onlineTraining/tools/netbeans/](http://java.sun.com/developer/onlineTraining/tools/netbeans/)

quote from that page: "Additionally, you are not stuck with JSP pages. You may, if you like, develop in PHP instead. For this article, though, we'll stick with JSP pages"

---

