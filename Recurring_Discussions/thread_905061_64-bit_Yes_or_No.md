---
title: "64-bit: Yes or No"
date: 2008-08-29
forum: Recurring Discussions
---

### Post by mjr2k on 2008-08-29
I'm considering a move from Windows XP MCE 2005 to Heron 64bit.  Here's a breakdown of what I do in MCE.  I'm running Heron 32bit on a Pentium 3 for the purposes of researching this move.

DVD ripping using DVD Decrypter
Use the MS office suite for school work (which won't matter in 6 months)
Photoshop for Image Manipulation
Nero and/or Roxio for CD/DVD burning
Windows Media for playing music in playlists
Tivo Desktop to transfer movies back and forth and some editing here and there.
Console Emulation that only uses .exe's

THe computer that is being considered for a 64bit install's specs:
AMD Athlon 64 X2 at 2.2Ghz (not sure of the 4 digit number after the X2)
3GB RAM (considering upping that to 4-5GB)
2 HD - 320GB and a 160GB both PATA
Motherboard integrated VGA, sound and 10/100
Currently has XP MCE 2005

My question for whoever can offer any input:
1) The considered computer could support the 64bit install if I'm not mistaken?  Would I benefit from the 64bit Heron?
2) Can I do at least 90% of what's in that list with Ubuntu?  If so, any recommendations?
3) Is anyone good with configuring Samba and any sort of Remote Desktop between Ubuntu and Windows Vista and XP?

Thanks for any input that anyone can provide!

---

### Post by Crafty Kisses on 2008-08-30
I'd say go with 64-bit.

---

### Post by tamoneya on 2008-08-30
```
if ram > 4GB:
    print "yes"
else:
    print "no"

```
Since you are going to be upgrading to 4-5GB I say yes.

---

### Post by Kilz on 2008-08-30
This topic has been discussed to infinity, please read the sticky.

---

### Post by Sef on 2008-08-30
> My question for whoever can offer any input:
1) The considered computer could support the 64bit install if I'm not mistaken? Would I benefit from the 64bit Heron?

Yes. Depends on what you do.

> 2) Can I do at least 90% of what's in that list with Ubuntu? If so, any recommendations?

Yes.

> 3) Is anyone good with configuring Samba and any sort of Remote Desktop between Ubuntu and Windows Vista and XP?


Please start a separate thread on that.


> Kilz  	
Re: 64-bit: Yes or No
This topic has been discussed to infinity, please read the sticky.  

+1

---

### Post by ansicplusplus on 2008-08-30
Hy mjr2k,

>>DVD ripping using DVD Decrypter
Ripping can be done. You will have to check which app is state of the art for DVDs.

>>Use the MS office suite for school work (which won't matter in 6 months)
Try OpenOffice.

>>Photoshop for Image Manipulation
Try Gimp.

>>Nero and/or Roxio for CD/DVD burning
Brasero Disc Burning / QDVDAuthor / Serpentine 

>>Windows Media for playing music in playlists
vlc f.e.

>>Tivo Desktop to transfer movies back and forth and some 
>>editing here and there.
vlc / mplayer / avidemux

>>Console Emulation that only uses .exe's
wine. You' have to try whether your apps work with wine or not. Use a VM with WindowsXP for apps that you can't use with ubuntu. 

Yours, ansicplusplus

---

### Post by insane_alien on 2008-08-30
64-bit should provide some speed up for DVD ripping (i've found a 10-20% reduction in encoding times.)

---

### Post by mjr2k on 2008-08-30
Thank you all for your replies!  I'm going to do the research and consider the upgrade.

---

### Post by michaelkahl on 2008-08-30
I'm running 64bit simply because I wanted to stack my rig with 4+GB of memory and decided to OC it.  64bit runs great for me both at work and at home.  I haven't had any troubles using rdesktop or mounting my network shares at work. 
I honestly try to avoid running windows programs on my ubuntu like  they are the plague.  I seriously think of it like that.  If I can get around using it, I will.  It can be tough since I do a lot of digital photogrpahy (mainly at home) but between gimp, rawtherapee, and bibble I don't have any problem.

---

### Post by Carl H on 2008-08-30
I've been running 64 bit Hardy for a few months and it's flawless. 

I personally have used Linux for a couple of years now, after giving it an initial try, and I'll never go back to Windows. Last week, I had to install some software for my wife on her XP machine, and I was initially confused as to what to do - I've got so used to the Linux way that Windows seems unnecessarily complicated now.

---

### Post by Yellow Pasque on 2008-08-30
> I personally have used Linux for a couple of years now, after giving it an initial try, and I'll never go back to Windows.
I can't say I'll **never** use Windows again, but I will do everything in my power to avoid connecting that disk (the last time was 2 months ago for a BIOS flash and I had to reactivate it over the phone because I changed the hardware). It's nice to be free of the Windows Genuine Disadvantage.

---

### Post by Fr@nKy on 2008-08-30
Today I was about to set up a Dual Boot System on my laptop, between Windows Vista Home Premium Service Pack 1 32-bit and Ubuntu 8.04.1 Hardy Heron, and I realized that once again I had to choose between 32-bit and 64-bit... Knowing that probably there should be no problema in choosing 64-bit I decided to look around Google about some information. Something I had already heard, but never I've never seen with my own eyes, was that 64-bit software tends to use more memory (even though I never believed in the twice more memory theory) so I decided to search for such comparison and I found this: [http://gquigs.blogspot.com/2008/07/blog-post.html](http://gquigs.blogspot.com/2008/07/blog-post.html)

After that I decided to run the tests myself using my ShipIt CDs containing 8.04 (not 8.04.1) and I got basically the same kind of numbers. So I conclude that 64-bit version of Ubuntu uses about 40 to 50 percent more memory... A few questions an thoughts arouse:

1 - Now I wonder in a 2GB system like my own what should I do? 

2 - Is this higher amount of used memory some kind of more advanced prefetch (a bit like Windows Vista's Superfetch) or is it really using much more memory? 

3 - A 10 to 20 percent increase would be acceptable but such a big difference? 

4 - Also this makes me think that following a 50% increase scenario someone with 2GB of RAM on a 64-bit system will "virtually" have 1.33(3) GB of RAM if compared to a 32-bit system.


Posing all this things... What version should I choose? (Well If I get 4GB in a near future I'll sure just skip 32-bit and go 64-bit but until then I just want what's best for my current system).

EDIT:

I'd also like to add:

5 - Is the 64-bit version already a "threat" to the 32-bit version? I mean is it getting a huge userbase boost that will eclipse the 32-bit version anytime soon?


I'd appreciate a an answer as soon as possible so I can decide what to do... HELP! Please!

---

### Post by bapoumba on 2008-08-31
Welcome to the Recurring Discussions.

---

### Post by amauk on 2008-08-31
> **mjr2k said:**
> DVD ripping using DVD Decrypter
Use the MS office suite for school work (which won't matter in 6 months)
Photoshop for Image Manipulation
Nero and/or Roxio for CD/DVD burning
Windows Media for playing music in playlists
Tivo Desktop to transfer movies back and forth and some editing here and there.
Console Emulation that only uses .exe's

- For DVD ripping - I personally use Handbrake ([http://handbrake.fr](http://handbrake.fr))
- OpenOffice, but if you really want to you can use MS Office under Wine
- Gimp, but if you really want to you can use Photoshop under Wine
- CD / DVD burning is included by default in Ubuntu
- Many options for music playback, give them a try
RhythmBox (default), Amarok, Exaile, Banshee, the list goes on

Last 2 I don't know anything about
never owned a TiVo, and I'm not sure what you mean by console emulation (Wine has a command prompt if that's what you mean?)

---

### Post by host07 on 2008-08-31
I found K9copy and Braesro works well for dvds

---

### Post by hessiess on 2008-08-31
> Console Emulation that only uses .exe's

find a differnt emulater.

if you have a 64 bit prosessor, you may as well use a 64 bit OS.

---

### Post by Fr@nKy on 2008-08-31
Well no one answered to my doubts and thoughts on this post: [http://ubuntuforums.org/showpost.php?p=5697285&postcount=12](http://ubuntuforums.org/showpost.php?p=5697285&postcount=12) :(

But in the sequence of that post I ask:

For the following system:

Processor
    Intel Core 2 Duo T7500 
Motherboard
    Intel PM965 (TOSHIBA SATELLITE A200-1QK)
Memmory
    2x1GB DDR2-667MHz 
Graphics Card
    AMD/ATI Mobility Radeon HD2600 256MB DDR2 + 768MB HyperMemory
Hard Drive
    Hitachi 250GB 4200RPM SATA
Sound Card
    Realtek HD (Onboard)


What version of Ubuntu would you recommend? 32-bit or 64-bit?

---

### Post by Bucky Ball on 2008-08-31
[QUOTE=Carl H]I've got so used to the Linux way that Windows seems unnecessarily complicated now.[/QUOTE]

lol. Here, here Carl H. Know the feeling but luckily my wife is now a Ubuntu convert to!

---

### Post by Canis familiaris on 2008-08-31
Well 64bit is very nice. 
I have used Ubuntu 64bit and a bit of Vista 64bit, both of them work pretty well.
I would vote that you to use 64bit.

---

### Post by Liviu-Theodor on 2008-09-02
You should use the 64 bit version, because you want more than 3 GB of memory, and because you want to use video editing (at least ripping), which is much faster than with 32 bit. And if you have done it already, please do not forget to mark the thread as [Solved].

---

### Post by Liviu-Theodor on 2008-09-02
> **Fr@nKy said:**
> Today I was about to set up a Dual Boot System on my laptop, between Windows Vista Home Premium Service Pack 1 32-bit and Ubuntu 8.04.1 Hardy Heron, and I realized that once again I had to choose between 32-bit and 64-bit... Knowing that probably there should be no problema in choosing 64-bit I decided to look around Google about some information. Something I had already heard, but never I've never seen with my own eyes, was that 64-bit software tends to use more memory (even though I never believed in the twice more memory theory) so I decided to search for such comparison and I found this: [http://gquigs.blogspot.com/2008/07/blog-post.html](http://gquigs.blogspot.com/2008/07/blog-post.html)

After that I decided to run the tests myself using my ShipIt CDs containing 8.04 (not 8.04.1) and I got basically the same kind of numbers. So I conclude that 64-bit version of Ubuntu uses about 40 to 50 percent more memory... A few questions an thoughts arouse:

1 - Now I wonder in a 2GB system like my own what should I do? 

2 - Is this higher amount of used memory some kind of more advanced prefetch (a bit like Windows Vista's Superfetch) or is it really using much more memory? 

3 - A 10 to 20 percent increase would be acceptable but such a big difference? 

4 - Also this makes me think that following a 50% increase scenario someone with 2GB of RAM on a 64-bit system will "virtually" have 1.33(3) GB of RAM if compared to a 32-bit system.


Posing all this things... What version should I choose? (Well If I get 4GB in a near future I'll sure just skip 32-bit and go 64-bit but until then I just want what's best for my current system).

EDIT:

I'd also like to add:

5 - Is the 64-bit version already a "threat" to the 32-bit version? I mean is it getting a huge userbase boost that will eclipse the 32-bit version anytime soon?


I'd appreciate a an answer as soon as possible so I can decide what to do... HELP! Please!

1. If you ever plan to add memory to your system, you should use the 64 bit variant. If you use video editing programs (even DVD ripping), you should use the 64 bit variant. If you want to run Windows programs trough WINE, I reccommend the 32 bit variant. If you want to use VMWARE, it is better with the 64 bit variant, because you can run both 32 and 64 bit OS on the virtual machine, and it is slightly faster.
2. I think is more with the fact the 64 bit pointers use more memory than the 32 bit pointers.
3. I think the more memory you have, the less percentage will be added by the 'default', so you will no be using 40%-50% more memory, but much less. This is why nobody reccomend using 64 bit OS on machines with less than 1 GB of memory, and why you should use 64 bit OS on more than 3 GB.
4. This increase will be only on 1 GB of RAM, less on 2 GB, so don't think like this. It will add only some amount of used memory, not a percentage (if it is 512 MB more, it will be 50% from 1 GB, but only 25% from 2 GB).
5. As (almost) nobody still produces 32 bit processors, we are in a process of transition from 32 bit to 64 bit OS-s and programs. As with the previous transitions (from 8 bit to 16 bit and from 16 bit to 32 bit), it will take some years. But there are still in use many computers with 32 bit processors, on which can not be run 64 bit programs. Today, there is virtually no one using 16 bit processors or OS-s (older than 386, I mean - we are using 32 bit processors from that antique times :), even 32 bit OS-s are much newer). In time, there will be less and less users of 32 bit processors and programs, but by then, I suspect, there will be on the market 128 bit processors. And someone will ask: "Is the 128-bit version already a 'threat' to the 64-bit version?" =P~

---

### Post by Liviu-Theodor on 2008-09-02
> **Fr@nKy said:**
> Well no one answered to my doubts and thoughts on this post: [http://ubuntuforums.org/showpost.php?p=5697285&postcount=12](http://ubuntuforums.org/showpost.php?p=5697285&postcount=12) :(

But in the sequence of that post I ask:

For the following system:

Processor
    Intel Core 2 Duo T7500 
Motherboard
    Intel PM965 (TOSHIBA SATELLITE A200-1QK)
Memmory
    2x1GB DDR2-667MHz 
Graphics Card
    AMD/ATI Mobility Radeon HD2600 256MB DDR2 + 768MB HyperMemory
Hard Drive
    Hitachi 250GB 4200RPM SATA
Sound Card
    Realtek HD (Onboard)


What version of Ubuntu would you recommend? 32-bit or 64-bit?

That depends on what you want to do. I think you will find your answer on my previous post, concerning your doubts and thoughts. But I will say the 32 bit variant, because of the video card :(. I heard only bad things about HyperMemory. It seems it uses the main RAM for this, so it acts exactly like an onboard video card (never seen one myself, though).

---

