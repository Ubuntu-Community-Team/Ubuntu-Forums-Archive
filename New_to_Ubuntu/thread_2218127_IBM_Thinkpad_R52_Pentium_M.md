---
title: "IBM Thinkpad R52 Pentium M"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by 393 on 2014-04-19
I am having problems installing my image onto an old thinkpad I have.  It is an IBM Thinkpad 1860 R52 Pentium M 1.7 GHz with 1gb ram.  I cannot get it to boot from the cd-rom or from a USB drive.  I am attempting to use DBAN hard drive wipe but when I get into change the boot drive (F1) and then reboot I am not able to use the DBAN iso in order to begin the process.
I realize that this is an older machine.  Is it even able to boot from the cd or USB drive?
I have used this image to erase another hard drive on a different model machine and installed my Ubuntu image just fine.
Can someone shed some light on what the issue is?
Is it the machine or is it the hard drive wipe program I am using (DBAN)?
Thank you

---

### Post by Braden_McCloskey on 2014-04-19
Systems that old can boot from CD, but USB can be temperamental. Have you tried booting into a Ubuntu Live CD? While in Live mode, you can install gparted and wipe your old hard drive that way, or you could even let the installer do it for you.

---

### Post by irv on 2014-04-19
It a PAE problem. See this link: [https://help.ubuntu.com/community/Lubuntu-fake-PAE]("https://help.ubuntu.com/community/Lubuntu-fake-PAE")

---

### Post by 393 on 2014-04-19
> **Braden_McCloskey said:**
> Systems that old can boot from CD, but USB can be temperamental. Have you tried booting into a Ubuntu Live CD? While in Live mode, you can install gparted and wipe your old hard drive that way, or you could even let the installer do it for you.

Will it totally wipe the drive out like Dban?  I want to completely clear the drive permanently.

---

### Post by Rob Sayer on 2014-04-21
> **irv said:**
> It a PAE problem. See this link: [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

This guy knows what he's talking about.  Read the link.

---

### Post by 393 on 2014-04-21
Thanks fellas (or gals).  Your time is appreciated.

---

### Post by 393 on 2014-04-21
I am downloading the files on another computer to a USB stick.
I downloaded dd_saucy-a2-installed-system_4Bg.img.gz and dd-sbd.img.dz and put them on a usb stick.

The only issue is that the windows xp version running on the Thinkpad currently won't let me unzip the file.  The hard drive has been corrupted and is running in safe mode.  Do I want to open the files in windows or boot right to the USB stick?

That is the reason I want to wipe the drive and start over with a new (non-windows) OS.

How do I install these files or a new operating system?

Thanks again for your time

---

### Post by mörgæs on 2014-04-21
Please open only one thread per topic. The other one has been jailed.

**Forcepae** is all you need. Please study the link posted above.

---

### Post by 393 on 2014-04-21
I studied the link above as advised, but I am still having problems.

I am aware that I have to use Forcepae in the boot options menu.  This is done by saving and image on a USB stick and booting the machine from the USB.  Once in, I can enter the boot options menu and change the text.
The instructions in the link above state that an older machine, like the one I am using, will work nicely with 14.04 LTS.  I downloaded Xubuntu 14.04 .iso and save it to the USB stick and attempted to boot from it.  I received the following error message:
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot:

I received the same error message when I attempted to boot a USB with mini.iso on it.
I understand that I have to get into boot options through the .iso on the USB image but I can't figure out which image I am supposed to use.
In the link's instructions it says that the 14.04 and Forcepae will work nicely but further down in the text it says not to use any version later than 12.04, but it also says 12.04 is not supported anymore.  Am I using the wrong version of 14.04?  What am I doing wrong?  
I am using a machine that has windows xp  running in safe mode and there is no internet connection.

Please advise.  

Thank you for your time.

---

### Post by mörgæs on 2014-04-21
1) Download the standard 32 bit ISO for Lubuntu 14.04
2) If you know that the computer boots from USB then create a bootable USB stick with Unetbootin. It's not the same as saving the ISO on the USB stick.
3) If you are unsure then burn a CD using whichever application you prefer. Choose 'burn from image' or something similar.

---

### Post by 393 on 2014-04-23
I did as you suggested:
--I use downloaded lubuntu 14.04 .iso.  32 bit.  
--I used Unetbootin to create a bootable usb stick with lubuntu on it.  Tried booting from the stick and the message it got was "Operating System missing".  Albeit a new message, but not the one I am looking for.  No sign of lubuntu.
--I burned the lbuntu 14.04 image to a cd and attempted to boot from the dvd drive.  Nothing, it went right ot my corrupted version of xp running in safe mode.
--I tried booting with the USB stick and the dvd in the drive.  The result was windows xp.
--I tried to open both the USB stick and the dvd from xp and run lubuntu.  Nothing.

What am I to do.  I thank everyone for their help.  I really would like to solve this and install lubuntu on this machine.
Any ideas?

---

### Post by mörgæs on 2014-04-23
Does the CD work when booted in another computer? 
Did you set the boot order to begin with CD? I believe it's controlled by the blue button.

Could also be a BIOS problem. If Windows is not completely dead you could consider to upgrade the BIOS.

---

### Post by 393 on 2014-04-23
I will try to make a new ISo disk

---

