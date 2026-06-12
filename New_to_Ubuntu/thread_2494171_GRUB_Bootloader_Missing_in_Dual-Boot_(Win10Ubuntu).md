---
title: "GRUB Bootloader Missing in Dual-Boot (Win10/Ubuntu) After Working with friends Drives"
date: 2024-01-07
forum: New to Ubuntu
---

### Post by nrpeyton on 2024-01-07
Hi,


I recently assisted a friend by installing Windows 11 on one of his NVMe drives and attempting non-destructive recovery on another. This involved frequent changes to the boot settings and plugging/unplugging drives, including my own.


Post this task (after handing his drives back), my dual-boot system (Windows 10/Ubuntu) no longer shows the GRUB bootloader in my 'ROG STRIX Z270H GAMING' motherboard's boot menu; only 'Samsung... 512GB SSD' and 'Windows Bootloader' are visible. Windows 10 boots normally, but I can't access Ubuntu.


I booted from a USB (Ubuntu 23.04) to access a 'Try Ubuntu' session, where I successfully mounted my Linux partition and viewed files. I installed and ran Boot-Repair with the recommended option, which completed with a success message. However, GRUB still doesn't appear in the boot menu after rebooting?


Here are the Boot-Repair logs:


**Before repair:** [https://paste.ubuntu.com/p/rDBP2Jm5zY/](https://paste.ubuntu.com/p/rDBP2Jm5zY/)
**After repair:** [https://paste.ubuntu.com/p/GH5ySgSQMx/](https://paste.ubuntu.com/p/GH5ySgSQMx/)


I'm looking for guidance on how to restore GRUB or otherwise access Ubuntu again.


Thanks in advance,


Nick Peyton

**Pictures of my BIOS **(set to optimised defaults)[B]:
[/B][https://1drv.ms/f/s!AoJyQR60QWlP6h6hSKHHBv57T9Ss?e=YfsFZ0](https://1drv.ms/f/s!AoJyQR60QWlP6h6hSKHHBv57T9Ss?e=YfsFZ0)
[IMG]https://onedrive.live.com/?authkey=%21ADKUEM%2DJ9Beuu70&cid=4F6941B41E417282&id=4F6941B41E417282%2113593&parId=4F6941B41E417282%2113597&o=OneUp[/IMG]

---

### Post by oldfred on 2024-01-07
Most UEFI seem to remove UEFI boot entries or modify them, when a drive is unplugged
And they seem to find Windows entry in ESP, but not any other system.

You should be able to use efibootmgr to add an entry or just reinstall grub using Boot-Repair or chroot.

For this error, many systems have additional settings in UEFI beyond Secure Boot.
Lenovo Locked UEFI/BIOS setting:
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
Lenovo Thinkpad T495 Boot Order Lock
[https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots](https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots)

---

### Post by tea for one on 2024-01-08
@oldfred
I hadn't seen these until now:-

Boot Order Lock
Lock UEFI BIOS Settings

Thanks for posting the latest UEFI tweaks (impediments?) - it's never-ending...........
I wonder what the next one will be?

---

### Post by nrpeyton on 2024-01-08
Hi everyone, I appreciate the responses so far. I've read the above posts and attempted various fixes, but issues with my GRUB setup persist.  I would appreciate further assistance.

My motherboard is the ASUS Strix Z270H Gaming, a mainstream enthusiast-grade/overclocking board. I've thoroughly checked all BIOS/UEFI settings, ensuring that both secure-boot and fast-boot are disabled. I've experimented with the Compatibility Support Module (CSM) settings, toggling between 'UEFI only' and 'UEFI+legacy' modes. With CSM disabled, only the Windows Boot Manager is visible in the boot options.  All other drives vanish, and I can't even load Ubuntu via my other drive's GRUB* (see below).*

I've managed to boot into Ubuntu by installing GRUB on a different SSD and running sudo update-grub in the terminal. However, this is just a stopgap solution as my primary/main SSD is no longer booting independently. Here are the key steps and commands I've tried:

[SIZE=4]Direct GRUB installation on the primary SSD (booted via other SSDs GRUB):[/SIZE]
```
[FONT=courier new]sudo grub-install /dev/sda[/FONT]
``` (after mounting, etc)


[SIZE=4]From a live USB:[/SIZE]

Mounting the necessary partitions and chrooting:

- ```
[FONT=courier new]for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt/ubuntu$i; done[/FONT]
```
- ```
[FONT=courier new]sudo chroot /mnt/ubuntu[/FONT]
```
```
[FONT=courier new]sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=Ubuntu[/FONT]
```




GRUB installation in UEFI mode:

```
[FONT=courier new]sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=Ubuntu[/FONT]
```

Attempting to manually add a boot entry with efibootmgr:

```
[FONT=courier new]efibootmgr -c -d /dev/sdb -p 2 -L "Ubuntu GRUB" -l '\EFI\Ubuntu\grubx64.efi'[/FONT]
```


Despite these varied attempts, I consistently encounter the error _***"EFI variables are not supported on this system"***_ across all methods.

To verify the status of secure-boot, I installed and ran mokutil, but it returned the same EFI variables error:

```
[FONT=courier new]~$ mokutil --sb-state[/FONT]
```_***"EFI variables are not supported on this system"***_ 

Given this situation, I'm looking for further insights or solutions to get my primary SSD to boot Ubuntu independently again. Any advice or suggestions would be greatly appreciated!

Nick

---

### Post by oldfred on 2024-01-08
If chrooting, you have to also mount the ESP.
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)

If specifying to install grub to another drive, partition other than sda1, you have to specify the drive & partition. And have to have an ESP. Generally already mounted in fstab if reinstalling from inside your install.
See
man efibootmgr
sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.


Also examples of use of efibootmgr in link below in my signature.

---

### Post by tea for one on 2024-01-08
> **nrpeyton said:**
> EFI variables are not supported on this system

In your UEFI settings, do you have other security options e.g.
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Device Guard or OS Optimised Defaults
If enabled, I suggest disable them.

---

### Post by nrpeyton on 2024-01-09
Hi, thanks for replies.

@olfred: I tried your suggestion (adding an entry manually).  I did it via the live USB. (The entry was added, but I still can't boot into Ubuntu in UEFI mode on my primary SATA SSD).  I *can *boot into Ubuntu in legacy mode from an old (now updated) GRUB on an older SSD.

@tea_for_one: I can only toggle it between PTT or dTPM, it is set to dTPM and 'other OS' (setting to 'other OS' I believe means secure-boot is off).  I'm definitely also on my motherboard's optimised defaults for UEFI/BIOS.  I can boot into Ubuntu from a legacy (non-UEFI) grub on another SATA SSD drive.  But I want my main drive to boot Ubuntu independently.

[B]
[SIZE=4]_View Device and Partition Info _[/SIZE][/B]
ubuntu@ubuntu:/$ **[COLOR=#B22222]sudo fdisk -l[/COLOR]**

Disk /dev/sdb: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A86380E7-0B19-4EF9-84A9-841BD5AD27CE

{
Device         Start       End   Sectors  Size Type
/dev/sdb1       2048    923647    921600  450M Windows recovery environment
**/dev/sdb2     923648   1128447    204800  100M EFI System**
/dev/sdb3    1128448   1161215     32768   16M Microsoft reserved
/dev/sdb4    1161216 770914175 769752960  367G Microsoft basic data
/dev/sdb5  975714304 976769023   1054720  515M Windows recovery environment
**/dev/sdb6  770914304 975714303 204800000 97.7G Linux filesystem**

Partition table entries are not in disk order.
}


**[SIZE=4]_Mounting 'EFI System Partition'_[/SIZE]**
ubuntu@ubuntu:/$ **[COLOR=#B22222]sudo mkdir /boot/efi[/COLOR]**
ubuntu@ubuntu:/$ [COLOR=#B22222]**sudo mount /dev/sdb2 boot/efi**[/COLOR]


**[SIZE=4]_Check Mount _[/SIZE]**
ubuntu@ubuntu:/$ [COLOR=#B22222]ls /boot/efi[/COLOR]
 EFI  'System Volume Information'
ubuntu@ubuntu:/$ ls /[COLOR=#B22222]boot/efi/EFI[/COLOR]
Boot  Microsoft  ubuntu 
ubuntu@ubuntu:/$ [COLOR=#B22222]ls /boot/efi/EFI/ubuntu[/COLOR]
BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi     

Looks Good [COLOR=#006400]&#10003;[/COLOR]

[SIZE=4]**_efibootmgr - Add Entry_**[/SIZE]
ubuntu@ubuntu:/$ **[COLOR=#B22222]sudo efibootmgr -c -d /dev/sdb -p 2 -L ubuntu -l \EFI\ubuntu\shimx64.efi[/COLOR]**
BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0001,0000,0005
Boot0000* Windows Boot Manager
Boot0005* UEFI: KingstonDataTraveler Duo, Partition 1
Boot0001* ubuntu [COLOR=#006400]&#10003;[/COLOR]

Looks Good (or so I thought, see below):



Rebooting didn't launch GRUB, even though the boot list showed the new 'ubuntu' entry. Disabling other boot options and selecting 'ubuntu' only redirected me back to the motherboard's UEFI/BIOS. The label **'P3: Samsung SSD 850 512GB ubuntu'** seems [SIZE=4]incorrect as it suggests Partition 3[/SIZE], which doesn't align with the partition specified in my efibootmgr command shown above or fdisk -l partition info.

Lastly, in olfred's reply, I'm not sure what you mean about [COLOR=#000000]fstab?  I did spend 30 minutes staring at the link in your signature, and a few hours reading subsequent links, etc. I've learnt a lot, but I'm getting lost. Any ideas?


Thanks, NIck
[/COLOR]

---

### Post by tea for one on 2024-01-09
> **nrpeyton said:**
> @tea_for_one: I can only toggle it between PTT or dTPM, it is set to dTPM and 'other OS' 
Can you double check the UEFI settings under [COLOR="#0000FF"]Advanced[/COLOR]?
Any sign of TPM or Discrete TPM?
Also, I noticed that one of your earlier screenshots indicated that Secure Boot was enabled - Can you toggle it to Disabled.

---

### Post by nrpeyton on 2024-01-09
> **tea for one said:**
> Can you double check the UEFI settings under [COLOR=#0000FF]Advanced[/COLOR]?
Any sign of TPM or Discrete TPM?
Also, I noticed that one of your earlier screenshots indicated that Secure Boot was enabled - Can you toggle it to Disabled.

TPM is handled in the PTT menu (video: [[SIZE=1]https://youtube.com/clip/UgkxsiIMnFlzQJiv0u6A7o_njZMNTluK-knb?si=TE8JEa47aV9tfc9a[/SIZE]]("https://youtube.com/clip/UgkxsiIMnFlzQJiv0u6A7o_njZMNTluK-knb?si=TE8JEa47aV9tfc9a")), the only toggle is between 'PTT' or 'dTPM'; I have it set to dTPM.  There is not a third choice, I have to pick one or the other.  I read that PTT is a TPM 2.0 software "emulator". dTPM is only v1.3. 

For secure boot, the 'enable/disable/ 'toggle' was "greyed out"!  I had to enter 'Key Management' and 'select 'Clear Keys'. Secure Boot toggle is now explicitly listed as disabled.

As it was the first time seeing secure boot disabled (explicitly) on that screen, I tried boot-repair again from a UEFI Live USB.  Still no luck: [https://paste.ubuntu.com/p/RyFbWbH5FW/](https://paste.ubuntu.com/p/RyFbWbH5FW/)

---

### Post by oldfred on 2024-01-09
I have seen a variety of systems with "locked NVRAM" issue, and not one simple solution.
Some UEFI have another setting beyond UEFI Secure boot.
Some reset UEFI to defaults. or just change some settings.

Try turning fast boot in UEFI settings off, until you get system working.

See ifyou have a setting like this:
Lenovo Locked UEFI/BIOS setting:
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
HP Zbook 15 NVRAM locked, install issues multiple settings
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)
[https://ubuntuforums.org/showthread.php?t=2489447](https://ubuntuforums.org/showthread.php?t=2489447)

Locked NVram
[https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up](https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up) & 
[https://ubuntuforums.org/showthread.php?t=2491460](https://ubuntuforums.org/showthread.php?t=2491460)  &
[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)
[https://ubuntuforums.org/showthread.php?t=2490084](https://ubuntuforums.org/showthread.php?t=2490084)

---

### Post by tea for one on 2024-01-10
> **nrpeyton said:**
> TPM is handled in the PTT menu, the only toggle is between 'PTT' or 'dTPM'; I have it set to dTPM.  There is not a third choice, I have to pick one or the other.  I read that PTT is a TPM 2.0 software "emulator". dTPM is only v1.3. 
For secure boot, the 'enable/disable/ 'toggle' was "greyed out"!  I had to enter 'Key Management' and 'select 'Clear Keys'. Secure Boot toggle is now explicitly listed as disabled.
As it was the first time seeing secure boot disabled (explicitly) on that screen, I tried boot-repair again from a UEFI Live USB.  Still no luck
It's pretty unusual that there isn't a UEFI setting to disable TPM, but, nevertheless, let's see what else can be done.

_Three suggestions_

(a) Boot into a live session and re-install grub via mounting the partitions and chroot (as you indicated in post 4)
This time, please post the command and output each time.

(b) In your video, I noticed that you have an option to boot into an EFI shell.
You can find the boot files there and try to start Ubuntu.
It's a bit fiddly if you haven't done it before.

(c) You can create a rEFInd Boot manager installed on a USB stick.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File
A USB with rEFInd for emergency use may help to find and boot an OS (if Grub is damaged/not responding)

Options include:-
Boot the kernel directly
e.g. Boot boot\vmlinuz-6.2.0-35-generic from 30 GiB ext4 volume

Find and boot the grub efi file
e.g. Boot EFI\ubuntu\grubx64.efi from 510 MiB FAT volume

Start an EFI shell
The instructions are similar to this:-
Identify your Efi System Partition e.g. FSO
Type FSO: i.e. FSO and colon symbol (press enter)
Then type \EFI\ubuntu\grubx64.efi (and hit enter)

Edit: If you can eventually boot into Ubuntu, it's worth trying to re-install Grub from a running session

---

### Post by nrpeyton on 2024-01-11
> **oldfred said:**
> I have seen a variety of systems with "locked NVRAM" issue, and not one simple solution.
Some UEFI have another setting beyond UEFI Secure boot.
Some reset UEFI to defaults. or just change some settings.

Try turning fast boot in UEFI settings off, until you get system working.

See ifyou have a setting like this:
Lenovo Locked UEFI/BIOS setting:
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
HP Zbook 15 NVRAM locked, install issues multiple settings
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)
[https://ubuntuforums.org/showthread.php?t=2489447](https://ubuntuforums.org/showthread.php?t=2489447)


Thanks for the response. Fast boot is off, and I'm booting the live USB in UEFI mode, confirmed by the 'UEFI' prefix in the boot option. My ASUS ROG firmware doesn't have a UEFI/BIOS lock setting. The closest is a security lock/password, but it's not set.


1st link: &#10003; No similar setting to UEFI/BIOS lock in my firmware.
2nd link: &#10003; No 'boot order' lock.
3rd link: &#10003; Conducted a hard reset by removing the CMOS battery and re-disabled secure boot, which is explicitly 'disabled'. (I learned to disable secure boot in ASUS ROG firmware, the 'PK' key must be deleted.
4th link: &#10003; Familiar with changing boot order and device settings, and overriding. Boot options definitely don't increase post-boot-repair in UEFI mode.

> **tea for one said:**
> It's pretty unusual that there isn't a UEFI setting to disable TPM, but, nevertheless, let's see what else can be done.



Thanks for reply; before I try each suggestion 1 by 1: What should I do with PCH-FW\PTT Configuration?  My UEFI firmware's optimised defaults are:
_TPM Device Selection - PTT or dTPM:_ dTPM
_PTP Aware OS - 'PTP Aware' or 'PTP Not Aware':_ PTP Aware

One final thing: despite 'Secure Boot' being listed expliclty as disabled and key-status expliclty listed as 'unloaded': If I try to launch the UEFI shell, I do still get a warning about 'secure boot'. I have tried running boot-repair again after clearing different combinations of key types.  No change to boot-repair's errors/warnings.  I even tried appending a 'DB' key for grubx64.efi and shimx64.efi.  I've spent days trying different combinations/settings.


**UPDATE/EDIT:**
I tried toggling dTPM to PTT, and with PTT, also tried both 'PTP Aware' and 'Not Aware': No combination of settings removed the 'secure boot' warning when trying to launch the EFI Shell.  *(Secure-boot was always still explicitly listed as disabled).*

---

### Post by tea for one on 2024-01-12
> **nrpeyton said:**
> PTP Aware OS - 'PTP Aware' or 'PTP Not Aware': PTP Aware
That's an unfamiliar phrase for me, so I conducted a brief internet search and found:-
[https://us.informatiweb.net/tutorials/it/bios/enable-the-tpm-2-0-module-on-your-motherboard.html](https://us.informatiweb.net/tutorials/it/bios/enable-the-tpm-2-0-module-on-your-motherboard.html)
Within this article, there seems to be an option to disable both PTT and PTP Aware OS
This could be the same as disabling TPM.
Certainly, worth further exploration.

I have a netbook, where an installed Xubuntu OS will not boot if PTT is enabled.
External USB devices will always boot.

PTT enabled - Successfully boots via EFI shell
PTT enabled - rEFInd successfully boots these options
[LIST]
[*]EFI\ubuntu\grubx64.efi
[*]boot\vmlinuz-5.15.0.91-generic
[*]starts EFI shell
[*]
[/LIST]
Re-installing Grub via a live session with chroot failed on my device.

In your position, I would first play around with the PTT/PTP settings.
If that proves unsuccessful, then pop rEFInd on a USB stick.

Edit: PTP acronym - Precision Time Protocol or Platform Trust Protocol?

---

### Post by nrpeyton on 2024-01-17
**TLDR:**
Having expended a week-long effort, I've implemented a temporary solution *(not a complete fix) *to my dual-boot issue. I created a 2.00MB  [FONT=courier new]bios_grub [/FONT]partition using GParted and reinstalled GRUB.  Currently, I can boot into Windows or Ubuntu by directly selecting the boot option from my motherboard's UEFI firmware (I.E., toggling EFI mode on/off). It's not ideal, as it doesn't allow me to boot Windows directly from GRUB, but it's a workable interim solution.


**Detailed Update:**
I'm currently preparing for a certification and found myself increasingly frustrated, having spent nearly a week trying to resolve this issue. However, I realise that this experience is not entirely a loss. It's reminiscent of my younger days learning through trial and error with Windows, only this time with Linux. It's an unexpected but valuable learning curve in understanding Linux more deeply.  

Time permitting I will definitely revisit this ASAP *(I don't accept defeat easily, lol). *

---

