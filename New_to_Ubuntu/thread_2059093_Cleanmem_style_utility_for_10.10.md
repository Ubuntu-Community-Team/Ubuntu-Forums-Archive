---
title: "Cleanmem style utility for 10.10?"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by I2k4 on 2012-09-17
Dual booting Lubuntu 10.10 and W7 on an Acer N270 netbook (1.5mhz, 1GB RAM), generally Lubuntu is noticeably snappier.  

Until recently under _both_ OSs I was having continual stalls and buffering on the resource-demanding Bloomberg.com live TV feed.  (YouTube, etc. video runs fine on less than hi-def.)  I like to keep the little pop out of the TV feed down in the screen corner while doing other things.

The thing is, I just came across the little _Windows utility_ CleanMem, in short form [SIZE=2]it periodically [SIZE=2]cleans memory and avoid [SIZE=2]swapping to the h[SIZE=2]ard drive[SIZE=2], and it [/SIZE]has essentially fixed the problem on W[SIZE=2]7.  I've searched here and googled for an equivalent utility for Lubuntu but can't find on[SIZE=2]e[SIZE=2], only a lot of discussions of [SIZE=2]Linux native memory management.  _I'd appreciate any information about a [SIZE=2]Linux utility that would do the same for Lubuntu 10.10[SIZE=2].[/SIZE][/SIZE]_  Th[SIZE=2]anks[SIZE=2].[/SIZE][/SIZE]

[SIZE=2](I[SIZE=2] don't[SIZE=2] know if[/SIZE][/SIZE] recent versions of Ubuntu, etc. [SIZE=2]have changed anything in this regard, but am not going to upgrade on [SIZE=2]the netbook[/SIZE].  The new versions are[SIZE=2] more sluggish all around than W7 [SIZE=2]and I'[SIZE=2]m sti[SIZE=2]cking with [SIZE=2]10.10 for the life of[/SIZE][/SIZE][/SIZE][/SIZE] this little machine.)[/SIZE] [/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by GeForce 9500GT on 2012-09-17
I can't think of anything else like Bleachbit or Ubuntu Tweak.

---

### Post by snowpine on 2012-09-17
This capability is built into Linux, check out the linked document, in particular the section "What is swappiness and how do I change it?"

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Generally speaking Flash on Linux is inferior to Flash on Windows, I have never had good flash playback on any of my 3 Atom-based computers. Rather, I download the video and watch it locally from my hard drive using VLC... just a suggestion.

---

### Post by I2k4 on 2012-09-18
Thanks for replies.  I use Bleachbit but obviously it's a one-off cleanup, not dedicated to memory and not automatic every 15 minutes.  My Lubuntu video experience with and without Flash has been fine on the Atom, e.g. on YouTube or Vimeo, and that's without the considerable OS tweaking I do to speed up Windows.     

Unfortunately downloading a video file isn't an option for a live real time TV stream like Bloomberg, which is the main problem. Windows 7 was just as bad until I found the little memory cleaner for it - would be great to have the same for Lubuntu.

---

### Post by mips on 2012-09-19
Have a look at that link snowpine gave you ;)

---

### Post by GeForce 9500GT on 2012-09-19
> **snowpine said:**
> This capability is built into Linux, check out the linked document, in particular the section "What is swappiness and how do I change it?"
 
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
 
Generally speaking Flash on Linux is inferior to Flash on Windows, I have never had good flash playback on any of my 3 Atom-based computers. Rather, I download the video and watch it locally from my hard drive using VLC... just a suggestion.
 
Hmmmm...... this looks a bit confusing to me:
 
> 

High RAM and low disk space With 2 GiB RAM and 30 GB hard disk, use 1 GiB for swap since hard disk space is very low.  
High RAM and high disk space With 2 GiB RAM and 100 GB hard disk, use 2 GiB for swap since hard disk space is plentiful. 

 
Shouldn't this be the opposite?? Like:
 

>  
High RAM and low disk space With 2 GiB RAM and 30 GB hard disk, use **2 GiB** for swap since hard disk space is **very low**. 
  High RAM and high disk space With 2 GiB RAM and 100 GB hard disk, 
 use **1 GiB** for swap since hard disk space is **plentiful**. 


 Same for the situation of Low Ram. I don't know, but it's been told to me when you have a lot of RAM and a lot of disc space there's no need for hugh swap.... :confused:

---

### Post by I2k4 on 2012-09-19
> **mips said:**
> Have a look at that link snowpine gave you ;)

Thanks, I'd looked at it - the issue isn't amount of swap, it's that the little Windows utility forces a cleanup of RAM every 15 minutes and _prevents using swap_.  That Bloomberg TV feed taxes the Atom 1GB RAM to the max.  Lubuntu plain vanilla and Windows (with ReadyBoost, fixed pagefile, various other tweaks) had exactly the same stalling and rebuffering problems, until the little app fixed it in Windows.  So I'm looking / hoping for a similar app or system setting for Lubuntu.

---

