---
title: "Having problems with wifi &gt;&lt;"
date: 2013-05-28
forum: New to Ubuntu
---

### Post by mordecaiisdispleased on 2013-05-28
I put Ubuntu 13.04 on my Dell Inspiron 1420 this morning. Previously, I had windows vista and my wireless internet worked.  Now it does not. I have never used ubuntu of any kind before, and am not really sure if I perhaps am missing the driver for my wireless card, but if someone could point me in the right direction, I'd be ever so grateful. Also, I'd be happy to post any necessary additional information.

---

### Post by chili555 on 2013-05-28
Awesome! Welcome to Ubuntu. We have a lot of fun here and we're happy you are joining us.

First, let's gather some information about your wireless card so we know what driver you need and how to install it. We are going to use the terminal because we can get the information quickly, easily and accurately. Please open the terminal with the shortcut Ctrl+Alt+t and type in:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Post the result and we'll proceed.

---

### Post by mordecaiisdispleased on 2013-05-29
I typed in what you said to into the terminal and below are results:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [
14e4:4311] (rev 01)

By the way, thanks for helping.  This is a tough, unforgiving world I've jumped into 0.0

---

### Post by WaltL on 2013-05-29
There is an askubuntu on installation of Broadcom wireless drivers which has some detailed information that might be helpful to you.
  [http://askubuntu.com/questions/55868/how-to-install-a-broadcom-wireless-driver](http://askubuntu.com/questions/55868/how-to-install-a-broadcom-wireless-driver)

---

### Post by chili555 on 2013-05-29
> **mordecaiisdispleased said:**
> I typed in what you said to into the terminal and below are results:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [
14e4:4311] (rev 01)

By the way, thanks for helping.  This is a tough, unforgiving world I've jumped into 0.0Please get a temporary wired ethernet connection and open the terminal again and do:```
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and enjoy your wireless!

There are many of us here on this forum that are anxious to help when you have any other problems.

---

### Post by mordecaiisdispleased on 2013-05-29
I did as instructed in your response, this is what happened:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree

Any idea what I did wrong, and how I can make this work?

---

### Post by chili555 on 2013-05-29
> E: Unable to locate package linux-firmware-nonfreeIs this the first time you've tried any updates or installations? Please try:```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```Now does it work?

---

### Post by mordecaiisdispleased on 2013-05-29
BOOGNISH BE PRAISED!!! It works! Thanks you oh so very much, you've made my day! If there's anything I can ever do for you, my email address is [email]1aa1340171@gmail.com[/email].

---

### Post by chili555 on 2013-05-29
I'm very glad it's working! Enjoy Ubuntu!

---

### Post by 3rdalbum on 2013-05-29
You might want to edit your post and remove your E-mail address, or spammers will find it.

Ubuntu is not tough and unforgiving. It's just very different. With two quick lines in the terminal Ubuntu downloaded and installed a driver for you, and there are also GUI ways of accomplishing the same thing. Ubuntu is easy, but different.

---

### Post by chili555 on 2013-05-29
>  there are also GUI ways of accomplishing the same thing. Ubuntu is easy, but different. Indeed.

I personally prefer the terminal because it's old-school like me; because it's generally quick and easy and because it usually gives meaningful feedback whether the command succeeds or fails. The feedback and Google often provide a solution if it failed.

I certainly could have asked that mordecaiisdispleased open Software Center and install linux-firmware-nonfree with the same result.

---

