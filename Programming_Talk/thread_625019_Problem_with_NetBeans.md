---
title: "Problem with NetBeans"
date: 2007-11-27
forum: Programming Talk
---

### Post by eUsha on 2007-11-27
Hi,

I need Help with Netbeans.

I've installed netbeans on my Ubuntu 7.10 system. But when I start it, I get a splash screen type window filled gray with color with a title  "License Agreement" . There is nothing else in the window that I can click or read. The only things I can interact with are the window controls.
 
I'm running:
64 bit Ubuntu on 64 bit AMD processor.( in case it's important )

---

### Post by ry0t on 2007-11-30
I have this problem as well.  I installed it through Synaptic Package Manager with all the dependencies.

---

### Post by ry0t on 2007-11-30
I logged in as root and the License Agreement worked and I could start Netbeans.  I uninstalled it now I'm trying to install it manually and not with the package manager.  We'll see how this goes...

---

### Post by ry0t on 2007-11-30
So now I installed it by downloading the bin from the netbeans website.

I did this in a terminal as root from my account (su)

/usr/local#  chmod +x netbeans-5_5_1-linux.bin 
/usr/local# ./netbeans-5_5_1-linux.bin 

// program installs...

Now the program starts up, but doesn't display any content in the window - just a grayed out screen with "NetBeans IDE 5.5.1" at the top of the window in the title bar.

:confused:

---

### Post by eUsha on 2007-12-07
HI:)

Just a minute ago I changed my desktop setting.

right click on desktop>Change Desktop Background>Visual Effects:
My settings were previously on Normal so I changed them to "None."

After this when I tried starting netBeans it worked fine for me.

---

### Post by tyoc on 2007-12-07
I have full effects, and with no problems open NB, but yes, it is an issue that sometimes the window doesnt display when effect are going...

A way or a workaround for solve the problem I have is press CTRL+"+" or CTRL+"-" that will "refresh" the window manager and hopefully you will see the content of the window now (also note that sometimes this workaroud can mess more the window [like hide the window border, thus the icons for maximize/restore, minimize and exit]).

---

### Post by glok_twen on 2007-12-08
these may provide some help:

[http://ubuntuforums.org/showthread.php?t=469396](http://ubuntuforums.org/showthread.php?t=469396)

[http://govath.wordpress.com/2007/10/22/netbeans-55-problem-with-beryl-on-ubuntu/](http://govath.wordpress.com/2007/10/22/netbeans-55-problem-with-beryl-on-ubuntu/)

---

