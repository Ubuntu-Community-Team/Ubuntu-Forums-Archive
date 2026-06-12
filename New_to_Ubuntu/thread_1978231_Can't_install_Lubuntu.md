---
title: "Can't install Lubuntu"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by vikbz on 2012-05-10
hello all, i have a small problem. I cant seem to install Lubuntu 11.10. I ran a dban to remove all the files off the previous Windows XP installation and now that it is clean I tried to install Lubuntu 11.10 since the 10.10 is now not being supported. The splash page comes up with the choice to install onto hard drive or use Live CD but when i choose either one, it just goes straight to a diagonal (-) blinking prompt and does NOTHING else!!! Any help with this would be MUCH appreciated.

thanks,

---

### Post by Rodney9 on 2012-05-10
> hello all, i have a small problem. I cant seem to install Lubuntu 11.10. I ran a dban to remove all the files off the previous Windows XP installation and now that it is clean I tried to install Lubuntu 11.10 since the 10.10 is now not being supported. The splash page comes up with the choice to install onto hard drive or use Live CD but when i choose either one, it just goes straight to a diagonal (-) blinking prompt and does NOTHING else!!! Any help with this would be MUCH appreciated.

Why use 11.10 ?

12.04 is the lastest and is a Long Term Support (LTS) version.


Burn the discs at the slowest speed you can.

Try a different brand of cd.

Check MD5SUM for your CD/DVD

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Rodney

---

### Post by sudodus on 2012-05-11
> **Rodney9 said:**
> Why use 11.10 ?

12.04 is the lastest and is a Long Term Support (LTS) version.


Burn the discs at the slowest speed you can.

Try a different brand of cd.

Check MD5SUM for your CD/DVD

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Rodney
+1
except that Lubuntu has not LTS (while Ubuntu, Kubuntu and Xubuntu have 5 or 3 years support, LTS).

---

### Post by mörgæs on 2012-05-11
If your computer supports it, you should try booting the alternate ISO from a USB stick.

---

### Post by vikbz on 2012-05-11
hello all thanks for the suggestions. First, I wanted to try 11.10 since I wasn't sure if the Unity desktop style would be here as in Ubuntu. Since I really don't like that look, i wanted to test the waters with 11.10. I burned the .iso to the CD on the lowest speed and i'm pretty sure its not that since before I tackled this PC, I managed to install 11.10 to a different PC using the exact same CD before. I will try to see if I can boot via USB with the .iso but does the .iso have to be the only file on the USB stick? i.e clean out everything BUT the .iso?

thanks and Ill let you all know how it goes...

---

### Post by MG&amp;TL on 2012-05-11
> **vikbz said:**
> hello all thanks for the suggestions. First, I wanted to try 11.10 since I wasn't sure if the Unity desktop style would be here as in Ubuntu. Since I really don't like that look, i wanted to test the waters with 11.10. I burned the .iso to the CD on the lowest speed and i'm pretty sure its not that since before I tackled this PC, I managed to install 11.10 to a different PC using the exact same CD before. I will try to see if I can boot via USB with the .iso but does the .iso have to be the only file on the USB stick? i.e clean out everything BUT the .iso?

thanks and Ill let you all know how it goes...

You need to use unetbootin-you can get a .exe for windows, or:

```
apt-get install unetbootin
```


Lubuntu will (AFAIK) have no Unity interface now, or in the future. We're sticking to LXDE.

---

### Post by vikbz on 2012-05-11
OK guys, update:

I cleaned out a GB USB stick I had here and copy/pasted the 11.10 iso. I then went into BIOS and found out that the USB feature is enabled although it doesn't show up as a choice to boot from. Nevertheless, when the choice came up on POST screen, it shows menu F2 and boot menu F10. I decided to pick F10 to choose the USB stick. 4 or 5 choices came up including the USB device. I chose this but nothing came up after it, not even the welcome to Lubuntu stuff that at-least came up after i tried the CD approach. Any more suggestions I could try? Like I mentioned before its a clean HDD w/out any OS since i ran DBAN (an OLDER version BTW since it was giving me trouble as well trying to use the newest version).

thanks again, :)

---

### Post by MG&amp;TL on 2012-05-11
> **vikbz said:**
> OK guys, update:

I cleaned out a GB USB stick I had here and copy/pasted the 11.10 iso. I then went into BIOS and found out that the USB feature is enabled although it doesn't show up as a choice to boot from. Nevertheless, when the choice came up on POST screen, it shows menu F2 and boot menu F10. I decided to pick F10 to choose the USB stick. 4 or 5 choices came up including the USB device. I chose this but nothing came up after it, not even the welcome to Lubuntu stuff that at-least came up after i tried the CD approach. Any more suggestions I could try? Like I mentioned before its a clean HDD w/out any OS since i ran DBAN (an OLDER version BTW since it was giving me trouble as well trying to use the newest version).

thanks again, :)

You can't just copy the ISO across. You need to use a iso-to-USB program, Unetbootin is one I recommend. :)

---

### Post by vikbz on 2012-05-11
ahh im using Ubuntu desktop on this machine i had the iso saved in. Is there a software i can install on this machine to run what you suggest i need? I thought it was a simple copy/paste scenario...thanks for the heads up!!!

---

### Post by MG&amp;TL on 2012-05-11
> **vikbz said:**
> ahh im using Ubuntu desktop on this machine i had the iso saved in. Is there a software i can install on this machine to run what you suggest i need? I thought it was a simple copy/paste scenario...thanks for the heads up!!!

If you're on an Ubuntu machine, Startup Disk Creator work nicely. As far as I know, it's installed by default. Or you can install UnetBootin from the software centre.

---

### Post by vikbz on 2012-05-11
hey man, no dice trying to install the iso using Unetbootin, it shows up as No Boot device and it doesn't move from there. I'm trying the startup disk creator to see if i have any luck but using the 10.10 version and then i'll try to upgrade it to 11.10 somehow.

---

### Post by vikbz on 2012-05-11
no dice on using the 10.10 with the startup disk creator either. It immediately gives me a BOOT ERROR and does nothing from there. What could I be doing wrong?

---

### Post by MG&amp;TL on 2012-05-11
> **vikbz said:**
> no dice on using the 10.10 with the startup disk creator either. It immediately gives me a BOOT ERROR and does nothing from there. What could I be doing wrong?

What is the disk formatted as? I find sometimes it won't work unless it's FAT or NTFS-for some unknown reason.

You also need to format the stick and make a partition over it first.

---

### Post by vikbz on 2012-05-11
hey guys, update:

I decided to download 12.04 iso just for kicks and burned it to a CD. Lo and behold, the installation started after about a minute of the horizontal prompt blinking and now i have a functioning 12.04 Lubuntu. Who would've known it needed the most updated version and not the earlier version? 

Anyhow, thanks for all the help!!!

---

### Post by sudodus on 2012-05-11
Have a look at the following threads, where the preparation of a USB drive is described. You need to walk through a few steps in order to succeed. There are several tools, and all of them make working USB boot drives for most computers.

But booting from USB is not fully standardized, so in your particular case on method might work, but not another one. I agree with MG&TL, that Unetbootin works well in most cases.


'unetbootin method':
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392") [The 16 GB drive is partitioned with Gparted. The first partition is used as a data partition because Windows can read it. (At least older Windows systems can only read the first partition on a USB drive.) See the attached picture in the thread above.] The important thing here is how to set up the partition to be bootable (in that case partition #2, but of course it can be #1, particularly if the drive is small, you should have only one partition: ***Use the FAT32 file system and the boot and lba flags, and after that run Unetbootin*** to install the operating system from the iso file.

'dd image of iso file':
[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073") This method can be very convenient, but is only working with a few versions of linux (including *ubuntu 11.10 and 12.04). And it is actually copying the iso file, but copying in a very special way, actually cloning it, including the first part of the drive, with the partition table (in this case MBR).

---

