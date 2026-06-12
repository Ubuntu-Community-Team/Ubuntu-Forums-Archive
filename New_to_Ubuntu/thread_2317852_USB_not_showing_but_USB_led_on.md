---
title: "USB not showing but USB led on"
date: 2016-03-20
forum: New to Ubuntu
---

### Post by Gatik_Kalra on 2016-03-20
Hi, I am new to ubuntu.

I am facing the following problem: I attached a USB to my machine and its led is ON but I can't see my USB. I did connect it to windows but no luck there as well. It would be great if someone could help :)

Thanks

---

### Post by oldrocker99 on 2016-03-20
Is the drive visible in a file manager? it may no show up on the desktop.

---

### Post by Gatik_Kalra on 2016-03-20
no it is not showing in file manager.

---

### Post by sudodus on 2016-03-20
Welcome to the Ubuntu Forums :-)

What kind of device is it - a USB pendrive (flash drive), or a USB hard disk drive, or some other kind of USB device?

If a storage device - is there data, that you want to recover?

---

### Post by Gatik_Kalra on 2016-03-20
Its a usb pendrive and there's nothing in it to recover.

---

### Post by sudodus on 2016-03-20
That makes it easier :-)

When the pendrive is inserted into the computer, please run the following command lines in a terminal window. Copy and paste the output of the commands to a reply. Put it within [noparse]```
tags
```[/noparse]

```
df
sudo parted -ls  # ... space minus ell ess
sudo lsblk -fm   # ell ess be ell key ...

```

This information will help us see if the pendrive is detected as a mass storage device, /dev/sdx, where x is the drive letter (a, b, c ...). If that is the case, there is a fair chance to recover it. If not detected, unplug and re-plug it and try again with those three command lines. If still not detected, there are problems.

---

### Post by sudodus on 2016-03-20
It is late here, and I will soon leave the keyboard for tonight, but I think there will be other people around, who can help you if necessary.

-o-

If the pendrive is not detected, I suggest that you

- try in other USB ports in the computer
- try in yet another computer (linux, Windows, MacOS, whatever is available)

If still no luck, I'm afraid the pendrive is damaged beyond repair with the tools that are available for normal people (like you and I).

-o-

If the pendrive is detected as a mass storage device, /dev/sdx, I suggest that you use ***mkusb's wipe menu*** to wipe the first megabyte and create a new partition table and file system. See this link

[mkusb's wipe menu](https://help.ubuntu.com/community/mkusb/wipe)

Maybe you get some useful tip from the following link

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by ajgreeny on 2016-03-20
What was the pendrive used for last time that it worked?

---

### Post by RobGoss on 2016-03-20
Hello and welcome, Is this a older machine were talking about sometimes it may not detect a USB device depending on hold old the machine. You might have to go into the BIO's and setup the correct boot options. I have a Toshiba laptop which came with Windows XP many moons ago that will not detect any USB devices. I can only install Ubuntu on it using my DVD drive.

---

