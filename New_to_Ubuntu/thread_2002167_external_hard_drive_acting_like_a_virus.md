---
title: "external hard drive acting like a virus"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by Airycat on 2012-06-12
12.04 LTS Just installed, but the problem began about a week ago and seems to be getting worse.

If I plug in my external hard drive (on which I store anything and everything), programs won't open (or are open, but invisible). It started out as an occasional file or program and now 90% of my mail (all mail I keep goes to the ehd) won't work  and I can only seem to run/open one or two programs/files at a time. NOT Good!:(  At first, when I unpluged the ehd, the unopened/invisible programs/files showed up. Now they may or may not. These invisible programs can sometimes include the bar at the top that has the sound, time, etc. on it unless the ehd is off when I start up. There is also a lot of drag time in the programs that do show up and work well otherwise. I don't get any messages except an occasional "Thunderbird is already running and unresponsive. Close that operation for this one to work." (not the exact wording) 

I ran ClamTK on the internal drive (which is OK), but did not see a way for it to scan the ehd. I'm told that Linux (practically) never gets viruses, so I'm assuming it's something on the external hard drive which was originally set up when I had Windows 7), but I also have a few programs that run on Wine and I have no idea if that makes my computer susceptible to Windows problems. I suppose it could also be something completely different, but I have no idea. 

I was doing a lot of graphics work when this started. I have no idea if that might be part of the problem. I assume the cache clears on restart, but I also remember in Windows I occasionally had to manually clear the cache. Do I have to do that here? If so, how?

Is there a way to see what's running on my computer (like Ctrl/Alt/Delete on Windows)?

After several months of no problems (other than not having a couple of Windows based programs I want), I'm frustrated.

Is this likely a virus on my ehd or is there some other problem? 

I did searches, but nothing that looked like this (to me) came up.

TIA
~Faith

---

### Post by mbzn01 on 2012-06-12
Don't know about clam on the external drive. It is possible though. I think you have to scan the directory for the drive (/mount/hd or /media/hd) or whatever the case.
Try htop for running processes.
sudo apt-get install htop.

---

### Post by Cheesehead on 2012-06-12
The symptoms you describe seem much more like failing hardware (perhaps drive) than a virus.

---

### Post by mastablasta on 2012-06-12
ther eis system informaiton monitor that does what you need. or in temrnial top or htop (after you install it)
 
it could be that there is a hardware error on your external disk. what file system do you use on it?

---

### Post by Sidewinder1 on 2012-06-12
Sounds hardware related to me as well. Perhaps you might run "Disk Utility" program in order to check the ext. HD. It should be {Disk Utility}, installed by default.
Side

---

### Post by Airycat on 2012-06-13
Thank you, Everyone.

 I ran Disk Utility and it said the drive was fine... but when I ran "check filesystem" I got an error messages:
[[img]http://farm6.staticflickr.com/5348/7367670448_3b20f31c3a.jpg[/img]](http://www.flickr.com/photos/airycat/7367670448/)
[Screenshot from 2012-06-12 14:24:59](http://www.flickr.com/photos/airycat/7367670448/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr

Later I got some other messages:
_Part 1_
[[img]http://farm8.staticflickr.com/7221/7182437691_8fddcbceb8.jpg[/img]](http://www.flickr.com/photos/airycat/7182437691/)
[Screenshot from 2012-06-12 01:09:40](http://www.flickr.com/photos/airycat/7182437691/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr
_Part 2_
[[img]http://farm6.staticflickr.com/5448/7182438535_924b074054.jpg[/img]](http://www.flickr.com/photos/airycat/7182438535/)
[Screenshot from 2012-06-12 01:09:51](http://www.flickr.com/photos/airycat/7182438535/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr


And this one at least 3 times:
[[img]http://farm8.staticflickr.com/7222/7367671362_1ec1f32778.jpg[/img]](http://www.flickr.com/photos/airycat/7367671362/)
[Screenshot from 2012-06-12 17:10:50](http://www.flickr.com/photos/airycat/7367671362/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr
Got a white screen when I tried to get a screenshot of the details. 

Another message I got (in the details) was that they drive was busy! Doing what, I don't know!  

From January until now I have never had any problems. Right now I have the ext. hard drive connected to my XP laptop running the antivirus scan. I'm doing the complete scan and it DID find something, but there is still so much to scan I can't see what it is, yet. I'll check back tomorrow to see if it's fixed or not and either ask more questions or mark this resolved. Sometimes the antivirus will choose something as unwanted that is something I've been using without problems for ages (but might have some adware)

Right now, other than not having most of my files, (and not being able to delete a nuisance file--different thread), things seems to be running smoothly. Do I need to worry about any permanent damage from the  "malicious or potentially unwanted software" the antivirus program found?

(The pictures are all full size at Flickr if you need to read them.)

~Faith

---

### Post by mastablasta on 2012-06-13
first off NTFS is a windows (microsoft) file system.
 
secondly i see you have a 2TB drive - are there any partitiions on it? has the drive been propperly aligned? for example: 
[http://en.wikipedia.org/wiki/Advanced_Format](http://en.wikipedia.org/wiki/Advanced_Format)
 
> When using Advanced Format drives with legacy operating systems, it is important to realign the disk drive using software provided by the hard disk manufacturer. Disk realignment is necessary to avoid a performance degrading condition known as cluster straddling where a shifted partition causes filesystem clusters to span partial physical disk sectors. Since cluster to sector alignment is determined when creating hard drive partitions, the realignment software is used "after" partitioning the disk. This can help reduce the number of unaligned writes generated by the computing ecosystem
 
[http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance](http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance)
 
[http://www.wdc.com/global/products/features/?id=7&language=1](http://www.wdc.com/global/products/features/?id=7&language=1)
 
 
if they are not aligned disk can suddenly become slow.

---

### Post by Sidewinder1 on 2012-06-13
First, what was stated above ^ . I didn't know anything about all of that;  thank you very much mastablasta for enlightening us :P .

Second, I noticed that the ext. HD in question is a Seagate, Free Agent drive. Unfortunately, from all that I have read, Seagate and their quality and control has gone down hill for many years. Their hard drives used to be one of the finest in the industry; ever since around 2005, I have read many complaints form others regarding shoddy mfg. etc. In addition, I purchased a Free Agent ext. HD around 2007 and returned it to Newegg {which they kindly replaced with a Western Digital} because my ubuntu had problems with the way Seagate's drives powered-down/hibernated.

And, finally, thirdly.. from your screen shots it would appear that your Seagate was 'mounted' when, in Disk Utility, you ran "Check Filesystem". If that command utilizes fsck {without internally unmounting and then re-mounting, after the check is completed} that is a potential for future problems. In the documentation of fsck it specifically states "Never run fsck on a mounted filesystem."

I know none of the above solves your problem and for that I apologize. I know how frustrating trouble-shooting can be and I just wanted to throw some ideas and thoughts, in your direction in the hope that you might have an "Ah-Ha." moment.

HTH,

Side

---

### Post by Sidewinder1 on 2012-06-13
Oh, I forgot (with that diatribe, above, you're wondering, how could that clown have forgotten anything).
As a suggestion and or question, why did you leave the formatting of that ext. drive set to NTFS? I know that's how they're shipped but, that's a Windoze file system. You're not using WUBI, are you? If so, I'll bow out of this thread.
Just for future reference all of my ext. HDs, both eSATA and USBs were reformatted to ext3 or ext4 on their arrival, for obvious reasons.

---

### Post by afixane on 2012-06-13
Try to run chkdsk in Windows (if you're dualboot with windows) or try fsck in Terminal :p

---

### Post by Airycat on 2012-06-13
Well, I chose the right forum, anyway. I'm more of a n00b than I realized! ALL my computer experience before this past January (discounting a few months in 1987 with a Tandy) has been with Windows.

mastablasta, I had no idea! I did know that NTFS was Windows, but I didn't know that it mattered since it was working fine until now. I will read the links later this afternoon and look for a SeaGate disk (which I don't remember having).

Does this mean that if I go back to a dual boot (because none of my language programs work in Ubuntu) I have to divide the ext hd, too? I was under the impression that hard drives (unless they held the OS) were plug and go... except I should have known, 'cause my son's Mac neets FAT files

Sidewinder1, I was chuckling all through your explanation of Seagate not being as good as it was. I had two Western Digital disks die withing a year of  purchase and I was lucky to retrieve any data. That's why this one is a SeaGate. I'm guessing quality everywhere is down.

More n00biness, I thought mounted meant connected and never would have thought to unmount it. (And yes, I'm bad about reading directions.)

The antivirus (on my Windows laptop) is still running after 17 hours of deep scanning this drive, so I still don't know what it found.... 

OK a Trojan and  some unwanted adware. Getting rid of that should help.  Next step, figuring out how to reformat the hd with 600 mb already on it. 

Thanks for all the help!

---

### Post by Airycat on 2012-07-10
Finally had my brother, visiting from the opposite coast, take a look at it. He put everything on the drive into a folder and now it's fine. Apparently there was an auto run on the drive and it ran as soon as it was turned on. I merely need to find the auto run (I think I know what it is) and delete it.

Thanks for the help. I learn from it, even when it doesn't directly solve my problem.

---

### Post by edfast on 2013-04-01
@ mastablasta, @ Sidewinder1; just to let you know that, your very fruitful discussion (diatribe, according to some..) helped me solve a somewhat related, though different issue with a non-showing hard drive. So, Kudos from the evesdropper in the flanks! Just thought you might want to know...:)

---

