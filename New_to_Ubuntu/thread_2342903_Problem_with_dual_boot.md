---
title: "Problem with dual boot"
date: 2016-11-11
forum: New to Ubuntu
---

### Post by nerdy2 on 2016-11-11
Hello everybody :)
I am new here and i need you help in order to solve my problem.
Yesterday i decided to make partition on my laptop (HP Pavilion 15-b103 (5i-3337U/4G/500GB)) and install Ubuntu 16.10. My laptop runs windows 10. Everything was ok in installation but the problem is that i can make dual boot..i mean to choose operating system when my laptop boots. I treid everything on goolge (disable safe mode, run repair boot on ubuntu, enable legacy mode, bios etc.) but still it boots directly to windows 10!!! :(
Can you please tell me how to fix it? I want to start using ubuntu but i don't want to delete windows.
Thank you in advance guys :)

---

### Post by mastablasta on 2016-11-11
boot from liveDVD or USB and us eboot repair to generate the boto into script. post results here.

also the BIOS things you mentione - you need ot do those before install. or reinstall after the mentioned BIOS/UEFI changes.

---

### Post by oldfred on 2016-11-11
You need to have Ubuntu in UEFI boot mode.
You may be able to use the UEFI boot menu, often f10 or f12, not sure with HP which keys.(my notes do have it, but different ways?)
 1) press esc key while booting to access start up menu 2) press F9 for boot devices menu.
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. (may be UEFI settings, not menu?)

You also may have a setting buried deep in UEFI that lets you set Ubuntu as a valid option.
      HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)

Most HP violate UEFI spec that says NOT to use description as part of UEFI boot. And of course only valid description is "Windows Boot Manager".
Depending on configuration there are multiple work arounds. Most dual booting use the fallback or hard drive default entry. And now Boot-Repair will automatically copy shimx64.efi to /EFI/Boot/bootx64.efi so you can boot the UEFI hard drive entry if you already have one. You may have to add one also.

Details on copying files also in link in my signature.

 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
     'Use the standard EFI file' in Boot-Repair's advanced options. Then you do not have to manually copy files, but still have to boot hard drive not ubuntu entry.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

