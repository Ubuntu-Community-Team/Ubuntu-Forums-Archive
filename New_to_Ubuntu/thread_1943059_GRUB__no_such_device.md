---
title: "GRUB : no such device"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by anadorian on 2012-03-18
(I realize that this issue has been resolved for other users, but my problem is slightly different as using a cd to reset the MBR is not possible)

 so I fond myself having a similar problem to others regarding grub not booting ubuntu after an update.  
 
I managed to find a work-around by booting one of the older kernels in the grub selection screen. 
 
New problem: 
 
My external IOMEGA 1TB HD just crashed today, and is not mounting, detectable, and giving a lovely click of death. 
 
My ubuntu partition was loaded to this external. and to boot even from  my cd-drive or my internal hard-drive I had to go through the grub menu  in the external. without that disk drive, i cannot get the system to  boot from its internal hdd or an optical drive. No matter what I select  from the boot-list it gives me a grub no such device error. I cannot run  a windows repair disk, nor can i run a live cd, nor can I boot the  internal windows partition. 
 
PLEASE HELP

---

### Post by chipbuster on 2012-03-19
What kind of computer are you running? All modern PCs that I know of allow you to change your boot order from the BIOS, so that you won't need to use bootloaders in a situation like this.

---

### Post by anadorian on 2012-03-19
its an old inspiron Im pretty sure 1525, its not right in front of me at the moment.
 
I forgot to mention that there is an admin password set blocking my access to bios, i tried blank and a bunch of other things but  cant unlock it, thing is this was my moms old pc and she would never have set a system admin password.... its probably impossible....

Unless there is a way to manually redirect grub to my optical drive with a command, or getting around the admin passcode, Im thinking my best option is to remove the internal hard-drive, attach it to a working pc, do a repair with a vista disk to reset the MBR  and then replace it into my computer and see if it boots properly.

thoughts?

---

### Post by oldfred on 2012-03-19
Does the admin password also prevent use of the one time boot key. Most computers have a one time boot key (f12 on mine) and BIOS usually tells you on first BIOS screen.

Most computers have a jumper on the motherboard that you change or short to reset BIOS password. You would have to look at vendor manual.

It sounds like you installed grub to the MBR of the internal drive but have the install on the external. It generally is suggested to install grub to the MBR of the external and leave the MBR of the internal unchanged. Then in BIOS set to boot external first. If not found it defaults to internal.

---

### Post by tbhatia4 on 2012-03-19
> **anadorian said:**
> (I realize that this issue has been resolved for other users, but my problem is slightly different as using a cd to reset the MBR is not possible)

 so I fond myself having a similar problem to others regarding grub not booting ubuntu after an update.  
 
I managed to find a work-around by booting one of the older kernels in the grub selection screen. 
 
New problem: 
 
My external IOMEGA 1TB HD just crashed today, and is not mounting, detectable, and giving a lovely click of death. 
 
My ubuntu partition was loaded to this external. and to boot even from  my cd-drive or my internal hard-drive I had to go through the grub menu  in the external. without that disk drive, i cannot get the system to  boot from its internal hdd or an optical drive. No matter what I select  from the boot-list it gives me a grub no such device error. I cannot run  a windows repair disk, nor can i run a live cd, nor can I boot the  internal windows partition. 
 
PLEASE HELP
just reset you bios settings to default
then try booting if this does not work create a usb disk of ubuntu and install boot repair in that
that would recreate your grub without removing any data

---

### Post by anadorian on 2012-03-19
> **oldfred said:**
> Does the admin password also prevent use of the one time boot key. Most computers have a one time boot key (f12 on mine) and BIOS usually tells you on first BIOS screen.

Most computers have a jumper on the motherboard that you change or short to reset BIOS password. You would have to look at vendor manual.

It sounds like you installed grub to the MBR of the internal drive but have the install on the external. It generally is suggested to install grub to the MBR of the external and leave the MBR of the internal unchanged. Then in BIOS set to boot external first. If not found it defaults to internal.

Yes the one time boot comes up normally and gives me a list. But no matter what I select, cd-dvd/rom, internal hdd it still goes to the Grub no such device error.

---

### Post by anadorian on 2012-03-19
> **tbhatia4 said:**
> just reset you bios settings to default
then try booting if this does not work create a usb disk of ubuntu and install boot repair in that
that would recreate your grub without removing any data

The admin password wont let me change bios settings, even just to restore to default...

is there a work-around to admin passcodes?, I cant imagine that if you lose the bios passcode you're simply out of luck to changing anything in that menu ever again.

---

### Post by oldfred on 2012-03-19
If you can choose to boot cd, and it boots to hard drive that indicates the cd is not a bootable CD. Are you sure you correctly burned & at slowest speed allowed &  it not just copied the ISO to the CD?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by chipbuster on 2012-03-19
> **anadorian said:**
> The admin password wont let me change bios settings, even just to restore to default...

is there a work-around to admin passcodes?, I cant imagine that if you lose the bios passcode you're simply out of luck to changing anything in that menu ever again.


There is, but it involves you ripping your computer apart and hunting for things on the circuit board. This is why I prefer to physically secure my computers over setting BIOS passes. 

---------------

I suppose a rather drastic solution would be to rip out your internal hard drive. As long as the optical drive is somewhere in your boot list, it should allow you to boot from it once the internal and external are taken out of the picuture.

---

### Post by anadorian on 2012-03-19
[QUOTE=oldfred;11778747]If you can choose to boot cd, and it boots to hard drive that indicates the cd is not a bootable CD. Are you sure you correctly burned & at slowest speed allowed &  it not just copied the ISO to the CD?"

Yes it is the cd I used in a live session to obtain files off a girls computer a week ago. Normally that would be correct, but it was behaving like this before the hd crashed, If the hd was not connected I could not boot to cd or internal hd even before.

The way I used to boot to cd or internal hd was to select those at the bottom of the grub menu where you select what linux kernel you want to use, if I tried to do it through one time boot menu it would still bring me to that grub screen on my harddrive, and made me go from there.

I know it was a NOOB oversight to allow that weird boot sequence to go un-corrected, but I really thot my HD was in no danger as it is stationary, and I have had good experiences with IOMEGA drives.

I also didnt foresee the bios being locked out on the laptop.

so to sum up. yes my cds are properly burned and bootable

no I cannot access bios
no I cannot access one-time-boot cd-rom
no i cannot access one-time-boot internal drive

new idea

what if I was to install ubuntu to a different external with the same drive letter as the dead one? maybe the grub stub would correctly mount it? 
if it detected grub with the same drive letter as it expects?

---

### Post by oldfred on 2012-03-19
I would say no, but I did see one user who actually did a reinstall and the grub in the MBR worked. You would have to have exactly the same version of grub or Ubuntu. And it will somewhat depend on how you installed. You may get an UUID not found error as the newer versions work by UUID not device. But if you can get to grub> or grub rescue you may be able to manually boot.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

