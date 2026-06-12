---
title: "Not sure how to dual boot menu"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by Gian_Ross on 2014-03-19
I read many posts about this and this seemed the closest [http://ubuntuforums.org/showthread.php?t=2194229&highlight=duel+boot+menu](http://ubuntuforums.org/showthread.php?t=2194229&highlight=duel+boot+menu). However, during boot up, I'll hit F8 to get to the boot menu and if I boot the  deive ending in 00N7B0 Ubuntu will boot fine. Could you please help me get the menu please. While reading those posts, I noticed a closed post about customizing the menu, which I'd like to be able to do.

TY :)

Rosso

---

### Post by su:bhatta on 2014-03-19
If  you did install Ubuntu it should by default load a GRUB .  You don't have to hit F8, GRUB screen will give the different boot options.
That is the first screen you should see when the computer boots up. There you will find the different OS's that you can choose from using the 'Arrow keys".
Did you choose to install GRUB in the same partition as the Ubuntu OS? 

You can run BOOT repair to reinstall GRUB.You can have a look at these threads: 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134) is this what you were looking for to customize GRUB?

---

### Post by Mark Phelps on 2014-03-19
Unfortunately, when you install a Linux distro on a drive for a machine already running another OS, GRUB does not always add the necessary entries.

To fix this, you may need to do the following:
1) Set your boot preference in the BIOS to boot the drive containing the Linux distro first in the sequence of drives
2) Boot into the Linux distro -- with all other drives connected
3) Open a terminal and enter "sudo update-grub".  This will run os_prober which will scan for other OSs on the drive and, if found, will add entries to the default GRUB config file for them.
4) Reboot

You should then get a GRUB menu with entries for Ubuntu and the other OS(s).

---

### Post by Gian_Ross on 2014-03-21
Sorry I haven't gotten back to you until now. My BIOS is only showing my SSD and my other drive. The only thing I can do is boot directly in to it.

TY :)

---

### Post by Mark Phelps on 2014-03-21
OK ... then boot into Ubuntu, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  This will list out the disks and partitions on your PC.

That will give us a better idea of what the BIOS is seeing.

---

### Post by Gian_Ross on 2014-03-21
It looks to me the boot is on the right drive?

> rosso@rosso-System-Product-Name:~$ sudo fdisk -l
[sudo] password for rosso: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1765

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    48828415    24413184   83  Linux
/dev/sda2        48830462   976771071   463970305    5  Extended
/dev/sda5        48830464    56641535     3905536   82  Linux swap / Solaris
/dev/sda6        56643584   976771071   460063744   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6324ee38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2   *      206848   234438655   117115904    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x28b45cf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 15.6 GB, 15606349824 bytes
116 heads, 52 sectors/track, 5053 cylinders, total 30481152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        8064    30481151    15236544    c  W95 FAT32 (LBA)

Disk /dev/mapper/cryptswap1: 3999 MB, 3999268864 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x52fad2f1


---

### Post by Mark Phelps on 2014-03-21
I'd worry about customizing the menu AFTER I got the default menu to work.

Linux doesn't use the boot flag, so that being on the "wrong" partition would not affect it.

Windows, however, requires the boot flag, and if your SSD is the 120GB drive (sdb), it looks like the boot flag is on the wrong partition -- presuming that sdb1 is the boot partition and sdb2 is the OS partition.

Also, you said your BIOS doesn't see the SSD, but "fdisk" is not going to see drives the BIOS doesn't see, and it DOES show the SSD (presuming it is the 120GB drive), so I'm confused about what you're claiming.

---

### Post by Gian_Ross on 2014-03-21
> [COLOR=#000000]My BIOS is only showing my SSD and my other drive.[/COLOR]

Do you mean the boot flag for windows is on the wrong partition or Ubuntu? I was claiming the BIOS doesn't show the drive with Ubuntu on it, in order to do what you said originally.

Thx

---

### Post by Gian_Ross on 2014-03-22
I believe I found a way to temporarily assign the Ubuntu drive. If so do you still want me to try these instructions? I'll await your response.

> **Mark Phelps said:**
> Unfortunately, when you install a Linux distro on a drive for a machine already running another OS, GRUB does not always add the necessary entries.

To fix this, you may need to do the following:
1) Set your boot preference in the BIOS to boot the drive containing the Linux distro first in the sequence of drives
2) Boot into the Linux distro -- with all other drives connected
3) Open a terminal and enter "sudo update-grub".  This will run os_prober which will scan for other OSs on the drive and, if found, will add entries to the default GRUB config file for them.
4) Reboot

You should then get a GRUB menu with entries for Ubuntu and the other OS(s).

Thx again :)

---

### Post by Gian_Ross on 2014-03-29
Mark,

I successfully ran that command, said it found it and reconfigured, but still no menu. Do I need to keep it set in the BIOS to boot the drive with Linux on it first?

TY :)

---

### Post by sotiris2 on 2014-03-29
So you ran ```
sudo update-grub
``` you saw it report finding windows but you still do not get a Grub menu on boot? Does it boot to Ubuntu or to Windows? 

With the Ubuntu drive selected as boot device hold down Shift during boot and you should get the Grub menu, check if Windows is listed there, and if it is select it. If it boots , then we have a very simple problem to make the grub menu appear by default. 

If you don't get a grub menu with shift, try selecting a different boot device and holding shift. It must be installed somewhere if you can boot Ubuntu even if not on Ubuntu's drive. 


Report back with results.

---

### Post by Gian_Ross on 2014-03-31
I switched to the drive with Linux, booted in to it and ran "sudo update-grub". After it said it reconfigured grub (something to that effect), I went back in to BIOS and switched the drive back. So yes, it boots up Windows. Is the problem, that I switched back to the original boot when it should of stayed with the drive that has Linux on it?

Thanks for your response :)

---

### Post by oldfred on 2014-03-31
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Then we can see where everything is installed. 
Also do not run auto fix with Boot-Repair as it installs grub to every hard drive. You want grub only on Linux drive & Windows on Windows drive and BIOS set to boot Linux drive by default.

---

### Post by Gian_Ross on 2014-04-01
I ran/installed and created the infomation: paste.ubuntu.com/7188033/ [email]boot.repair@gmail.com[/email].

Thx for the help :)

---

### Post by oldfred on 2014-04-01
You have the grub boot loader in the MBR of drive that is sda. And a Windows boot loader in sdb.
From BIOS or one time boot key (f12 on my system but varies by vendor) you should be able to directly boot with grub or Windows. 
If you set BIOS to boot sda as default then you should get grub menu to boot Ubuntu or Windows. Then if you ever had issues with drive sda, you still could use one time boot key to boot Windows directly.

You did install grub to the PBR or partition boot sector of sda1. That is extremely rarely used and not recommended. But it is not an issue. Windows does have to have its boot code in the Windows PBR as well as MBR.

---

### Post by Gian_Ross on 2014-04-01
What did I do wrong during installation to cause "[COLOR=#000000]partition boot sector of sda1"? Is there a way to remedy it, even though you say it won't be an issue?


Ok, I know have the enu with OS options, could you please tell me what I need to edit/do in order to make windows the default boot, as well as the time to choose?

TYVM :)[/COLOR]

---

### Post by sotiris2 on 2014-04-01
If you are seeing the menu. Count what option windows is in the list. (press left arrow to make it stop and not boot automatically). 

Get in ubuntu, run 

```
gksudo gedit /etc/default/grub
```

In the text file that opens, find the line 

  **GRUB_DEFAULT=0**

change the 0 to the previous number to the one windows was in your list. For example if windows was fifth put 4. It's because the first choice is 0.
Other useful options here are:

 **GRUB_TIMEOUT=10**

Where you can change the 10 to how many seconds you want the menu to wait before booting the default option. 

Now save and close. And run again

```
sudo update-grub
```

---

### Post by Gian_Ross on 2014-04-02
[[COLOR=#000000]sotiris2[/COLOR]]("http://ubuntuforums.org/member.php?u=1845661")[COLOR=#000000] ,

TYVM for those instructions that takes care of that.

Thx everyone :)
 
I forget how to close this?[/COLOR]

---

### Post by Iowan on 2014-04-02
Close - as in mark [SOLVED]?
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

