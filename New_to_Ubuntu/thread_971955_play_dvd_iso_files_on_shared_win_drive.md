---
title: "play dvd iso files on shared win drive"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by eeeek on 2008-11-05
Sorry if this doesn't belong in the Absolute Beginner Talk, but...

My question regards playing dvd iso files from a shared windows drive. 

I am running 8.04 and have a shared windows drive set up. I can successfully view files in this shared drive. In fact, last night, I was able to play a VOB file from this shared drive. 

I have done a little reading and found that people seem to have the most success getting iso files to play in VLC. I can't seem to get VLC to see anything off the networked drive. Is this even possible?

I won't be at my home linux computer for a few hours, so I'm going off memory, here. 

By the way, I did a hardware test with the old computers I use to experiment with Linux. My current box is an 800mhz Pentium III with 512mb of RAM and it plays video files like a charm. But the old, old computer I have (900mhz Athlon, 384mb RAM) didn't play video so well - lots of skipping, video struggled to keep up with the sound. I thought it was interesting that the greater RAM, but slower CPU played the video better. Neither box can stream video off the internet perfectly, which is unfortunate. Anyways, just a little sidetrip, there.

Any suggestions with playing dvd iso files on my shared windows drive would be greatly appreciated.

Thanks,

---

### Post by inportb on 2008-11-05
I think you're looking at a networking bottleneck. I experience the same while playing a DVD ISO over a 10mbps connection. You might be able to improve performance slightly by mounting the ISO on the server and sharing the mounted directory instead, but I have a feeling a more reliable network connection might be the kicker.

You can mount a samba share using smbfs, which renders any networking activity transparent.

---

### Post by eeeek on 2008-11-05
Well, from what I can tell, the folder is already mounted. I can browse to it just fine in the file manager. 

But when I open VLC, I can't seem to path to anything on the shared drive. I tried pasting in the path, but that didn't work (sorry, I don't have the error message in my head).

Another thing I've tried, without success, is I installed gmount. Again, it didn't look like it would let me mount anything outside of the host computer. In other words, I couldn't mount the shared windows drive.

I tried a similar approach on mplayer and Totem. 

Again, I double-clicked on a .vob file in the shared folder and it played just fine. But for obvious reasons, it would be really nice if I could easily plan the dvd off the iso file that's located in the shared folder.

---

### Post by egalvan on 2008-11-05
> **eeeek said:**
>  

did a hardware test with the old computers I use to experiment with Linux. My current box is an 800mhz Pentium III with 512mb of RAM and it plays video files like a charm. But the old, old computer I have (900mhz Athlon, 384mb RAM) didn't play video so well - lots of skipping, video struggled to keep up with the sound. I thought it was interesting that the greater RAM, but slower CPU played the video better.


Yep, more RAM is almost always a better speed-up than a faster CPU.

Also, if that is an Athlon, and not an AthlonXP, then the PIII will run rings around it.

The Athlon is very inefficient, with a very small cache, slow FSB and high temps.

The AthlonXP, on the other hand, with a much bigger cache, far  better FSB speeds, will smoke anything from Intel with similar speed ratings.

If your Athlon mobo will take the XP series, then you may want to spend the $10-$15 to upgrade... XP-1700 and up are considered obsolete junk, and you may even get it free.

Of course, up-grading to a full 512M will work even better.

And yes, I do still use these older machines...RAM is the only thing that has  been expensive....

---

### Post by eeeek on 2008-11-06
So..... Does anyone know how I can play a dvd iso file on a shared windows network drive?

I installed smbfs last night, but it wasn't clear to me how to use that in solving my problem. Like I said earlier, the drive is visible on the file manager and I can access other types of files just fine. Is there a separate step to mounting the iso file specifically?

Thanks

---

### Post by eeeek on 2008-11-06
I just learned the following:

> *VLC cannot play files over the network unless you manually mount it to a directory via the mount command in the console.*

from: [http://forum.eeeuser.com/viewtopic.php?id=12466]("http://forum.eeeuser.com/viewtopic.php?id=12466")

So this means I have to mount the iso file outside of VLC. I thought of that and have tried, but without success. I tried using gmount, but I'm still a little hazy on file locations across shared drives. I guess I still have more learning to do.

---

### Post by randcoop on 2008-12-17
Mounting across the network shouldn't make any difference (unless your network drive isn't granting you permission).  The mount command to use in the command line (a terminal) is ```
sudo mount -t iso9660 -o loop [path to file/filename.iso] [your mount directory]
```

Once it's mounted, VLC will play it.

---

