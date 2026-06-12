---
title: "problems with adobe flash player"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-16
i downloaded the tar.gz file from the adobe website to my desktop,and extracted it.then right clicked it and clicked open,finally choosing run in terminal,this successfully installedit,and i could watch flash videos on the net.but,the next day,i discovered that though the videos were playing well,there wasn't any sound.then i googled for it,and finally installed some application titled"audio support for flash player 9"(i don't remember the exact title).then i restarted firefox and clicked on a youtube video,it started playing well with sound,but after sometime,it caused the firefox to terminate.i relaunched firefox,and this time the video wasn't played.
then i again installed the tar.gz package downloaded from the adobe website.
the videos start playing well,but in the midst of a video firefox gets terminated instantly.
how do i solve this problem?

---

### Post by dje on 2008-08-16
try running this in a terminal:
```
sudo apt-get install flashplugin-nonfree libflashsupport
```
do be aware that the adobe flash plugin for linux is buggy and does crash firefox from time to time

dje

---

### Post by Tom--d on 2008-08-16
> **dje said:**
> try running this in a terminal:
```
sudo apt-get install flashplugin-nonfree libflashsupport
```
do be aware that the adobe flash plugin for linux is buggy and does crash firefox from time to time

dje

From time to time :P
all the time. Thats flash player 9 with libflashsupport.

I would install the new flash player 10 rc 
Sooooo much better. Haven't crashed once! *touch wood*

Download it from here [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz)
Extract it. 
double click the install flash and run in terminal.
Just follow the instructions. 

:D

---

### Post by dje on 2008-08-16
> **Tom--d said:**
> From time to time :P
all the time. Thats flash player 9 with libflashsupport.

I would install the new flash player 10 rc 
Sooooo much better. Haven't crashed once! *touch wood*

Download it from here [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz)
Extract it. 
double click the install flash and run in terminal.
Just follow the instructions. 

:D

i can't recommend flash 10 every time ive tried it firefox just segfaults at startup :(

dje

---

### Post by ajgreeny on 2008-08-16
Flash 10rc has been great for me with no problems at all.  Download the tar.gz of the rc version of 10, extract it and then copy **libflashplayer.so** to **/usr.lib/flashplugin-nonfree**, having first renamed the current version as a named backup, in case v10 is a problem to you.  You will not then need the libflashsupport, so can remove that.

---

### Post by stonecoldjha on 2008-08-16
i uninstalled flashplugin non free from synaptic,and also the libflashsupport,and then reinstalled them.then i extracted the adobe flash player9 installer tar.gz,and then opened the extracted folder.then i ran the script in the terminal,the following was the output:


dirname: extra operand `(2)/flashplayer-installer'
Try `dirname --help' for more information.

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 9 will be installed in your home directory.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...





----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/sonu/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `/libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n): 

now what do those statements in the bold mean?is there anything wrong?well,videos are playing on the youtube,though i don't know at this point of time whether it would abruptly terminate firefox.

---

### Post by stonecoldjha on 2008-08-16
still firefox terminates in the middle of watching a video unpredictably.how can i fix this?isn't there a way to completely uninstall everything and then reinstall,or some other way?

---

### Post by stonecoldjha on 2008-08-16
how do i get rid of this?

---

### Post by ajgreeny on 2008-08-17
Have you tried my way from post #5.  It has worked for me for the last three updates of flash, 9 to 10b1, to 10b2, to 10rc, and all have worked fine.  I do not have the libflashsupport on my system.

Give it a try!

---

### Post by billgoldberg on 2008-08-17
I really advise you do ditch flash player 9 and espicially libflashsupport.

I have easy to follow instructions (copy/paste) on my blog to delete flash and install flash 10rc.

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

---

### Post by t0p on 2008-08-17
Why have you been installing flash from the adobe site?  A simple 
```
sudo apt-get install flashplugin-nonfree
```
will install flash 9 without at least some of the problems you are having.  Though as others have pointed out, maybe flash 10 willl be better. (Maybe not.)

**EDIT:** follow ajgreeny's advice, methinks.  Flash 10 seems to be working fine here anyway.

---

