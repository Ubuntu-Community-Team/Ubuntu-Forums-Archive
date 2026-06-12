---
title: "gnu grub version 2.02 beta2-36 ubuntu3.17 I'm frozen in this -need help!"
date: 2018-02-28
forum: New to Ubuntu
---

### Post by davidhopton on 2018-02-28
My wife's laptop's only soft ware is Ubuntu 16.? -- When she was updating she may of bumped a computer key --she is not sure but when she looked up her screen was blank with the subject heading. All the solutions to this problem I found on the net do not work (or maybe I don't know how) So I bought a Linux DVD for Ubuntu but can't get it to run F11 and 12 keys do not respond on rebooting and I continue to get "grub" on reboot.    Any suggestions will be appreeciated. Thank you

---

### Post by oldfred on 2018-02-28
Are you getting grub> or grub rescue>  ?
If DVD not booting then not made correctly or system has major hardware issues. 

Usually better to just download a current Ubuntu and install to flash drive (or DVD). But I have burned so many coasters (bad disks) that I now only use flash drives. 

Do not copy ISO to flash drive but use installer. Or if system is newer UEFI, you can do it yourself.

 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by davidhopton on 2018-03-01
1. I am getting grub
2. Laptop is less than 2 yrs old -doubt hardware prblm. (HP Pavilion)
3. DVD bought from Amazon it is version 16.04.3 default desktop (utility) LTS edition -as you say it may still be faulty
4. I have flash drives but how do I know if UEFI or predecessor?
5. Is there no way to get out of gru grub? rather than reinstalling from disk or flash dr.?

---

### Post by oldfred on 2018-03-01
You need a working live installer to use as a repair disk.

If new system, almost sure to be UEFI. And then you have to have UEFI on in UEFI settings. If you installed previously in both BIOS (incorrectly) and then in UEFI which worked, but updated system. Then if UEFI settings revert to BIOS, it gives grub> as incompatible version.

If you know partitions you may be able to manually boot.

 [https://help.ubuntu.com/community/Grub2#Command](https://help.ubuntu.com/community/Grub2#Command)  & Rescue Mode
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:

   ls
  set root=(hdX,Y)
  linux /vmlinuz root=/dev/sdXY ro
  initrd /initrd.img
  boot 

       #show you the available partitions
ls
#look for boot files on the partitions
ls (hd0,1)/boot
# continue until you see vmlinuz-X.X.xxxx
#then boot that linux replacing hd0,1 with your partition 
    


If you have working live installer, you use this:
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by davidhopton on 2018-03-01
I appreciate the time you have spent with me, but most of what you advise I don't fully understand. This computer is frozen in grub --I can't even get command prompt. I'll look for help elsewhere but thank you

---

### Post by davidhopton on 2018-03-03
I&#8217;m back again - ls responds as follows "secure boot forbids loading module from (hd0,gpt2)boot/grub/x86_64-efi/ls.mod."

---

### Post by jeremy31 on 2018-03-03
I would go into UEFI/BIOS settings and disable Secure Boot, if that option is there

---

### Post by davidhopton on 2018-03-04
UEFI/BIOS response is ' can't find command uefi/bios"

---

### Post by oldfred on 2018-03-04
That is not a command. That is a setting in UEFI.
And many systems call UEFI Secure Boot setting "Windows" with "Other" as other setting. But fine print says if using Windows 7, use "Other" as Windows 7 does not support UEFI Secure Boot.

---

### Post by davidhopton on 2018-03-04
How can one use a setting when all  I have is a black screen as described in original post? It states-"Minimal BASH- like line editing is supported. For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device or file completions."  TAB opens to 12 lines of command --none of which work.  
 The only software on this laptop is Ubuntu.

---

### Post by oldfred on 2018-03-04
If UEFI you have to use whatever key your UEFI uses often f2 or delete to get into UEFI.
But if you left UEFI fast boot on, you may not have much if any time to press any key.
You then need to do a full cold boot not a warm reboot.

Cold boot is as if system has been totally off for long time or cold system.
You can remove power, if laptop remove battery, and hold power switch for 10 sec or so to drain any remaining power.
Then boot and immediately press correct key to get into UEFI.
If that does not work you may have to remove coin battery on motherboard or jumper pins on motherboard to reset system. 
Sometime just disconnecting drive also resets UEFI.

---

