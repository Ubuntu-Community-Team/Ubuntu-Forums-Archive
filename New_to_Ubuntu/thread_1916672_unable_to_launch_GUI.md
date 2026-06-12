---
title: "unable to launch GUI"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by dfa5000 on 2012-01-28
Greetings all. Thanks in advance for your help.

I am a novice Linux user trying to get started with Ubuntu 11.10 but having trouble. I have searched documentation and other threads but have been unable to figure this out on my own.

I installed version 11.10 using an ISO image burned to CD and verified by md5sum. Initially I experienced the black screen issue so I had to use the parameter "nomodeset" to boot succesfully. The graphical installation completed and I was prompted to reboot.

The problem is that now I can access GRUB and use the parameter "nomodeset" to boot, but the desktop/graphical interface does not load. I have access to the terminal to log in and I have tried the command "startx" only to receive a number of messages including "Fatal server error: no screens found" (I am unable to copy and paste because I am currently using a separate computer for internet access).

I have entered the command "lspci | grep VGA" which returns the message "00:01.0 VGA compatible controller: ATI Technologies Inc Device 9647".

Please offer any suggestions you can. Thanks.

---

### Post by drs305 on 2012-01-28
dfa5000

Welcome to Ubuntu and the Ubuntu Forums.  :-)

In the terminal try this to start the GUI:
```
sudo service lightdm start
```

If that works, try installing your video driver by clicking the icon in the upper left (DASH Home) and typing Additional Drivers.

I'm no graphics expert so if that doesn't help you'll have to wait for another repsonse.  Good luck.

---

### Post by bogan on 2012-01-28
Hi!, **dfa5000**,

Are you able to boot correctly from the CD?

From the tty Terminal try:```
 sudo service lightdm start 
```  instead of 'StartX'

[ *If you were using an earlier version it would be 'gdm' instead of 'lightdm'.*]

Chao!, **bogan**.

Edit: drs305 beat me to it, just. Leave it to you.

---

### Post by dfa5000 on 2012-01-28
> **bogan said:**
> Hi!, **dfa5000**,

Are you able to boot correctly from the CD?

From the tty Terminal try:```
 sudo service lightdm start 
```  instead of 'StartX'

[ *If you were using an earlier version it would be 'gdm' instead of 'lightdm'.*]

Chao!, **bogan**.

Edit: drs305 beat me to it, just. Leave it to you.
Thank you drs305 and bogan.

Entering the command "sudo service lightdm start" returns the message "lightdm start/running, process 6825" and takes me to a screen which displays a number of messages (it appears I can also access this screen by typing Alt+F7).

The messages include a number of lines for starting/stopping processes, with [fail] next to "Stopping automatic crash report generation". I also see listed "Starting Userspace bootsplash" and "Stopping Userspace bootsplash", although both have [OK] next to them.

I am unable to enter commands on this screen, and I am unsure what to try next. Any suggestions are appreciated.

EDIT: If I "Try" Ubuntu using the CD, the command "sudo service lightdm start" returns the message "lightdm  start/running, process 3188" and takes me to the same screen but this time I notice the following message "Starting load fallback graphics devices [fail]". Hope this helps.

---

### Post by bogan on 2012-01-28
Hi!, **dfa5000,**

drs305 Posted:> I'm no graphics expert so if that doesn't help you'll have to wait for another response.   The same applies to me, I do not know enough about ATI graphics, except I think you need a suitable driver.

Hope the following may assist:

Have you tried booting to the recovery safe mode.?

When you get to that hung screen - the same as with Crtl+Alt+F7, that's the Graphics screen normally - Pressing:  Crtl+Alt+F1, or Crtl+Alt+F2, should give you another hung list or a tty2 Text Terminal login screen.You could also try adding ' --verbose text' to the grubmenu entry instead of 'quiet splash' which may give you a better idea of where the hang up is.

Chao!, **bogan**.

---

### Post by dfa5000 on 2012-01-29
Thank you bogan. I am able to boot in recovery mode although still without graphical interface. I will try your suggestion and update this thread as I make progress.

---

### Post by dfa5000 on 2012-01-31
Adding the boot parameter "--verbose text" does not reveal anything obvious as far as I can tell. Taking a chance I downloaded and tried to install fglrx but ran into issues with that as well.

I realize the biggest issue is my low skill level with GNU/Linux so I will have to do more research. I was just hoping to use the familiar graphical interface (as a MS escapee) to smooth the learning curve.

Thanks again for any help you can offer.

---

### Post by dfa5000 on 2012-02-01
You were correct that I simply needed an appropriate driver, bogan. This issue was resolved after I took the following steps.

1. Reviewed /var/log/ Xorg.0.log for errors
2. Installed the graphics driver using this HOWTO [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
3. In my case I had to install additional packages such as debhelper and dh-modaliases that I found referenced elsewhere
4. I found similar steps detailed in this thread [http://ubuntuforums.org/showthread.php?t=1796653&page=2](http://ubuntuforums.org/showthread.php?t=1796653&page=2)
5. In my search I also found a helpful Unofficial Wiki for the AMD Linux driver

---

