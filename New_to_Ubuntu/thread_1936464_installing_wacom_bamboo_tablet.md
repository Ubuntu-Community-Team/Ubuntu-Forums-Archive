---
title: "installing wacom bamboo tablet"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by twocorners on 2012-03-06
):P i'm getting a wacom ctl-460 tablet in a few days and i'll be using it in ubuntu 10.04. i have 2 questions :

has anyone tried this method of installation? is it dependable? >> [https://www.linux.com/learn/tutorials/347367-using-a-bamboo-tablet-with-ubuntu-1004](https://www.linux.com/learn/tutorials/347367-using-a-bamboo-tablet-with-ubuntu-1004)

will any windows pop up once the tablet is in use? my computer is shared with other people and it would be nice if they weren't aware of a tablet being used on it, since that would prevent me from getting to use it at all. so how hard would it be to hide the evidence of the tablet, so to speak?

thanks in advance!

---

### Post by winh8r on 2012-03-06
If you go to the Ubuntu Software Centre and enter "wacom" there is a package named 

```
xserver-xorg-input-wacom
```

with the drivers for wacom devices.

I don't quite understand the second part of your question though, there is nothing "wrong" with using a wacom tablet, why this would cause you to lose access to the computer is beyond me.

Besides if anyone has physical access to a computer, which they do in your case , then they can find out anything they want about your account and what is in it simply by running a Live CD and browsing through your files.

Probably better to be up front and honest with the other people concerned or buy your own computer and don't share it.

---

### Post by Favux on 2012-03-06
Hi twocorners,

The Wacom X driver is installed by default in Ubuntu.  It's called xf86-input-wacom and it's the main thing the xserver-xorg-input-wacom package contains.

For your Bamboo Pen (CTL-460) you will need to update the wacom.ko (USB kernel driver/module) that comes with Lucid's 2.6.32 kernel to get a wacom.ko that supports your model of tablet.  Instructions for compiling input-wacom to get a newer wacom.ko are on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

None of this results in any obvious trace that a tablet is being used.  When it is plugged into a USB port you can see it in the output of the *xinput list* command in a terminal.  And the hotplugging events will show in the Xorg.0.log in /var/log.

---

### Post by twocorners on 2012-03-28
> **Favux said:**
> Hi twocorners,

The Wacom X driver is installed by default in Ubuntu.  It's called xf86-input-wacom and it's the main thing the xserver-xorg-input-wacom package contains.

For your Bamboo Pen (CTL-460) you will need to update the wacom.ko (USB kernel driver/module) that comes with Lucid's 2.6.32 kernel to get a wacom.ko that supports your model of tablet.  Instructions for compiling input-wacom to get a newer wacom.ko are on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

Well, everything went fine, until I restarted and tried the tablet out. After typing "lsmod | grep wacom" nothing happens. What am I missing?  =S

---

