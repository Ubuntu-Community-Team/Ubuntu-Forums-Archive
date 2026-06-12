---
title: "setting up wireless for BCM4306"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Hector40 on 2008-04-29
Hi,
  I a planning on using the directions found at [linuxwireless.org]("http://linuxwireless.org/en/users/Drivers/b43") to install the firmware for my wireless card.

   Unfortunately I don't know enough about Linux to know which instructions to follow.:confused:  My best guess from what I have been able to figure out is I would use the b43 driver for Linux-2.6.24, firmware 4.80.53.0 and firmware extractor b43-fwcutter v. 011.

  Any help in pointing me in the right direction would be appreciated.

---

### Post by agim on 2008-04-29
I would avoid fwcutter. I have never made it work.

Here are the steps that I followed.

The only difference is instead of using this command

ndiswrapper -i bcmwl5.inf

you will have to use your own driver, not bcmwl5.inf.

Good luck

Edit: Sorry, here is the link:
[http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy)

---

### Post by agim on 2008-04-29
Apparently others have found this to work.

check if it shows up in System->Administration->Hardware Manager if so then just enable it, then configure the network settings in System->Administration->Network

thats a quote from this post:[http://ubuntuforums.org/showthread.php?p=4835039#post4835039](http://ubuntuforums.org/showthread.php?p=4835039#post4835039)

hope it helps

---

### Post by Hector40 on 2008-04-29
It does not show up in the Hardware Manager.  I am pretty sure that I need to install the firmware.

I want to try out what I mentioned in my  original post but I need to know what version is the Linux kernel in Ubuntu 8.04.  Also how do I find out which driver to use from b43, b43legacy or bcm43xx drivers?

---

### Post by Hector40 on 2008-04-29
How do I delete the files in the firmware directory?

---

### Post by sam_delta on 2008-04-29
try installing b43-fwcutter using aptitude in the terminal, it will automaticly ask to fetch the firmware and it will set it up/

```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```

make sure you answer Y, for yes when prompted if you want to fetch the firmware

restart pc,and go into system/administration/hardware drivers and enable broadcom

tell us how it goes
sam

---

### Post by Hector40 on 2008-04-29
> go into system/administration/hardware drivers and enable broadcom

I installed b43-fwcutter and had it fetch the firmware. I then restarted the computer.  But when I go to 'Hardware Drivers' nothing shows up. The window is blank.  It doesn't list any components.

---

### Post by Hector40 on 2008-04-29
I don't know why nothing shows in the 'Hardware Drivers' window but it is working.  I went to 'Network Manager' on the top bar and I saw that I had a signal. I then entered the network password and it is working now.

Thanks for everyones help! :)

---

### Post by sam_delta on 2008-04-29
no problem :) enjoy ubuntu

---

