---
title: "64 bit or 32 bit"
date: 2010-06-22
forum: Recurring Discussions
---

### Post by anand_30 on 2010-06-22
I just bought new desktop.Here are its specifications:-
intel i3core 2.93Ghz
2Gb DDR3 RAM
500Gb HD

Currently I am using Windows 7 32 bit.
I dont know very much about sound and display drivers.But in windows its showing realtek high definition audio.

I have used ubuntu 10.04 32bit on my older desktop.Now i can't decide which ubuntu i should install?

I have few questions:-

1.If i install 64 bit will it give my that 'extra' boost?

2.I have seen some problems regarding flash player plugin for 64 bit ubuntu version while browsing ubuntuforums.Will that plugin work for me?Since i use most of my desktop for browsing and playing flash games,that plugin is important for me.

3.Three is only 55Gb of un-partitioned space at the end for ubuntu.Is that sufficient?I have given small space considering that i can't access ext4 from my windows.

4.Some people here say that new programs are compiled and designed to work in 32 bit.64 bit versions are not available sometimes.Will that affect me?

5.If i install 32 bit am i under-utilizing system hardware?

Please help me to get out of this confusion.
Thanks in advance.

---

### Post by Spr0k3t on 2010-06-22
1. Yes... but the significance is hard to tell unless you look at the numbers
3. I have Ubuntu on 8GB and that's good enough for a small system with a little extra.
4. There are also some things which have been written specifically for 64bit and no 32bit options are available.
5. Of course.  However, by how much is up to you to determin.

If you had more than 3.65GB of memory, you could install the PAE version of the kernel for 32bit addressable space beyond the 4GB memory limit.  Eventually, most things will move to 64bit since all new computer systems are capable of processing in 64bit architechure.  The only thing I see holding everyone back (not just you) is flash.

---

### Post by TriBlox6432 on 2010-06-22
Installing 32 bit with those specs is pointless.  Unless you have more than 3.5gb of ram there wont be any difference.

---

### Post by anand_30 on 2010-06-22
> **Spr0k3t said:**
> 1. Yes... but the significance is hard to tell unless you look at the numbers
3. I have Ubuntu on 8GB and that's good enough for a small system with a little extra.
4. There are also some things which have been written specifically for 64bit and no 32bit options are available.
5. Of course.  However, by how much is up to you to determin.

If you had more than 3.65GB of memory, you could install the PAE version of the kernel for 32bit addressable space beyond the 4GB memory limit.  Eventually, most things will move to 64bit since all new computer systems are capable of processing in 64bit architechure.  The only thing I see holding everyone back (not just you) is flash.

Thanks.:)

So 2Gb of memory will disqualify me using PAE version of kernel?Don't know about PAE.just read on wikipedia but its above my head.

---

### Post by amauk on 2010-06-22
> **anand_30 said:**
> Don't know about PAE.just read on wikipedia but its above my head.It's a hack to overcome the inherent 4Gb address space limit on 32bit systems
(2^32 = 4Gb)

It uses a virtual address space mechanism to transparently shuffle around the RAM mappings

You can address the full extent of RAM, but an individual processes cannot use more than 2Gb

It's a hack
If you have a 64bit capable system, there's no reason (besides some proprietary software that (for some unexplainable reason) are reluctant to go 64bit) not to use a 64bit OS

---

### Post by Windows Nerd on 2010-06-22
> **anand_30 said:**
> Thanks.:)

So 2Gb of memory will disqualify me using PAE version of kernel?Don't know about PAE.just read on wikipedia but its above my head.
The whole point of a PAE Kernel is so a 32 bit OS can use more than 3.65 MB of RAM if you have it. Otherwise there is not much of a point. 

Scott

---

### Post by anand_30 on 2010-06-22
Thank you amauk and Scott.
It means that THE HACK will not be useful to me.](*,)

---

### Post by prshah on 2010-06-22
> **anand_30 said:**
> 
1.If i install 64 bit will it give my that 'extra' boost?

2.I have seen some problems regarding flash player plugin

3.Three is only 55Gb of un-partitioned space at the end for ubuntu.Is that sufficient?I have given small space considering that i can't access ext4 from my windows.

4.Some people here say that new programs are compiled and designed to work in 32 bit. Will that affect me?

5.If i install 32 bit am i under-utilizing system hardware?

I've recently (about 2 months back) switched from 32bit to 64bit (fresh install).

1. 64-bit gives a huge performance boost when handling number or graphics intensive operations (video transcoding, GIMP renders, etc). Day-to-day performance will be unchanged. ffmpeg transcoding finishes in 33% of the time it took in 32bit.

2. I had absolutely no problems with flash; just installed restricted-extras, launched the browser, clicked "install plugin" on the first flash enabled page it found.

3. Personally speaking, I would stick 55GB to W7; however, it's more than enough, provided you keep your home directory pruned from time to time (Eg, remove heavy downloads, etc). 

4. Nope; all programs, 32-bit, 64-bit, whatever work fine.

5. After I switched, I am very happy with 64bit; I think going back to 32bit will make me FEEL as though the system is underutilized; but there is no such thing actually.

Hope these help; my recommendation would be to go with a fresh 64bit install. I use Ubuntu (Gnome) btw.

---

### Post by anand_30 on 2010-06-22
> **prshah said:**
> I've recently (about 2 months back) switched from 32bit to 64bit (fresh install).

1. 64-bit gives a huge performance boost when handling number or graphics intensive operations (video transcoding, GIMP renders, etc). Day-to-day performance will be unchanged. ffmpeg transcoding finishes in 33% of the time it took in 32bit.

2. I had absolutely no problems with flash; just installed restricted-extras, launched the browser, clicked "install plugin" on the first flash enabled page it found.

3. Personally speaking, I would stick 55GB to W7; however, it's more than enough, provided you keep your home directory pruned from time to time (Eg, remove heavy downloads, etc). 

4. Nope; all programs, 32-bit, 64-bit, whatever work fine.

5. After I switched, I am very happy with 64bit; I think going back to 32bit will make me FEEL as though the system is underutilized; but there is no such thing actually.

Hope these help; my recommendation would be to go with a fresh 64bit install. I use Ubuntu (Gnome) btw.

Good to hear that flash is working.I hope i am as lucky as you in that case.

So you think from that 55 Gb space i should format all with NTFS and then install ubuntu ina bout 20 Gb?

I can see 55 gb unpartitioned space at the end in disk management but how to format it?

I am little bit afraid of doing 'New Simple Volume' as its new desktop.Is it the correct way?

---

### Post by Gone fishing on 2010-06-22
You may have problems running Flash on 64bit systems?

[http://ubuntuforums.org/showthread.php?t=1358591&highlight=64+bit+flash](http://ubuntuforums.org/showthread.php?t=1358591&highlight=64+bit+flash)

---

### Post by anand_30 on 2010-06-22
> **Gone fishing said:**
> You may have problems running Flash on 64bit systems?

[http://ubuntuforums.org/showthread.php?t=1358591&highlight=64+bit+flash](http://ubuntuforums.org/showthread.php?t=1358591&highlight=64+bit+flash)

There should be previous version of flash player available for 64bit ubuntu.

Why this happens the two imp things that i want namely flash player and a good CAD on my favourite os ubuntu are not there?

---

### Post by Windows Nerd on 2010-06-22
> **anand_30 said:**
> Good to hear that flash is working.I hope i am as lucky as you in that case.

So you think from that 55 Gb space i should format all with NTFS and then install ubuntu ina bout 20 Gb?

I can see 55 gb unpartitioned space at the end in disk management but how to format it?

I am little bit afraid of doing 'New Simple Volume' as its new desktop.Is it the correct way?
If it's unpartitioned space, (Windows Disk Manaement reads it as "Unallocaed Space"), you are free to partition that space in a linux partition with GParted, linux's own partitioner on a Linux Live CD. Just make sure that if you are shrinking/resizing partitions,**Back up any data on your partitions that you don't want to lose**. 

If you have 55 GB of unallocated space, 30 GB (or however much you want, but around 15+ GB should be plenty, so long as you don't start storing a lot of media on that partition) can be formatted in Linux Ext3/Ext4 (Ext4 is newer, but some people say it has more bugs, I have gotten no bugs with my use of ext4). 

As far as mount points when the Linux partitioner asks, just make your partition mount at / (root). There is better ways to do this, but since you seem a bit unfamiliar with the process creating one partition should be the easiest for you.

You will also want to create a SWAP partition, but the size is dependant on the size of your RAM. The general rule with swap: if you have less than ~2 GB RAM, it should be 1.5 - 2x your RAM. If you have more than 2, it should be anywhere from 1x-1.5x your RAM. 

If I did not clarify something or if you would like an explanation of stuff, just ask.

Scott

---

### Post by philinux on 2010-06-22
Moved to recurring discussions

---

### Post by oldos2er on 2010-06-23
> **anand_30 said:**
> There should be previous version of flash player available for 64bit ubuntu.


[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

 64-bit flash has a significant security bug. [http://www.adobe.com/support/security/advisories/apsa10-01.html](http://www.adobe.com/support/security/advisories/apsa10-01.html)

---

### Post by nrs on 2010-06-23
I still use 32bit because I have severe performance degradation using 64bit Flash. 32bit Flash is still a pig but it's a lot more usable, IMO. There also exists a massive security vulnerability that Adobe has declined to patch for 64bit, AFAIK.

---

### Post by anand_30 on 2010-06-24
> **Windows Nerd said:**
> If it's unpartitioned space, (Windows Disk Manaement reads it as "Unallocaed Space"), you are free to partition that space in a linux partition with GParted, linux's own partitioner on a Linux Live CD. Just make sure that if you are shrinking/resizing partitions,**Back up any data on your partitions that you don't want to lose**. 

If you have 55 GB of unallocated space, 30 GB (or however much you want, but around 15+ GB should be plenty, so long as you don't start storing a lot of media on that partition) can be formatted in Linux Ext3/Ext4 (Ext4 is newer, but some people say it has more bugs, I have gotten no bugs with my use of ext4). 

As far as mount points when the Linux partitioner asks, just make your partition mount at / (root). There is better ways to do this, but since you seem a bit unfamiliar with the process creating one partition should be the easiest for you.

You will also want to create a SWAP partition, but the size is dependant on the size of your RAM. The general rule with swap: if you have less than ~2 GB RAM, it should be 1.5 - 2x your RAM. If you have more than 2, it should be anywhere from 1x-1.5x your RAM. 

If I did not clarify something or if you would like an explanation of stuff, just ask.

Scott

Hey thanks but oops i gave only 1gb space for swap.Does that matter??(Sorry i did installation before reading your post ).
I formatted that 55Gb with NTFS in windows,then using ubuntu 64bit live CD i made partition of 25gb for root / and 1gb swap area at the end. 

64 bit wooohoooo!!!!!!!!!
Its lighting fast os,liking it very much.

No problem uptill now.Installed restricted extras**.FLASH is working fine** just saw youtube video.Sound is also working great.All in all great system.

THANK YOU UBUNTU and all you people who helped me.:guitar:

---

### Post by anand_30 on 2010-06-24
> **oldos2er said:**
> [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

 64-bit flash has a significant security bug. [http://www.adobe.com/support/security/advisories/apsa10-01.html](http://www.adobe.com/support/security/advisories/apsa10-01.html)

Thanks.
Hope they will make upcoming version more secure.

---

### Post by anand_30 on 2010-06-24
> **nrs said:**
> I still use 32bit because I have severe performance degradation using 64bit Flash. 32bit Flash is still a pig but it's a lot more usable, IMO. There also exists a massive security vulnerability that Adobe has declined to patch for 64bit, AFAIK.

No performance degradation here,flash is working nice.:popcorn:

---

### Post by Windows Nerd on 2010-06-24
> **anand_30 said:**
> Hey thanks but oops i gave only 1gb space for swap.Does that matter??(Sorry i did installation before reading your post ).
If you have some 2GB odd of RAM, you should be okay. The only problem will be using suspend-to disk (More commonly called "Hibernate"),  because when you do that Ubuntu saves the contents of your RAM to your Swap space. If you have filled up all 2GB of RAM, it won't fit in the 1GB of Swap space.

There won't be a problem unless you choose the hibernate feature. With Ubuntu's lightning fast boot, not many people use hibernate anymore, because it takes the same (or in my experience, more) time to boot up from Hibernate than from a normal shutdown.

Scott

---

### Post by anand_30 on 2010-06-25
Thanks Scott.
i don't use hibernate feature so that will not affect me.

Hey just for fun i tried 64 bit live CD into 32 bit acer dual core laptop of my friend and it worked.So does that iso support both 32 as well as 64 bit?

---

### Post by formaldehyde_spoon on 2010-06-26
> **anand_30 said:**
> No performance degradation here,flash is working nice.:popcorn:
Yep, 64 bit flash good for me too.

---

### Post by WinterRain on 2010-06-26
> **formaldehyde_spoon said:**
> Yep, 64 bit flash good for me too.

To beat a dead horse, FLASH WORKS GOOD IN 64BIT!!!!

Go here to get the last version adobe released. [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Just extract it and put it in ~/.mozilla/plugins. Easy.

---

