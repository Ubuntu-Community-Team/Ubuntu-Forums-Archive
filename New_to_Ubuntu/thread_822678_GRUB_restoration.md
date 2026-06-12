---
title: "GRUB restoration"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Syndacate on 2008-06-08
I just had a 3-4 hour fight with my computer because I'm into playing with other distros, but to me, liveCD's and VM/parallels stuff is useless.  So I went to try FreeBSD, who's boot loader did not play nice (froze up) with my computer (DV9000).  So I used a program called unetbootin through windows which changed the boot.ini file to boot FreeBSD without their gay boot loader.  So it installed, and put their boot loader back on, and then I was stuck.

Here's where things got bad:  I tried to put GRUB on, though there was no distributions installed to get it from - I was trying to install it from live CD's, I couldn't even compile it from source because gparted doesn't have a C compiler and I didn't have any distros handy.

Finally I went to Ubuntu's live CD to skip the install and install GRUB - well it didn't skip the install, so I got Ubuntu on it (not sure if I'm going to keep it or not, 10Gb is kinda small for what I'd give Ubuntu, though it'd provide some Linux stability..) - I use Ubuntu daily on my desktop, afraid to upgrade I'm playing in gutsy.

That's all irrelevant, the point is I need a fast way to restore GRUB in case I put any other bad operating systems on that rape my boot record, which begs an interesting question.

I knew I wanted to use GRUB when I formatted the computer, so I put Windows XP Pro (Vista's bootmgr was killing me with GRUB) on the second hard drive (it runs dual 80's), but ONLY the primary was bootable.  My premise for this was that I could install GRUB on the primary boot record and point to the windows part on the second hard drive..Though while I didn't have GRUB installed, XP still booted fine.  If my computer can't boot off the 2nd hard drive (you can't switch the options around in the BIOS), how the heck was it booting the second disk?  Only answer I could come up with was if it couldn't load the boot record in the first drive, it went to the second, since the first drive was blank it defaulted to the second.

With that in mind, I thought it would be rather important to take note of the fact that I NEED GRUB installed because of the amount of partitions + I want windows to stay alive and the like - So I need a fast, quick, (don't really care if it's easy) way to install GRUB back on that first boot record.

I ran into some instructions online that said I can simply copy the drive (without specifying a partition) and it'll copy the boot rec - like:

dd if=/dev/sda of=/media/USB/grub.bin

Would that work?  I need like a guaranteed way of backing up or restoring GRUB in case this crap happens again.

Sorry for making the post so long.

Thanks for your time.

---

### Post by louieb on 2008-06-08
Sounds like a dedicated GRUB partition was made just for you.  Doesn't need very much room mine is  16MB and only has 2 MB used. (mostly splash screens). Great to when you play with multiple OS that come and go.

Here's a good  how to if you have any questions I be around off and on.
[IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

Look around the page all kind of good stuff on GRUB.

---

### Post by bumanie on 2008-06-08
To reinstall grub, boot live cd; go to terminal
> sudo grub
> find /boot/grub/stage1  Output will be (hdx,x)
> root (hdx,x) inserting the corresponding numbers in place of x + a mention of the file system
> setup (hdx)  use first number only, most often (hd0)
quit
As for the booting question, I believe you have given yourself the answer. As primary is blank/raw, the next potentially bootable device would be searched for, in your case the 'secondary' hard drive.
Hope this helps. 
By the way grub and windows get on much better if windows is on the primary drive, on the first partition. You will save yourself many potential headaches by setting up that way with windows installed before any linux distro's.

---

### Post by meierfra. on 2008-06-08
```
dd if=/dev/sda of=/media/USB/grub.bin
```
This will try to copy you whole drive  hard drive to that file. I don't see any reason why you  want to do that.

---

### Post by meierfra. on 2008-06-08
> Sounds like a dedicated GRUB partition was made just for you

I agree.

Backing up Grub does not make much sense. Reinstalling Grub is pretty easy, and your backup probably would not work, since your configuration has changed.  Grub comes in two parts:  One part is on the MBR  or a boot sector. The other part needs to be on some partition. So if you want Grub to be independent from your various OS's, you need to dedicated Grub partition.

---

### Post by Syndacate on 2008-06-08
> **meierfra. said:**
> ```
dd if=/dev/sda of=/media/USB/grub.bin
```
This will try to copy you whole drive  hard drive to that file. I don't see any reason why you  want to do that.

That's what I thought, but some site with GRUB info said differently, which is why I posted here.

[quote=meierfra.]I agree.

Backing up Grub does not make much sense. Reinstalling Grub is pretty easy, and your backup probably would not work, since your configuration has changed. Grub comes in two parts: One part is on the MBR or a boot sector. The other part needs to be on some partition. So if you want Grub to be independent from your various OS's, you need to dedicated Grub partition.[/quote]

Well I was hoping to make an image out of it that I could just slap on the boot record if things got nasty.

[quote=bumanie]As for the booting question, I believe you have given yourself the answer. As primary is blank/raw, the next potentially bootable device would be searched for, in your case the 'secondary' hard drive.
Hope this helps.
By the way grub and windows get on much better if windows is on the primary drive, on the first partition. You will save yourself many potential headaches by setting up that way with windows installed before any linux distro's.[/quote]

I saw that how-to re-install GRUB method before, but I thought since you're searching /boot it was copying it out of an existing installation with GRUB.  Though I'm now assuming that's the /boot of the CD?

Why is putting windows on the primary drive a better idea in terms of saving me headaches?  Then I would have to use the windows boot loader to boot something on my second hard drive, unless the distro put the /boot partition on the boot record of the primary in which case it makes no difference.

[quote=louieb]Sounds like a dedicated GRUB partition was made just for you. Doesn't need very much room mine is 16MB and only has 2 MB used. (mostly splash screens). Great to when you play with multiple OS that come and go.

Here's a good how to if you have any questions I be around off and on.
IDBS make a dedicated GRUB partition

Look around the page all kind of good stuff on GRUB.[/quote]

How would a dedicated GRUB partition help me?  Any OS that I install will still slap their boot loader on the boot record.

---

### Post by meierfra. on 2008-06-08
> How would a dedicated GRUB partition help me? Any OS that I install will still slap their boot loader on the boot record.


Just  need to  install the boot loader of the new OS to the "boot sector" of the partition of your new OS, instead to the MBR (every OS I ever installed gave me that option)

Then  add the following to your menu.lst  on your grub partition.

title  Another OS which isn't nearly as good as Ubuntu
chainloader (hd2,3)+1 


Of course you need to replace (hd2,3) by  the appropriate numbers for the partition of your new OS

---

### Post by meierfra. on 2008-06-08
> dd if=/dev/sda of=/media/USB/grub.bin

This will try to copy you whole drive hard drive to that file. I don't see any reason why you want to do that.

That's what I thought, but some site with GRUB info said differently, which is why I posted here.


There is a variation of the command which can be used to add an OS to the XP bootloader:

1) Install  the boot  loader of your new OS to the boot sector of its partition.

2)   "dd if=/dev/sda5 of=New_OS.bin bs=512 count=1"

(where /dev/sda5 is the partition of your New_OS

3)  Copy New_OS.bin to the C: drive  of your Windows partion.
   (or you could have mounted your Windows partition in Step 2 and use "dd" to directly place  "New_OS.bin" on the C" drive)

4)  Add the line "C:\New_OS.bin" to boot.ini

(If the  new OS and Windows are on different hard drives, the procedure is slightly more complicated)

But if you use  this method and the Windows Partition becomes corrupt, you will not be able to boot into any of your OS's.

So using a dedicated Grub partition is easier and more reliable.

---

### Post by Syndacate on 2008-06-08
Alright, So I just create a partition of 16mb or so and every time I put on an OS I have it install the /boot partition to that?  Then when using grub just use the chainloader command?  So this way GRUB is always being used?

---

### Post by meierfra. on 2008-06-08
> every time I put on an OS I have it install the /boot partition to that? 

No. Don't make a separated boot partition and don't used the grub partition as a boot partition. The  location of the boot loader  is not the same  as the  location of /boot.

Say you are installing your new OS on /dev/sda5.   At some stage during the installation process you will have the option to choose a location  for your boot loader.   The default location of the  boot loader is  the MBR ("/dev/sda"  or (hd0)" . Change it to /dev/sda5.  (This will put the boot loader on the first sector of /dev/sda5)

For example  when you install Ubuntu, you have to choose "advanced" at step 7 of the installation to change to location of the boot loader.

---

### Post by louieb on 2008-06-08
> **Syndacate said:**
> 
How would a dedicated GRUB partition help me?  Any OS that I install will still slap their boot loader on the boot record.

Most non Microsoft OSs play nice and have the option of installing their boot loader code in the boot sector of their install partition.  - Making it easy to **chainload **the new OS from GRUB.  

Don't get confused a hard drive has one and only one MBR. Each partition  on the drive has a boot sector. 

** meierfra** has given you  a lot of good stuff on GRUB. Its just a fact of life that if your going to play with multiple OSs   your going to have to get good using one boot loader or another. Around here most of us use GRUB and thats what you'll get the best here help with.  The link I gave you earlier has everything I ever needed to know about GRUB. 

Have fun.

---

### Post by Syndacate on 2008-06-09
> **meierfra. said:**
> No. Don't make a separated boot partition and don't used the grub partition as a boot partition. The  location of the boot loader  is not the same  as the  location of /boot.

Say you are installing your new OS on /dev/sda5.   At some stage during the installation process you will have the option to choose a location  for your boot loader.   The default location of the  boot loader is  the MBR ("/dev/sda"  or (hd0)" . Change it to /dev/sda5.  (This will put the boot loader on the first sector of /dev/sda5)

For example  when you install Ubuntu, you have to choose "advanced" at step 7 of the installation to change to location of the boot loader.

How, the only OS I've ever been able to do that with is Gentoo.  Gentoo let me select more than one mount point for each thing.  Ubuntu won't.

What i mean is if I was to go into Ubuntu install, and say I had NOTHING else on the hard drive, but say I wanted to put the boot loader on the boot part of the partition (not the MBR), so I set root (/) to /dev/sda1, but then I can't set /boot to /dev/sda1, how do you select more than one thing on the same partition?  By default it'll install to the master boot record, and since the mount point of sda1 is taken by root, you can't set /boot to sda1.

I'm sorry if this sounds stupid, previously I've only dealt with one hard drive / 2 OS (windows and X OS) so I don't know much about bootloaders in the like, with one HD it's easy, you install windows, then the boot rec of the OS you install gets written on top - simple simple.  Now I'm getting into messing around with the partitions and extended partitions and logical **** and it's all massively confusing to me.  I've tried getting explanations on it all but it's just not clicking :(.

Tomorrow I'm going to try to put FreeBSD on this computer (not my laptop that I was speaking of in the original post) (just experimenting, won't be overwriting Ubunutu, sep hard drive).  Now I know damn well that it'll install its stupid boot loader.  So from what I think I know, is I can install it to the one partition that's there (the other partition is a NTFS formatted storage partition), and then I have to set the root there (obviously), but then I have to set the /boot there also, so it doesn't throw the boot on the MBR and overwrite GRUB.  Now I know damn well from past experience you can set /dev/sdb1 to "slice" (root) - or you can set it to /boot - but I don't know the "both" option.  If I don't set it then it'll install to the MBR, which isn't what I want.  I mean on this computer it's not bad because I can just unplug my Ubuntu/Windows disk and the other disk will primary up and since it's the only OS there (the rest is NTFS storage) I can let it take up the MBR of that disk, then just swap it around in the BIOS depending on what I want to boot - though that's not the RIGHT way to do it, that's just circumventing it.

---

### Post by meierfra. on 2008-06-09
The location of the bootloader  has nothing to do with mounting partitions.  It also has nothing to do with the mount point of /boot. The bootloader does not occupy a whole partition, but only one sector.

The bootloader is always installed to the first sector of a hard drive (the MBR) or  the first sector of a partition (the boot sector). During the installation you will have the opportunity  to choose where you would like to install the  bootloader.   Just choose   "/dev/sda3" or whatever your "/" partition is mounted to.  This will not effect your "/" partition  in any way.
But do not install the boot loader to the  Windows Partition. The first sector of the Windows partition, contains the boot loader for Windows, you don't want to overwrite that.

At what time during the installtion you can choose the location of the boot loader  depends on the OS. In Ubuntu you can do this at the last step, step 7. (Mounting partitions happens at step 3 or 4)

I recommend against a separate boot partition. Boot partitions are useful for servers, but in my opinion  are just a hassle for normal users.  In particular, I would not share a boot partition between different OS's.

---

### Post by Syndacate on 2008-06-09
> **meierfra. said:**
> The location of the bootloader  has nothing to do with mounting partitions.  It also has nothing to do with the mount point of /boot. The bootloader does not occupy a whole partition, but only one sector.

The bootloader is always installed to the first sector of a hard drive (the MBR) or  the first sector of a partition (the boot sector). During the installation you will have the opportunity  to choose where you would like to install the  bootloader.   Just choose   "/dev/sda3" or whatever your "/" partition is mounted to.  This will not effect your "/" partition  in any way.
But do not install the boot loader to the  Windows Partition. The first sector of the Windows partition, contains the boot loader for Windows, you don't want to overwrite that.

At what time during the installtion you can choose the location of the boot loader  depends on the OS. In Ubuntu you can do this at the last step, step 7. (Mounting partitions happens at step 3 or 4)

I recommend against a separate boot partition. Boot partitions are useful for servers, but in my opinion  are just a hassle for normal users.  In particular, I would not share a boot partition between different OS's.

I'm in Ubuntu's installation menu right now.

On step 4/7, partitioning.

I set the mount point of /dev/sda2 to / (root).  Now there's no way to also mount /boot there.  It will not let me.  It's /boot mounted there, or / mounted there, not both.  It's the same with every other OS so I'm assuming I'm missing something.  You cannot do both.  It's a drop down menu for the partition, you can either have it set to /boot, or have it set to /.

As I said before, Gentoo is the only distro which allowed me to install both the root and the /boot part to the same place.

---

### Post by meierfra. on 2008-06-09
You need to choose the location for the boot loader at  step 7.   At step 7, click on advanced. Then pick /dev/sda2 for the location of the boot loader.

---

### Post by Syndacate on 2008-06-09
> **meierfra. said:**
> You need to choose the location for the boot loader at  step 7.   At step 7, click on advanced. Then pick /dev/sda2 for the location of the boot loader.

Where do I put the /boot partition in step 4?

---

### Post by meierfra. on 2008-06-10
> Where do I put the /boot partition in step 4?

Nowhere. You don't need a /boot partition.  (If you really want a separate boot partition, you will have to create an extra partition before you install ubuntu:  Size about 200MB, format ext3)

---

### Post by Syndacate on 2008-06-10
> **meierfra. said:**
> Nowhere. You don't need a /boot partition.  (If you really want a separate boot partition, you will have to create an extra partition before you install ubuntu:  Size about 200MB, format ext3)

Oh, I gotcha.

So the only thing I have to select is a root partition?  Because I can select the same SWAP partition later from inside the OS by typing "swapon /dev/sdaX", right?

---

### Post by meierfra. on 2008-06-10
During installation you should mount  the swap partition as swap (although the installer often does that automatically)

Did you create the Grub partition yet?  If you want to have a dedicated Grub partition, you need to create a small partition (say 50MB, format ext3)

Also you do not need to reinstall Ubuntu to  use a Dedicated Grub Partition. Only Grub needs to be reinstall

```
sudo grub-install /dev/sda1 
```
(where sda1 is the location of you Ubuntu "/"-partition,

---

