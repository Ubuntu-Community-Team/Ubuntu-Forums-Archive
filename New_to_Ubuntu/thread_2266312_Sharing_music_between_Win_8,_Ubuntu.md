---
title: "Sharing music between Win 8, Ubuntu"
date: 2015-02-21
forum: New to Ubuntu
---

### Post by waxcan on 2015-02-21
Hi folks,
Noob here. My machine dual boots Ubuntu and Win 8, and I'd like to be able to share music between the two. The primary goal is to be able to run playlists in Clementine and iTunes from the one directory.

I've seen a few methods to do this with the best appearing to be the creation of a third partition that could be access by both. I'm acutely aware that this would have been answered many times - which is ironically the problem, since I do not know which option is the most reliable or appropriate. I've followed instructions before only to create a mess I lacked the experience to untangle.

The methods to create that partition vary and I'm weary of messing things up.

So what do you experienced folks recommend (short of dumping win :) )? A shared partition would be useful to share other files, photos and so forth. I'll be pretty much always using Ubuntu, with Win there for other users.

A link or instructions that don't assume knowledge would be perfect.

My drive is around 1tb.
Here's a GParted screen shot.

[IMG]http://i.imgur.com/OH2VCfg.png[/IMG]

---

### Post by nerdtron on 2015-02-21
/dev/sda4 is the windows partition with music right? Or you want to shrink your /dev/sda5 linux partition and create another partition?

If you go on the first route, just Open clementine and point the player to import music from the mounted windows partition. That should be enough. But then the only problem is auto mounting. Since once you reboot and the partition is not automatically mounted, you can't play your files.

We can setup automouting of the /dev/sda4 partition if you like.

---

### Post by waxcan on 2015-02-22
Thanks Nerdtron!
I'm guessing it's probably easier to dump my music, vids, and so on on the Windows partition. So how should I automount?
Thanks!

---

### Post by jacobpratt909 on 2015-02-22
I suggest trying to get a thumb drive to temporarily hold the music until you **_SAFELY_** (keyword is safely) shrink a partition until you have an unformatted partition that is around 1 GB, then what you should do is format the unformatted partition to FAT32, because both Ubuntu and Windows can read that partition. Then put your music in there and enjoy! Be sure to do this safely, as shrinking a partition can sometimes corrupt data if not done correctly! I do not want you having a format party (having to reformat everything), because I have had many of those, and they suck.

-Wyz

---

### Post by jacobpratt909 on 2015-02-22
I accidentally posted two times, sorry :/

---

### Post by waxcan on 2015-02-22
Thanks Jacob!
That's precisely what I've done :)

I moved my large music collection and everything else off to an external drive and wiped the disk clean, reinstalling Win 8 before applying updates and shrinking it.

I then installed Ubuntu and was going to create a FAT32 partition but didn't know anything about mount spaces and the other requirements that need to be entered to make the partition work.

A separate partition would be gold. As it stands I can afford to have everything on the computer lost since i have external USB recovery for both OSes and my data, I just don't know how to go forward.
Thanks!

---

### Post by jacobpratt909 on 2015-02-22
In Ubuntu (using GParted) you can format the unformatted partition and then go into the program you use to look around in your files, choose the partition that is newly formatted to FAT32, and going into it should automatically mount it, if not, then we need someone with more than 50 beans.

-Wyz

---

### Post by waxcan on 2015-02-22
So I shrunk Windows from GParted (haven't yet booted into it to test) and came up with the Fat32 partition I named Storage.

I couldn't shrink sda4 however. GParted wouldn't allow me to drop the slider. Perhaps I need to do this from BIOS or from some otherwise logged-out state? 447 Gbs is too much for my Ubuntu install :)

Thanks!

[IMG]http://i.imgur.com/OEh47LE.png[/IMG]

---

### Post by HermanAB on 2015-02-23
Uhmmm... Linux can read and write NTFS perfectly well.  You only needed to mount the Windows partition in Ubuntu /mnt.

---

### Post by newb85 on 2015-02-23
+1 to HermanAB's point.  The days when a common FAT32 partition was recommended because Ubuntu's support of NTFS wasn't good enough are in the past.  That's not to say using a common FAT32 partition won't still work.

And, as jacobpratt909 pointed out, simply navigating to that partition in your file browser will automatically mount it once.

If you want to automount the partition on boot, my suggestion is that you go to [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) and read the Manual Setup Help section under Systemwide Mounts.  Then post any questions you have here.

---

### Post by waxcan on 2015-02-23
Thanks folks,
Am I right in that I can't shrink sda5 while Ubuntu is loaded? Wondering how I can resize it otherwise. GParted won't let me shrink or expand it while logged in.
Thanks

---

### Post by nerdtron on 2015-02-23
You can't resized while Ubuntu is running. Boot into live mode and be sure the partition is unmounted and then try to resize it. If you going to share this partition with windows, NTFS is a good option since Linux ca read/write ntfs very well.

---

### Post by jacobpratt909 on 2015-02-23
Just boot up with the live CD, and then resize the certain partition Ubuntu was in. [COLOR=#ff0000](WARNING!) [/COLOR][COLOR=#000000]you can still screw up your data (though that is true with anything these days)
Best of luck,

-Wyz[/COLOR]

---

### Post by waxcan on 2015-03-02
Everything is running okay, I'll just add that I wrecked grub in moving my Ubuntu boot partition so that the two unallocated partitions could be merged as a single storage partition. I was warned by GParted that this could happen, and there are fixes available (I just opted to reinstall Linux because the fixes didn't work for me).

I followed the auto-mount thread that you guys referred to and it now loads perfectly.

Thanks so much!

---

