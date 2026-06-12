---
title: "Ubuntu and multi core processing?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by ingrid_ozikem on 2008-05-30
I'm considering building a good multi-core (double /quad) desktop and had questions about whether Ubuntu can take advantage of the following features. I've heard a lot about Vista and core duo but I'd love to hear your advice on whether Ubuntu can (be honenst) truly take advantage of the following choices:

1. Multi-core (double / quad)
2. 64 bit vs 32 bit
3. Intel vs AMD


  I don't plan to buy Windows and so don't want to build a machine that Ubuntu doesn't really work on or make full use of.

PS: Would also appreciate any recommended hardware forums for Ubuntu / linux people building their own desktops..

---

### Post by |{urse on 2008-05-30
I have installed linux on many many quad/dual cores on ubuntu and even more on fedora so far every single install has seen all cores supported. To check whether all cores are seen run this command.

> cat /proc/cpuinfo

every core will be listed individually as well as a lot more pertinant info. 
To do a "burn in test"

[http://www.passmark.com/ftp/bitlinux.tar.gz](http://www.passmark.com/ftp/bitlinux.tar.gz) <--- go nab that and extract it to wherever. there will be a binary named "burnintest" run it and it will test everything from 2d/3d rom/floppy/hdd cpu etc. etc. It's what we use here at Journey ^^

64bit vs 32bit = well. that depends on whether you are running a program that actually utilizes 64bit arch. 32bit is all I've ever needed unless it was a number crunching box.

So far as intel vs. amd.. lol i hate to say intel but "intel!" even though AMD holds fonder memories for me, if that makes any sense. Now mind you, I havent had a chance to play with the new phenoms on linux.

---

### Post by Joeb454 on 2008-05-30
I have Ubuntu running on an Intel Core 2 Duo right know actually :) Works brilliantly :)

---

### Post by |{urse on 2008-05-30
Oh so far as the AMD phenom,

[http://www.journeysystems.com/?custom_built_pcs&price=4](http://www.journeysystems.com/?custom_built_pcs&price=4)

I get to load and test these with fc9 and gutsy on monday so if you had your heart set on an AMD multicore you can wait till then and i'll post my findings.

---

### Post by ingrid_ozikem on 2008-05-30
Do post back with your AMD experience! I'm buying things over the next several weeks and I might go with Intel after all but I'm sure having your info here will be useful to many in the future!

I assume when you say linux can "see" all the cores, it is also able to use them? This is what puzzles me -- does it depend on the kernel or do my individual programs need to be compatible with multi-core systems? Will they just get stuck working on a single core? 

Will the kernel distribute each instance of Firefox to the same core? Can a single instance of a single program like Mathematica/ music encoding use both cores?

Thanks for your answers!

---

### Post by Joeb454 on 2008-05-30
I have no idea how it works, but if both cores are needed they'll get used :) Also if you're compiling stuff from source, you can specifically utilize them then as well :)

---

### Post by |{urse on 2008-05-30
i surely will let you know the benches/compatibility probably monday evening.

so far as seen/used that depends on whether your application uses load-balancing. Most modern audio/graphics rendering applications are "load balanced" or evenly distributed between all of your cores, a lot of that is decided in your cpu not your os anyway. The only *nix app i've ever used that did not make use of both cores was wine, but I'm sure it wasn't properly configured to use all cores (a bit of pebcak).

---

### Post by Efros on 2008-05-30
I currently have Ubuntu 8.04 64 bit installations on a C2Q Q6600, an AMD x2 5000+ dual core, a dual core AMD x2 3800+, and a AMD64 3200+. Would like to play with a phenom but my wife may divorce me!

---

### Post by Joeb454 on 2008-05-30
That's a good point - Most dual cores are also 64 bit compatible - the Core 2 Duo range is (I'm on my 64 bit install now)

---

### Post by Vicfred on 2008-05-30
i have been running ubuntu on 2 cores since 2 years ago and it is fine (AMD X2 3800+)

---

### Post by |{urse on 2008-05-30
^^ my buddy jason at work says his x2 rocks with fedora. Now if only his brand spankin new hd3800 radeon worked lol. come to think of it I just remembered that i like linux on opterons even better than on xeons so i would like to change my favorite cpu brand from intel back to AMD again (lol i change my mind constantly)

---

### Post by inportb on 2008-05-30
So I've been using Ubuntu 8.04 on an AMD Turion 64 X2 in 32-bit mode, and it's been just great. Both cores are utilized.

---

### Post by ingrid_ozikem on 2008-05-31
I was poking around on hardware sites a little more and wanted to import a frequent debate they have (in the context of windows vista & its apps) to Ubuntu.

Slower Quad core or faster dual core?

Not an academic question because 2 of the most common and affordable Intel chips in the $200 price range are:

Intel Core 2 Duo E8400 Wolfdale 3.0GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor
(~$188)
and 

Intel Core 2 Quad Q6600 2.4GHz LGA 775 Processor
(~$210)

So the second one has 4 cores but each at 2.4 GHz.. the first one has two cores but faster. The consensus seems to be that if your programs can't use all 4 cores, the second option is bad. There is a lot of discussion all over the place about Windows programs on this but I'd really like to stick to Ubuntu.

Would love to hear if people think Ubuntu can *USE* all 4 cores.. do future versions of Ubuntu plan to use all cores? ( or is this really up to the CPU? )

---

### Post by Efros on 2008-05-31
Depends on what you're doing, my quad core is mostly used for video compression and editing which it does very quickly, especially when oced to 3GHz

A word on fedora, I tried core 9 and it installed but with a really cruddy resolution with no LAN drivers on my machine, wiped and reinstalled Heron which correctly ids both my graphics card and my LAN card.

---

### Post by perlluver on 2008-05-31
Even in Slackware there are two kernels, generic and SMP, which is for symmetric processors, meaning dual core or higher.  So I am almost certain most of the latest Linux distributions can handle dual core processors.

---

### Post by |{urse on 2008-05-31
> **ingrid_ozikem said:**
> I was poking around on hardware sites a little more and wanted to import a frequent debate they have (in the context of windows vista & its apps) to Ubuntu.

Slower Quad core or faster dual core?

Not an academic question because 2 of the most common and affordable Intel chips in the $200 price range are:

Intel Core 2 Duo E8400 Wolfdale 3.0GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor
(~$188)
and 

Intel Core 2 Quad Q6600 2.4GHz LGA 775 Processor
(~$210)

So the second one has 4 cores but each at 2.4 GHz.. the first one has two cores but faster. The consensus seems to be that if your programs can't use all 4 cores, the second option is bad. There is a lot of discussion all over the place about Windows programs on this but I'd really like to stick to Ubuntu.

Would love to hear if people think Ubuntu can *USE* all 4 cores.. do future versions of Ubuntu plan to use all cores? ( or is this really up to the CPU? )

Yes, for example i just installed fedora on a core 2 quad with an NVIDIA 9800 gtx. It saw all cores and load balanced the burn in test across all 4 cores. Very Very snappy machine. I also ran Quake Wars: Enemy Territory with all the graphical options maxed out. All four cores were used on this app as well.

If you're trying to do something where each core has a job, like nodes on a cluster use a transport layer like ipvs, which is really cool for huge networks serving email and other net based services. For jobs like hardcore gfx rendering on a render farm no patch is necessary, a single 2.6xxx kernel can be the master node with the appropriate software. Kernel 2.6 takes full advantage of modern multicore processors.

INTEL:
> Semiconductor technological advances in the recent years have led to the inclusion of multiple CPU execution cores in a single processor package. This processor architecture is known as Multi-Core (MC) or Chip Multi Processing (CMP). Any application which is well optimized and scales with SMP will take immediate benefit of the multiple execution cores, provided by the Multi-core architecture. Even if the application is single-threaded, multi-tasking environment will take advantage of these multiple execution cores. 2.6 Linux kernels take instant advantage of the MC architecture. MC also brings in performance optimization opportunities which will further enhance the performance. This paper captures the recent enhancements to the 2.6 Linux Kernel which better support and enhance the performance of Multi-core capable platforms.

More on IPVS (though you probably will never use it):

[http://www.linuxvirtualserver.org/software/ipvs.html](http://www.linuxvirtualserver.org/software/ipvs.html)

---

### Post by SunnyRabbiera on 2008-05-31
Ubuntu and linux in general has a very dynamic kernel, so it will be able to use a dual core or more processor.
But its management is no where near that of windows, that just takes processor power just because it can... linux uses it only when needed.

---

### Post by |{urse on 2008-05-31
Yeah Sunny's right the windows kernel bites for multicore. 2.6 is waay more intuitive. That's why darn near all supercomputers use linux.. for instance the behemoth blue gene:

[http://domino.research.ibm.com/comm/pr.nsf/pages/rscd.bluegene-picag.html/$FILE/PB016598.JPG]("http://domino.research.ibm.com/comm/pr.nsf/pages/rscd.bluegene-picag.html/$FILE/PB016598.JPG")

uses linux

[sc06.supercomputing.org/schedule/pdf/pap178.pdf]("sc06.supercomputing.org/schedule/pdf/pap178.pdf")

---

### Post by rabbit20 on 2008-07-07
I am having a bit of trouble with my AMD 4200, when i am running a program that needs cpu, like google earth, my second core will ramp to 99.9% while my first core sits at around 19%. any idea on how to correct this and get the cores to balance?

the same goes for my server that is running a Intel Core 2 Quad Q9450 the second core is always running higher then the rest but all in all they appear to balance, just the 2nd core runs higher

---

### Post by mcduck on 2008-07-07
> **rabbit20 said:**
> I am having a bit of trouble with my AMD 4200, when i am running a program that needs cpu, like google earth, my second core will ramp to 99.9% while my first core sits at around 19%. any idea on how to correct this and get the cores to balance?

the same goes for my server that is running a Intel Core 2 Quad Q9450 the second core is always running higher then the rest but all in all they appear to balance, just the 2nd core runs higher

You can't do anything about it. If the program is made to only run in single thread it's impossible to use more than one CPU core to run it.

Sadly this currently applies to majority of programs available, no matter what OS you are running.

---

### Post by hogwartsnigel on 2008-07-10
Hi Guys,
Just looking to summarize as I am building my first machine..here is what I have at present
Asus PK5 Pro, Niper 7300w PSU, Lian LI Server case 5 fans, 2 Asusge 7600gts (Non sli), 2 Asus dvd/rw 20x drives, 4gb 800mhz ddr2 Ballistix tracer, 4 x internal IDE (1 x 320gb and 3 x 250gb Maxtor and 2 sata drives (2 WD 120gb non raided), will be accessing 2 x USB x 2 drive 250gb each, wifi networked, 1Mitsubishi 21" CRT, and 1x Dell 1905fsp LCD.

I use the machine for all usual pc everday stuff, a little sound editing, lots of graphic editing in Gimp, and video/ dvd creation etc...which processor?
Using Ubuntu Ultimate 64, if I dual boot it'll be another Linux flavour NEVER Windows.

Quad Intel (Q6600, Q6700, Q9 series)
AMD Phenom series
or go Duo Core??
Thanks

Nigel

---

### Post by bodhi.zazen on 2008-07-10
Just google search the cpu.

Ubuntu comes pre installed with some of these CPU so in general you will be fine.

I have seen Ubuntu run on dual quad core Xeon processors (8 cpu).

---

### Post by hogwartsnigel on 2008-07-10
Thanks Bodhi,
I have every faith in Ubuntu working with the multi core cpu's, was I guess hi-jacking a little (for which I apologise) and looking at recommendations for the CPU to install in the system.

Thanks

Nigel

---

### Post by bodhi.zazen on 2008-07-10
From what I have seen intel > the AMD Phenom series

The Phenom is spotty with Linux, although it varies by CPU.

The intel seem solid, as in the Xeon

---

### Post by hogwartsnigel on 2008-07-10
Thanks,
Yes I hate to say it as I've always loved AMD but I am favouring the Intel. NOw the question Quad or duo???
Thanks
Nigel

---

### Post by bodhi.zazen on 2008-07-11
You can get a nice Phenom. Just do your  homework first ...

I liked this site :

[http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)

As always with hardware, get as much as you can reasonably afford. The quad cores are not *that* much more then the dual cores, so long as you are not wanting the absolute fastest.

You can get a Xeon quad core for as little as $ 200 (US) with very little effort, and I bet you can do better then that if you try. Of course on the high end a quad core will cost you 2,000 ...

---

### Post by suri.mahendra on 2008-07-11
I'm running a biostar k8m800 with an AMD x2 processor (dual core).  It works swimmingly with Hardy.

The question is no longer 64 vs 32.  32 is obsolete.  When you can find it, it costs just as much if not more than 64.  The question comes down to availability and cost of parts as they need to be replaced.

---

