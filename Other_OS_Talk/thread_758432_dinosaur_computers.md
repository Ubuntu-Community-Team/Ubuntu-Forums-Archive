---
title: "dinosaur computers"
date: 2008-04-18
forum: Other OS Talk
---

### Post by cartisdm on 2008-04-18
I'm proud to say I finally my new (old) IBM Thinkpad 600e running with Xubuntu Feisty.  My friend was going to throw it out and called me to see if I knew of a place she could drop it off.  I told her my apartment!!!

What old computers do you all have?  This is my first old guy with a successful linux install.  I don't have everything configured perfectly because its still really slow.  What OS do you all use for them?

---

### Post by kerry_s on 2008-04-18
for such a low spec system, you really want to use a very minimal distro, so you can get some good working speed.

dsl is my top choice for those kind of specs.->
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

i just been helping a friend with his 366mhz 128mb ram, i installed dsl in virtualbox just to help him. he's using the 4.2.5 current version.
my systems 450mhz 256mb ram running a custom debian install.

---

### Post by LightB on 2008-04-18
Oldest thing I have here somewhere is an K6 300Mhz. We're talking 11 years old, maybe more. Doesn't even have a ps/2 keyboard port. Has some ISA slots and a few ports I don't even recognize.  Only Linux that has worked is old puppy and dsl. Both are pretty lacking compared to standard distros that are meant to be installed to the harddrive. It's kind of a little project of occasional boredom of mine. Weeks ago I installed dsl to it, but it's an imperfect system if you actually want to use it like a regular distro. The package manager is borked by default, dma is disabled, different system partitions aren't set up by default, and no Xorg, just reliable but slow Xvesa. Also issues with users.

Other famous contenders which crashed and burned in my case included Antix and Vectorlinux. PC just too old for the included kernels I guess. Older versions of stuff was also suggested to me, but I passed on that. There's not much point in doing that. Might as well install on it my first distro, Redhat 9, that'd be sure to work too.

The gleam of hope, I was directed towards TinyMe, though I haven't gotten around to fire it up yet, but it shows promise.

---

### Post by kerry_s on 2008-04-18
> **LightB said:**
> Oldest thing I have here somewhere is an K6 300Mhz. We're talking 11 years old, maybe more. Doesn't even have a ps/2 keyboard port. Has some ISA slots and a few ports I don't even recognize.  Only Linux that has worked is old puppy and dsl. Both are pretty lacking compared to standard distros that are meant to be installed to the harddrive. It's kind of a little project of occasional boredom of mine. Weeks ago I installed dsl to it, but it's an imperfect system if you actually want to use it like a regular distro. The package manager is borked by default, dma is disabled, different system partitions aren't set up by default, and no Xorg, just reliable but slow Xvesa. Also issues with users.

Other famous contenders which crashed and burned in my case included Antix and Vectorlinux. PC just too old for the included kernels I guess. Older versions of stuff was also suggested to me, but I passed on that. There's not much point in doing that. Might as well install on it my first distro, Redhat 9, that'd be sure to work too.

The gleam of hope, I was directed towards TinyMe, though I haven't gotten around to fire it up yet, but it shows promise.


well, if you got a little experience under your belt, the best thing is to go custom, build the system to your needs instead of trying to find a distro that fits your needs.

i do mine using a debian base, only install what i use, remove anything i'm not going to use. you'd be surprised at how easy it is to go custom.
i use the net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

at the package selection i uncheck everything, that gives me just the base.
i log in as root and get just enough to get me to the gui->
apt-get install xorg (synaptic jwm mc)<what i prefer
type> exit
log in as my user
type> startx
i open synaptic and keep adding what i want. synaptic is optional, i prefer to use it, it's easier to browse and decide what i want.

---

### Post by LightB on 2008-04-18
Yeah, Debian is a great, I do know how to set it up, but it would be too much work in this case for a machine that may just as likely be abandoned than used. I could go even further in custom and do LFS, and inevitably learn stuff along the way, but the idea of compiling every application at that speed doesn't sound good to me. I think a prepared, typical distro for these purposes can be very useful, that's what I was looking for first. If the PC needed to be used I'd do what I had to do with debian, or whatever, for sure.

---

### Post by SunnyRabbiera on 2008-04-18
Linux can work miracles, it can make "obsolete" computers brand spankin new :D

---

### Post by el_ricardo on 2008-04-18
if u definatly want to stick with ubuntu, go with ubuntulite, as longas you've got an internet connection (does it have ethernet?) all you do to install it is install an ubuntu command line system, then download and run a script from the [ubuntulite website]("http://ubuntulite.tuxfamily.org") and it configures the system beautifully for low end hardware. removes a bunch of uneccasary stuff, and installs openbox, fbpanel, xmms, abiword, synaptics, rox file manager and xterm. a very simple install, you can't do much with the base, but it leaves for moulding the system to exactly your needs.

supposedly the minimum requirements are a 200MHz CPU, and 64MB of RAM, I've got it installed on my old p3 700MHz, with 320MB RAM, and it works absolutely beautifully, haven't got round to compiling a custom kernel for it, but when that's done it will be even better!

---

### Post by K.Mandla on 2008-04-18
Moved to Other OS Talk.

Crux Linux FTW!

---

### Post by Bungo Pony on 2008-04-18
I use DSL 3 (I don't like version 4) which uses Fluxbox and that nifty little mount tool. Fits all my needs very well for old PCs under 128M RAM. Anything after that gets TinyMe. Never did like Puppy.

---

### Post by anticapitalista on 2008-04-18
LightB, If you want to use antiX on a K6 you'll have to use Spartacus version, based on Mepis 6.5.

---

### Post by wolfen69 on 2008-04-18
> **cartisdm said:**
> I'm proud to say I finally my new (old) IBM Thinkpad 600e running with Xubuntu Feisty.  My friend was going to throw it out and called me to see if I knew of a place she could drop it off.  I told her my apartment!!!

What old computers do you all have?  This is my first old guy with a successful linux install.  I don't have everything configured perfectly because its still really slow.  What OS do you all use for them?

what are the specs on that laptop?

---

### Post by cartisdm on 2008-04-18
> **wolfen69 said:**
> what are the specs on that laptop?

I know this is a complete newb question but.....where the heck can I find the system specs in Xubuntu?!!  I'm sure I'm completely missing it somewhere but I've looked everywhere....

---

### Post by LightB on 2008-04-18
> **anticapitalista said:**
> LightB, If you want to use antiX on a K6 you'll have to use Spartacus version, based on Mepis 6.5.

I already approached that issue on that very post. It is an old version. In fact I wasn't even able to find a non-expired download source. Torrents or actually scrounging one up is besides the point. Point is it's old.

---

### Post by LaRoza on 2008-04-18
I just got [http://esupport.sony.com/US/perl/model-documents.pl?mdl=PCVJ100](http://esupport.sony.com/US/perl/model-documents.pl?mdl=PCVJ100)

For $15 off this forum (community market)

I put in an old hard disk I had, and installed (a bunch of OS's, but settled on) Debian Lenny. 

I still need to get a NIC (ordered) and I have RAM in the mail so I can max this computer out at 256 MB.

---

### Post by jrusso2 on 2008-04-18
This place is like an old computer grave yard.  When I moved I threw out everything less then 233 mhz.

But I still have a two Pentium 233 mmx, A Celeron 400 mhz laptop, and P2 450 mhz, and P3 700 mhz, a dual P3 933 server, a 1 ghz P3 and 1 ghz Athlon, and a P4 2 ghz here among the older stuff.

All of it runs some version of Linux and some are dual boots with various versions of Windows.

---

### Post by cartisdm on 2008-04-19
Woah.....seriously.  Great suggestion on the Puppy.  I had never even heard of it until now.  I downloaded a liveCD of DSL too but didn't really devote too much time to it.  After playing around with wireless for a while I just gave up and bought a USB adapter from Linksys.  Works great and now I have wi-fi.

Thanks guys! This is 100x faster on this old machine!!

---

### Post by init1 on 2008-04-19
I've got an old laptop with 64MB ram and a 8GB hard drive. I've got it running ttylinux and freedos (perfect for playing dungeon crawl :D).

---

### Post by andrewjoy on 2008-04-19
Oldest pc i have hmm

An acorn A3010 with a 12mhz ARM 250 32-bit RISC CPU.

1MB ROM
1MB RAM

No harddrive

I think in admin mode or sumthin you could install apps on the ROM.

Acorn pcs where only sold in the UK( i think they sold a select few modles in germany) , its broken now tho i am looking for a working one that i can play around with bring back the old days oh yeh.

---

### Post by anticapitalista on 2008-04-19
> **LightB said:**
> I already approached that issue on that very post. It is an old version. In fact I wasn't even able to find a non-expired download source. Torrents or actually scrounging one up is besides the point. Point is it's old.

It is old (Ubuntu Dapper repos), but not as old as RedHat9, DSL or even some Puppy Linux iso's.

You can get a download from here:
[http://mirror.cs.vt.edu/pub/MEPIS/antix/old/](http://mirror.cs.vt.edu/pub/MEPIS/antix/old/)
[http://mepis.gabston-howell.org/download/released/AntiX/](http://mepis.gabston-howell.org/download/released/AntiX/)

---

### Post by metallicamaster3 on 2008-04-19
I've gotten Vista installed on a Dual PII 378MHz w/ 64MB RAM.

Now booting... that's a different story xD

---

### Post by Hygelac on 2008-04-19
I have a few old machines.  One is an AMD K6-2 (380MHz) with 192MB RAM and a 4GB hard drive.  Nothing is installed; I just use DSL and Knoppix and such on it, when I need to use it.  I have a PIII (450MHz) too, which I use every day as an alarm clock.

The oldest one I have right now is some kind of 80486 with 12MB RAM and a 325MB drive.  It runs Win95; I haven't completely switched to Linux yet because I can't part with useful programs like Direct Cable Connect...  :lolflag:

---

### Post by mips on 2008-04-21
> **andrewjoy said:**
> 
Acorn pcs where only sold in the UK( i think they sold a select few modles in germany) , its broken now tho i am looking for a working one that i can play around with bring back the old days oh yeh.

They were actually sold across the world in many countries, even over here. They were just not as popular as the Amigas & Atari ST computers. I always wanted an Archie.

---

