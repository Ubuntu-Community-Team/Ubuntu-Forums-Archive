---
title: "Installed Windows 8 after Ubuntu 14.04 LTS, Boot-Repair doesn't work"
date: 2014-11-07
forum: New to Ubuntu
---

### Post by Gaurav_Chhabra on 2014-11-07
Hi guys,

I installed Windows 8 after Ubuntu 14.04 LTS. Ubuntu was installed on one of the SSD, (I've got two 128 GB SSD's) and following which I installed Windows on the other one.

I was aware of losing the GRUB bootloader and used the boot-repair tool to repair the bootloader. However, it did not seem to work. The following is the Boot-Info URL for my attempt:
[http://paste.ubuntu.com/8859852/](http://paste.ubuntu.com/8859852/)

I tried using the boot-repair-disk, but it didn't work either as I had expected, since it basically uses the same tool.

Any help would be highly appreciated. [IMG]http://ubuntuforums.org/images/icons/icon11.png[/IMG]

Thanks

---

### Post by oldfred on 2014-11-07
I might have disconnected the other drive when installing Windows. It may have installed correctly if sdb was really seen as sda, or perhaps if UEFI was changed to default boot from sdb.

It looks like Windows installed in UEFI mode on sdb, but used the efi partition in sda for its boot files.
But you now have a Windows boot loader in sdb's MBR which would be for BIOS boot. But both drives are gpt and Windows only boots in UEFI mode from gpt partitions.

Boot-Repair does pick up some minor errors like install image is oversize and reports that in summary, but grub says it reinstalled without error or code 0.
 Reinstall the GRUB of mapper/ubuntu--vg-root into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

From UEFI menu with secure boot off, and UEFI on can you boot either Ubuntu or Windows? Both should work.
But do not turn on CSM/BIOS boot mode as that will not work to try to boot Windows from sdb. 

You do have Ubuntu installed in full drive LVM mode which uses a separate efi partition if UEFI and separate ext2 partition for /boot, both outside LVM.

---

### Post by mansonfan78 on 2014-11-07
Get a live cd of the version of Ubuntu you are using (if you don't already have one) and just reinstall grub.  [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by Gaurav_Chhabra on 2014-11-14
Sorry for the late reply, I didn't seem to get an email notification for the replies. 
As for removing the other drive, I don't think that's possible, since they're both inbuilt SSDs. 
Also, the thing is, I can't figure out how to get to the UEFI menu on my VIAO Z.  
PS: By default the system boots to Windows and I can't figure out how to boot into Ubuntu at all.

Appreciate your reply, if you help me any further with this problem, it would be awesome.

---

### Post by irv on 2014-11-14
Awhile ago I installed Ubuntu with Win8 and could not boot into Ubuntu. 
From Win8  hold down the [Shift] key and rebooted. I then go to advance setting and go into the BIOS. Both installed should be in the boot section and all you need to do is change the boot order and it should boot into the grub and you can chose which OS to boot to. In my case Win8 didn't boot because when I installed Ubuntu I wiped out Win8.
I fixed all that and everything works now.

---

### Post by oldfred on 2014-11-14
Was this originally a Windows 8 system?
Sony and others internally modify UEFI to only boot the UEFI entry with Windows in the description.
Were you able to boot Ubuntu directly from UEFI menu before, or had you done one of the work arounds to make it work with a Sony?
UEFI still boots hard drive entry so most users find they can modify (or create if not there) the /efi/Boot/bootx64.efi to really be grubx64.efi. Then from UEFI you can set hard drive as a boot option and boot grub/Ubuntu.

Other work arounds:
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Script to auto create grub as bootx64.efi. Have not tried this and just saw it today:
       script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

  Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)

 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)
Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

---

### Post by Gaurav_Chhabra on 2014-11-14
So initially it had a Windows 7, which I formatted entirely and installed Ubuntu on one of the two SSDs. This was working perfectly fine, till I installed Windows 8 after which this entire issue started. Also, I tried getting into UEFI using the "Assist" button, doesn't seem to be working with me. 
This is extremely frustrating since I had a kml file on my ubuntu which I really need and I can't. Do you suggest to modify bootx64.efi to grubx64.efi ?

> **oldfred said:**
> Was this originally a Windows 8 system?
Sony and others internally modify UEFI to only boot the UEFI entry with Windows in the description.
Were you able to boot Ubuntu directly from UEFI menu before, or had you done one of the work arounds to make it work with a Sony?
UEFI still boots hard drive entry so most users find they can modify (or create if not there) the /efi/Boot/bootx64.efi to really be grubx64.efi. Then from UEFI you can set hard drive as a boot option and boot grub/Ubuntu.

Other work arounds:
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Script to auto create grub as bootx64.efi. Have not tried this and just saw it today:
       script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

  Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)

 One Sony user

Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)
Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

---

### Post by Gaurav_Chhabra on 2014-11-14
I mounted /dev/sda1 on /mnt and these are the files that I have on it:
ubuntu@ubuntu:/mnt$ cd EFI/
ubuntu@ubuntu:/mnt/EFI$ ls -l
total 12
drwxr-xr-x 2 root root 4096 Nov  6 23:54 Boot
drwxr-xr-x 3 root root 4096 Nov  6 23:50 Microsoft
drwxr-xr-x 2 root root 4096 Oct 29 02:55 ubuntu
ubuntu@ubuntu:/mnt/EFI$ ls -l Boot/
total 1324
-rwxr-xr-x 1 root root 1354472 Sep 20  2012 bootx64.efi
ubuntu@ubuntu:/mnt/EFI$ ls -l ubuntu/
total 3416
-rwxr-xr-x 1 root root     121 Nov 14  2014 grub.cfg
-rwxr-xr-x 1 root root  956792 Nov 14  2014 grubx64.efi
-rwxr-xr-x 1 root root 1178240 Nov 14  2014 MokManager.efi
-rwxr-xr-x 1 root root 1355736 Nov 14  2014 shimx64.efi
ubuntu@ubuntu:/mnt/EFI$ ls -l Microsoft/Boot/
total 4160
-rwxr-xr-x 1 root root   32768 Nov 14 16:19 BCD
-rwxr-xr-x 1 root root   28672 Nov  6 23:50 BCD.LOG
-rwxr-xr-x 1 root root       0 Nov  6 23:54 BCD.LOG1
-rwxr-xr-x 1 root root       0 Nov  6 23:54 BCD.LOG2
drwxr-xr-x 2 root root    4096 Nov  6 23:54 bg-BG
-rwxr-xr-x 1 root root 1354472 Sep 20  2012 bootmgfw.efi
-rwxr-xr-x 1 root root 1350888 Sep 20  2012 bootmgr.efi
-rwxr-xr-x 1 root root   65536 Nov  6 23:54 BOOTSTAT.DAT
-rwxr-xr-x 1 root root    4186 Jun 26  2012 boot.stl
drwxr-xr-x 2 root root    4096 Nov  6 23:54 cs-CZ
drwxr-xr-x 2 root root    4096 Nov  6 23:54 da-DK
drwxr-xr-x 2 root root    4096 Nov  6 23:54 de-DE
drwxr-xr-x 2 root root    4096 Nov  6 23:54 el-GR
drwxr-xr-x 2 root root    4096 Nov  6 23:54 en-GB
drwxr-xr-x 2 root root    4096 Nov  6 23:54 en-US
drwxr-xr-x 2 root root    4096 Nov  6 23:54 es-ES
drwxr-xr-x 2 root root    4096 Nov  6 23:54 et-EE
drwxr-xr-x 2 root root    4096 Nov  6 23:54 fi-FI
drwxr-xr-x 2 root root    4096 Nov  6 23:54 Fonts
drwxr-xr-x 2 root root    4096 Nov  6 23:54 fr-FR
drwxr-xr-x 2 root root    4096 Nov  6 23:54 hr-HR
drwxr-xr-x 2 root root    4096 Nov  6 23:54 hu-HU
drwxr-xr-x 2 root root    4096 Nov  6 23:54 it-IT
drwxr-xr-x 2 root root    4096 Nov  6 23:54 ja-JP
drwxr-xr-x 2 root root    4096 Nov  6 23:54 ko-KR
drwxr-xr-x 2 root root    4096 Nov  6 23:54 lt-LT
drwxr-xr-x 2 root root    4096 Nov  6 23:54 lv-LV
-rwxr-xr-x 1 root root 1263856 Jul 26  2012 memtest.efi
drwxr-xr-x 2 root root    4096 Nov  6 23:54 nb-NO
drwxr-xr-x 2 root root    4096 Nov  6 23:54 nl-NL
drwxr-xr-x 2 root root    4096 Nov  6 23:54 pl-PL
drwxr-xr-x 2 root root    4096 Nov  6 23:54 pt-BR
drwxr-xr-x 2 root root    4096 Nov  6 23:54 pt-PT
drwxr-xr-x 2 root root    4096 Nov  6 23:54 qps-ploc
drwxr-xr-x 3 root root    4096 Nov  6 23:54 Resources
drwxr-xr-x 2 root root    4096 Nov  6 23:54 ro-RO
drwxr-xr-x 2 root root    4096 Nov  6 23:54 ru-RU
drwxr-xr-x 2 root root    4096 Nov  6 23:54 sk-SK
drwxr-xr-x 2 root root    4096 Nov  6 23:54 sl-SI
drwxr-xr-x 2 root root    4096 Nov  6 23:54 sr-Latn-CS
drwxr-xr-x 2 root root    4096 Nov  6 23:54 sv-SE


And on sudo efibootmgr -v, the following is the output:
ubuntu@ubuntu:/$ sudo efibootmgr -v
BootCurrent: 0000
BootOrder: 0001,0002,0000
Boot0000* EFI USB Device    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,800,3f8400,4f40d894)RC
Boot0001* Windows Boot Manager    HD(1,800,100000,fb31484d-ee7c-4e13-987f-d59077f342c3)File( \EFI\ubuntu\shimx64.efi)
Boot0002* Windows Boot Manager    HD(1,800,100000,fb31484d-ee7c-4e13-987f-d59077f342c3)File(\EFI\Microsoft\Boot\bootmgfw.efi)


Really appreciate your prompt replies.

---

### Post by Gaurav_Chhabra on 2014-11-14
Hey, I tried the method you mentioned, but my vaio doesn't show any boot section or to change the boot order.

> **irv said:**
> Awhile ago I installed Ubuntu with Win8 and could not boot into Ubuntu. 
From Win8  hold down the [Shift] key and rebooted. I then go to advance setting and go into the BIOS. Both installed should be in the boot section and all you need to do is change the boot order and it should boot into the grub and you can chose which OS to boot to. In my case Win8 didn't boot because when I installed Ubuntu I wiped out Win8.
I fixed all that and everything works now.

---

### Post by oldfred on 2014-11-14
Your UEFI shows two Windows Boot Manager boot options. One is really shimx64.efi and the other is really Windows or bootmfgw.efi.

Do both options work? Or is system confused with two similar names?
Do you also have a one time boot key, often f12. Some require both a initial key like your assist and then f12 or f10. Perhaps some of the other Sony threads mention how they did it.

Shim is the version of grub that will also work with secure boot on. But best to have secure boot off.
Most rename bootx64.efi and make either grub or shim have the bootx64.efi name. Then booting hard drive from UEFI menu boots Ubuntu while Windows entry still boots Windows.

---

### Post by Gaurav_Chhabra on 2014-11-14
I'm not quite sure what you mean by "Do both options work?" Also, I'll check about the one time boot key, also, do you recommend renaming shimx64.efi to bootx64, I'm not quite sure how that would fix the issue.
> **oldfred said:**
> Your UEFI shows two Windows Boot Manager boot options. One is really shimx64.efi and the other is really Windows or bootmfgw.efi.

Do both options work? Or is system confused with two similar names?
Do you also have a one time boot key, often f12. Some require both a initial key like your assist and then f12 or f10. Perhaps some of the other Sony threads mention how they did it.

Shim is the version of grub that will also work with secure boot on. But best to have secure boot off.
Most rename bootx64.efi and make either grub or shim have the bootx64.efi name. Then booting hard drive from UEFI menu boots Ubuntu while Windows entry still boots Windows.

---

### Post by oldfred on 2014-11-14
Can you get to UEFI boot options or one time boot key and choose Windows? And does it show two options for Windows and one is grub(shim) & the other Windows.

Yes many users of Sony & HP amoung others rename bootx64.efi in the /Boot folder in the efi partition. Then copy grub or shim into it and rename grub to bootx64.efi. Then from UEFI boot menu choose to boot hard drive.

I just saw this were a user scripted the entire rename.
       script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

---

### Post by Gaurav_Chhabra on 2014-11-14
I just can't get to the UEFI boot options, tried the "Assist" key. Also, there seems to be no one time boot key. (Just for information sake, it's a Sony Viao SVZ1311DGXX.)
In addition, I copied the shim to the Boot folder and renamed it to bootx64.efi. Didn't do the trick.

> **oldfred said:**
> Can you get to UEFI boot options or one time boot key and choose Windows? And does it show two options for Windows and one is grub(shim) & the other Windows.

Yes many users of Sony & HP amoung others rename bootx64.efi in the /Boot folder in the efi partition. Then copy grub or shim into it and rename grub to bootx64.efi. Then from UEFI boot menu choose to boot hard drive.

I just saw this were a user scripted the entire rename.
       script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

---

### Post by oldfred on 2014-11-14
There has to be a way to get into UEFI/BIOS. 

Some systems will reset if you totally power down, remove battery, hold power switch for a minute to drain residual power and reboot. That reboot should then let you use what every are the correct keys to get into UEFI.

My motherboard has its own fast boot in UEFI besides the fast boot in Windows. Both UEFI & BIOS normally review entire system on every boot to see if hardware has changed. Fast UEFI boot skips that check as most times hardware has not changed. But because it is fast you may not be able to get into UEFI to change settings. Mine also has a setting to use normal boot after a power failure or full power down. But even that is settable and then I think you may create cases where you could not get into system?

---

### Post by JeQhdMD on 2014-11-14
Gaurav - - when you get the VAIOcare | rescue mode black screen, have you tried the F2 key to get into BIOS?

---

### Post by Gaurav_Chhabra on 2014-11-15
Hey guys,

I'm sorry if I forgot to mention, I can get into the BIOS by pressing F2, but there's no UEFI boot options/menu there to choose which Operating System to boot into. Just the option of switching it between Legacy and UEFI. And for some reason, on using the Shift key while restarting from Windows 8, it doesn't show me the UEFI firmware settings.

---

### Post by oldfred on 2014-11-15
Some may have a setting to turn on the boot options. My motherboard required me to turn on USB ports for booting and go into CSM mode to turn on other settings also.
A few systems have had to have a password set to allow yourself to do additional settings. But never lose that password, if required or else you may brick system.

---

