---
title: "Boot other OS from USB/DVD device"
date: 2014-09-07
forum: New to Ubuntu
---

### Post by ilias3 on 2014-09-07
Hello everyone, 

I am using a HP-Pavlion g6-2250ev laptop with OS : Linux Ubuntu 12.04. Bios : Insyde F.26
Before I installed the ubuntu i used to have Windows 8.0 installed by the manufacturer.
After the replacement of windows with ubuntu, i can not anymore boot with neither bootable dvd nor usb stick.
I do not know wheter its an OS or Bios issue, so, can anyone assist me in this matter?

Thank you all in advance,
Cheers!

---

### Post by stalkingwolf on 2014-09-07
first check your bios boot order.   I think either F1 or F2 will get you into the setup.      Also either F8 or F10 should bring up a one time boot menu you should be able to boot from there.

You should have an icon on the desktop for computer.  if you open it do your dvd and thumb drive show up there?

---

### Post by ilias3 on 2014-09-08
1. yes they show up , they are working in other computers!
2. yes i have checked and tried everything from the bios options. with bootable usb, with bootable dvd, with secure boot enabled and disabled, with leagacy enabled and disabled, with EFI file also, nothing is working. I am really trying and nothing seems to work! Isn there any other way more "extreme" to wipe everything out and restart everything with an empty disk drive? or sth like that?
thanks in advance

---

### Post by mcduck on 2014-09-09
wouldn't help anything. At the point when you are selecting which device you want to boot from, no OS is running yet so they have no way of affecting your ability to boot from a CD. It's definitely up to your BIOS settings to get this working.

Also, it's quite common for modern BIOSes to have a separate key for selecting the boot device when you start the computer (regardless of what the actual BIOS settings might be). I recommend checking if your system has one, and trying that if changing the BIOS settings doesn't seem to work.

edit: According to the user manual for your computer, the boot order changing works by pressing ESC while starting the machine, and then selecting F9 for boot device options. (keep in mind that this way of selecting boot device is not saved in BIOS settings, it's just telling the system what device to use on *that* boot)

---

### Post by ilias3 on 2014-09-10
The thing is that, I have tried both the options of booting from USB and DvD in the boot-up screen and it redirects me to use and "EFI" file.. I don know that it is.

---

### Post by yancek on 2014-09-10
It isn't clear to me whether you have replaced your windows 8 with Ubuntu or if you still have both on the computer.  
EFI is a different method of booting than the previous mbr method.  With EFI you have a separate partiiton on the drive where specific files for both windows/Linux would reside and boot from.   Being unable to boot from a flash drive or DVD is not relevant to the operating system you have installed but needs to be changed in the BIOS setup.  On my HP Pavilion, there are multiple options to boot from a usb, one under CD/DVD which doesn't do anything and another under the Hard Drive option which enables boot from usb.  Check through all the options.

---

### Post by Vladlenin5000 on 2014-09-10
In UEFI mode some systems force the boot USB or optical devices trough a UEFI boot sub-menu.

---

