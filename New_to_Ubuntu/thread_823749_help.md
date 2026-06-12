---
title: "help"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by blake7 on 2008-06-09
hi does any one know what a live cd is??

i have a problem and someone said to use this cd to find lost data on my unbuntu 8.04 whaich load on to my laptop with wuki(in windows)

cheers

---

### Post by Cypher on 2008-06-09
The LiveCD is the version of Ubuntu that will load and run completley from the CD without messing up whats on your HD. You can use this to get a fully functional version of Linux and then recover anything you have on the HD's.

Grab your copy from [here]("http://www.ubuntu.com/getubuntu/download").

---

### Post by ibutho on 2008-06-09
A live cd is a version of Linux (or any OS for that matter) that can be run completely from a cd/dvd without installing it.

---

### Post by blake7 on 2008-06-09
thank you i do that now cheeers

---

### Post by blake7 on 2008-06-09
hi do u know how i get that data back??
when i load up the live cd will it show me the way??

---

### Post by ibutho on 2008-06-09
When you load up the live cd, you will be presented with a GNOME environment just like Ubuntu thats installed on the hard drive. When you go to the Places menu, there should be icons representing the hard drive partitions on your computer. You can click on those icons to mount the partitions and copy the data there to USB stick or maybe a USB hard drive.

---

### Post by ChildOfMana on 2008-06-09
When you load the Live CD it should automatically detect and mount your drives (make them readable and writable) so you can browse for your files in the same way you would if you were running the OS off the Hard Drive.

You could then copy your files to a USB Drive if you have one or even use the Brasero Disk Burning suite from within the live CD to copy them to CD/DVD.

Hope this helps :)

---

### Post by ChildOfMana on 2008-06-09
lol beat me to it ibutho

---

### Post by Duck2006 on 2008-06-09
Some reading on data recovery that may help.

[http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)

---

### Post by blake7 on 2008-06-09
thanks again 
i be so happy if i can sort all this out get my files back.
still down loading the iso
so hopefull not long now chheeers

---

### Post by hyper_ch on 2008-06-09
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by blake7 on 2008-06-09
hi sorry to be so stupid
but i down loadeed ubuntu-8.04-desktop-i386  i also down loaded infra recorder

what do i do now

cheers

---

### Post by blake7 on 2008-06-09
hi sorry to be so stupid
but i down loadeed ubuntu-8.04-desktop-i386 i also down loaded infra recorder

what do i do now

cheers

---

### Post by ibutho on 2008-06-09
You have o burn the iso to a cd. Make sure you choose to burn it as a cd image instead of a data disc.

---

### Post by blake7 on 2008-06-12
how do i save my documant with live cd

---

### Post by Cypher on 2008-06-12
You'll want to use some external storage, a USB flash drive, an external HD or something. Once you plug that external drive in you should see it appear on the desktop. You should then be able to copy your files from the HD to it.

---

### Post by issih on 2008-06-12
The process goes something like this:

1) insert ubuntu live cd into cd drive.
2) reboot computer.
3) enter bios and ensure cd drive is set to boot ahead of hard drive.

Now let the computer boot from the cd, and select the option to try ubuntu without changing your system,

Eventually you will get an ubuntu desktop (it will take a while) which is running entirely from the cd drive.

You will then need to 'mount' the hard drive you want to rescue data from. I noticed that you said you are using wubi, so this guide will be handy, it tells you how to mount the wubi hard drive.

[https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)

At this point you can copy the data from the mounted wubi drive. You could paste it onto a usb key, or you could probably just drop it into a folder in the mounted windows drive somewhere. You should then be able to get at the files from within windows.

Hope thats useful

---

