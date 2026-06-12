---
title: "iCall"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-12-25
I have been trying to install icall using these commands see top post
[http://ubuntuforums.org/showthread.php?t=1493306]("http://ubuntuforums.org/showthread.php?t=1493306")
 I get these errors

```
cmcanulty@HPTech:~$ sudo apt-get install libqt4-core libqt4-gui libogg0 libtheora0
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libogg0 is already the newest version.
libtheora0 is already the newest version.
libqt4-gui is already the newest version.
libqt4-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cmcanulty@HPTech:~$ wget "http://www.icall.com/desktop/download/?version=beta&os=linux"
--2012-12-25 16:15:05--  http://www.icall.com/desktop/download/?version=beta&os=linux
Resolving www.icall.com (www.icall.com)... 74.112.133.183
Connecting to www.icall.com (www.icall.com)|74.112.133.183|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://www.icall.com/error/404.php?h=www.icall.com&p=/desktop/download/?version=beta&os=linux&q=version=beta&os=linux&r= [following]
--2012-12-25 16:15:05--  http://www.icall.com/error/404.php?h=www.icall.com&p=/desktop/download/?version=beta&os=linux&q=version=beta&os=linux&r=
Reusing existing connection to www.icall.com:80.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://www.icall.com/404?q=?version=beta [following]
--2012-12-25 16:15:05--  http://www.icall.com/404?q=?version=beta
Reusing existing connection to www.icall.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html?version=beta&os=linux.4'

    [  <=>                                  ] 25,924       117K/s   in 0.2s    

2012-12-25 16:15:06 (117 KB/s) - `index.html?version=beta&os=linux.4' saved [25924]

cmcanulty@HPTech:~$ tar zxvf iCall-7.0-beta.tar.gz
tar (child): iCall-7.0-beta.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
cmcanulty@HPTech:~$
``` 

yet it looks installed see the screenshot and I have it marked as executable. I have searched quite a bit and find nothing

---

### Post by MishaX2 on 2012-12-25
1. Goto [http://www.icall.com/](http://www.icall.com/) and download the client for linux. (Direct link: [http://client.icall.com/bin/iCall-linux32.run](http://client.icall.com/bin/iCall-linux32.run))
2. Open a terminal and go to the directory where you downloaded the file to
3. Type the following in the terminal: > chmod +x iCall-linux32.run4. Type the following in the terminal: > ./iCall-linux32.run5. Follow the instructions on the screen

Let me know if this works for you.

Good luck!

---

### Post by cmcanulty on 2012-12-26
still get no app running could it be because I am running 64bit?


```
cmcanulty@HPTech:~$ chmod +x iCall-linux32.run 
cmcanulty@HPTech:~$ ./iCall-linux32.run 
cmcanulty@HPTech:~$ icall
No command 'icall' found, did you mean:
 Command 'ical' from package 'itools' (universe)
 Command 'icalc' from package 'radiance' (universe)
icall: command not found
cmcanulty@HPTech:~$ 

```

---

