---
title: "what is the difference between 32bit and 64bit"
date: 2010-01-26
forum: Recurring Discussions
---

### Post by Extract_Here on 2010-01-26
Just what is the difference?

---

### Post by nhasian on 2010-01-26
if your CPU supports it, it is recommended to use 64bit OS.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by Extract_Here on 2010-01-26
so i have a athlon x2 dual core should i get the 64 bit or 32 bit of karmic

---

### Post by Atzu on 2010-01-26
I believe 64bits uses better dual-core and its used for 4gb+ ram 

You may want to read this post on omgubuntu! (amazing ubuntu blog :p) : [http://www.omgubuntu.co.uk/2009/12/ubuntu-64bit-really-is-faster-than.html](http://www.omgubuntu.co.uk/2009/12/ubuntu-64bit-really-is-faster-than.html)

---

### Post by philinux on 2010-01-26
> **Extract_Here said:**
> Just what is the difference?

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by nhasian on 2010-01-26
> **Extract_Here said:**
> so i have a athlon x2 dual core should i get the 64 bit or 32 bit of karmic

you can google it to see if your cpu supports 64bit.  you will need to know the model number.  you can get more info on your cpu with this terminal command:

```
lshw -C cpu
```

---

### Post by Extract_Here on 2010-01-26
i have 4gb ram and x2 dual core on a asus motherboard and i currently have 32bit of ubuntu running should i get the 64 bit if i want it to run better?

---

### Post by philinux on 2010-01-26
> **Extract_Here said:**
> i have 4gb ram and x2 dual core on a asus motherboard and i currently have 32bit of ubuntu running should i get the 64 bit if i want it to run better?

See the benchmarks above.

However, if your system is running fine I would leave it until you next reinstall. I have home on it's own partition and I do a clean install every new release. All my settings remain in tact from programmes to desktop customisation.
Ive been running 64 bit since I bought the machine 2 years ago.

---

### Post by nhasian on 2010-01-26
agreed.  since there is no upgrade path you would have to do a fresh install.  might as well wait for Lucid Lynx 10.04 :)
Or at least 10.04 Alpha 3 on Feb 25th if your impatient like me.

> **philinux said:**
> if your system is running fine I would leave it until you next reinstall.

---

### Post by Marc St Louis on 2010-01-26
I don't know that much about computers but I believe it refers to the number of bits of information that can be processed at one time

---

### Post by Extract_Here on 2010-01-26
how can i check if my cpu can use 64 bit without checking on the web. because frankly there are alot of athlon x2 cpus that have diff specs.

---

### Post by ibuclaw on 2010-01-26
64bit technically uses more memory... pointers, longs and other bits of memory addresses being bigger on 64bit architectures. ;)

Other than that, no difference - at least - it is stable enough to not have any sort of strange bug that doesn't exist in 32bit.

Regards
Iain

---

### Post by philinux on 2010-01-26
> **Extract_Here said:**
> how can i check if my cpu can use 64 bit without checking on the web. because frankly there are alot of athlon x2 cpus that have diff specs.

Open a terminal.

```
uname -m
```

If it returns x86_64 then you have a 64 bit capable machine.

---

### Post by bodhi.zazen on 2010-01-26
> **philinux said:**
> Open a terminal.

```
uname -m
```If it returns x86_64 then you have a 64 bit capable machine.

That is not true, uname -m only tells us about if the kernel was compiled for 32 or 64 bit.

To determine the capabilities of the processor, use

```
grep ' lm ' /proc/cpuinfo
```

If the above command returns anything, you have a 64 bit processor regardless of if you are running 32 or 64 bit Ubuntu.

---

### Post by philinux on 2010-01-26
Thanks for the catch bodhi, more coffee needed here.

Post the output of this.
```
grep 'model' /proc/cpuinfo
```

---

### Post by theozzlives on 2010-01-26
If I understand right, 64 bit refers to how wide the data bus is. If you have 4 GB of RAM, I suggest you get 64 bit Ubuntu.

---

### Post by bodhi.zazen on 2010-01-26
> **philinux said:**
> Thanks for the catch bodhi, more coffee needed here.

No problem, it is a very common misunderstanding, one I have made in the past.

---

### Post by PCA on 2010-01-27
It has to do with how many data bits could be processed at a given time. The 64bit CPU would have a 64bit wide data bus and registers. So, technically it would be faster in crunching big numbers. Also the program should be written specifically to exploit the larger datawidths. 

I'm not too good with software, but this should be beneficial for programs like Photoshop(I apologize for referring to a windows app, I'm somewhat new to Ubuntu). However reports from benchmarking programs show that the improvements are only marginal, I don't know why.

Due to the large no. of software available for 32-bit OS, below 4GB main memory and also because of stability problems I use a 32bit version even though I have a 64bit processor.

---

### Post by nhasian on 2010-01-27
i found this as well:

[http://www.amd64.org/fileadmin/user_upload/pub/64bit_Linux-Myths_and_Facts.pdf](http://www.amd64.org/fileadmin/user_upload/pub/64bit_Linux-Myths_and_Facts.pdf)

> **PCA said:**
> Due to the large no. of software available for 32-bit OS, below 4GB main memory and also because of stability problems I use a 32bit version even though I have a 64bit processor.

---

### Post by Roger Allott on 2010-01-27
> **nhasian said:**
> you can google it to see if your cpu supports 64bit.  you will need to know the model number.  you can get more info on your cpu with this terminal command:

```
lshw -C cpu
```

I've just run that command and this was my output:
```
:~$ lshw -C cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.15.13
       serial: 0000-06FD-0000-0000-0000-0000
       size: 1GHz
       capacity: 1GHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
```

The line "width: 64 bits" would seem to indicate to someone like me (very stoopid re hardware) that I could install Ubuntu 64-bit, which comes as a bit of a nice surprise, particularly as my machine came pre-installed with only the 32-bit version of Windows Vista.

Could someone please confirm that I'm reading the output correctly?

Is there anything else I should check before trying to install a 64-bit O/S?

---

### Post by Paqman on 2010-01-27
> **Roger Allott said:**
> 
Could someone please confirm that I'm reading the output correctly?


Indeed you are. All of the Core 2 Duos are 64-bit anyway.

---

### Post by pirateghost on 2010-01-27
> **Roger Allott said:**
> I've just run that command and this was my output:
```
:~$ lshw -C cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.15.13
       serial: 0000-06FD-0000-0000-0000-0000
       size: 1GHz
       capacity: 1GHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
```The line "width: 64 bits" would seem to indicate to someone like me (very stoopid re hardware) that I could install Ubuntu 64-bit, which comes as a bit of a nice surprise, particularly as my machine came pre-installed with only the 32-bit version of Windows Vista.

Could someone please confirm that I'm reading the output correctly?

Is there anything else I should check before trying to install a 64-bit O/S?

my guess is that your computer probably came with 3gb of ram or less too?
i have noticed for the last couple of years that manufacturers are selling computers that have 3gb of ram or less with 32bit OS preinstalled, probably to keep the number of phone calls down to a minimum:
"i bought my computer with 4gb of ram and its telling me that it only has 3gb when i turn it on!  i want my money back!"
reason for a lack of 64bit installs?
they want more compatibility across the board and people are likely to have trouble understanding 64bit vs 32bit when they need to install drivers/software/etc and will be more inclined to call support.

---

### Post by Roger Allott on 2010-01-27
> **pirateghost said:**
> my guess is that your computer probably came with 3gb of ram or less too?
i have noticed for the last couple of years that manufacturers are selling computers that have 3gb of ram or less with 32bit OS preinstalled, probably to keep the number of phone calls down to a minimum:
"i bought my computer with 4gb of ram and its telling me that it only has 3gb when i turn it on!  i want my money back!"
reason for a lack of 64bit installs?
they want more compatibility across the board and people are likely to have trouble understanding 64bit vs 32bit when they need to install drivers/software/etc and will be more inclined to call support.

My machine has only 2Gb of memory. Does that mean that I shouldn't bother to install Ubuntu 64-bit?

---

### Post by wmcbrine on 2010-01-27
The difference is 32.

But seriously... in this context, we're talking about an extension to Intel's x86 processor architecture, designed by AMD a decade ago. If you're an old-timer like me, you may remember the transition from "16-bit" to "32-bit" (or even 8-bit to 16-bit). It's like that... except that some of the biggest differences between x86 and x86-64 -- the differences that give most of the performance boost -- actually have nothing to do with 64-bitness per se. (I'm thinking mainly of the increased register count.)

The meaning of the numbers becomes clearer if you're a programmer working in a low-level language -- preferably assembly, but C is enough to give some insight. To really explain it, I'd have to explain the concepts of registers and memory addressing. Probably you don't want me to. :)

Theoretically, there are trade-offs to using 64-bit vs. 32-bit code. In practice, due to those extra registers, x86-64 code is almost always faster, often *much* faster, than equivalent x86 code.

And yes, 64-bit mode lets you address more memory, but for most people, this isn't the issue it seems. Even 32-bit operating systems can* handle more than 4 GB of total RAM in the system; it's the per-process limit that's raised. The better reason to use 64-bit** is because it's faster.

* Well, Linux can. Windows *could*, but apparently it doesn't. (?)

** In the sense of x86-64 vs. x86, only... this doesn't necessarily apply to 64-bit architectures in general. That is to say, 64-bit PowerPC (for example) may not be faster than 32-bit PowerPC, because it doesn't incorporate the *other* kinds of changes that x86-64 does vs. x86.

---

### Post by mvalviar on 2010-01-27
I just found out that I have a dual core 64bit cpu. Should I get a 64 bit lynx? I only have 1gig of ram though. :p

---

### Post by texaswriter on 2010-01-27
Well, I have a Pentium D and a Core 2 Duo, and I don't think 64-bit would help me much. I'm not installing it as both computers have <4GB... The next desktop I build will be a 4+ core AMD or Intel and will definitely be a 64-bit build... If anybody has any recommendations for great 4 core or plus AMD processors, and good mobo's that go with it, I'd appreciate it. [can message me if you don't want to screw up continuity of thread]... 

But otherwise, I'd recommend this to people: if your system has less than 4GB and things work, why change now. Next reinstall or next computer, excellent time to get in step with the world then. 

I don't mind tempting fate, I just like to minimize such occurrences if possible. :D

---

### Post by wmcbrine on 2010-01-27
It doesn't matter how much RAM you have. A 64-bit distro makes the best use of your 64-bit processor.

P.S. 64-bit Ubuntu is perfectly stable. I've been using it for over five years.

---

### Post by audiomick on 2010-01-27
I tend to agree with Texaswriter. If the machine is up and running, and you wouldn't have thought about it if you hadn't read this thread (sort of thing...), leave the change to the next update. Changing means a re-install, so you may as well wait until you can combine that with an upgrade.

---

### Post by Roger Allott on 2010-01-27
> **wmcbrine said:**
> It doesn't matter how much RAM you have. A 64-bit distro makes the best use of your 64-bit processor.

P.S. 64-bit Ubuntu is perfectly stable. I've been using it for over five years.

I'll take that as being authorative for the time being, so I'll be installing the 64-bit version of Lucid when it comes out in April.

Is there a good selection of apps written for 64-bit OSs? For example, OpenOffice, Firefox, Chrome (or Chromium), Google Earth, etc. etc.

If 64-bit versions of apps are not available, do 32-bit versions run without problems?

Can I filter Synaptic to only show me 64-bit apps?

---

### Post by pirateghost on 2010-01-27
> **texaswriter said:**
> Well, I have a Pentium D and a Core 2 Duo, and I don't think 64-bit would help me much. I'm not installing it as both computers have <4GB... The next desktop I build will be a 4+ core AMD or Intel and will definitely be a 64-bit build... If anybody has any recommendations for great 4 core or plus AMD processors, and good mobo's that go with it, I'd appreciate it. [can message me if you don't want to screw up continuity of thread]... 

[B]But otherwise, I'd recommend this to people: if your system has less than 4GB and things work, why change now. Next reinstall or next computer, excellent time to get in step with the world then. 

I don't mind tempting fate, I just like to minimize such occurrences if possible.[/B]  :D
this is some of the best advice i have seen so far.  there is no reason to switch if everything is currently set up the way you want.  next build, hop on the 64bit bandwagon.

feel free to message me with your requirements for hardware, my job requires me to stay on top of current and upcoming hardware, so i like to help out where i can and assist people in making these kinds of decisions

> **wmcbrine said:**
> It doesn't matter how much RAM you have. A 64-bit distro makes the best use of your 64-bit processor.

P.S. 64-bit Ubuntu is perfectly stable. I've been using it for over five years.

this too.  lets get this image out of the minds of the unknowing that somehow 64bit is this mysterious creature that if manhandled too much will bite and maim anyone in its path.

---

### Post by mvalviar on 2010-01-27
On lynx I'll be getting the 64bit then. It worries me that I might encounter problems with some apps like wine.

---

### Post by pirateghost on 2010-01-27
> **mvalviar said:**
> On lynx I'll be getting the 64bit then. It worries me that I might encounter problems with some apps like wine.

if an app doesnt have native 64bit support, there is a 99.99% chance that it will work absolutely fine as 32bit running in 64bit environment.  the more that 64bit is utilized, the more developers will write code for it and further advance computing technology.

---

### Post by HappyFeet on 2010-01-27
> **wmcbrine said:**
> It doesn't matter how much RAM you have. A 64-bit distro makes the best use of your 64-bit processor.


Actually it does matter. Having 1gb or less of ram would hinder your computer, using a 64bit OS. (unless you never multi-task, and *just* surf the web) It is recommended to have at least 2gb ram.

I read an article somewhere where they said 64 is inherently more stable than 32. I can't prove it, or find that article anymore, but in my own experience, 64bit seems snappier and extremely stable. I personally will never go back to 32bit.

---

### Post by HappyFeet on 2010-01-27
> **mvalviar said:**
> On lynx I'll be getting the 64bit then. It worries me that I might encounter problems with some apps like wine.

Wine, and every other app I've used (which is a lot) works perfectly in 64. Windows is still trying to catch up in supporting 64bit, while linux is 99.999999999999999999% there already. In other words, don't worry about it.

---

### Post by wmcbrine on 2010-01-27
> **HappyFeet said:**
> Actually it does matter. Having 1gb or less of ram would hinder your computer, using a 64bit OS.Nonsense. That computer where I've been running 64-bit Ubuntu for five years? 1 GB RAM. And yeah, I ran 32-bit on it before that (although that was with Mandrake), and yeah, 64-bit was noticeably faster from day one.

The only time my RAM ever gets low is when I'm running VirtualBox (with some enormous chunk of RAM dedicated to it).

---

### Post by wmcbrine on 2010-01-27
> **Roger Allott said:**
> Is there a good selection of apps written for 64-bit OSs?The entire distro is 64-bit, with only a few tiny exceptions, like Adobe Flash. Only some closed-source stuff is 32-bit, and there's not much of that; you'd have to go out of your way to get it. It's a very different situation from Windows, where 64-bit still feels quasi-experimental.

---

### Post by vivjo on 2010-01-28
Hi All, 
Just to add up ,the basic difference between the 32-bit and 64-bit architecture by an example
lets say you have 10 packets and  can send 5 at at time , so if u use a 32 -bit system , u can send it in two rounds whereas in 64bit architecture you can send it in one go, 
so basically it measure up how much data u can send between various peripherals
so in short


[B]64-bit --->  Twice of 32-bit in every regard
[/B]
Thanks, 
Viv

---

### Post by texaswriter on 2010-01-28
Heh, just a reality check for *most 64-bit users*: Hey, I won't deny progress.. First off, the actuality of it is that manufacturers have **stopped** developing new technology for 32-bit, though they will still sell them obviously, so all new technology is moving towards improving 64-bit. In time they will start dropping support for 32-bit and working it into a smaller and smaller scheme of the processor... It will likely be supported though somewhat for at least a decade [even though 64-bit has ben easily out for 5 years]. 

Anyways, reality check is this: run any program that is not super intense [any game 5 years or older], web browsing, [insert most stuff people do on computers that is not task-oriented processor intensive], and 64 bit, 32 bit, 32bit w/pae,... not much difference... Maybe 20% here or there with 64 bit... but that doesn't translate much to actually getting stuff done faster. Most improvement/optimizations are going to occur user side, having an os and interface [in applications] that is conducive to shortcuts and other customizations that entail greater and greater proficiency with more use. 

Now, obviously if you need lots of processor power for constant calculations, then 64 bit is going to be a no brainer. 

But for most typical users [not sure how typical *most* linux users are lol], any dual core with 32 bit os is going to be fine... And a HUGE reason not to upgrade is flash... lol, I use flash how many times a day? oh yeah lots... 

Anyways, if you are that power user who is constantly running intense programs, 64 bit is great, otherwise, don't delude yourself into thinking you are gaining so much... I mean, look at Windows 7, it's not even mandatory that you get 32 bit... probalby be 5-10 years before next ms os comes out, eh, srry, lemme say that again, 5 years and then 2-3 years before the NEXT ms os that's worth anything comes out.. so you know, 8-10 years... 64 bit will be likely mandatory then... 

Personally, from a programming standpoint, most programs shouldn't be needing 64 bit variables... It's overkill when most variables defined could be char and int...  
 
As far as I'm concerned, it's just a way to double memory usage: increase hardware sales faster... more software sales... bleah!!!!

---

### Post by wmcbrine on 2010-01-28
> **texaswriter said:**
> And a HUGE reason not to upgrade is flashActually not. Back in the day, this was an issue, as was Java.* So we'd run 32-bit Firefox in our 64-bit distros, just to work with the plugins. (Even then, there was no reason the rest of the distro had to be 32-bit.) But nowadays, the default setup with 64-bit Ubuntu uses (IIRC) a shim to run the 32-bit Flash plugin in a separate process, so it can work within a 64-bit browser.** There's also, finally, a native 64-bit plugin available from Adobe -- for Linux only! -- though Ubuntu hasn't made it the default yet.

> *As far as I'm concerned, it's just a way to double memory usage*64-bit code is slightly larger than 32-bit, but not double. Only pointers and longs are doubled; as you note, most data is still chars and ints, and the instructions are no larger.

* Java is now native 64-bit, and open source. :D

** This idea of running plugins in their own processes is becoming a new standard, I think. Safari does it, Chrome does it, and it looks like Firefox is heading that way too.

---

### Post by oldos2er on 2010-01-28
> **wmcbrine said:**
> The entire distro is 64-bit, with only a few tiny exceptions, like Adobe Flash.

There is 64-bit flash, it's just not in the repositories yet. 
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

---

### Post by mvalviar on 2010-01-28
Wow. I should have known that I have 64bit cpu earlier. I do use computing intensive programs like blender. 

Will flash work OTB? I don't use it much but by wife do. Mostly youtube and facebook games.

I guess I'll just buy more RAM and I'm sure to get more out of my machine.

---

### Post by meindian523 on 2010-01-28
You don't NEED to buy more RAM to use 64 bit. And yes, Flash works OOTB, from personal experience here.

---

### Post by 3rdalbum on 2010-01-28
> **vivjo said:**
> Hi All, 
Just to add up ,the basic difference between the 32-bit and 64-bit architecture by an example
lets say you have 10 packets and  can send 5 at at time , so if u use a 32 -bit system , u can send it in two rounds whereas in 64bit architecture you can send it in one go, 
so basically it measure up how much data u can send between various peripherals
so in short


[B]64-bit --->  Twice of 32-bit in every regard
[/B]
Thanks, 
Viv

Sorry Viv... this is not true. 64-bit numbers can be calculated quicker on 64-bit. There is no additional bandwidth to peripherals, and no additional speed for non-64-bit number calculations. The only other source of extra speed on 64-bit is the greater RAM addressing capability - if you have 4 GiB or more of RAM, you can access it all for cache on 64-bit.

---

### Post by mvalviar on 2010-01-28
ok I'm convinced and I want to try it. Which iso is it? All I see is amd64. Where is the i86_64?

---

### Post by pirateghost on 2010-01-28
> **mvalviar said:**
> ok I'm convinced and I want to try it. Which iso is it? All I see is amd64. Where is the i86_64?
amd64 is the iso you need, regardless of whether your cpu is intel or amd.

---

### Post by Roger Allott on 2010-01-28
> **mvalviar said:**
> Wow. I should have known that I have 64bit cpu earlier.

Yes, I feel a bit of a drongo for not realising I had a 64-bit CPU ages ago!

What I would appreciate though is some clued up techie person explaining what's going on with my PC.

I've attached a screenshot of my System Monitor resources tab, where it shows that I have two CPUs functioning. As I've only got 32-bit Ubuntu running, does this suggest that my OS is trying to provide me with what, in effect, is 64-bit functionality?

And if it's doing that, what would be the advantage of moving to 64-bit Ubuntu?

---

### Post by pirateghost on 2010-01-28
> **Roger Allott said:**
> Yes, I feel a bit of a drongo for not realising I had a 64-bit CPU ages ago!

What I would appreciate though is some clued up techie person explaining what's going on with my PC.

I've attached a screenshot of my System Monitor resources tab, where it shows that I have two CPUs functioning. As I've only got 32-bit Ubuntu running, does this suggest that my OS is trying to provide me with what, in effect, is 64-bit functionality?

And if it's doing that, what would be the advantage of moving to 64-bit Ubuntu?
no, you have a dual core CPU which your system sees as 2 cpus, this is NOT the same as a 64bit system.  the first 64bit cpus were all single core and there are a few still around today (AMD mostly).  dual core does not = 64bit.

---

### Post by NoaHall on 2010-01-28
No, it's not 32 bit functionality. The cores, most of the time, perform different jobs - in a sense, they are completely different processors, squished onto one. Switching to 64 bit means that the processor can use 64 bits at a time. This means it's a lot quicker for some things, but on the whole, just a little faster. Oh, and you can access more than 3.4GB of RAM too.

---

### Post by hessiess on 2010-01-28
64 bit processors are able to work on 64 bits of data at a time, simple as that. This does not result in an speed improvement except for applications which are working with varry large numbers, i.e. crypto and to some extent graphics. The main performance enhancing feature of the AMD64 architecture is that it has a lot more registers, reducing memory reads/writes.

---

### Post by llawwehttam on 2010-01-28
I have been using 64 bit for a while now and there is definitely a performance difference. Have a look at the 64 bit link in my signature.

---

### Post by Roger Allott on 2010-01-28
> **NoaHall said:**
> No, it's not 32 bit functionality. The cores, most of the time, perform different jobs - in a sense, they are completely different processors, squished onto one. Switching to 64 bit means that the processor can use 64 bits at a time. This means it's a lot quicker for some things, but on the whole, just a little faster. **Oh, and you can access more than 3.4GB of RAM too.**

Uh??? Could you please explain how I can access "more than 3.4GB of RAM" when I've only got 2GB of RAM on-board?

---

### Post by NoaHall on 2010-01-28
> **Roger Allott said:**
> Uh??? Could you please explain how I can access "more than 3.4GB of RAM" when I've only got 2GB of RAM on-board?

If you have it. Obviously.

---

### Post by llawwehttam on 2010-01-28
> **Roger Allott said:**
> Uh??? Could you please explain how I can access "more than 3.4GB of RAM" when I've only got 2GB of RAM on-board?

What he means is that 32 bit can only utilize about 3.4 Gb ram if your lucky whereas 64 bit can use a lot more. I think I heard it can support up to 128 GB ram. Of course it can only use the amount of RAM you have installed.

---

### Post by Sef on 2010-01-28
Moved to Recurring Discussions.

---

### Post by nhasian on 2010-01-28
i should point out that you can access 4+ gigs of ram with 32bit just fine using a kernel with PAE enabled:

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

so you dont _have_ to upgrade to a 64bit OS if you dont want to, but as I recommended earlier, if your CPU supports 64bit then it is advisable to use a 64bit OS.  

also although i linked to it before, i think you guys may have missed it:

[Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1")

> Only a very small drop in performance can be found with the PAE kernel in the PostMark disk test, but the 64-bit kernel was immensely faster.

In the fourteen tests for this article we did not find using Ubuntu's 32-bit PAE kernel to have a dramatic performance impact whether it be positive or negative. Granted, we were using just 4GB of system memory that is common to many desktops, but if using 8GB, 16GB, or even a greater memory capacity the performance penalties are perhaps higher. By far though exhibiting **the best performance was the Ubuntu 64-bit kernel** that often ended up being leaps and bounds better than the 32-bit kernel. Unless you have technical or business reasons for not migrating to 64-bit Linux with compatible hardware, there is no reason to stick around with a 32-bit kernel and worrying about physical address extension.

---

### Post by bodhi.zazen on 2010-01-28
> **nhasian said:**
> i should point out that you can access 4+ gigs of ram with 32bit just fine using a kernel with PAE enabled:

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

so you dont _have_ to upgrade to a 64bit OS if you dont want to, but as I recommended earlier, if your CPU supports 64bit then it is advisable to use a 64bit OS.  

also although i linked to it before, i think you guys may have missed it:

[Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1")

Fedora has offered a PAE kernel for some time, and as of Ubuntu 9.04 Ubuntu offers a PAE kernel in the repositories.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kernel+pae&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kernel+pae&searchon=name&subword=1&version=all&release=all)

---

### Post by mvalviar on 2010-01-28
Ok I'm on a 64 bit machine now. First up an nvidia driver. I can't install it through System>Admin>Hardware drivers. 

I try to activate it and I get the prompt for my password then it hangs. If I kill to try again it says you are not authorized without prompting me for a password.

---

### Post by bodhi.zazen on 2010-01-28
> **mvalviar said:**
> Ok I'm on a 64 bit machine now. First up an nvidia driver. I can't install it through System>Admin>Hardware drivers. 

I try to activate it and I get the prompt for my password then it hangs. If I kill to try again it says you are not authorized without prompting me for a password.

The nvidia driver works fine for all my 64 bit machines. 

So I would assume your issue is hardware specific and not 32 vs. 64 bit specific, hard to say without a bit more detail.

---

### Post by Zoot7 on 2010-01-28
The only concernable difference anyone is going to notice from an end user's point of view as regards running a 64bit OS as opposed to a 32bit OS is a large increase in performance when it comes to applications that require a large amount of "Number Crunching" eg. - Simulations, Audio/Video Conversion etc.
This is due to the fact that the CPU can use it's (already) 64bit ALU to it's full capacity. 

The increased memory addressing allowing it to use more RAM than 3.2/3.3/3.4GB is largely redundant unless you've applications that require RAM by the bucketload anyway.

---

### Post by pirateghost on 2010-01-28
> **mvalviar said:**
> Ok I'm on a 64 bit machine now. First up an nvidia driver. I can't install it through System>Admin>Hardware drivers. 

I try to activate it and I get the prompt for my password then it hangs. If I kill to try again it says you are not authorized without prompting me for a password.
i noticed this when setting up a computer on a slow internet connection.  i just had to wait, it was actually downloading the drivers but it took forever.

---

### Post by mvalviar on 2010-01-28
got the drive installed. The Hardware Manager wasn't so useful. I had to try to active desktop effects and the driver got installed from there. 

Everything else is smooth sailing. 

Better performance in blender and cinelerra. I should have used 64 bit earlier.

---

### Post by cascade9 on 2010-01-29
> **llawwehttam said:**
> What he means is that 32 bit can only utilize about 3.4 Gb ram if your lucky whereas 64 bit can use a lot more. I think I heard it can support up to 128 GB ram. Of course it can only use the amount of RAM you have installed.

Just a touch more than 128GB. 256TB currently, with the ability to extend that to 16EB (exabyte).

---

### Post by Roger Allott on 2010-02-07
> **Roger Allott said:**
> Yes, I feel a bit of a drongo for not realising I had a 64-bit CPU ages ago!
And I'll report myself for being a double-drongo.

Despite learning that one cannot simply assume that a CPU is 32-bit because Windows 32-bit is installed on it, I bought an old desktop PC from a friend on Friday and put Ubuntu 32-bit onto it.

And now, using Ubuntu and the Linux commands mentioned in this thread, I find that it has a 64-bit CPU. D'OH!!

---

### Post by Alexandre Putt on 2010-02-07
Unless you have a lot of RAM, I wouldn't bother. I have a Dual Core with 4GB, and I used both 32-bit and 64-bit versions of Ubuntu. 

I see little immediate gain. At the same time x64 has some minor unpleasant issues.

---

### Post by texaswriter on 2010-02-07
> **Alexandre Putt said:**
> Unless you have a lot of RAM, I wouldn't bother. I have a Dual Core with 4GB, and I used both 32-bit and 64-bit versions of Ubuntu. 

I see little immediate gain. At the same time x64 has some minor unpleasant issues.

I can't agree more with that. I like where x64 is going, but right now, unless you are into those hardcore processing tasks that *do* benefit, 32bit is just fine. 

In 5 years, after they've nerfed 32 bit even more [already started to happen], then 64 bit will be better, aka mandatory. That's basically the only way they are going to get 64 bit to do all processes better than 32 bit... because fact of the matter is people don't need 64 bit accept for memory allocation.. So, instead of screwing people over, create a way to use less memory [as in programs not use that much memory, READ: Programmers have to use brains to design programs that don't need that much memory], or create a way to address infinitely more blocks of memory [hey, this has been done before... google DoubleDuty and see if that brings up anything... It was actually a way to multiltask on a 30 year old computer.. READ: PRogrammers who made that program had brains]. 

No, 64 bit is ridiculous... I laugh every time I hear somebody point to a benchmark that PROVES DECISIVELY that for EVERYDAY NORMAL activities t hat 64 bit provides NO advantage, in fact sometimes a disadvantage.. Oh, but they seem to think that extreme processing tasks that NO ONE PERFORMS somehow proves that 64 bit rules. That's interesting at the least... 

Certainly 64 bit is providing some other improvements, but these improvements could be provided without forcing people up a slippery slope of inefficiency. 

:o

---

### Post by wmcbrine on 2010-02-08
> **texaswriter said:**
> I laugh every time I hear somebody point to a benchmark that PROVES DECISIVELY that for EVERYDAY NORMAL activities that 64 bit provides NO advantage, in fact sometimes a disadvantage.I'd laugh too, since such a benchmark would be clearly erroneous.

---

### Post by HappyFeet on 2010-02-09
> **texaswriter said:**
> I can't agree more with that. I like where x64 is going, but right now, unless you are into those hardcore processing tasks that *do* benefit, 32bit is just fine. 

In 5 years, after they've nerfed 32 bit even more [already started to happen], then 64 bit will be better, aka mandatory. That's basically the only way they are going to get 64 bit to do all processes better than 32 bit... because fact of the matter is people don't need 64 bit accept for memory allocation.. So, instead of screwing people over, create a way to use less memory [as in programs not use that much memory, READ: Programmers have to use brains to design programs that don't need that much memory], or create a way to address infinitely more blocks of memory [hey, this has been done before... google DoubleDuty and see if that brings up anything... It was actually a way to multiltask on a 30 year old computer.. READ: PRogrammers who made that program had brains]. 

No, 64 bit is ridiculous... I laugh every time I hear somebody point to a benchmark that PROVES DECISIVELY that for EVERYDAY NORMAL activities t hat 64 bit provides NO advantage, in fact sometimes a disadvantage.. Oh, but they seem to think that extreme processing tasks that NO ONE PERFORMS somehow proves that 64 bit rules. That's interesting at the least... 

Certainly 64 bit is providing some other improvements, but these improvements could be provided without forcing people up a slippery slope of inefficiency. 

:o
How is 64bit screwing people over? How is it inefficient? Wow, some people.

I've been using 64bit for a year and a half now, and have not had 1 problem doing anything. This is coming from a power user that does everything. Please, enlighten me oh genius.

---

### Post by texaswriter on 2010-02-12
> **HappyFeet said:**
> How is 64bit screwing people over? How is it inefficient? Wow, some people.

I've been using 64bit for a year and a half now, and have not had 1 problem doing anything. This is coming from a power user that does everything. Please, enlighten me oh genius.

I will not respond to your question in so much as invalidating it. I never said you would have a problem. It was not suggested you would have a problem. I do not need to enlighten you about something I did not say. I never claimed to be a genius and your sarcasm is not appreciated. 

I never said 64bit is screwing people over in and of itself. It is the constant requirements of MORE processing power and MORE memory. When in fact programmers could just use resources efficiently, they choose to use more and more for no reason. 

You want a perfect way that computer manufacturers [the hardware manufacturers] control the market to constantly require more processing power, bigger data bus, and more RAM... It happened over 10 years ago with SCSI. Yes, SCSI was a way to more closely match HDD data speeds to bus speeds. It has been AND CONTINUES to be the NUMBER ONE BOTTLENECK in all forms of computing.

The data bus is not the bottle neck. We do not need to address more memory per application, we need to make virtual memory more useable. We need to make applicatiosn more efficient at using current mnemonics and registers... We don't need to force people to arbitrarily double all memory addresses. 

So, to summarize, you don't need to put words in my mouth, I talk enough myself.

---

