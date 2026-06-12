---
title: "Having trouble installing Unrevoked 3 on 14.04"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by courtneyking1990 on 2014-05-14
I have this thread open in Installs too, but I think it's better here since I am a beginner and this room gets more hits. I wanted to move and delete the old post but I don't see a way to do that. BTW, I'm on Ubuntu 14.04

I'm trying to use Unrevoked 3 to root my HTC EVO 4G phone. I've never been able to start the rooting process since Unrevoked doesn't open. I've been googling around and these are the steps I've found that I've been using:

[COLOR=#000000][FONT=verdana]1. Download latest unrevoked for linux[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]2. extract to desktop[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]3. set phone settings to: USB Charge only [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana](menu>settings>connect to pc>default connection type>charge only) [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]4. enable phone settings to USB debugging (menu>settings>applications>development>USB debugging-check)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]5. connect phone to computer[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]6. open a terminal[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]7. type in terminal: cd /home/username/Desktop (hit enter)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana](Use your own "username" above. The prompt in terminal will begin with username@computername.)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]8. type in terminal: chmod +x reflash (hit enter)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]9.type in terminal: sudo ./reflash (hit enter)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana](it will ask for your administrative password, enter)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]10. Wait for the rooting process to finish.

After step 9, I always get this error and I don't get the prompt to put in my password:
[/FONT][/COLOR]./reflash: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

I tried to install whatever the lib in the error is but I get told it doesn't exist or whatever. I'm at a lost for what to do. I expected this to be a simple process and the frustrates the hell out of me.

---

### Post by HiImTye on 2014-05-14
libgtk-x11-2.0.so.0 is part of the package 'libgtk2.0-0'
the file list is [here](http://packages.ubuntu.com/trusty/amd64/libgtk2.0-0/filelist)

---

### Post by deadflowr on 2014-05-14
Thread Closed
Dupe here
[http://ubuntuforums.org/showthread.php?t=2224076](http://ubuntuforums.org/showthread.php?t=2224076)

For the record, if you don't know where to put a thread, hit the report post button at the bottom of the post and state so, and we will look into where it can best be put.

---

