---
title: "It seems Ubuntu cannot support computers wth 3TB hard drives?"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by Samizdat_Press on 2012-01-14
I am trying to install Ubuntu 11.10 (dual boot) and am choosing the custom option so I can create separate partitions but I get an error every single time when I hit "add". 

**"Starting sector number, 4,295,469,056 exceeds the msdos-partition-table-imposed maximum of 4,294,967,295"**


I have a 1.5TB drive as my main HDD, and a 3TB HDD as the slave.   (I think the error is coming from the fact that I have a 3TB HDD)

It will let me add the /boot partition @ 258mb but will not let me add any others (SWAP, /home, /root etc). 

What does this error mean? Changing the size of the proposed partition doesn't change anything, nothing works. I am trying to install it on my 1.5TB master drive (where my current win7 OS lives). If I try selecting the "free space" on my 3TB drive it won't even let me hit the "add" button. 


I have been trying for 2 days to install Ubuntu but can not get it to work. Please help :(



System:

i7 3.4ghz
10GB RAM 
1.5TB HDD
3TB HDD
Win7 SP1

---

### Post by carl4926 on 2012-01-14
[http://askubuntu.com/questions/84538/trouble-creating-3tb-ext4-partition-due-to-msdos-partition-table-imposed-error](http://askubuntu.com/questions/84538/trouble-creating-3tb-ext4-partition-due-to-msdos-partition-table-imposed-error)

---

### Post by hansdown on 2012-01-14
Welcome to the forum, Samizdat_Press.

You need to defrag, in windows, then shrink the partition, in windows, then try the install, choosing the right drive, and "use free space".

[http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html](http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html)

EDIT:

carl4926, seems to have a better cure.

---

### Post by Samizdat_Press on 2012-01-14
> **carl4926 said:**
> [http://askubuntu.com/questions/84538/trouble-creating-3tb-ext4-partition-due-to-msdos-partition-table-imposed-error](http://askubuntu.com/questions/84538/trouble-creating-3tb-ext4-partition-due-to-msdos-partition-table-imposed-error)

Thank you for the reply Carl. I have already done that though :(. 

"If you need a partition larger than 2TB, you will need to repartition  the drive using the GUID Partition Table (GPT) format for the disk."

I have done this already. My 3TB drive isn't recognized by Win7 so it shows as one 2TB drive and the remaining ~700GB shows up as a separate partition (in windows it shows up as a third drive) So it stops at 2 gigs and then the remainder shows up as a second separate HDD. GUID format. 

"If  you are not trying to boot off this new disk, you are unlikely to run  into any compatibility problems"

I am not trying to boot off the larger disc. I am trying to install it on the 1.5 TB one. 


The problem is that it combines it all together and I can't seem to make it differentiate between the two drives so that this conflict can be resolved.

---

### Post by Samizdat_Press on 2012-01-14
> **hansdown said:**
> Welcome to the forum, Samizdat_Press.

You need to defrag, in windows, then shrink the partition, in windows, then try the install, choosing the right drive, and "use free space".

[http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html](http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html)

EDIT:

carl4926, seems to have a better cure.

Thank you hansdown for the advice and also the warm welcome. I will defrag now and then try the process again. Will report back once completed in a few minutes.

Edit: I am assuming I should shrink the main partition on my 1.5TB HDD (the one where my program files is located) and make it large enough for my Ubuntu installation right?

---

### Post by oldfred on 2012-01-14
Download to liveCD from repository gdisk and run this (if not sdb change to whatever drive it is):

```

sudo apt-get install gdisk
sudo gdisk -l /dev/sdb
```

Did you create any partitions before using gparted?

---

### Post by mastablasta on 2012-01-14
> **Samizdat_Press said:**
> 
Edit: I am assuming I should shrink the main partition on my 1.5TB HDD (the one where my program files is located) and make it large enough for my Ubuntu installation right?

don't know how many partitions you have, but yeah you can shrink whichever you want. just remember that there is a limited number of primary partitions that can be on the disk. no worries as linux can install to extended.


also regarding ext4 file system disk size support:
> 
Large file system
The ext4 filesystem can support volumes with sizes up to 1 [exbibyte (EiB)]("http://en.wikipedia.org/wiki/Exbibyte") and files with sizes up to 16 [tebibytes (TiB)]("http://en.wikipedia.org/wiki/Tebibytes")

---

### Post by Samizdat_Press on 2012-01-14
Okay so I was able to get past the installation phase by getting it int GPT format, shrinking the hard drive etc. It still gives me the error on the3TB HD but the 1.5TB one doesn't give me any problems so I installed it to that.

I then used EasyBCD to set up the dual boot menu on startup. 

Now, when I choose Ubuntu, it takes me to a command prompt "GRUB>" 


Is this where I should specify where my /boot kernel etc is?" It doesn't say what it needs to know so I am just shooting in the wind.


Edit: It looks like this. Note this is a screenshot from what appears to be an older version. I am using 11.10.   Should this be happening after a fresh install?

[IMG]http://aaron-kelley.net/wp-content/uploads/2011/04/grub.png[/IMG]

---

### Post by grahammechanical on 2012-01-14
Ubuntu uses a bootloader called Grub (GRand Unified Bootloader). Even if Ubuntu is the only Operating System on the machine Grub will still be used but if there was only on OS then the Grub menu would not appear.

It is my guess that the boot loader that you have set up is not booting into Ubuntu but it is booting into Grub and because Grub is not configured to load the Ubuntu boot file then what you are getting is the Grub command line.

I am not expert enough to advise you further.

Regards.

---

### Post by spacecheck on 2012-01-14
> Is this where I should specify where my /boot kernel etc is?Yes. What is shown, when you enter the command: ```
ls
``` ? Details on how to move forward from your position are shown here:
[https://help.ubuntu.com/community/Grub2 ]("https://help.ubuntu.com/community/Grub2")
probably best beginning around [chapter 8 section 2]("https://help.ubuntu.com/community/Grub2#GRUB_2_Prompt_Usage") "GRUB 2 Troubleshooting Preparation"
[]("https://help.ubuntu.com/community/Grub2")

---

### Post by oldfred on 2012-01-14
Since you have two drives, have you tried booting from other drive? You may have the newest grub in the other drive.

Do you have a separate /boot? Most desktops do not nor need one. Servers, RAID or LVM systems may need one. New systems with UEFI has an efi partition that has boot files for every install.

Boot-Repair will often repair minor booting issues and can run bootinfo script. Run the new test version of boot script as it has some fixes that make it better.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Samizdat_Press on 2012-01-14
Okay so I reinstalled the whole thing because apparently my error was using FreeBSD instead of letting Grub handle it.

So I reinstalled it, and now the computer upon restart boots directly into Win7. So how do I go about using GRUB to make it so that I have the option of which OS to boot into on startup?


Edit: my bios is UEFI x86_64 if that helps.

---

### Post by Samizdat_Press on 2012-01-14
So I have Ubuntu installed on dev/sda but I can't figure out how to dual boot into it. I can't figure out how to make grub work either. I asked elsewhere and they said installing grub would overwrite my windows bootloader and destroy my win 7 so can't do that. 

Is there any easy way to make the computer dual boot once Ubuntu is installed? Using FreeBSD just brought me straight to the "GRUB>" command line. 

Here is a screen-shot of my fdisk -l

[IMG]http://i817.photobucket.com/albums/zz94/CitizenStew/ee4d8c77.jpg[/IMG]



I tried "sudo grub-install /dev/sda" but it said device could not be found. Apparently that is good because it would have wrecked my window7 OS if it worked according to someone else I asked. Please help guys :(

---

### Post by carl4926 on 2012-01-14
I have a suggestion for you.

I understand, (but I stand to be corrected,) that Fedora 16 could help you.

I want to point you to a thread at openSUSE where I work. Mostly because it contains the info I think might enlighten you
[http://forums.opensuse.org/forums/english/get-technical-help-here/install-boot-login/470470-help-getting-error-parted-magic.html](http://forums.opensuse.org/forums/english/get-technical-help-here/install-boot-login/470470-help-getting-error-parted-magic.html)

It's a long read and the user 6tr6tr, I'm fairly sure didn't know exactly what he had.
Irony is, Fedora was mentioned but we never used it, but rather Ubuntu.
But in either case it seems it was not even necessary.

---

### Post by oldfred on 2012-01-15
You do not have a FAT efi partition as the first partition, so your Windows is installed in MBR/BIOS mode. Your only gpt drive is the second one. Windows installs to gpt only in UEFI.

Post bootinfo script otherwise we are guessing at your overall configuration.

---

### Post by mastablasta on 2012-01-16
> **oldfred said:**
>  
Post bootinfo script otherwise we are guessing at your overall configuration.
 
 
that and it's not true that windows will be destroyed. it just replaces their boot loader so that grub selects which system will boot instead of windows boot loader.

---

