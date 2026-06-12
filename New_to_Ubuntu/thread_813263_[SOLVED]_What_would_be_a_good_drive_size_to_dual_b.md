---
title: "[SOLVED] What would be a good drive size to dual boot?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Tsurugi13 on 2008-05-30
I am a bit of a modder in Halo PC and SWBF2, but nothing I've found can run them in Ubuntu. I've tried Wine several times, and other programs don't support Directx, other than VMware fusion, which is Mac only and a beta anyway. What would be a good drive size If I were to dual boot between Ubuntu 8.04 and XP? Most everything is on Ubuntu, XP would be games only, but those games can have files upwards of 500 mb for one addon map, which there may be a dozen of. At one point my addon folder in SWBF2 was 8 gb by itself. Any idea of what a good drive size would be? I think mine is around 80 gb right now.

---

### Post by ninjabob7 on 2008-05-30
Ubuntu doesn't need a whole lot of space. I had 10GB for the main partition and 5GB for the home until recently. Right now I have a 200GB drive with 108GB for XP, 20 for shared, 2GB swap, 1GB Linux boot, 10GB Linux home, 20GB linux main, and 20GB empty partition. There's also a system recovery thing that takes 8. If you plan on using Ubuntu as your only linux, you could probably do 25GB for a single partition and give the rest to Windows.

---

### Post by Tsurugi13 on 2008-05-30
Right now I think the entire drive is for Ubuntu. Would I need to reinstall it and give it a smaller partition? I'm no good at this stuff...

---

### Post by housam on 2008-05-30
I'll suggest to do :
reformat the entire disk
partition it to 4 partitions 
- 15 GB for xp ntfs format ( to be the first install )
- 20 GB for ubuntu ext3 format ( to be the 2nd install )
- 2 GB for the swap
- the rest for the data ntfs format ( can be accessed from both systems )

Use Gparted to do the partitioning.

---

### Post by Tsurugi13 on 2008-05-30
I installed Gparted, and when I opened it up, I saw this:
[IMG]http://lh3.ggpht.com/indigobjames/SEB-ltEIA1I/AAAAAAAAAGw/fVkPA4BUpf4/Screenshot--dev-sda%20-%20GParted.jpg?imgmax=640[/IMG]

What does ANY of that mean?

---

### Post by sayakb on 2008-05-30
You don't need more than 10GB for the /. Also, if you keep your files on the NTFS partition in Ubuntu, you don't need a separate /home either. So just keep one single partition for / (which would include /home), 1GB for SWAP (or 2-3GB or whatever your RAM size is), and the remaining for Windows (NTFS). Keep all your data on the NTFS partition even when you use Ubuntu.

---

### Post by WRDN on 2008-05-30
> **Tsurugi13 said:**
> I installed Gparted, and when I opened it up, I saw this:
[image]
What does ANY of that mean?

The ext3 partiton is what Linux currently has, and the swap partiton is already there so theres no need to worry about creating that. Select the largest partiton in the graph (ext3) and click the "Resize/Move" button. Then, use the slider or type the size you want to reduce it. 
Using the figures housam gave, you could shrink the ext3 partition to 20Gb. Then, with the new unallocated space, create a new partiton, and give it 15Gb (for XP). Finally, the last unallocated space can all be used as a single partition (ntfs) for sharing files.

---

### Post by housam on 2008-05-30
Installing Gparted will not let you do the partitioning because your partitions are mounted. the best way is to download it from[[COLOR="Red"]_ here_[/COLOR]]("http://gparted.sourceforge.net/livecd.php") and burn it to have a gparted live CD. then boot from it and do the job.

Or boot from ubuntu live cd and go for system >> admin. >> partition editor ( gparted ) . but you have to unmount the partitions first.

---

### Post by Unix_Slayer on 2008-05-30
I use two separate drives. I don't want my Kubuntu touching Winblows.

---

### Post by ugm6hr on 2008-05-30
> **Tsurugi13 said:**
> Right now I think the entire drive is for Ubuntu. Would I need to reinstall it and give it a smaller partition? I'm no good at this stuff...

I would also recommend starting again, because editing your current setup will probably take longer.

Either way, you'll need to backup first.

Anyway - my suggestion for partitions:

XP: as much as you need (sda1).
sda2 - extended partition with whatever is left after XP, divided into 3 logical drives as below.
Ubuntu /: 10GB ext3 (sda5)
Ubuntu /home: whatever is left ext3 (sda6) - based on your current usage, 5GB may even be enough...
Ubuntu swap: 1.5x RAM or max 1GB (unless you use suspend to RAM) (sda7).

If you are just using XP for games, I don't see any point in having an NTFS drive for sharing files.  In any case, fs-driver allows XP to read/write to ext3.

A separate /home allows more than just keeping files - email folders / desktop setup etc will stay even after new installations.

If you want to try and achieve this without having to reformat, let me know.

> What does ANY of that mean?
You have a 150GB HD (not 80GB).  sda1 is where Ubuntu lives (combined / and /home). sda2 is an "extended" partition, which can be subdivided (although you only have sda5).  The sizes of all the partitions are given in GB.

---

### Post by sayakb on 2008-05-30
> **ugm6hr said:**
> You have a 150GB HD (not 80GB).  sda1 is where Ubuntu lives (combined / and /home). sda2 is an "extended" partition, which can be subdivided (although you only have sda5).  The sizes of all the partitions are given in GB.

I guess its a 160GB hard drive.. I too have 149GB available on one of my laptops.. man I miss the 10GB when it comes to storing music ;)

---

### Post by Tsurugi13 on 2008-05-30
I would love to not have to kill my precious Ubuntu to install XP (<==looks like a face lol) Because of the amount of customizing i've done. Thanks for all the help!

---

### Post by sayakb on 2008-05-30
@OP
You don't need 20GB for Ubuntu. As you may keep your data on the Windows partition even when you're on Ubuntu, you may just give it 10GB or as ugm6hr said, give it max 15. I have given 10GB to root and I have about 8-9 desktop environments installed. I haven't even used up 5GB of my / ;)

---

### Post by Tsurugi13 on 2008-05-30
Like I said in the first post, Modding can take up gbs really fast, so I think I might want to be generous with my partitions.

---

### Post by sayakb on 2008-05-30
Exactly.. and for that same reason, you need a huge Windows drive :)

---

### Post by housam on 2008-05-30
> **Tsurugi13 said:**
> I would love to not have to kill my precious Ubuntu to install XP (<==looks like a face lol) Because of the amount of customizing i've done. Thanks for all the help!

You can install xp without killing ubuntu.
resize ubuntu partition to 15 GB then create 2 new partitions ntfs format . one 15 gb for xp and the other is the rest for your data.
but after installing xp , ubuntu will not boot unless you recover grub using [[COLOR="Red"]_this guide _[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?")

---

### Post by ninjabob7 on 2008-05-30
> **LinuxIsInnovation said:**
> You don't need more than 10GB for the /. Also, if you keep your files on the NTFS partition in Ubuntu, you don't need a separate /home either. So just keep one single partition for / (which would include /home), 1GB for SWAP (or 2-3GB or whatever your RAM size is), and the remaining for Windows (NTFS). Keep all your data on the NTFS partition even when you use Ubuntu.
*I* used up my 10GB / before I used up my 5GB home. It's a lot easier to make a big partition and not need to resize it later. I also install a lot of junk and forget to uninstall it when I find a better alternative. Actually right now my / is only 52% full out of 20GB, so 15 should be pretty safe.
I think the rule for swap is 2x your memory if your memory is 512MB or less, and the same as your memory if you have at least 1GB.
If you haven't installed a lot of stuff yet, you'd probably be better off backing up your /home and reinstalling. Make sure you create your user on the new install before you restore /home. You might also want to backup parts of /etc, but not unless you know what you're doing, because restoring /etc/fstab, for example, will mess up the system.
A separate /home partition is better but not really needed. If you're doing only one, make it at least 20.
As far as a shared data partition, another option is to use ext2ifs, which allows Windows 2000/XP to read/write Linux partitions normally. There's also explore2fs, which is a program that lets you read from Linux partitions only.

---

### Post by ugm6hr on 2008-05-30
> **housam said:**
> You can install xp without killing ubuntu.
resize ubuntu partition to 15 GB then create 2 new partitions ntfs format . one 15 gb for xp and the other is the rest for your data.
but after installing xp , ubuntu will not boot unless you recover grub using [[COLOR="Red"]_this guide _[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?")

Agree.  Except I still don't see any value in a NTFS data partition if XP is purely for gaming.  Just make XP partition bigger (and perhaps consider more than 15GB for Ubuntu too).

WRT long term planning - given you are repartitioning, consider creating a separate /home (which could act as a "data" partition for both OS (fs-driver).

Benefits of /home partition: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
How to create separate /home: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Don't forget to backup before doing any partitioning work.

---

### Post by Tsurugi13 on 2008-05-30
After many a screw-up and a long time, I managed to do something. I got the gparted live CD and did this:
[IMG]http://lh3.ggpht.com/indigobjames/SEB-ltEIA1I/AAAAAAAAAHQ/cTchbVrBk9g/Screenshot--dev-sda%20-%20GParted.jpg?imgmax=640[/IMG]
Did I do all right? So now I just have to install XP in the big unallocated spot right? right?

---

### Post by ninjabob7 on 2008-05-30
That should be alright. Not sure, but you might need/want to create the XP partition using gparted rather than letting XP do it. Make an NTFS partition in the empty space, and make it bootable (actually that might not matter, but easier not to have to redo it). You shouldn't have to format it, as XP will do that, but if the XP CD doesn't see the new partition, try formatting it. 
Also, make sure you have some sort of boot disk to get into Ubuntu as XP will steal the MBR and wipe out GRUB. Once you're in Ubuntu, you can reinstall GRUB and XP will be fine.

---

### Post by timandjulz on 2008-05-30
Be extra careful if you have used Linux software RAID.  (mdadm)  and/or LVM (logical volume management)

When you run the install, gparted does not know about raid volumes or LVM and thinks you can wipe them out.  VERY BAD FLAW!  I came close to losing my RAID volumes thanks to this flaw.  Luckily I didn't do the usual click-click-click without reading.  I feel sorry for the people that do.

---

### Post by Tsurugi13 on 2008-05-31
Um... I'm not sure what that is. I have the live CD I used to install Ubuntu, and I'm about to install XP. Here goes!

Wait... Gparted won't let me make it an ntfs filesystem. Any ideas on why?

---

### Post by Tsurugi13 on 2008-05-31
I'm going to finish this tonight, so If I don't get any replies within 10 or so minutes, I'll just try letting windows handle the formatting.

---

### Post by ugm6hr on 2008-05-31
> **Tsurugi13 said:**
> I'm going to finish this tonight, so If I don't get any replies within 10 or so minutes, I'll just try letting windows handle the formatting.

Just format it to any "Windows" filesystem - vfat, fat32 etc.

When installing Windows, tell it to reformat.

---

### Post by Tsurugi13 on 2008-05-31
I got XP installed and used the guide suggested earlier to reinstall GRUB, but now I don't know how to boot from windows. HELP!

---

### Post by ugm6hr on 2008-05-31
> **Tsurugi13 said:**
> I got XP installed and used the guide suggested earlier to reinstall GRUB, but now I don't know how to boot from windows. HELP!

Have a look at /boot/grub/menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```

It should have something like this at the bottom:
> title  Microsoft Windows XP Home #An entry for a Windows installation
root   (hd0,1)
makeactive
chainloader +1

If there is no Windows entry - add the following to the bottom:
> title  Microsoft Windows XP 0 #An entry for a Windows installation
root   (hd0,0)
makeactive
chainloader +1

title  Microsoft Windows XP 1 #An entry for a Windows installation
root   (hd0,1)
makeactive
chainloader +1

title  Microsoft Windows XP 2 #An entry for a Windows installation
root   (hd0,2)
makeactive
chainloader +1

Then save and reboot.

Try the Windows options out at reboot - make sure you have a timeout set on the grub file too.

I suspect it will be the 2 option you need.  Once you've worked out which it is - just go back into Ubuntu and delete the extra entries that don't work.

---

### Post by Tsurugi13 on 2008-05-31
Hooray! Thank you Ubuntu community! The dual boot worked and I'm on my way to modding!:biggrin:

---

### Post by housam on 2008-05-31
congratulations

---

### Post by billgoldberg on 2008-05-31
> **Tsurugi13 said:**
> Right now I think the entire drive is for Ubuntu. Would I need to reinstall it and give it a smaller partition? I'm no good at this stuff...

if you install xp after you installed ubuntu you will need to reinstall the grub bootloader. Windows will overwrite it.

This can be done easily with "super grub disk" or from the ubuntu live cd (google for it).

I also have a gaming partition of xp, I gave it 30gb (command and conquer and cs:s), ubuntu has 220gb.

---

### Post by housam on 2008-05-31
[SIZE="2"] It is important to mark [ SOLVED ] on each solved problem[/SIZE]

---

### Post by ugm6hr on 2008-05-31
@housam:

I agree.  In fact, I have marked it solved for the OP.

Can I suggest you avoid using large text, since this can be interpreted as shouting online.

---

### Post by housam on 2008-05-31
> **ugm6hr said:**
> @housam:

I agree.  In fact, I have marked it solved for the OP.

Can I suggest you avoid using large text, since this can be interpreted as shouting online.

I agree , I didn't mean it but just wanted to show it to every one.
I already edited it.

---

### Post by Tsurugi13 on 2008-05-31
Thanks everyone so much for the help. I even got my games installed!

---

