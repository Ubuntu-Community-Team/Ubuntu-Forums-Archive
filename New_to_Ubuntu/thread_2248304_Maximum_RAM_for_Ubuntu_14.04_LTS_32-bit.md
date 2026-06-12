---
title: "Maximum RAM for Ubuntu 14.04 LTS 32-bit"
date: 2014-10-13
forum: New to Ubuntu
---

### Post by John_Patrick_Mason on 2014-10-13
Hi everyone,

I'd like to make some upgrades to my old Sony VAIO  VGC-RB45G desktop in order to make it faster. I currently have Ubuntu 14.04 LTS installed alongside Windows XP, which I will soon delete in  order to free up that space for the Ubuntu partition, given Microsoft's  end of support for the latter.
Specifically I'd like an answer to the following questions:
How come my computer in general is so slow (Unity, the Ubuntu Software Center, Firefox freezing)?
Is it because I'm low on RAM?
If so, what is the maximum amount of RAM that Ubuntu 14.04 LTS 32-bit can support?
What is the maximum amount of RAM I can have based on the hardware specs below?

Processor Intel Pentium 4 CPU 3.00GHz x 2
Graphics Intel 915G x86/MMX/SSE2
Memory 993.2 MiB (~1GB)
OS type 32-bit
Disk 133.9 GB

Thanks in advance,

Mason

---

### Post by papibe on 2014-10-13
Hi John_Patrick_Mason.
> **John_Patrick_Mason said:**
> 
How come my computer in general is so slow (Unity, the Ubuntu Software Center, Firefox freezing)?
Vanilla Ubuntu (with Unity and compiz) requires accelerated graphics to work smoothly. Pentium 4 is not the fastest processor either.
> **John_Patrick_Mason said:**
> 
Is it because of the RAM?
It plays a role, but not that much. It does when you have several applications open.
> **John_Patrick_Mason said:**
> 
What is the maximum amount of RAM I can have based on the hardware specs below?
A lot. The standard 32bit kernel now by default uses an extension called PAE. I'm pretty sure you can maximize the hardware limit of your machine.

There are several approaches to improve performance:
[LIST]
[*]Use another version that does not need hardware accelerated graphics like Xubuntu or Lubuntu.
[*]Get an SSD.
[*]Get more RAM.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by grahammechanical on 2014-10-13
May I suggest that you consider the amount of memory that the graphic adapter has as a possible cause of this problem?

> [h=3]32-bit x86 RAM limit[COLOR=#555555][[/COLOR][edit]("http://en.wikipedia.org/w/index.php?title=RAM_limit&action=edit&section=13")[COLOR=#555555]][/COLOR][/h][COLOR=#252525][FONT=sans-serif]*See also: [3 GB barrier]("http://en.wikipedia.org/wiki/3_GB_barrier") and [PCI hole]("http://en.wikipedia.org/wiki/PCI_hole")*[/FONT][/COLOR]
[COLOR=#252525][FONT=sans-serif]In non-PAE modes of [x86]("http://en.wikipedia.org/wiki/X86") processors, the [RAM]("http://en.wikipedia.org/wiki/RAM") is always limited to 4 GB.[/FONT][/COLOR]


> [COLOR=#252525][FONT=sans-serif]Limits on physical memory for 32-bit platforms also depend on the [/FONT][/COLOR][Physical Address Extension]("http://en.wikipedia.org/wiki/Physical_Address_Extension")[COLOR=#252525][FONT=sans-serif] (PAE), which allows 32-bit systems to use more than 4 GB of physical memory.[/FONT][/COLOR]

I believe that 32 bit Ubuntu only comes with a PAE kernel. The non-PAE kernel version of Ubuntu was dropped some months/years ago.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Can you install 64GB in that machine? That is the maximum. I am thinking that if you have Ubuntu 14.04 installed then you must have a CPU with PAE or 14.04 would not have installed.

Regards.

---

### Post by John_Patrick_Mason on 2014-10-13
Wow, thanks papibe for the prompt reply.
I see adding a solid state drive and more RAM might help.
Would adding a graphics card be of any help too?

I've had this desktop since 2005 and I don't see why I should throw it away just because support has run out for Windows XP. It's kind of like an old car, you become proud of it, even though it's not the fastest it gets the job done. Plus, I've always wanted to try out Ubuntu (started with 12.10), so this was the perfect opportunity to do so when I knew support for Windows XP was about expire.

---

### Post by Bucky Ball on 2014-10-13
I have an old desktop with a P4 processor (32bit). I chucked in an SSD and 4Gb of RAM and it now flies. ;)

Apart from that, and as suggested, try Xubuntu or Lubuntu.

---

### Post by d4m1r on 2014-10-14
Yes, upgrading the HDD to a SSD and upgrading the RAM will help A LOT in terms of performance....

Ubuntu can support 1 ton of RAM, some Ubuntu servers run 128GB RAM for example but your question should not be how much RAM can Ubuntu support....But how much RAM can your laptop support. Your laptop is currently slow because you only have 1GB of RAM. You should get at least 2, preferably 4. You need to find out first however, how many RAM slots (DIMM slots) your laptop has (1 or 2), and how much RAM can your laptop (motherboard) can support. You can find this out by searching by your make + model in Google. Then just install the new SSD and the RAM yourself, burn Ubuntu (64 bit version) to a CD and do a new install.

All problems solved and I guarantee if you upgrade to at least 2GB of RAM (if not more), you will notice a big difference in speed/performance.

---

### Post by ibjsb4 on 2014-10-14
A vgc-rb45g[COLOR=#ff0000]x[/COLOR] looks to have a two gig (ram) limit.

---

### Post by Bucky Ball on 2014-10-14
> **d4m1r said:**
> burn Ubuntu (64 bit version) to a CD and do a new install.



Don't do this as you claim to have a 32bit processor. It's a P4 (pentium 4). You need the 32bit version. ;)

---

### Post by whitesmith on 2014-10-14
Make sure you have PAE support. Otherwise the most memory addressable on a 32-bit system  is roughly 3 GB (4 can be installed but some of that will be absorbed by system processes). Also, Pentium 4 is old and slow. I'd go with Lubuntu as this OS makes fewer hardware demands than Ubuntu.

---

### Post by kc1di on 2014-10-14
you will need PAE support.  to go beyond 3 Gigs of Ram
not all P4's had it.  you can tell by copying and pasting this command in a terminal.
```
grep --color=always -i PAE /proc/cpuinfo
```
if you get any output it is PAE capable if there is no out put it's not. 


With that old a machine I would opt for Xubuntu or Lubuntu myself.  or maybe Ubuntu-mate. 
Unity needs quite a bit of GPU power. 

Just a suggestion. :)

---

### Post by qyot27 on 2014-10-14
> **Bucky Ball said:**
> Don't do this as you claim to have a 32bit processor. It's a P4 (pentium 4). You need the 32bit version. ;)
The OP never actually claimed to have a 32-bit processor, it was a question about the 32-bit version of Ubuntu (which could be taken as evidence that the CPU is only 32-bit, but not necessarily).  Some P4 models toward the end did include x86-64 support, but you have to know which exact model you have.  They said they've had the computer since 2005, so it could very well be one of those models.

I download both the 64-bit and 32-bit ISOs and then use [MultiCD](http://multicd.tuxfamily.org/) to combine them into a single ISO and burn both to the same disc.  That way I don't waste DVDs and am prepared for whichever type the target computer is equipped with.


Several other things:
[list][*]It's not just a matter of 'adding more RAM'.  You want to make sure the RAM type matches the motherboard (non-DDR vs. DDR vs. DDR2, etc.), and that the *speed* of the RAM is actually high enough to provide a boost in performance.  You could put in a full 2 GBs, but if you're using the lowest speed, it wouldn't do much good performance-wise.  It'd probably just take [some of] the burden off of swap.  The motherboard will again determine what speed you can put in there.  [Crucial](http://www.crucial.com/usa/en/compatible-memory-for/Sony/vaio-vgc-rb45gx) says it only supports DDR, and they've got PC3200, which is the highest speed for that level.  A 1GB stick is close to $30, a dual channel kit is close to $60.
[*]A graphics card would take the burden off the CPU, provided you can disable the integrated graphics (this can be done in the BIOS, or if that's not an option, it can sometimes be blacklisted in the OS and forced off that way - that's what I have to do with my i810e graphics).
[*]Said graphics card has to match the expansion slot type.  Since it's from 2005, and I assume it was an economy model even back then, chances are this computer only supports Conventional PCI or AGP, it probably won't support PCI-Express.  So you have to look for cards that support the right type.  The good news is that cards like this now run in the $30-50 range or so.  They won't be power models, but they'll be able to do the job.  ZOTAC makes a Conventional PCI card with a GeForce GT 610 on it (which will do hardware decoding of H.264, VC-1, and MPEG-2, not sure about MPEG-4 ASP, and should be more than new enough to handle the graphics load required by Unity), which is what I'd look at myself if it weren't for the fact my GeForce 6200 card is still running perfectly.  A GT 610 is an odd exception, since most Conventional PCI card manufacturers stopped using newer GPUs several generations prior to that; the 6200 seemed to be close to the top of what you'd still be able to get in a regular PCI card when I bought it, although I did see PNY cards with 8xxx and 9xxx series chips in them pop up later, and then that GT 610 card I just mentioned appeared in 2012.[/list]

---

### Post by mörgæs on 2014-10-14
> **kc1di said:**
> you will need PAE support.  to go beyond 3 Gigs of Ram
not all P4's had it.

Yes they did, as had Pentium 3. In general PAE is mentioned too much in Ubuntuforums, for example in this thread where it is irrelevant and only confuses people.

What original poster needs is focusing on software solutions before hardware. A fresh install of Lubuntu 14.04.1 is an easy test. 

IF another GB of RAM is needed anything that fits will be an advantage, also if it's slower than the modules already there.

---

### Post by Mike_Walsh on 2014-10-15
Taking an educated guess, I would say you're looking at an absolute limit of 4GB anyway.

I run an Athlon 64; it was the Pentium 4's direct competition at that time (2003-2006). Almost all motherboards of the time were DDR1.....and I have yet to see one that had more than four RAM slots.

The biggest DDR1 stick was 1 GB; ergo, 1 GB x 4 gives you a maximum of 4 GB.

But morgaes is right; what will be of more use to the OP will be advice about software first.....specifically lighter weight OSs. I can enthusiastically recommend Lubuntu; and I know people who happily run it on 'top-end' systems, with 16 or even 32 GB of RAM.....simply because it leaves them a very high percentage of their system resources to do with as they please.

Regards,

Mike.

---

### Post by thomsonjosh on 2015-04-27
> **kc1di said:**
> you will need PAE support.  to go beyond 3 Gigs of Ram
not all P4's had it.  you can tell by copying and pasting this command in a terminal.
```
grep --color=always -i PAE /proc/cpuinfo
```
if you get any output it is PAE capable if there is no out put it's not. 


With that old a machine I would opt for Xubuntu or Lubuntu myself.  or maybe Ubuntu-mate. 
Unity needs quite a bit of GPU power. 

Just a suggestion. :)

I ran the command you mentioned and got the following output:

```
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss syscall nx lm constant_tsc pni ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm
```

The 7th flag does show 'pae', which conflicts with your comment as I am not able to have 4GB (It results in disabled networking abilities). Setting the RAM to 3GB doesn't disable any network abilities.
We are running an Ubuntu 14.04 LTS 32-bit on a virtual host. (MS's Hyper-V).

Have you any clue to what future steps I may take to resolve this 3GB restriction?

Note: We are running platform specific software that requires a 32-bit OS, so we are determined to get this current server unrestricted.

Thanks.

---

