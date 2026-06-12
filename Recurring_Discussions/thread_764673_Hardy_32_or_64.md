---
title: "Hardy: 32 or 64?"
date: 2008-04-24
forum: Recurring Discussions
---

### Post by judolars on 2008-04-24
Is there still any reason not to use the 64-bits version of Ubuntu? I went back to 32 bits for a number of reasons:
[LIST]
[*]The Flash and Java browser plugins didn't work well (or at all),
[*]some multimedia codecs weren't included
[*]and, if I remember correctly, not all packages in the 32-bits repository were available in the 64-bits repository.
[/LIST]
Have these issues been mended now, and are there any other issues one should be aware of before choosing Hardy 64?

---

### Post by lizzard on 2008-04-24
I use 64bit and I can assure you neither flash nor multimedia codecs should be a problem. And most packages are available for 64bit too.

---

### Post by Canis familiaris on 2008-04-24
Is there any problem with WINE in Ubuntu for AMD64?

---

### Post by lizzard on 2008-04-24
> **Anurag_panda said:**
> Is there any problem with WINE in Ubuntu for AMD64?

Never had any issues with WINE. So I'd say: no problems.

---

### Post by Canis familiaris on 2008-04-24
What would be the advantages of 64bit Ubuntu over the 32bit version?

---

### Post by judolars on 2008-04-24
> **Anurag_panda said:**
> What would be the advantages of 64bit Ubuntu over the 32bit version?

If I understand correctly, not much. :) Apparently, it is possible to optimize programs to make better use of x86-64 processors, but usually the 64-bit programs are just recompiled versions of the 32-bit ones. (Correct me if I'm wrong.)

For me, it just *feels* a lot better to use the 64-bit version. And maybe, just maybe, I get some small performance boost somewhere.

---

### Post by NightwishFan on 2008-04-24
Much faster, no problems. If you have a 64bit processor, you should be using 64bit Hardy. :KS

---

### Post by Archmage on 2008-04-24
> **Anurag_panda said:**
> What would be the advantages of 64bit Ubuntu over the 32bit version?

First of all you can use more than 4 GB, secondly if the code is optimize for 64-bit, it can run slightly faster. My server runs 64 bit and I never notice any problem.

---

### Post by jespdj on 2008-04-24
> **Anurag_panda said:**
> What would be the advantages of 64bit Ubuntu over the 32bit version?
You should turn this question around: If you have a 64-bit capable processor, then why would you run the 32-bit version? What would be the advantages of running the 32-bit version on a 64-bit processor?

---

### Post by judolars on 2008-04-24
Another good reason (which I just thought of) for using 64-bits Ubuntu is this: The more people using 64-bits operating systems, the more programs will be optimised and compiled for 64-bits processors. And 64 bits are the future, I think we can agree on that.

For instance, Macromedia have yet to release a native 64 bits Flash plugin, despite that the longest bug report page I've ever seen is the one where people are requesting just that.

Apparently, I'm not a man of principle, seeing as I went back to 32 bits... Time to redeem myself, I think. Hardy 64 it is!

---

### Post by hermes0710 on 2008-04-24
I had some problems with 64bit packages in the past(w32codecs,libdvdcss???).
I will install hardy on hp dv9770ev and i can't decide if 62 or 32 should be my choice... Any suggestions?

---

### Post by Philip Farrugia on 2008-04-24
I've been using Gutsy 64bit without much trouble but I'm downloading Hardy 32bit first and will then try the 64bit maybe.  When switching to 64bit everything seemed super-fast but now I've installed lots of stuff it doesn't seem so fast.

Some applications were harder to install and some refused under 64bit. best thing is to try both and then decide for yourself!

---

### Post by jespdj on 2008-04-24
> **hermes0710 said:**
> I had some problems with 64bit packages in the past(w32codecs,libdvdcss???).
Were you trying to install 32-bit packages on 64-bit Ubuntu? Why? [Medibuntu](http://www.medibuntu.org/) has w64codecs and a 64-bit libdvdcss2 available. You don't need to use those 32-bit packages on 64-bit Ubuntu.

---

### Post by hermes0710 on 2008-04-24
Thanx philip.

The time i installed 64b there were no 64b versions of w64codecs and libdvdcss.

Anyway, i'll stick to 32b...

But anyway, i think that 64b should be more promoted... Its the future, am i wrong???

---

### Post by sweeneytodd on 2008-04-24
i reckon its safer and smarter to be a bit behind the 8 ball and stay with 32bit until you can be assured everything will run without to many issues

---

### Post by Robstarusa on 2008-04-24
I run 64-bit myself on pretty much everything, however I believe 32-bit can recognize/use up to 64G ram, however no single process can use more than 4G (less I think with OS overhead).

---

### Post by ratanx on 2008-04-24
I'll go ahead and ask... Is there a list of 64 bit programs? I'm most interested in Firefox, Thunderbird, XChat, VLC and Pan Newsreader, since these are my most used programs.

---

### Post by ire on 2008-04-24
No issues here with Hardy 64bit - running on a Lenovo Thinkpad T61.

Installed and working:

- Flash
- Java
- Skype
- Wireshark
- VMWare Workstation (64bit)
- Nessus
- GoogleEarth
- Kvpnc (replacement for Cisco VPN client which doesn't work for me yet

I can't say if it's faster or not, this is my first install of Ubuntu on my laptop, but I like it so far!


ETA:

ratanx - Thunderbird works, as does FF (but it's 3.x beta, which has been flawless so far), Xchat - don't use that, but just installed it to check it out, looks fine, and listening to online radio station right now with VLC.

---

### Post by ratanx on 2008-04-24
> **ire said:**
> 


ETA:

ratanx - Thunderbird works, as does FF (but it's 3.x beta, which has been flawless so far), Xchat - don't use that, but just installed it to check it out, looks fine, and listening to online radio station right now with VLC.

Thanks for the reply. So I assume then these programs are either 64-bit native, or will work anyway? I was under the impression if the program in question was not 64-bit native, there would be a degradation in performance.

---

### Post by John.Michael.Kane on 2008-04-24
I have tested Hardy 64bit - running on an Intel Dual core, and have not experienced issues with.

Testing:

- Flash
- Skype
- Acid-rip
- Blender
- Movie playback
- Thunderbird
- Xchat

---

### Post by reimerjc on 2008-04-24
> **Robstarusa said:**
> I run 64-bit myself on pretty much everything, however I believe 32-bit can recognize/use up to 64G ram, however no single process can use more than 4G (less I think with OS overhead).

No, 32-bit processors can only address 4GBs (2^32) unless you use paging.

---

### Post by Bastaard on 2008-04-24
I got a 64-bit AMD but I've always been using the 32-bit Ubuntu line, because there's no 64-bit driver for my wifi card to use with ndiswrapper. I've read some articles about it though and I believe the 64-bit version hardly gets you any speed increase apart from specialist software (video encoding mainly).

---

### Post by ire on 2008-04-24
> **ratanx said:**
> Thanks for the reply. So I assume then these programs are either 64-bit native, or will work anyway? I was under the impression if the program in question was not 64-bit native, there would be a degradation in performance.

I couldn't speak to that - this is my first dip into Ubuntu on the desktop/laptop, but I don't see any sort of performance hit.

---

### Post by frogotronic on 2008-04-24
> **Anurag_panda said:**
> Is there any problem with WINE in Ubuntu for AMD64?


Here's my two cents:

I had nothing BUT issues with AMD64.  Very poor integration with multimedia, hard lock-ups; major issues with WINE.  Firefox 3b5 is a terrible choice for Hardy at the moment.

Probably a lot to do with just Hardy and being shiny and new - maybe after a month of wide-release these issues will be solved.  I'll try again in a few months.

One overall disturbing problem = x64 kernel ran 5oC hotter on my laptop than x32.

- CH

---

### Post by hermes0710 on 2008-04-24
Thanx cement, the heat factor was enough... 32 it is...

---

### Post by John.Michael.Kane on 2008-04-24
> **hermes0710 said:**
> Thanx cement, the heat factor was enough... 32 it is...

The heat factor raised by cement_head was based on his hardware. The outcome of a 64bit install on your hardware hermes0710 may have a completely different outcome.

You should not base installing 64bit completely on other users experience unless you have the exact same hardware configuration, and even then you may not have issues.

I would suggest those interested in 64bit run it alongside your pre-existing 32bit installs, and test it the same way you tested 32bit.

For guide to setting up 64bit look here [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by frogotronic on 2008-04-24
> **John.Michael.Kane said:**
> The heat factor raised by cement_head was based on his hardware. The outcome of a 64bit install on your hardware hermes0710 may have a completely different outcome.

You should not base installing 64bit completely on other users experience unless you have the exact same hardware configuration, and even then you may not have issues.

I would suggest those interested in 64bit run it alongside your pre-existing 32bit installs, and test it the same way you tested 32bit.

For guide to setting up 64bit look here [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

I agree with JMK, its more than likely the HP 6910p laptop, which seems t really like Gutsy.  I'm very attracted to x64 for a number of high intensity calculation based apps.  I think that the kernel issues will probably be dealt with in the next few months.  I'll probably try Hardy x64 when F3 gets out of beta.

---

### Post by modestmelody on 2008-04-24
I've gone back and forth several times using 64bit versus the 32bit version of Ubuntu.  After Gutsy, I'll never use 32bit again.  I've run into exactly 0 problems running 64bit Gutsy.  As with any upgrade, like the recent one to Hardy, I'm going to wait 2-4 weeks for some of the very basic bugs on either side (32 or 64) to get cleaned up and then jump in.

Btw, I used to do fresh install of Ubuntu each time I upgraded-- no longer.  Again, since upgrading Gutsy, I have no problems simply upgrading.

---

### Post by hermes0710 on 2008-04-24
> **modestmelody said:**
> I've gone back and forth several times using 64bit versus the 32bit version of Ubuntu.  After Gutsy, I'll never use 32bit again.  I've run into exactly 0 problems running 64bit Gutsy.  As with any upgrade, like the recent one to Hardy, I'm going to wait 2-4 weeks for some of the very basic bugs on either side (32 or 64) to get cleaned up and then jump in.

Btw, I used to do fresh install of Ubuntu each time I upgraded-- no longer.  Again, since upgrading Gutsy, I have no problems simply upgrading.


I suppose there is no way of changing mode from 32 to 64 bit without clean installing or am i wrong?

---

### Post by SnakeHips on 2008-04-24
> **judolars said:**
> Another good reason (which I just thought of) for using 64-bits Ubuntu is this: The more people using 64-bits operating systems, the more programs will be optimised and compiled for 64-bits processors. And 64 bits are the future, I think we can agree on that.


+1

---

### Post by lazyart on 2008-04-24
> **modestmelody said:**
> I've gone back and forth several times using 64bit versus the 32bit version of Ubuntu.  After Gutsy, I'll never use 32bit again.  I've run into exactly 0 problems running 64bit Gutsy.  As with any upgrade, like the recent one to Hardy, I'm going to wait 2-4 weeks for some of the very basic bugs on either side (32 or 64) to get cleaned up and then jump in.

Ditto.  I just went to Gutsy 3 weeks ago, simply because I had forgotten to upgrade.  So I waited for a Friday night and pulled it down so if I did have any issues I could get them fixed up over the weekend (I work from home on my Ubuntu box).

Happy to say I had a free weekend.  Everything Just Worked.  I'll give this a couple weeks as well (not 5 months this time) and then I'm on to Hardy, staying 64 bits all the way.

---

### Post by Nico0020 on 2008-04-24
I really would like to switch to 64 hardy.  I haven't yet installed the new version yet as I need to start the torrent.  

Anyways, I have a dual core 1.6ghz on my lappy with only 1gig of ram, and a decent video card.  I think i remember reading that processes use up more ram under 64bit, so to do the same things I do in 32 bit, I would need more ram/it get used up more quickly, is that true?  As of now, im going to download both.

---

### Post by John.Michael.Kane on 2008-04-24
> **Nico0020 said:**
> I really would like to switch to 64 hardy.  I haven't yet installed the new version yet as I need to start the torrent.  

Anyways, I have a dual core 1.6ghz on my lappy with only 1gig of ram, and a decent video card.  I think i remember reading that processes use up more ram under 64bit, so to do the same things I do in 32 bit, I would need more ram/it get used up more quickly, is that true?  As of now, im going to download both.

While more ram is better. You can run 64bit on the machine in question, however. Are you sure you have one GB or ram, as some laptop video cards use system memory thus instead of having a full gig you might have only like 936 MB.

---

### Post by Arceliar on 2008-04-24
I've got a single core, 1 gig of ram (shared with video card) laptop and 64 runs better than 32 did on my machine. Actually, I had nothing but problems with the 32 bit install of hardy, but that was about a month ago when it went beta so they could have fixed whatever was causing lockups on my machine. If they did, I'll still stick with 64, as it runs better than 32 did (even when 32 wasn't freezing X up on me).

It's all a matter of your own machine. If you have a 64 bit processor then you might as well try both if you can. If there's no significant difference then I for one would err on the side of a 64-bit install for..well, any of the reasons that people have already mentioned.

I mean...why have a 64 bit processor if you're not going to use it?

---

### Post by lancest on 2008-04-24
Runnung Hardy on 3 GB - AMD 64 desktop, Nvidia 7300. Bulletproof. Compiz rocks. I see no reason to use 32 bit. Upgraded from RC. Google Earth, Skype run perfectly.

---

### Post by Nico0020 on 2008-04-24
yea, I have a Nvidia GEforce GO series card, so it has its own ram and doesnt need to use the onboard ram.  So do you think my system would run worse or more of the same with just 1GB of RAM?

---

### Post by John.Michael.Kane on 2008-04-24
> **Nico0020 said:**
> yea, I have a Nvidia GEforce GO series card, so it has its own ram and doesnt need to use the onboard ram.  So do you think my system would run worse or more of the same with just 1GB of RAM?

Of course more ram is better in certain use cases, however. In your case the system will should perform fine with one GB. 

IMHO the only way to find out is to do an install on the system in question.

---

### Post by NightwishFan on 2008-04-24
I use 64-bit on 895mb of ram, I barely use half of it even under heavy use.

---

### Post by movieman on 2008-04-24
> **Nico0020 said:**
> I think i remember reading that processes use up more ram under 64bit, so to do the same things I do in 32 bit, I would need more ram/it get used up more quickly, is that true?

Depends on what you're doing; I compiled a simple C program in 32-bit and 64-bit, and the 64-bit program was smaller. Similarly, if you're working with bitmaps, a 1000x1000 bitmap at 32 bits per pixel is exactly the same size in 32-bit and 64-bit operating systems.

My 64-bit system at home has 4GB, but when using it for web browsing and the like I rarely see it even get up to 1GB used, including the disk cache.

---

### Post by old_geekster on 2008-04-24
Truthfully, I can't say that I have found 64-bit to be much faster than 32-bit.  I used 32-bit Ubuntu from Edgy to Gutsy.  Then, I decided to upgraded to 64-bit Gutsy.  Since I had both versions of the same distro on the same computer back to back, I had a good chance to compare.  I use 64-bit because I have a 64-bit processor.

---

### Post by arang on 2008-04-25
hi guys i feel in the same way as the OP, i have a PC with 4Gb of RAM and a NVIDIA 8800GT video card, and i've been using gutsy in 32 bits with the server kernel and with envy to install the latests drivers of nvidia, so anyone knows if the new 32 bit kernel uses the 4Gb by default or its still 3gb and change, and also i kind of need the latests nvidia driver cos my graphic card and cos most drivers available thru repos contain bugs in compiz and the like so anyone could confirm me this?

---

### Post by mivo on 2008-04-25
> **ratanx said:**
> Thanks for the reply. So I assume then these programs are either 64-bit native, or will work anyway? I was under the impression if the program in question was not 64-bit native, there would be a degradation in performance.

Quite the contrary. 32-bit programs run on a 64-bit system tend to be a little faster, too. Take a look at [this article]("http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1"), it answers many of your questions. :) (It talks about Windows in some places, but the same principles apply to Linux.)

---

### Post by nowhere@cox.net on 2008-05-01
I could have sworn 32bit limit is <4GB (like 3-3.5) in practicality. I know my 32 Vista only sees 3GB. This is why I went 64bit Gutsy and I HAVE had problems with flash and java plug-in and my system is currently a mess right now because of the hatchet job I did installing the 32bit libraries.

You need to be careful when considering the opinions of others (including me) when deciding tho. Hardware and what software you will use will be the deciding factors. I see a lot of posts saying 64bit rocks but no list of the known problematic software packages...

---

### Post by NightwishFan on 2008-05-01
I believe it is windows can only see like 3gb of ram but the total number you can see is much higher but less efficient after so much, something like that.

---

### Post by old_geekster on 2008-05-01
> **old_geekster said:**
> Truthfully, I can't say that I have found 64-bit to be much faster than 32-bit.  I used 32-bit Ubuntu from Edgy to Gutsy.  Then, I decided to upgraded to 64-bit Gutsy.  Since I had both versions of the same distro on the same computer back to back, I had a good chance to compare.  I use 64-bit because I have a 64-bit processor.

I had to do a follow-up on my statements.  Last night I did a clean install of HH 32-bit.  It had been two distros since I had used it (32-bit).  I found it to be extremely slow.  At first, I thought that it was a bad instll.  So, I reinstalled it.  There was no change.  After using it for a day, I decided to do a clean install of HH 64-bit.  The difference is estounding.  I am now a true 64-bit fan.:guitar:  Even downloads are much faster.  In my opinion, if you have the equipment to run it, HH 64-bit is the way to go!!

---

### Post by p_quarles on 2008-05-01
Moved to Recurring Discussions.

---

### Post by mivo on 2008-05-02
> **old_geekster said:**
> It had been two distros since I had used it (32-bit).  I found it to be extremely slow.  At first, I thought that it was a bad instll.  So, I reinstalled it.  There was no change.  After using it for a day, I decided to do a clean install of HH 64-bit.  The difference is estounding.

It's interesting how experiences can differ. I had used 64-bit Feisty, Gutsy and Hardy (the latter for a couple days), then dropped back to 32-bit Hardy because the old workarounds for 32-bit Javaws/browser plugin in a 64-bit system no longer worked for me (others are luckier). I expected 32-bit to be slower, however, even a few days later I still notice no difference on my system. It's as fast as 64-bit Hardy was (and it's faster than Feisty and Gutsy) and uses 10-15% less memory (though that's somewhat irrelevant since I never seem to use more than one out of the three GB my box has, except for disk caching).

So right now, and for me, running 32-bit is far more convenient since I'm a heavy user of JavaWS and the browser plugin (the free alternatives don't work with the applets I need to use). My downloads are also as fast as before, but I don't see how the choice of 32- or 64-bit should affect that aspect.

I feel that the choice for 64-bit should depend on one's individual software needs. I don't seem to be using any software that benefits in any noticeable way from 64-bit.  Once Sun releases 64-bit versions of Java Web Start and the browser plugin, I'll switch back to the 64-bit Ubuntu, but only out of principle -- I don't see any advantages on my current computer and my current software usage/needs over the 32-bit Ubuntu.

---

### Post by Saint Angeles on 2008-05-02
i have a pentium 4 with "hyperthreading" technology. I can install 64 bit or 32 bit but I chose 32 bits because it seems faster. when running 32 bit, my processor "tricks" the OS into thinking I have 2 32-bit processors.

also, theres a couple things that 64 bit hasnt quite got yet (flash player comes to mind)... i'm not saying that 32-bit is better, just that its better for my processor.

---

