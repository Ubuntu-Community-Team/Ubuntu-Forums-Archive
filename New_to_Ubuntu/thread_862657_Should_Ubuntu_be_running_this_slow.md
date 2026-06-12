---
title: "Should Ubuntu be running this slow?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Polish Rifle on 2008-07-17
I recently cleaned out my entire system and installed Ubuntu 8.04 on my Dell Dimension 2350.  Here are the specs:

2.00 Ghz Intel 4 Processor
256 MB of RAM
60 GB Hard Drive


I am fully aware that 256 MB RAM is not a lot and I actually ordered a gig the other day to help speed things up.  But I am VERY surprised with how slow Ubuntu is operating on my system.  It takes me over 5 minutes to install any missing plug-ins on Firefox and any application takes anywhere from 30 seconds to 2 minutes to start.  

I applied some of the popular tweaks to Ubuntu but it doesn't seem to be helping (could of coded them wrong).  Should the RAM bring me up to speed if I'm at 1 GB?

---

### Post by Morpheun on 2008-07-17
You're certainly not going to be running at any real considerable speeds with only 256mb but it should be better than what you described. Perhaps try memtest?

---

### Post by nowshining on 2008-07-17
in a terminal do this:

sudo apt-get install htop
(ur pw won't show as you type)
from there - once installed type htop at the command prompt, is the CPU @100% or so?

Also note that P4's have a tendency to go to 100% quickly - so don't be suprised..

---

### Post by m_ad on 2008-07-17
I recently installed Xubuntu on a very similar Dell computer with only 256mb also. I couldn't even get the Ubuntu Live CD to run, so I had to go with Xubuntu.

---

### Post by Polish Rifle on 2008-07-17
I installed htop and after restarted my computer it showed that I was hovering around 30%.  What I noticed was that 209 out of my 256 MB of RAM were being occupied.  I'm guessing this is the root of the problem.  

I thought about installing Xubuntu, but from a lot of opinions on this message board it sounded like the performance differences didn't vary that much.

---

### Post by someonestolemyname on 2008-07-18
In my experience Xubuntu is much lighter weight than Ubuntu. I got my old P4 128 meg RAM comp to run Xubuntu at a decent speed (It's my headless server now =).

I would try Xubuntu and see if that seems faster. If so, maybe your installation got screwed somehow?

You're missing out on all the fun w/o a gig of ram or more though. 2 gigs makes anything fast.

---

### Post by monolux on 2008-07-18
I think you're trying the wrong OS, use xubuntu its much lighter. I had a ubuntu on 256 ram it was as you described. Then changed to xubuntu much lighter,still a little laggy do.

---

### Post by Jim! on 2008-07-18
Ubuntu is a modern OS, It's not exactly going to fly on 256MB RAM;)

---

### Post by ugm6hr on 2008-07-18
Do you use an integrated graphics on the motherboard?

If so, it is likely some of your 256MB is being used as graphics memory, thus reducing the system RAM below the 'minimum' 256MB.

Xubuntu (XFCE) uses less RAM than Gnome, so will run faster on your system.  When you get the extra RAM, that difference is less evident.

---

### Post by hyper_ch on 2008-07-18
try to run vista on 256mb ram ;)

---

### Post by Drizzel on 2008-07-18
I only have 256mb of ram myself and Ubuntu is running just fine. Its actually faster running faster than xp pro. I have a 666mb swap (autoconfig automagicly sized it that way not me) :). Maybe its the swap, but its fast and responsive. I'm thinking of making the swap 1gb to see if it speeds things up even more.

---

### Post by hansdown on 2008-07-18
> **hyper_ch said:**
> try To Run Vista On 256mb Ram ;)

+100.

---

### Post by cariboo on 2008-07-18
Open a Application-->Accessories-->Terminal and type:

```
free
```

This is the output of free on my computer, I have 2GB ram:

```
             total       used       free     shared    buffers     cached
Mem:       2025292    1805080     220212          0     114928     974756
-/+ buffers/cache:     715396    1309896
Swap:      5662872          0    5662872
```

As you can see I have 1.8GB used 220MB free my swap is 5GB with 0 used. Linux uses ram in a different way than windows and it will use as mucn as it can, even if nothing is running, right now I have 1 terminal open and firefox with 3 tabs. Even with so much ram being used programs open instantly. The only program that seems to take more then 2 seconds to load is Open Office. For more info on Linux memory usage have a look at this link.

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

Jim

---

### Post by ugm6hr on 2008-07-18
> **Drizzel said:**
> I only have 256mb of ram myself and Ubuntu is running just fine... I'm thinking of making the swap 1gb to see if it speeds things up even more.

Probably not.  Optimal swap is generally 1.5-2x RAM.

You can use system monitor to see how much swap is being used.

---

### Post by Canis familiaris on 2008-07-18
You can try Puppy. It will run really fast in your system.

---

### Post by |{urse on 2008-07-18
I have an old POS system running knoppix installed to hdd. It has a Intel Coppermine 850Mhz processor with 64 mb's of EDO ram. It is without a doubt the snappiest linux machine i own. Mind you, It's not going to run Quake wars: Enemy Territory or Compiz-fusion lol but it does it's job ^^

---

### Post by Frenske on 2008-07-18
I have a dual boot machine annd everything in Ubuntu runs faster than in Windows XP. It is probably not a Ubuntu problem you have on your machine. I have 2.6GHz P4 (single) and 128-bit 6600GT video card - not exactly a speed demon either - and everything runs smooth in Ubuntu.
When your 1GB RAM arrives you will notice a considerable speed-up in performance.

If it still does not perform any better there might other issues such a faulty network drivers and you should come back to the forum again.

---

### Post by philinux on 2008-07-18
If you've got a gig coming just stick with it for now.

Once installed you'll notice a big difference.

---

### Post by RyanVanDiemen on 2008-07-18
Exactly, I have 1GB and it runs great (using more xubuntu now but used to have gnome before and everything was great) and I even have slower processor than you.

---

### Post by Polish Rifle on 2008-07-18
I think I will stick with Ubuntu and wait for the gig.  What would I miss out on if I switched to Xubuntu?

I have my computer dual booted and Windows XP runs faster currently (it's bare bones XP though).  I ran the mem test and checked my free ram.  At start up I have 200/256 MB in use.  

I also have a horrible integrated video card.  I have never been huge on gaming or graphics so it does the job, but now I'm weary of it if it's slowing me down.

---

### Post by lisati on 2008-07-18
My laptop has 256Mb RAM, a 1.4GHz Celeron M & a 40Gb HD (currently 30Gb for Ubuntu & its swap partition, 10Gb for XP) - it seems to work well enough with Ubuntu 7.04, even though I had to use the alternate disk for the initial setup.

I use it mainly for email, browsing, and occasionally troubleshooting my home network.

---

### Post by CatKiller on 2008-07-18
Performance in Ubuntu does seem to be memory-limited much more than it is processor-limited. Once you get that extra RAM in there, it'll be fine.

---

### Post by stalkier on 2008-07-18
> **hyper_ch said:**
> try to run vista on 256mb ram ;)

I have actually seen variants designed to run on 256MB. These are hacked OS though so of course they are going to run better. ;)

---

### Post by cjv8888 on 2008-07-18
Xubuntu is sort of boring and with less fun and effects to play with than Ubuntu.
I have one machine with 256 Mb RAM initially and it was also slow and occasionally crashed. It is upgraded now to 550 Mb and runs well. It can even multitask.

---

### Post by Polish Rifle on 2008-07-18
> **lisati said:**
> My laptop has 256Mb RAM, a 1.4GHz Celeron M & a 40Gb HD (currently 30Gb for Ubuntu & its swap partition, 10Gb for XP) - it seems to work well enough with Ubuntu 7.04, even though I had to use the alternate disk for the initial setup.

My computer seemed to run fine on 7.04, but after daily updates and eventually the upgrade it slowed down significantly.  I also used the alternate-text.  I think you guys are right though.  The RAM is the main factor and will make a difference.  I hope all will be well with a gig.  Should be here on Monday.

---

### Post by Polish Rifle on 2008-07-22
Installed the gig of RAM today.  For those who are just joining us on this thread, here are my computer's specs:

[LIST]
[*]2.00 Ghz Processor
[*]256 MB of RAM (originally)
[*]60 GB Hard Drive
[/LIST]

Put in the RAM about 10 minutes ago and so far everything flies.  I expected the Internet load time to be faster but I think that is just a Firefox issue (switching to Opera 9.5 anyway).  Boot time was about the same but switching between windows and opening programs is pretty fast.  Not the "blink of an eye" fast, but I'm pretty satisfied.  

Hopefully it remains this speedy and I'll report how the comp does with heavier stuff.

---

### Post by Polish Rifle on 2008-08-02
Final Update:

I don't think I have to say much about this.  Upgrading my RAM 4fold has really done the job.  I haven't had any loading problems and I even have enough resources to run some effects.  

With RAM being cheap right now I encourage everybody to get at least a gig in their system if they are gonna use Ubuntu full time.

---

### Post by Joeb454 on 2008-08-02
If you're using a standard Ubuntu installation, 1GB would make it run quick.

Xubuntu however would most likely run fine with 512Mb

---

### Post by tad1073 on 2008-08-02
Ubuntu runs fine for me. See Sig. for specs.

---

### Post by ugm6hr on 2008-08-03
> **Joeb454 said:**
> Xubuntu however would most likely run fine with 512Mb

Or even 256MB with shared graphics (as I have on a work computer - no media playing though)...

---

### Post by Mazlaghan on 2008-12-18
Hiya,

Had a similiar problem with the speed. Running Ubuntu on a Dell D400. Had 256mb RAM to start and noticed that after each update my machine got slower and slooower and slooooower.

Upgrading RAM is the solution. Got a cool 1GB Module upgrade for about $40.- and Ubuntu is flying fast now! If you are thinking of upgrading to a newer machine think again. 

With a 1GB Ram upgrade Ubuntu runs fast.

I will keep this notebook for another few years

:)

---

### Post by maestrobwh1 on 2008-12-29
Or even XP for that matter... 

I do notice that Firefox 3.x is much slower than any other browser I have used with any Ubuntu since Dapper... and my machines have been getting faster, so I don't know what is up with that.

I can run FF 3 in Arch, and I don't see the lag at all.

---

### Post by cham93086 on 2009-01-07
I recently switched from Ubuntu to Xubuntu for performance reasons, and there is a great improvement.  the only thing your missing out on in Xubuntu is some of the smoothness in graphics--like the difference between Vista and XP.  As far as interface goes, I've found Xubuntu to be slightly less idiot friendly, but, I'm adapting well (although still an idiot).  if you want to try it out, just install the package:

```
$ sudo apt-get install xfce
```

then in the login screen, you can select your session--pick XFCE.  

if you decide you like it, you can then tweak XFCE to be a little faster.  if you don't like it, you can uninstall it.

---

### Post by ugm6hr on 2009-01-07
> **cham93086 said:**
> ```
$ sudo apt-get install xfce**4**
```


A small error there.

---

### Post by dadozgb on 2009-01-07
How fast it can run depends on a hardware and individual setup. I run it on geforce 8400 with 2 gb ram with compiz, preloaded oofice, emerald and cairo dock, mta server,.. and it uses around 400 mb ram. You can always switch to some less hardware consuption win manager like icewm.

---

