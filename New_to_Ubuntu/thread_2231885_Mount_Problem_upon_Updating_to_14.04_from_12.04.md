---
title: "Mount Problem upon Updating to 14.04 from 12.04"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by Pao_Rodulfo on 2014-06-28
Help please. I have just updated my ubuntu 12.04 to 14.04 and the update manager has prompted me to restart my computer to finish the update. However, after rebooting I get a black screen MS-DOS like screen which says:

```

mount: mounting /dev/loop0 on /root failed: Invalid argument 
mount: mounting /dev on /root/dev failed: No such file or directory 
mount: mounting on /sys on /root/sys failed: No  such file or directory 
mount: mounting on /proc on /root/proc failed: No such file or directory 
Target filesystem doesn/t have requested /sbin/init. 
No init found. Try passing init= bootarg. 

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash) 
Enter 'help' for a list of built-in commands.

(initramfs)

```

I have also attached the picture of the actual screen.


I'd be very glad if someone could help me fix this :( 

P.S. I'm somehow new in using ubuntu. So please speak to me as if I am a child in the first grade :)

[ATTACH=CONFIG]254310[/ATTACH]

---

### Post by kansasnoob on 2014-06-28
The first thing I'd do is boot an Ubuntu live DVD or USB and try running a disk check on the Ubuntu partition(s) using Gparted:

[ATTACH=CONFIG]254312[/ATTACH]

Alternatively you may do basically the same thing from the CLI using:

```
sudo fsck /dev/sd**[COLOR="#FF0000"]xy[/COLOR]**
```

Where the **[COLOR="#FF0000"]x[/COLOR]** is the drive designation and the **[COLOR="#FF0000"]y[/COLOR]** is the partition designation.

---

### Post by Pao_Rodulfo on 2014-06-29
Hi. I have tried the first method you suggested, the one using GParted using a live USB. The process of "check" was completed but when I tried to boot to Ubuntu again, I still get the same screen. I opt to try the second method with the sudo code but I do not know what to exactly put in "x" and "y". I'm supposed to attach the screenshot but apparently the .png files were corrupted probably because it was from the live USB. However, as far as I can remember, my partition allocated for the Ubuntu is /dev/sda5 or something like that. 

Are there any other ways to solve my problem? I'm sort of afraid to reinstall the whole OS since the last time I did that, my laptop had MBR problems upon booting. I hope you can help me with this. Thank you!

---

### Post by newb85 on 2014-06-29
I'm not very experienced with this, but it sounds like it could be related to your fstab.  From the Live Disc, navigate to and open the file /etc/fstab on the Hard Drive.  Copy and paste the contents here.

---

### Post by Pao_Rodulfo on 2014-06-29
I have just realized the code part. haha. is it right that I have typed: sudo fsck /dev/sda5? I tried it though and still no good. Attached is the picture of the result. Cheers!





[ATTACH=CONFIG]254329[/ATTACH]

---

### Post by Pao_Rodulfo on 2014-06-29
Hi! Here's what it said:

overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by netgooroo on 2014-06-29
It seems to me that your HDD is not being seen for whatever reason. 

Can you tell us a bit more about your system and is Linux your only OS that you have installed on the hard drive? 

Thanks!

---

### Post by Pao_Rodulfo on 2014-06-29
> **netgooroo said:**
> It seems to me that your HDD is not being seen for whatever reason. 

Can you tell us a bit more about your system and is Linux your only OS that you have installed on the hard drive? 

Thanks!

Hello. I also Windows 7 installed alongside Ubuntu. My PC is a Dell Vostro 1014n with 320gb HDD running on Intel Core Duo. I have three major partitions: 100gb for the Default Filesystem of Windows (C:/), 200gb for my own files (D:/), and 20gb/15gb (I can't Exactly remember but in windows, I have a drive named F:/ which has the wubi and it says 15gb) allocated for Ubuntu. I suppose I also have a 100MB partition for the System Reserve of Win7. Help please.. Thanks!

---

### Post by yancek on 2014-06-29
>  I have a drive named F:/ which has the wubi and it says 15gb) allocated for Ubuntu.

Does that mean you had Ubuntu 12.04 installed using wubi and have now tried to update that?  wubi is no longer being developed or supported and I would not expect it to work on 14.04 although you may get lucky.  If you are using wubi, then you have Ubuntu installed inside windows as a program and not on a separate partition.  You need to clarify if you are using wubi.

---

### Post by kansasnoob on 2014-06-29
> **Pao_Rodulfo said:**
> Hello. I also Windows 7 installed alongside Ubuntu. My PC is a Dell Vostro 1014n with 320gb HDD running on Intel Core Duo. I have three major partitions: 100gb for the Default Filesystem of Windows (C:/), 200gb for my own files (D:/), and 20gb/15gb (I can't Exactly remember but in windows, I have a drive named F:/ which has the wubi and it says 15gb) allocated for Ubuntu. I suppose I also have a 100MB partition for the System Reserve of Win7. Help please.. Thanks!

I did not know we were dealing with Wubi :(

Is it even truly supported in 14.04?

You're clearly not alone:

[http://ubuntuforums.org/showthread.php?t=2226912](http://ubuntuforums.org/showthread.php?t=2226912)

[http://ubuntuforums.org/showthread.php?t=2217829](http://ubuntuforums.org/showthread.php?t=2217829)

I just never liked Wubi because the file system ended up being borked every time there was a power outage.

---

### Post by Vladlenin5000 on 2014-06-29
> **kansasnoob said:**
> Is it even truly supported in 14.04?

Included? Yes
Supported? No

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by Pao_Rodulfo on 2014-06-29
> **yancek said:**
> Does that mean you had Ubuntu 12.04 installed using wubi and have now tried to update that?  wubi is no longer being developed or supported and I would not expect it to work on 14.04 although you may get lucky.  If you are using wubi, then you have Ubuntu installed inside windows as a program and not on a separate partition.  You need to clarify if you are using wubi.

Problem is that I was not the one who did this to my PC. As I have ordered this, I requested that I would like to have a dual boot system with ubuntu and it was delivered to me with two operating systems. However, upon booting, I don't see the GRUB so I guess Ubuntu has been installed thru wubi. What can I do now?

---

### Post by Pao_Rodulfo on 2014-06-29
> **kansasnoob said:**
> I did not know we were dealing with Wubi :(

Is it even truly supported in 14.04?

You're clearly not alone:

[http://ubuntuforums.org/showthread.php?t=2226912](http://ubuntuforums.org/showthread.php?t=2226912)

[http://ubuntuforums.org/showthread.php?t=2217829](http://ubuntuforums.org/showthread.php?t=2217829)

I just never liked Wubi because the file system ended up being borked every time there was a power outage.

Sorry about that :( as I have said, I'm not quite familiar with these things yet. What can I do now with my Ubuntu? :(

---

### Post by kansasnoob on 2014-06-29
> **Pao_Rodulfo said:**
> Sorry about that :( as I have said, I'm not quite familiar with these things yet. What can I do now with my Ubuntu? :(

I'm not at all familiar with Wubi. I tried it a long, long time ago but I live in a rural area where power outages are quite common and quickly figured out Wubi was a bad choice for me. But it sounds like Wubi is now poorly supported at best, or possibly not supported at all :(

So I think it's time to consider an actual dual-boot but **[COLOR="#FF0000"]lets start with what NOT to do[/COLOR]**! 

I assume you can still boot Win 7 OK, is that right?

There is a very nasty Ubuntu installer bug that's been wiping out Windows and other OS's left and right:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

We darn sure want to steer clear of that disaster so if you can still boot Windows OK I'd begin by downloading Ubuntu 14.04 (Trusty) here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Then creating a live DVD as shown here:

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

Or if you prefer a live USB look here:

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Then check that media for defects:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

Once you've gotten that far you'll want to boot to the live desktop and collect some vital info before proceeding beginning with opening a terminal and posting the output of:

```
sudo parted -l
```

I'd think you could also retrieve and backup any important data from the Wubi install using the Live DVD but I don't know Wubi well enough to help with that.

Above all lets not make things worse, so be patient and let's develop a safe plan of action.

---

### Post by Pao_Rodulfo on 2014-06-30
> **kansasnoob said:**
> 

You're clearly not alone:

[http://ubuntuforums.org/showthread.php?t=2226912](http://ubuntuforums.org/showthread.php?t=2226912)

[http://ubuntuforums.org/showthread.php?t=2217829](http://ubuntuforums.org/showthread.php?t=2217829)

I just never liked Wubi because the file system ended up being borked every time there was a power outage.

Hi kansasnoob! I have visited these links and it has helped me fix the mounting problems! Thanks a lot! However, as you've said, if wubi is not supported anymore, how can I fix this? (In order to prevent this from hagaining suppose I'd update to the next LTS) or is it just editing the lupin thing all over again? Cheers!

---

### Post by kansasnoob on 2014-06-30
> **Pao_Rodulfo said:**
> Hi kansasnoob! I have visited these links and it has helped me fix the mounting problems! Thanks a lot! However, as you've said, if wubi is not supported anymore, how can I fix this? (In order to prevent this from hagaining suppose I'd update to the next LTS) or is it just editing the lupin thing all over again? Cheers!

If you have 14.04 working in Wubi you may be good to go until April 2019:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I mean there's a lot to say for the old axiom, "if it ain't broke don't fix it".

There are a number of reasons why even dual-booting is not foolproof, and with Win 7 many OEM's began using 4 primary partitions out-of-box so dual-booting is complex, and if Windows ever requires a full reinstall then it's basically time to start all over with both Windows and Ubuntu.

---

### Post by Pao_Rodulfo on 2014-06-30
> **kansasnoob said:**
> If you have 14.04 working in Wubi you may be good to go until April 2019:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I mean there's a lot to say for the old axiom, "if it ain't broke don't fix it".

There are a number of reasons why even dual-booting is not foolproof, and with Win 7 many OEM's began using 4 primary partitions out-of-box so dual-booting is complex, and if Windows ever requires a full reinstall then it's basically time to start all over with both Windows and Ubuntu.

It ain't broke indeed. Haha. Thanks for your help!

---

### Post by yancek on 2014-06-30
> However, upon booting, I don't see the GRUB so I guess Ubuntu has been installed thru wubi. 

I have never used wubi myself but, from what I have read about it, it is installed as a program inside windows in much the same manner as installing a system in VirtualBox software.  The wubi installer creates an entry in the windows boot menu file.  You should be able to remove the Ubuntu wubi (if you decide to do that) from Programs or Program Files in windows.  If you now have Ubuntu 14.04 working for you, just leave it as it will be supported for almost five more years.

---

