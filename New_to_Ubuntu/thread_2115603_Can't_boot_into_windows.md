---
title: "Can't boot into windows"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by hpkeyser on 2013-02-13
Help! I'm unable to boot into my windows partition now.  I installed 12.04 LTS x64 and now when I'm trying to boot back into my windows partition I can't do it.  I've tried loading up into a windows disk to do a bootrec /fixmbr and a /fixboot, but the fixboot isn't working.  It's saying that there's nothing to be found.  I also tried the bootrepair in linux and it didn't work.  Can someone please help me?

Thanks

---

### Post by carl4926 on 2013-02-13
If it's not already, in Ubuntu install Gparted

Then with Gparted, take a screen of your HD

Or using a terminal post the result of this
```
sudo fdisk -l
```

---

### Post by hpkeyser on 2013-02-13
sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
256 heads, 63 sectors/track, 90845 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x527cd163

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1440065535   720031744   83  Linux
/dev/sdb2      1440067582  1465147391    12539905    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5      1440067584  1465147391    12539904   82  Linux swap / Solaris

[http://imgur.com/FgXzBgU](http://imgur.com/FgXzBgU)  sda
[http://imgur.com/oCn25h9](http://imgur.com/oCn25h9)  sdb

---

### Post by carl4926 on 2013-02-13
Windows is still there and you should be able to access your files there from Ubuntu if necessary

Please try the following
Make sure Ubuntu is updated
Then do:

```
sudo update-grub
```

I am wondering though, that your windows HD is sdb not sda
That is OK, but not usual
Were the HD's always that way?

---

### Post by hpkeyser on 2013-02-13
I am able to access the files from ubuntu.  I'm going to update the grub in a minute.  Also, the windows partition seems to be sda based on what i'm seeing in gparted. Ubuntu is on sdb.  I think the problem lies in the error i'm receiving on gparted for that one part of the drive. I'll post a picture so that you can see the details more.

[http://imgur.com/kIMGLSQ](http://imgur.com/kIMGLSQ)

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda3
Found Windows Recovery Environment (loader) on /dev/sda4
done

---

### Post by Mark Phelps on 2013-02-13
Since these are physically separate drives, I would try the following:

First, disconnect the Ubuntu drive and see if you can boot from the Win7 drive.  I suspect that will not work.

Second, how did you do the Win7 repair commands? Did you boot from a Win7 DVD? Or did you try running them from a Win7 command line?

If you used a DVD, then boot from that (with ONLY the Win7 drive connected), select the Repair option, and run that three times -- as sometimes, it takes all three passes to get it booting again.

---

### Post by carl4926 on 2013-02-13
I agree with @MP

Just add the win7 repair:
With just the windows HD connected

> Win7 Boot repair:
Boot off the windows 7 installation DVD
Proceed to the screen "Windows 7 / Install Now" BUT DO NOT click to install
Select to "Repair your computer"
Select/put the radio button/dot next to "Use recovery tools that can help fix problems" --> Next
Select "command prompt"
enter this command: Bootrec.exe /FixBoot
enter this command: Bootrec.exe /FixMbr
enter this command: exit
Click to Restart 

---

### Post by arpanaut on 2013-02-13
With the efi partition on the Win drive, I suspect it was installed with uefi enabled, and it looks like Ubuntu was installed in legacy bios mode, so I presume that the win is not booting because efi has been turned off.

Suggestion, install "Boot Repair" and generate the boot info report, then post the pastebin url here, it should give suggestions of how to fix at the end of the report. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Further reading:  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by hpkeyser on 2013-02-13
So i'm going to run boot repair again. i'm looking at the advanced options and i have the option to restore the MBR, should i allow that before I run it or should i just run a recommended pass and then generate the boot report?


Here's the pastebin: [http://paste.ubuntu.com/1646236/](http://paste.ubuntu.com/1646236/)

---

### Post by hpkeyser on 2013-02-13
@carl and @MP.  Your recommendation is that I remove the linux drive and then go ahead and boot into the repair for windows with only the windows as the active drive? Then once that has been done a couple of times, remount the linux drive and hopefully I'll be able to see a dual boot screen on the way into windows?

I'm going to see if that works. Hopefully the pastebin info might shed some light on the issue while I'm working at this.  I'll get back you you guys in a bit with any results

---

### Post by arpanaut on 2013-02-13
did you see this at the bottom of the Pastebin file:
> Boot successfully repaired.  
You can now reboot your computer. 
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file

---

### Post by hpkeyser on 2013-02-13
So how do i get my BIOS to do that then? it's an american megatrends BIOS if that helps.  I'm really unsure of how to get this up and going.

Also, I tried letting it reboot, and it loaded up to the starting windows screen (Win7) and then it acted as though it were going to try to do a startup repair and then came back to the grub boot loader.

I'm caught in a boot loop here.  It keeps coming back to the GRUB boot loader. Also, when I tried booting the disk for Windows via UEFI boot, and then went to do the repair I got an error from windows like this:

> This version of System Recovery Options is not compatible with the version of Windows you are trying to repair.  Try using a recovery disc that is compatible with this version of Windows.

My guess is because I'm running 7 home premium and the disk I've got is 7 professional.  

Also, when I tried to do the fixboot on a non-UEFI boot, I was able to get into the repair tools.  I got into the command prompt and fixmbr worked, but fixboot did not.  I got an error:

> element not found

Any and all help is appreciated.

---

### Post by carl4926 on 2013-02-13
> **hpkeyser said:**
> @carl and @MP.  Your recommendation is that I remove the linux drive and then go ahead and boot into the repair for windows with only the windows as the active drive? Then once that has been done a couple of times, remount the linux drive and hopefully I'll be able to see a dual boot screen on the way into windows?

I'm going to see if that works. Hopefully the pastebin info might shed some light on the issue while I'm working at this.  I'll get back you you guys in a bit with any results

Correct
With just the windows drive connected, try the repair.

But why are you not in possession of the same windows version as you have installed.? Perhaps it's time to backup the files from your windows install and do a clean install of windows 7 pro?
You could revert it back to a standard MBR partition table too?

---

### Post by charlesDean on 2013-02-14
Hello,
As some one told you should be able to access your files there from Ubuntu.

write code : sudo update-grub

---

### Post by hpkeyser on 2013-02-14
> **carl4926 said:**
> 
But why are you not in possession of the same windows version as you have installed.? Perhaps it's time to backup the files from your windows install and do a clean install of windows 7 pro?
You could revert it back to a standard MBR partition table too?

I'm not in possession of the same disk because it came preloaded with Home Premium and it didn't ship with that disk along with it.  I've only got a Professional disk because I'm still a student and it's included in my tuition to have that. I'm not looking forward to having to draw all of my windows files into a hard drive and then reinstalling windows.  If i do end up doing that, will I still be able to dual boot if the MBR recognizes linux on the secondary drive?

---

