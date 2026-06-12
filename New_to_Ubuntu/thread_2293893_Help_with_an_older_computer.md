---
title: "Help with an older computer"
date: 2015-09-08
forum: New to Ubuntu
---

### Post by bluebaron2 on 2015-09-08
So before reading, I know this question has been asked a billion times around the forums so I apologize. But this is my issue:


I have a very old desktop PC, which is basically very outdated. I remember it was purchased around 2004, and it served me well throughout the years. I don't use it anymore at all, I mainly use my smartphone, tablet or laptop. But instead of the PC just sitting there and dusting, I wanted to put life into it. It runs Windows XP well, but I wish to change it to a Linux distro. I tried many of the versions suggested by other people, Lubuntu, Xubuntu, LXLE, Mint, Crunchbag Linux etc. (Yes both Ubuntu and Debian.) My computer doesn't run well with them... I always thought Linux is lighter than XP but nevermind. 

So yesterday I installed Edubuntu 7.04 (I had an old CD and I thought why not.) It runs perfectly, no lag, isn't sluggish and there aren't any graphical glitches. But the downside of all it, is the lack of support and outdated applications. So, I'm here asking for suggestions on which distro to try? My computer has the following specs: A very old Celeron 1.7 GHz (Single core), 512MB of RAM and an ATI Radeon 9250. (I tried both Puppy and DSL, but they aren't good.)
[I]
NOTES: [/I]
[LIST]
[*]You can suggest any of the distros than I tried, but with some tips on how to make them run faster. (Like tune down visual effects.)
[*]The thing with with those distros, especially Lubuntu and LXLE is that they run good on terms with speed and performance - but they seem to get bugged graphically. I heard that older ATI cards aren't supported very well, so that may be the reason. (Light blue and black vertical lines appear on some elements as the bottom bar and windows)
[/LIST]

Any help is greatly appreciated! :)

---

### Post by grahammechanical on 2015-09-08
Your expectations are limited by the lack of RAM and by the lack of capability of the video adapter.

Newer proprietary video drivers often drop support for older video adapters. Nvidia no longer supports my Nvidia adapter. I can no longer use the latest proprietary video drivers.

When I install Ubuntu & the flavours of Ubuntu I do not tick the box "Install third party software." In this way I avoid using a proprietary video driver and use the open source video driver. I can still install a proprietary video driver but it has to be an older version (legacy).

My machine has twice the RAM and a video adapter that has 1 GB of its own memory. I think it is the 1 GB of video memory that gives me a good visual experience even with the very latest versions of Kubuntu and Ubuntu/Unity.

Regards.

---

### Post by mastablasta on 2015-09-08
> **bluebaron2 said:**
> [I]
NOTES: [/I]
[LIST]
[*]You can suggest any of the distros than I tried, but with some tips on how to make them run faster. (Like tune down visual effects.)
[*]The thing with with those distros, especially Lubuntu and LXLE is that they run good on terms with speed and performance - but they seem to get bugged graphically. I heard that older ATI cards aren't supported very well, so that may be the reason. (Light blue and black vertical lines appear on some elements as the bottom bar and windows)
[/LIST]



there are multiple issues with that PC. Celeron, ATI and RAM.

The ATi card i supported but will use CPU many times. 

I installed Kubuntu with low fat settings package = effects turned off (not sure if it was 12.04 or 14.04, but I think it's 14.04) on Athlon 64 3200+ Single core 2,4 Ghz, 1 GB ram and Radeon 9200 128 MB. this is what I get - computer performs well on desktop tasks but will fail at any games. On windows XP with proper drivers it will run the likes of Morrowind and similar games from that day well. But in Linux all the acceleration is done by CPU and CPU has only one core so it really can't run any games well. not even older ones. maybe some strategy games would work. for desktop and browsing it works OK. Issue is the driver. ATI dropped support for the card and opensource drivers are what they are. not much is happening on the older cards. these seem to be half supported.

in your case - how about installing this and then build form there on: 
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


If IceWM works ok have a look at AntiX. If you are ok with something more spartan try ToriOS or simple but still nice Bodhi

Another option might be Debian with LXDE or the old CentOS if you have the time for it.


I have the old Chrunchbang XFCE/Debian (I think distro is now sadly abandoned) running on 1,2 Ghz Celeron, 256MB ram of which 32 MB is reserved for the GPU. desktop apps ran, you tube ran (lowest setting). so it is doable the question is what you get from it.

---

### Post by Mike_Walsh on 2015-09-08
Hi, bluebaron2. And 'Welcome' to the Forums.

Hmm. You say you don't like Puppy? What don't you like **about** it?

I'm genuinely interested here, because alongside my main 2005 Compaq desktop PC (which isn't even recognisable anymore, compared to how it was when new.....it's been **that **heavily upgraded over the years!), I have an elderly Dell laptop, from 2002.....an original Inspiron 1100. Built like a brick outhouse, and just as solid. It originally ran a 2.2 GHz single-core Celeron, with 128 MB of RAM. Even XP, which it came with, was....shall we say, 'leisurely'. *coughs*

(That's a kind way of putting it..!)

In recent months, I've uprated the Celeron to a 2.6 GHz Pentium IV, and the RAM to its supported max of 1 GB. Not a lot by today's standards, I know. I finally bid XP 'adieu' last year, when EOL hit. She now dual-boots Xubuntu 14.04.2 LTS.....and Puppy Linux; the current 'flagship' release, Tahrpup 6.0 (which is based on Ubuntu's 'Trusty', anyway).

Much as I like Xubuntu, I find myself using Tahrpup way more of the time, simply because it's **so** damn responsive. Slick, nippy, and very smooth. Sure, I accept that Puppy is definitely something of an acquired taste.....but as has been stated on these forums so many times, 'use whatever OS and/or desktop works for you'. I'll go along with that.

(And, like all Linux distros, Puppy is infinitely customizable; you can definitely 'make it your own'.) :)

Puppy just 'works' for me. And the old Dell is still happily leading a productive life. C'est la vie...


Regards,

Mike. ;)

---

### Post by bluebaron2 on 2015-09-08
Thank you all for your quick and helpful responses. 

I know this PC is very old, but I don't need it for 3D acceleration. It will be used mostly by my little brother to watch YouTube videos, paint, DVDs and listen to some music. I'm downloading Lubuntu right now, and I will attempt to install it again and optimize it.

---

### Post by SeijiSensei on 2015-09-08
Increasing the memory to 1 GB or 2 GB would make an enormous difference.

---

### Post by chemist931 on 2015-09-12
I have a desktop that came with Windows XP in 2005. Similar graphics card, 512 MB RAM, and a terrible processor.  It runs Ubuntu slowly (faster than my 2014 laptop does with Windows 10!!!), and I bet with Xubuntu it would be great.  I don't really see how a computer of yours would not be usable with Xubuntu and maybe the Gnome desktop.  The problem with upgrading the RAM is that the desktop probably only takes DDR2 RAM, and it might be hard to find RAM like that with the right pin configuration.  Even then, the motherboard might not take more than a few GB of RAM.  Wipe everything on your hard drive one way or another, and start afresh with Xubuntu.

---

### Post by sudodus on 2015-09-12
- Does that computer boot from USB? (I have a Dell tower from January 2004, and it boots happily from USB.)

- Maybe you can get second-hand (used) RAM from a computer of the same age. 1 GB RAM is *much* better than 512 MB RAM. The operating system might run, but many application programs today will need more RAM, and cause swapping, which makes the computer lag seriously, if you have too little RAM.

- The old graphics is probably supported better by an older (but still supported) operating system. The oldest version of the Ubuntu family is 12.04 LTS. ToriOS is a re-spin based on this version. There are also versions of Bento, Bodhi and LXLE, that are based on it.


I would recommend ToriOS which is ultra-light. You can get via these links. The current daily built iso-file is quite experimental, but there is an older beta iso-file and an OEM version (available as a compressed image file), that are more stable.

[The official ToriOS website](http://torios.net)

[url=https://drive.google.com/folderview?id=0BzX-18u3W1sQSGRuYUQzZEdId0k&usp=sharing
]A temporary web-site uploaded by me[/url]

Other good candidates are Wary Puppy and TahrPup (that are recommended in earlier posts).

Particularly if you want to play video (youtube), you must select a very light desktop environment, or maybe only a plain window manager without any bells and whistles, for example jwm, fluxbox, openbox.

See the following link to check how much RAM an idle system is using. ToriOS is running idle around 90 MB RAM.

[9w/RAM and disk usage tests with Trusty non-pae](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

Whatever you download, check it with md5sum.

---

### Post by kurt18947 on 2015-09-13
> **SeijiSensei said:**
> Increasing the memory to 1 GB or 2 GB would make an enormous difference.

That is my thought as well. I've purchased RAM off Ebay with good success. There are resources to help with purchasing the correct stuff - here's one:

[http://www.kingston.com/us/memory/upgrades?ktc_campaign=US_Kingston_DRAM_Shop&gclid=CLbwprKp9McCFceQHwodtgUM9g](http://www.kingston.com/us/memory/upgrades?ktc_campaign=US_Kingston_DRAM_Shop&gclid=CLbwprKp9McCFceQHwodtgUM9g)

Here's another - I use the advisor tool.

[https://www.crucial.com/](https://www.crucial.com/)

Once you know the correct type you can go shopping.  A very cursory search on Ebay finds 2 1 GB. desktop sticks for <$10 U.S. When I've purchased DRAM on Ebay, I always make sure there's a return option. My first action after receiving it is to remove any currently installed memory in the intended machine, plug in the newly arrived DRAM and run memtest86 for a few hours. Memtest is present on most live CDs/USBs and runs from the CD/USB, no installation required. If memtest runs with no errors, I reboot or install the desired O.S.

I have an HP desktop that shipped with Windows ME:shock:. Blistering 667 Mhz. Celeron (the original one) and 64 Meg. RAM. It would boot puppy but wouldn't do anything more. I purchased 512 MB. PC-100 RAM, a vintage Nvidia PCI video card and ethernet card. I think my total investment was around $20. It's quite slow but functional as a desktop machine but it performs yeoman service as a torrent server for various deserving linux distros.

---

### Post by Mike_Walsh on 2015-09-13
+1 with regards to extra RAM.

chemist931 makes it sound as though even DDR2 RAM is prehistoric.....and rarer than hen's teeth. Not quite the case.....yet!

Both my machines (sorry, all **three** of my machines....I keep forgetting the 'new' acquisition!) are of a vintage (2003-5) where DDR1 RAM was the highest-spec available. Here in the UK, it's still relatively easy to purchase the stuff new.....both SoDIMMs **and **DIMMs. I've just purchased 2 x 1 GB of DDRI @PC-3200 in the 200-pin SoDIMM form factor, for a 12 yr old Dell laptop.

You just need to shop around. There's still plenty of the stuff out there. It is, however, becoming more expensive, due to the fact that there's no longer much call for it.....and suppliers aren't shifting stock so quickly.


Regards,

Mike. ;)

---

### Post by Geoffrey_Arndt on 2015-09-13
With 512 mg of ram, and the older gen. celeron, a distro that would be functional and fast is **Antix** . . . based on debian test branch.    

The issue is not so much the distro (or Linux, which is just the kernel), but what desktop is being used.    One of the default desktops for Antix is Fluxbox - - which runs very fast with 512.   It's a rather "spartan" looking desktop, but does the job.

[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

---

### Post by Sweet_Baby_Jamie on 2015-09-15
I have a really old relic of a hand-me-down from my parents with the same specs as yours.  A Dell desktop that they bought in 2000.  It runs **LXLE** 12.04 just fine.  The newer one, 14.04 is a little sluggish on it, but 12.04 is great.  They both have the same support life, so if 14.04 is giving you trouble you can try 12.04.  All up-to-date stuff and it's Ubuntu at it's core so you get all the great simplicity of trouble-free installation and updating.

---

