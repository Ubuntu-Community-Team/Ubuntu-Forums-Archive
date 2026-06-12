---
title: "Quick Question: Is a Swap Partition Necessary?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by psyoptic on 2008-10-30
I was reading about common partition layouts and most of them mentioned a swap partition that would be used in case my system ran out of memory. I currently have 2 Gb of DDR2 800 MHz memory, so would I really need a swap partition? I really doubt Ubuntu would be as resource hungry as Vista and go beyond that limit. What do you guys think I should do? Personally, I don't think it's necessary, but I'd appreciate any feedback.

One more thing I'd like to ask is, how would making a /home partition really keep my settings intact if I planned on doing a fresh install for a future release. Would I just have to do an install over the old /root partition?

---

### Post by nynoah on 2008-10-30
Yes

---

### Post by Zzl1xndd on 2008-10-30
You can in fact work without a swap partition although I don't recommend it unless you are running on a solid state drive.

as for your second question many settings are stored in hidden folders in your home partition so when you do a fresh install and have a separate home partition those setting are picked up.

---

### Post by vanden12 on 2008-10-31
> # To begin with, let's say that computers have changed a lot since swap was first used :

    * At first, swap was needed to extend real memory capacity. You would use swap so that the available memory would be the addition of the ram space and the swap space.
    * Nowadays, ram are often big enough so that we could use the computer without any swap at all. 

#

Some programs really are memory-consuming :

    *

      Sometimes, something big (like OpenOffice, Neverwinter Nights or some video editor) make the entire system need extra memory.
    * In these cases, swap will be used to make the system able to handle the extra load. 

#

Extra memory might come in handy :

    * Unforeseeable events, might and will happen (a program going crazy, some action needing much more space than you thought, or any other unbelievable combination of events).
    * In these cases, swap will give you an extra delay to figure out what happens or to finish something. 

#

Swap can optimize memory usage :

    *

      Hard drives are considerably slower than RAM. So when you need a file (be it a data file, like this video you're watching again and again, executables, like Firefox, or libraries), Linux reads the file into RAM and keeps it there so than the next time you need it again, it's already in RAM and data access is much faster (thousands of times faster). We call these portions of RAM that accelerate disk read "cached memory." They make a huge difference in terms of responsiveness.
    * Linux automatically moves RAM reserved by programs but not really used in swap so that this ram can serve the better purpose of having more cached memory. 

#

Hibernation needs swap

    *

      The hibernation feature (suspend-to-disk) writes out the contents of the memory to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size. The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition, and can not use a swap file on an active file system. 

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

So yes and no... 

It helps if you have a little extre space to give to the swap but it not really needed...

---

### Post by aramadia on 2008-10-31
A swap partition isn't necessary for 2GB.  Just to clarify a hard disk would be worse for swap space than SSD.

Also configuration files are stored in /etc.  You might care about /var too.

---

### Post by kansasnoob on 2008-10-31
> **nynoah said:**
> Yes

+1. The answer is yes!

I quite often run multiple Linux OS's and I share swap. When I first started doing so I didn't understand the uuid thing so the swap I thought I was sharing did not work with all of my OS's.

Things like editing video or even pics can eat enough resources that you should always have at least 1GB swap!

The old rule was double the size of memeory, but 1 GB is sufficient!

---

### Post by psyoptic on 2008-10-31
> **kansasnoob said:**
> +1. The answer is yes!

I quite often run multiple Linux OS's and I share swap. When I first started doing so I didn't understand the uuid thing so the swap I thought I was sharing did not work with all of my OS's.

Things like editing video or even pics can eat enough resources that you should always have at least 1GB swap!

The old rule was double the size of memeory, but 1 GB is sufficient!

Thanks for the helpful tip!

I think I'll go with 2 gb just to be safe, but I'll keep the 1 gb note in mind. Thanks!

---

### Post by nynoah on 2008-10-31
Really, I would sacrifice storage to make sure it ran correctly.  You can burn 4 gigs onto a DVD.  So memory storage is not really a huge deal when you are talking about 2 more gig.  IF you are doing a lot of multi tasking go with more.

---

### Post by hyper_ch on 2008-10-31
swap is also needed for hibernation... as harddisk space is cheap I don't really see a reason to not use swap. I have 4 gb ram and use 4gb swap (well, I normally run multiple VM together but that's not the point).

---

### Post by akiratheoni on 2008-10-31
> **nynoah said:**
> Really, I would sacrifice storage to make sure it ran correctly.  You can burn 4 gigs onto a DVD.  So memory storage is not really a huge deal when you are talking about 2 more gig.  IF you are doing a lot of multi tasking go with more.

Agreed. I have a 500GB hard drive and 2GB RAM and so sacrificing 2-4 GB for swap isn't a big deal for me. Even if I had less than 200GB, 2-4GB isn't that much space, really... and if it means my system runs fine, then I'll do it.

---

### Post by pansz on 2008-10-31
Yes you need a swap partition because nowadays the main purpose of swap partition is NOT to extend your memory when you run out of memory but to optimize memory usage.

According to kernel code, the memory algorithm is different when switch-off the swap.

I would recommend a swap between 128M and 2G, if you don't like the swap just make it 128M, if you want a swap please don't make a swap more than 2G.

having an 128M swap is way better than no swap at all!

---

### Post by lH)4~mK0e on 2008-10-31
From all my experience as a linux user, I have read in numerous places about swap partition configuration.  You can have a swap partition up to 2x the size of your physical RAM (sometimes more depending on the system).  If you think in terms of the more mainstream O/S, swap is similar to Virtual Memory.  Swap gets used when the system runs out of reasonable RAM to perform a certain function.  Unlike Virtual Memory, a swap partition is a dedicated area.  VM tends to find an area of the drive that makes the most sense to it dynamically and changes locations as needed, usually causing fragmentation.

---

### Post by psyoptic on 2008-10-31
> **akiratheoni said:**
> Agreed. I have a 500GB hard drive and 2GB RAM and so sacrificing 2-4 GB for swap isn't a big deal for me. Even if I had less than 200GB, 2-4GB isn't that much space, really... and if it means my system runs fine, then I'll do it.

Good point. Would doubling the amount of space for my swap (4 gb as opposed to 2 gb) create any benefits performance-wise?

---

### Post by akiratheoni on 2008-10-31
> **psyoptic said:**
> Good point. Would doubling the amount of space for my swap (4 gb as opposed to 2 gb) create any benefits performance-wise?

I don't think I ever went above 1GB in all of the times I've used Ubuntu, 2GB for swap should be fine.

---

### Post by Rolcol on 2008-10-31
If you really don't want to have another partition for swap, you can create a swap file.

[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

---

### Post by hyper_ch on 2008-10-31
if you are on 32 bit you can't address more than 4gb ram. Keep that in mind. However you could get the kernel server or manually recompile the generic one with PAE. That would then allow you to address more.

---

### Post by SunnyRabbiera on 2008-10-31
Swap does come in handy even with higher memory, its best for hibernation mode and is useful to keep you out of issues.

---

### Post by nynoah on 2008-10-31
I have used more than 2 gig of my swap.  Swap also prevents your computer from locking up when a programs starts to glitch.  I have watch my swap rise higher and higher as I multi task and I am thankful for having it.  But then again I can REALLY tax my system.  Heck right now I am using 15% of it

---

### Post by 3rdalbum on 2008-10-31
I have a computer with 1.25 gigabytes of RAM. The most swap it ever uses is 17 megabytes. However, I'd recommend either having as much swap as you have RAM (so you can hibernate) or don't have any swap at all. My current machine does not have any swap space at all.

---

### Post by Christopher on 2008-10-31
I have 8gigs of system memory, should i have a swap of 8gigs? Thank you in advance.

---

### Post by hyper_ch on 2008-10-31
if you want to hibernate then you should have a leat equal swap as ram... otherwise, see how much swap you use when you fire up all your usual things :) maybe 2gb would be sufficient, just to have some :)

---

### Post by Paqman on 2008-10-31
> **tweakedenigma said:**
> I don't recommend it unless you are running on a solid state drive.


> **aramadia said:**
> a hard disk would be worse for swap space than SSD.


Sorry to veer off topic slightly, but i'm interested in why this is? I'm leaning towards switching to SSDs (at least for the OS) in the near future, but there's not a lot of technical info around about them in practical terms.

Why would a faster hard drive negate the need for swap space?

---

### Post by rsambuca on 2008-10-31
> **Christopher said:**
> I have 8gigs of system memory, should i have a swap of 8gigs? Thank you in advance.

I honestly don't think you will need your swap.  I can't imagine any circumstance where you will be come close to using 8 GB of Ram.

---

### Post by Duck2006 on 2008-10-31
On my other system i don't run a swap partition and it runs fine with 660Mb of ram. If your going to run video editing or some thing that needs a lot of ram then yes run a swap file.

---

### Post by m_duck on 2008-10-31
@ Paqman
From what I have seen (regarding setting up a new OS on my eeePC with SSD) swap is generally not advised, nor are keeping log files on a solid state disk. This is due to the fact that many have a finite amount of disk writes before they fail, so disabling swap and logging on the disk, and putting it all in memory can increase the life of the disk. I don't know anything really about it, just regurgitating what I have read.

I have 4GB ram and tend to use a 512MB swap (though Ubuntu's installer decided it wanted to give me 10GB once...). The swap is rarely but occasionally used and I do not use hibernation.

---

### Post by solitaire on 2008-10-31
My laptop has 512Mb of ram and it's currently using 90Mb of Swapfile (i've set aside 1.5Gb for swap)

Think the general rule of thumb (in my experience) is: 
if you have 1Gb or less of memory then a min of combined 2Gb of Memory / Swap avalible, that gives you a stable system. 
if you have 1Gb - 2Gb of memory then a min of 1Gb set aside as swap
Over 2Gb it's your discretion.

*Note* if you are doing Multimedia stuff like video or picture editing then i'd add 1Gb to the above limits :D lol!!

---

### Post by Christopher on 2008-10-31
Ok thank you everyone for the info.

---

