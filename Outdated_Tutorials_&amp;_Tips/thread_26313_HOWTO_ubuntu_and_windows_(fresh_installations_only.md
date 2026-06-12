---
title: "HOWTO: ubuntu and windows (fresh installations only)"
date: 2005-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by vnbuddy2002 on 2005-04-12
This is a guide to help you install both ubuntu and windows on one hard drive. This only apply to fresh installations only (both ubuntu and windows).

The important thing is to keep things in order. The first thing you should note is that you should always install windows before linux. Windows is needed to be on the first primary partition, otherwise it will refuse to install.


My setup would be (I used Ubuntu to do the partition)

Primary
/hda1   = FAT32 (Windows OS) ~ 10GB
/hda2   = ReiserFS(linux /boot) ~ 100mb

Extended
/hda3   = ReiserFS(linux swap) ~ 1GB
/hda4   = ReiserFS(Linux /) ~ 20GB
/hda5   = FAT32 (Windows Applications and sharing) the rest of the free space

:) This is only my setup. You will need to adjust them at your own flavor.

Now, start to install windows
Once finished installing windows, go to "Start > Run" type in "regedit"
Go to HKEY_LOCAL_MACHINE > Microsoft > Windows

You should be able to locate "C:\Program Files" as one of its key. Change it to 
"[DriveLetter of (/hda5)]:\Program files". This will maintain windows' performance in a long run.


Next, you are ready to install Ubuntu. If you dont' know what "Ubuntu" is then you shouldn't be here..  :-P

Once finished installing Ubuntu, make sure you follow the guides from "http://www.ubuntuguide.org" on how to mount your FAT32 partitions "correctly".

:) I know there aren't many people doing what I am doing, but I hope this tip helps,even only for a few people.

Edited on "04/12/2004"
- I am glad that it does help  :-P

---

### Post by XDevHald on 2005-04-12
Very affective guide and should be added to the ubuntuguide.org as well.

I have this printed and ready to use because I will be needing winblows for my programs that they require me to use.

---

### Post by maqi on 2005-04-12
Nice setup :) 

Just a question - should that registry change be to "<DriveLetter>:\Program Files"?

---

### Post by stevenyu on 2005-04-12
Can someone show me how to share files and printer between ubuntu and windows?  I got samba installed and setup up the samba.conf but still i can't see the windows sharing and windows can't see the ubuntu sharing

---

### Post by vnbuddy2002 on 2005-04-12
Follow my guide lines at:

[http://ubuntuforums.org/showthread.php?p=129315](http://ubuntuforums.org/showthread.php?p=129315)


In addition to that, open "fstab" to remount your "/hda5 = FAT32", it will stay in your home directory. Here is a simple "How".

sudo gedit /etc/fstab

look for FAT32 Partitions, rewrite that line to:

```
/dev/hd[whatever it says there]   /home/[your login name]/win1   user, umask=000  0   0
```


With FAT32, you dont' have to worry about file permissions. 

It should appear on the network as "win1" folder.

:) I hope it helps.

---

### Post by jerome bettis on 2005-04-13
[QUOTE=vnbuddy2002]The important thing is to keep things in order. The first thing you should note is that you should always install windows before linux. Windows is needed to be on the first primary partition, otherwise it will refuse to install.[/QUOTE]

man that is soooooooo not true.

you can easily install windows after linux, and it does not have to have the first primary partition.  personally, it has the last primary partition of my drive, and i installed it several months after ubuntu. 

here's how.

partition your disk however you see fit, just make sure you give windows a primary one.  windows does need a primary partition on the first drive of the system, but the whole thing of it needing the first one is a big myth.  if you rarely use it, it's probably a good idea make it at the very back of the disk, so it doesn't take up a faster part of your drive.

install ubuntu, and format your windows partition with fat 32.  you can mount it at /windows (or where ever) if you'd like.

put the windows cd in (oh noes!) ... the installer will see all of your partitions, but the FAT 32 one should stand out.  hopefully it's labeled as C: (the first time i installed this it was, i ended up doing again later on and it decided it was going to be E: - i didn't even change anything!!   :grin: no big deal though, E: works just as well).  so go ahead and select the partition you want to install to and if it asks anything about overwriting the MBR just say yes (we'll fix this in a minute).

now when you boot the windows bootloader comes up and grub has dissappered.  you should have a few choices here (windows, unidentified operating system etc) but these do nothing.  windows should boot fine and your linux partitions should be sitting there in oblivion.  

now comes the hard part, we need to install grub.  there are several ways of doing this, you just need to get to a root shell.  you could use a knoppix or ubuntu live cd (recommended), or you could use the ubuntu installation cd.  i've done this and it's somewhat of a pain because you have find and mount your hard drive yourself.  if anybody needs help doing this just ask, i'll explain.  

but assuming your using a live cd of some sort (the gentoo installation cd works well too), and you're at a root shell with your hard drive mounted somewhere, all you have to do is chroot into the directory where it's mounted.   then just type grub-install /dev/hda ... now you can boot into linux again, but before you reboot you should edit /boot/grub/menu.lst to add an option for windows.

if you installed to the fourth primary partition on the first hard drive (/dev/hda4) then add this to the bottom of that file:

title Windows
map (hd0,0) (hd0,3)
map (hd0,3) (hd0,0)
rootnoverify (hd0,3)
chainloader +1

the map lines are needed to fool windows into thinking it has the first partition (they virtually swap the devices).  grub device numbers start with 0 instead of 1.  as another example /dev/hdb6 is (hd1,5) .. chainloader +1 calls the windows bootloader.

hopefully that's everything.  it worked fine for me, any questions just ask.

---

### Post by vnbuddy2002 on 2005-04-13
If you read it carefully, when you create the /windows partion, it automatically puts that partition as primary or the first primary.

The order is important, like I stated above, windows is REQUIRED to install before UBUNTU because Windows will look for MBR. If the MBR is not recognize by windows, it wouldn't proceed any further.

jerome bettis, "man that is soooooooo not true." 

Why don't you try to install UBUNTU before Windows? and tell me the result?

:) I am not arguing or anything. I am just trying to prove my point.

---

### Post by jerome bettis on 2005-04-13
BS

did you see what i said??  i did install windows AFTER ubuntu and it works fine!!!!

seriously, it does not need the first partition!!! if you want to stop over i can show you exactly how i did it!!

---

### Post by jerome bettis on 2005-04-13
here's some more (& better explained) methods of restoring grub

[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by vnbuddy2002 on 2005-04-13
I tried your way before I came up with this tip on my desktop computer. It did not take it. I used "Windows XP SP1a" for the that.

for the previous post, I wasn't aware that you installed windows after ubuntu. It seems like we have conflict results. May be we should wait for the results from other users.

It might be the version of Windows CD. I don't really know.

---

### Post by jerome bettis on 2005-04-13
[QUOTE=vnbuddy2002]I tried your way before I came up with this tip on my desktop computer. It did not take it. I used "Windows XP SP1a" for the that.

for the previous post, I wasn't aware that you installed windows after ubuntu. It seems like we have conflict results. May be we should wait for the results from other users.

It might be the version of Windows CD. I don't really know.[/QUOTE]
 that's possible.  i used the original release of windows xp pro.  but i can prove it's possible.  other people have been able to do the same.  hopefully some people try this out and say 'it worked' or 'it doesn't work' and we can figure out why.  but i'm 100% sure it's possible to install linux first, and then put windows at the very last part of the disk.

[http://www.google.com/search?q=installing+windows+after+linux&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial](http://www.google.com/search?q=installing+windows+after+linux&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial)

---

### Post by Buffalo Soldier on 2005-04-13
I haven't tried installing M$ Windows after installed GNU/Linux. But from what I've read these are my assumptions:[list]
[*] It is possible to install M$ Windows after installing GNU/Linux
[*] It is relatively easier for newbies to install M$ Windows first
[/list]

---

### Post by maqi on 2005-04-13
[QUOTE=Buffalo Soldier]I haven't tried installing M$ Windows after installed GNU/Linux. But from what I've read these are my assumptions:[list]
[*] It is possible to install M$ Windows after installing GNU/Linux
[*] It is relatively easier for newbies to install M$ Windows first
[/list][/QUOTE]

I have and I totally agree with you! In fact I'd go further:

Installing windows anywhere will trash your MBR from the POV that it will overwrite your GRUB or LILO MBR with the Windows MBR and booting Linux from a normal power up will no longer be an option. Windows does not play nice with other OSes. This is not so hard to recover from, eg, grub bootdisk, distro bootdisk/rescue CD, etc, etc.

But it's easier and less time-consuming to put Windows first no matter who you are.

---

### Post by kuleali on 2005-04-13
thanks for the howto

---

### Post by emmbec on 2005-04-13
I used the partitioner to create a partition for linux and windows. While installing windows xp it recognized 3 UNKOWN partitions (in the partitioner I set up one fat 32 partition primary for windows, another ext3 primary for linux and the swap) I chose the partition corresponding to that of FAT 32 (I knew that because of the space I gave to windows) and chose to partition it as NTFS. I finished installing windows, and now I want to install UBUNTU. BUT when I try to install it, when I get to the step on partitioning, it recoginzez the 3 partitions correctly, one NTFS, another ext3 and one swap. I don't want the partitioner to format again, I want it to use the ext3 partition for ubuntu, but it says that everything will be lost if I continue. I am afraid of losing my windows instalation, I don't have anything important but I just spent the entire evening installing software on windows and I'll hate to lose it. If anyone knows how to install ubuntu withou losing my windows instalation please let me know. Thanks

---

### Post by vnbuddy2002 on 2005-04-14
Don't worry. The it won't format your FAT32 partitions, if you are using manual instead of the automatic.

don't touch your FAT32 partition, leave it the way it is.

Delete the Ext3, create 2 new Ext3 partions

/boot   = ~ 80-100MB
/          = The rest of the space


Then you are good to go.

---

### Post by tony_st on 2005-08-20
I've successfully installed Windows XP on a hard drive after initially installing Ubuntu Debian Linux, and I can dual boot from grub.  I wasted a lot of time with some stupid pitfalls, but here they are in case someone else is trying this.

0) Have a bootable CD program like Knoppix or Ubuntu bootable around.

1) The windows XP installer likes to make it's own partitions.  Originally, I made the  partition and formatted it FAT32 myself, but after installing Win XP on that, it would not boot.  So, let the Win XP installer both create the partition and format it FAT32.

2) The Windows XP installer is stupid and could not create a fourth partition in the free space in the middle part of my drive.  I had already created three paritions.  It thought that all partitions were taken (I am using only primary parititions like this: boot, windows, linux swap, linux).  The solution to this was to temporarily delete my linux swap partition, and then recreate it after the Win XP installation.

3) Make sure the drive letter to be assigned is C:\   This may not be important for other people, but it was for me, because my machine is a laptop with lots of proprietary drivers to install.  When my first installation assigned this as the E:\ drive, the windows installation went fine but a lot of the subsequent drivers failed.  I don't know what makes the Win XP installer pick the drive letters.  I lucked out and the second time it picked C:\ and after that I had no problems.  (I was messing around with fdisk, using the expert options, and the reorder partitions)

4) My additions to the grup menu.lst file are:
```
title		Windows XP
root	(hd0,1)
makeactive
chainloader	+1
```
As you may see from above, I installed Win on my second partition on my first hard drive.  I did not need the "map" lines mentioned in a previous reply.  I think you do need those if your Win partition is on a second drive, but not on the first hard drive.  I also found "root" worked as well as "rootnoverify" so left it at that.  "makeactive" is probably not necessary if you only have one M$ Win installation, but I left it in for good measure.

---

