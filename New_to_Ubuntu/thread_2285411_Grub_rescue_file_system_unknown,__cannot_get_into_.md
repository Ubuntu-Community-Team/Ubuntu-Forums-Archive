---
title: "Grub rescue file system unknown,  cannot get into bios, unable to boot from usb or cd"
date: 2015-07-05
forum: New to Ubuntu
---

### Post by mentalmotivation83 on 2015-07-05
First i cannot enter bios. I have to enter a password and a HDD/SSD password upon startup then it goes directly to grub rescue. Upon typing "ls" i get,
(hd0) (hd0,msdos5) (hd0,msdos1)
Upon entering all those i still get filesystem is unknown. Tried to boot from usb and cd without success. Any help or input will be greatly appreciated. Thanks.

---

### Post by yancek on 2015-07-05
Did the usb and CD you tried work when you tried them on another machine or are you able to do that?
How did you create the bootable flash drive, what specific software or method did you use?
Did you burn the DVD as an image file?
Do you have Ubuntu or some other Linux already installed on the first and fifth partitions of your hard drive?
Or, do you have some other operating system on those partitions?
Is this a new install?  Has it ever booted?

---

### Post by mentalmotivation83 on 2015-07-05
I am downloading a bootable usb now and will try again. Im puting ubutu 14.04.2 on a bootable usb using linuxlive usb creator 2.9.3

---

### Post by mentalmotivation83 on 2015-07-05
I am a newbie on linux for pc's. I am an expert on android OS though if that helps at all.

---

### Post by mentalmotivation83 on 2015-07-05
When i bootup my laptop i try to boot into bios but it asks for a password then a HDD/SSD password. After i enter the 2 passwords it takes me to grub rescue. I accidentally setup the 2 passwords in bios and might have disabled the FN/function key in bios. Idk the boot order in bios for the HDD, usb, cd etc... 
Any help is much appreciated. Thank you.

---

### Post by sandyd on 2015-07-05
Hi, what model of laptop is this?

---

### Post by mentalmotivation83 on 2015-07-05
A toshiba satalite. Ty for replying.

---

### Post by lisati on 2015-07-05
> **mentalmotivation83 said:**
> A toshiba satalite. Ty for replying.

Which version of Toshiba Satellite? There are several different models of Toshiba Satellite, with differences between models that can sometimes make an important difference when troubleshooting.

---

### Post by lisati on 2015-07-05
***Threads merged.***

Please don't start multiple threads for the same problem, it can dilute the community's ability to help.

---

### Post by mentalmotivation83 on 2015-07-05
C855d-s5201

---

### Post by mentalmotivation83 on 2015-07-05
Sorry about that. Im new to the forum.

---

### Post by oldfred on 2015-07-06
Did you install in UEFI or BIOS boot mode.

May be best to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If UEFI:
Some other Toshiba's which may have same issues & solutions as often very common across model of same brand.

 Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)
Toshiba C55D-A5163 - Installation of Lubuntu on computer with Windows 8.1 Feb 2015
[http://ubuntuforums.org/showthread.php?t=2267268](http://ubuntuforums.org/showthread.php?t=2267268)

---

### Post by Cordthundertree on 2015-07-06
Is your USB stick on a USB hub? If so, unplug it from the hub and use a port on your computer. When I did that it fixed all of my problems.

---

### Post by mentalmotivation83 on 2015-07-06
> **Cordthundertree said:**
> Is your USB stick on a USB hub? If so, unplug it from the hub and use a port on your computer. When I did that it fixed all of my problems.
What do you mean exactly? Im a newbie to this. Sorry.

---

### Post by mentalmotivation83 on 2015-07-06
> **oldfred said:**
> Did you install in UEFI or BIOS boot mode.


May be best to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If UEFI:
Some other Toshiba's which may have same issues & solutions as often very common across model of same brand.

 Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)
Toshiba C55D-A5163 - Installation of Lubuntu on computer with Windows 8.1 Feb 2015
[http://ubuntuforums.org/showthread.php?t=2267268](http://ubuntuforums.org/showthread.php?t=2267268)

I think bios but i cannot access it. I dont have a standard F10 key and i think i disabled the FN key in bios.

---

### Post by oldfred on 2015-07-06
You may be able to get into BIOS with a full power down. If laptop remove battery. And hold power switch for 10 sec or so to drain all power.

If that does not work, you have to open up system and remove motherboard battery or jumper some pins on motherboard. You have to review details of your specific motherboard to know what to do.

---

### Post by mentalmotivation83 on 2015-07-07
I figured out a differant way. Ty to all that helped me. First i had to take out the small flat battery by the motherboard for a few seconds then put it back in. Powered on my laptop and went straight to the bios menu. Then I downloaded a android app called drivedroid and downloaded a iso img to boot up throgh my phones mass storage.

---

