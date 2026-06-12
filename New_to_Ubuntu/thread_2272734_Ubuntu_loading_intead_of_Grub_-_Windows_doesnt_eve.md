---
title: "Ubuntu loading intead of Grub - Windows doesnt even start from bios"
date: 2015-04-08
forum: New to Ubuntu
---

### Post by MountainAsh on 2015-04-08
Hi,

I installed windows on a 1tb SSD the other day and today went through the instructions of installing ubuntu on a second 1tb SSD. I then disabled fast boot etc.

I clicked the bottom option allowing me to choose the disk.

Noted down that my windows 8.1 was installed on sda.

Created the partitions for sdb (to install ubuntu). They were swap, ext4 /home and ext 4 /.

I then selected that it installed the boot loader to sda because I read that it does something with the master boot record in windows.

I then clicked install

When I started up the computer it went right in to ubuntu not showing grub or anything, so I went in to the bios and tried to manually boot in to the windows 8.1 drive. It didnt work. This is when I thought that I had over written it so I went in to Ubuntu and opened up Disks. This then showed me that the NTFS partitions for the Windows 8.1 were still there.

Does anyone know why it isnt giving me an option to boot in to windows or what is wrong and how to solve it?

Thanks.

---

### Post by michi1983 on 2015-04-08
Hi,

first of all please post the output of ```
sudo fdisk -l
``` so we can verify that all partitions from windows are still here :)

Second, what version of Ubuntu did you install? 14.04? 14.10?

Third, please post the output of ```
 grep menuentry /boot/grub/grub.cfg
```

---

### Post by MountainAsh on 2015-04-08
1. There is more, but i think they are for my other drives so not really needed? (The others are all currently empty as this is a new build)

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xec9c9239

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848  1953521663   976401408    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5a9a803d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     7813119     3905536   82  Linux swap / Solaris
/dev/sdb2         7815166  1953523711   972854273    5  Extended
/dev/sdb5   *     7815168    27344895     9764864   83  Linux
/dev/sdb6        27346944  1953523711   963088384   83  Linux
```

2. 14.04

3. Can you possibly explain what this one is showing? Is it that its uefi?
```
if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
  menuentry_id_option=""
export menuentry_id_option
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-bec23916-98e5-4249-a39c-5ec4ae0c49ef' {
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-bec23916-98e5-4249-a39c-5ec4ae0c49ef' {
    menuentry 'Ubuntu, with Linux 3.16.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-33-generic-advanced-bec23916-98e5-4249-a39c-5ec4ae0c49ef' {
    menuentry 'Ubuntu, with Linux 3.16.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-33-generic-recovery-bec23916-98e5-4249-a39c-5ec4ae0c49ef' {
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-advanced-bec23916-98e5-4249-a39c-5ec4ae0c49ef' {
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-recovery-bec23916-98e5-4249-a39c-5ec4ae0c49ef' {
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
```

---

### Post by michi1983 on 2015-04-08
Your output of grub.cfg shows that it doesn't recognize any Windows Partitions.
Can you start Windows when you hit the boot selection button on startup? So that you can explicitly chose the hard disk where Windows is installed on?

[Here ]("http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot")is another link which might help you.
And another one [here]("http://linux.about.com/od/LinuxNewbieDesktopGuide/ss/The-Ultimate-Windows-81-And-Ubuntu-Dual-Boot-Guide_15.htm") and [here]("http://linux.about.com/od/LinuxNewbieDesktopGuide/tp/3-Ways-To-Fix-The-UEFI-Bootloader-When-Dual-Booting-Windows-And-Ubuntu.htm").

Both say that it is important to switch OFF fastboot in Bios.

---

### Post by MountainAsh on 2015-04-08
No, I can't. But why would that be when it was working fine before installing Ubuntu and the files are all there?

Ill have a read through that now.

---

### Post by michi1983 on 2015-04-08
> **MountainAsh said:**
> No, I can't.

What you mean with you can't? The hard disk - where Windows is installed - doesn't show up at all when you hit the boot selection button?
Or do you click on it and it does what exactly?

> **MountainAsh said:**
> [COLOR=#000000]But why would that be when it was working fine before installing Ubuntu and the files are all there?[/COLOR]

Because you installed another bootloader (grub) which is new to the system. and it handles the starting process of your computer. you might also have made a mistake about uefi/efi but I am not familiar with this uefi stuff :/

---

### Post by MountainAsh on 2015-04-08
Whilst testing the booting from the windows SSD. I noticed that it loads up a purple screen briefly then cuts out before loading in to Ubuntu could this be the grub trying to start and failing?(I thought that the grub menu was all black though so not sure)

---

### Post by MountainAsh on 2015-04-08
> What you mean with you can't? The hard disk - where Windows is installed  - doesn't show up at all when you hit the boot selection button?
Or do you click on it and it does what exactly?

When I boot one disk it goes to ubuntu (what it does when I turn it on)
When I select the other it goes dark a curser flashes breifly then back in to the bios boot menu.

Will double check fast boot in the bios - I turned it off in windows for 100% though

---

### Post by michi1983 on 2015-04-08
Hm, here is the exact same problem:
[http://ubuntuforums.org/showthread.php?t=2217538](http://ubuntuforums.org/showthread.php?t=2217538)

You might find the answer here

---

### Post by oldfred on 2015-04-08
You have a new system, so it is UEFI with CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You have the old BIOS with MBR partitioning that BIOS uses, not the newer UEFI with gpt partitioning.
How you boot install media for both Windows & Ubuntu is how it then is installed UEFI or BIOS.

With two drives you should have just installed grub to sdb and left a Windows boot loader in sda. Then in BIOS you can switch which drive to boot from, but when booting sdb, grub will offer Windows as an alternative.
Some also just connect one drive to install Windows, then just connect the other drive to install Ubuntu. Then each drive is totally separate and can be booted from BIOS. You have to run sudo update-grub to get grub to then find the Windows install when Windows drive is plugged back in.

There are some advantages to UEFI and gpt partitioning. But you would have to totally reinstall both systems.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

I also prefer with larger drives to have smaller system partitions like 25GB for Ubuntu and rest of drive as /home or what I use /mnt/data and other partitions for backup, installers and others. Windows system partition typically needs to be twice the size of Ubuntu but also can have a separate NTFS data partition. That also is an advantage if you want to read/write to NTFS from Ubuntu as writing into the Windows system partition often leads to issues. But either way you must have Windows fast startup or always on hibernation off.

You probably left the fast startup on in Windows. With the hibernation flag set the NTFS driver in Linux will not let you mount the NTFS partition, normally. But then os-prober cannot see into NTFS partition to find the Windows boot files. You probably have to restore a Windows boot loader to sda with your Windows repair disk or installer or Boot-Repair to boot Windows and turn off fast startup.

      
 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://mjg59.dreamwidth.org/24869.html](http://mjg59.dreamwidth.org/24869.html)

---

### Post by MountainAsh on 2015-04-08
Thanks for your help.
I didn't see the latest reply but I decided to re install anyway. I know have them both on separate SSD's (also removed the swap space after learning that was bad).

Fast boot and secure boot is and always was off. As was fast startup in windows power options.

Now the issue has changed that the grub menu appeared once but then I ran sudo update-grub and it never appeared since. Also I can't seem to put the drive with Ubuntu on it in to the boot priority list (Motherboard is Asus X99-E).

But thanks anyway!

---

### Post by oldfred on 2015-04-08
Install Boot-Repair into Ubuntu or Ubuntu live installer and run just the summary report.
Do not run auto fix as that will install grub to all drives.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

