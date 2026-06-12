---
title: "Tired of fighting Win8-Ubuntu12.04 Dual boot."
date: 2013-07-01
forum: New to Ubuntu
---

### Post by HairLesApe on 2013-07-01
Will one of these options work?
live CD with a portable USB hard drive formatted to est4 mounted at /.
VBox Ubuntu image, start 12.04 app with external USB hard drive formatted to est4 mounted at /.
Ineed a quick stable solution, my daughter needs both os for her research project, and I am not a gunslinger. But will be her main support. I have Win7 ('09 version) with 12.04 running now, but need to coexest with Win8/uefi/secureboot.

---

### Post by RonanZer0 on 2013-07-01
Please explain more clearly what you need.

---

### Post by oldfred on 2013-07-01
UEFI and secure boot complicate it. And is system an Ultrabook as those have dual video & Intel SRT (uses RAID) which add even more issues. 
Most systems will work with UEFI.

Does system boot with secure boot off?

You must have fast boot off and secure boot off. You also need to make a Windows repair flash drive and full backup of Windows and the efi partition.

Links to details for many UEFI issues in link in my signature.

---

### Post by HairLesApe on 2013-07-01
Thanks for the reply OldFred.
The hardware I'm using is a Toshiba L855 with i7 quad and 8 MB RAM. UEFI was on, boot speed was normal, secure boot was on.
While attemting to load my recovery disks the UEFI crashed (I suppose). Now I can't boot from any device. Blue screen fault 0xc000000f.
I bought an identical Toshiba to eperiment with. I have read that switching from UEFI and turning off secure boot has worked the system is unstable. have you had that problem?
I had hoped to bypass the system config problems byopening Ubuntu 12.04lts in VBox and offering storage from a USB portable drive. Could this work?

---

### Post by oldfred on 2013-07-01
Never tried VBox. 
Some Toshiba's have had issues but if you have UEFI/BIOS with latest version it should help.

 Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)

Other Toshiba

 Toshiba laptop C850 Windows 7 with upgrade to 8 version -  sudodus
[http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025](http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025)
 [SOLVED] Can't install Windows 8 & Ubuntu in Toshiba Portege Z930 with explanation how by OP feb 2013
[http://ubuntuforums.org/showthread.php?t=2114290](http://ubuntuforums.org/showthread.php?t=2114290)

      
 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries


 The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)

---

### Post by ryan516 on 2013-07-01
I've had to fight using Ubuntu on Win. 8 dual booting. What you need to do is install the 64 bit version of Ubuntu, and it should work fine!

---

