---
title: "Wireless connection"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Murphae on 2012-05-15
Brand new Noob.  No wireless connection.  12.04 just installed, got into terminal and did lspci and got
dave@ubuntu:~$ 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

read thru all previous fixes that worked for others and no luck.  Know  guys like me are a PIA on stuff like this, but any help would be appreciated!

---

### Post by kc1di on 2012-05-15
Hi Welcome to Ubuntu and Linux,

I have that same card it will work fine.
but you have to install a driver for it. 
you'll need a LAN (Hardwire connection for a moment)

Then go to System tools and click on additional drivers.
it should offer you Broadcom-sta driver. install that reboot
and your wireless should be working.

---

### Post by Murphae on 2012-05-15
Thanks, Dave.  I did this once before and it still didn't work.  Try it again?

---

### Post by TBABill on 2012-05-15
+1 but if you have already installed it and it's not working properly, you can reinstall it via terminal and that sometimes helps. Do so by ```
sudo apt-get install --reinstall bcmwl-kernel-source
```
 
Note: If you ever do an install you can actually activate it in the live session without ever connecting via ethernet. Then once you set it up in the live session, it'll be established and working in the new nistall without ever needing an ethernet connection to download the driver. You just activate it via additional drivers (while booted from the LiveDVD or CD), then when it finishes don't restart. Instead just ```
sudo modprobe wl
```The wireless will work a few moments later, then you proceed with the install and automagically it'll work in the fresh install.

---

### Post by Murphae on 2012-05-15
Says that my driver is active and currently in use.  Still unable to get wireless connection.

---

### Post by kc1di on 2012-05-15
> **Murphae said:**
> Says that my driver is active and currently in use.  Still unable to get wireless connection.

What type of laptop do you have? 
mine's a dell and there is a hard wire button (I'm not at that machine right now) but I think it like the 3 Fkey in it will turn off the wireless card. and give no indication on ubuntu that it's off.  so worth checking.

---

### Post by kc1di on 2012-05-15
you may also want to try this.

```
 sudo apt-get install rfkill
```
```
rfkill unblock all
```

---

### Post by Murphae on 2012-05-15
Have a Dell Studio laptop.  Wifi button is lit up.  Just tried redoing the reinstall and got a warning   no support for locale: en_US.utf8

did sudo modprobe wl and no connection

---

### Post by Murphae on 2012-05-15
also did rfkill suggestion

---

### Post by kc1di on 2012-05-15
> **Murphae said:**
> also did rfkill suggestion

does network center show your router? offer any connections?

---

### Post by Murphae on 2012-05-15
AHA!!!  Tried all of this again and I have the connection.  You guys are awesome.  Thanks for the help and I'm SURE I'll be back!

Dave

---

### Post by Hadaka on 2012-05-15
Here is an excellent post that should help you out.
[http://ubuntuforums.org/showthread.php?t=1966631](http://ubuntuforums.org/showthread.php?t=1966631)

hope this helps

---

### Post by GregA on 2012-05-15
See this:    [http://askubuntu.com/questions/99651/apt-get-warning-no-support-for-locale-en-us-utf8](http://askubuntu.com/questions/99651/apt-get-warning-no-support-for-locale-en-us-utf8)

BTW, did you verfiy the md5 checksum (to ensure no error download)?

---

### Post by kc1di on 2012-05-15
> **Murphae said:**
> AHA!!!  Tried all of this again and I have the connection.  You guys are awesome.  Thanks for the help and I'm SURE I'll be back!

Dave

Glad you got it going :)

---

### Post by Hadaka on 2012-05-15
this is an excellent post.it may help clean your driver
issue up. good luck



[http://ubuntuforums.org/showthread.php?t=1966631](http://ubuntuforums.org/showthread.php?t=1966631)

---

### Post by Hadaka on 2012-05-15
oops..i posted while you were posting..didnt see you got it going.
GREAT!...mark this thread solved to possibly help others.

---

