---
title: "Trying to fly  a jet  with a learner's permit time to seek help"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by RabidFalcon on 2012-12-31
hello new to ubuntu here .  now that its out in the open a little background on what im trying to do here. i have " dell 518 desktop duo core intel " about 6 months ago Hdd went poof , To make long story short lost all programing " windows vista" ( was'nt impressed anyways) . Ok  getting off track here, replaced Hdd  with 500 gb hard drive and installed puppy linux  as no help in trying to reinstall win vista . then installed  Ubuntu 12.10 i386 from web site .  i have been watching the vid's and reading  on needed software after fresh install . and  tinkering with diff programs to try to run alot of the same games i was playing " w/ win vista" . have been in a fighting battle to get Virtual system to attempt to Dl and install a few games but dont seem to be doing something right . any up-to-date advice on which direction i need to attempt to go and better  advice on which  Virtual install will work best  with my system . will be happy to post any info needed if can figure how to knock it out of the system (lol). thankz in advance for any and everyones time .

---

### Post by JiuJitsu500 on 2012-12-31
VirtualBox, VMWare, or any virtual machine at all will take a pretty massive hit when gaming through it, with ANY host machine that's not a $5,000 beast.

Linux as a desktop to me is the absolute best in every single area I can think of except for one - new, modern games. Linux, BSD, Macintosh, anything but windows will be lightyears behind in this area for the forseeable future. It's simply because M$ has market share around 90% of desktops.

This all means you can run a hell of a computer with Ubuntu latest and greatest with all the latest, fastest, best drivers in the world all optimized to absolute peak performance... but the kernel cannot run windows-specific programs AS efficiently as windows. But, I can play Slender, Modern Warfare 1,  Age of Empires 3, and Elder Scrolls Oblivion perfectly fine without emulation beyond WINE.

For your games, try WINE first. Look it up in the software center, install it, and any .exe you open will act just like a old version of windows and run pretty much like windows - just inside your already-running operating system. It's better than a Virtual Machine for a lot of things.

But, it still takes a hit thanks to the translation from how the windows kernel allocates resources to the linux kernel. Even if that allocation exactly matches, it's the translation that slows it down. Kind of like the lag in a phone call from across the world, wirelessly.

Virtualizing though only allocates your set parameters for the entire machine, which acts exactly like a real machine in every way it can. But, because you cannot physically allocate 100% of your computer (CPU, RAM, Storage, etc...) to a VM, it takes a hit too. Gaming on Linux is difficult because of this, unless it's developed or converted specifically for Linux in a tarball or debian or whatever. Virtualizing is best for things like iTunes or the Zune software when a USB is shared from host to VM, since Linux has no ability to decode a Zune or properly run newer iTunes and work with new iDevices... I know, I keep trying to get my girlfriend's iPad functioning under iTunes through WINE, and my Zune... adly, my VM is how I can do that easily.

In short, you're better off installing Windows 7 to play modern games. I think W8 is atrocious on a desktop, I'm no fan of Apple, and XP runs out of support soon. Vista just plain sucks. Windows 7 is the pinnacle of Windows in my eyes, and pirate bay has plenty of illegal copies, but please don't pirate software... Microsoft NEEDS that money.

I would Dual-Boot. I have Windows 7 on one SSD of mine, and Ubuntu 12.04 on another. I virtualize 2 macs (and own one, it's legal), Free-BSD 9.1, Slacko-Puppy, A highly-customized Ubuntu super-nasty edition experiment I have, and one machine for whatever new ubuntu is available. I've attempted Solaris too, but screw that. I play with all of them and most of the time use WINE to do anything - like rosetta stone - for windows except for play games, then I boot into Windows 7 and blast off with Skyrim with 20 mods or Battlefield 3 or Warfighter. None of which is possible under liux without a machine twice a s powerful as one that could run those games on high video.

---

### Post by Mark Phelps on 2012-12-31
The other problem you're going to have trying to run Windows games in Linux is the lack of hardware-accelerated DirectX11 drivers for Linux.

While open-source drivers are OK for 2D graphics, they don't provide the framerates needed for modern 3D games.

So, if you can't install such restricted drivers, you can't get decent frame rates.

---

### Post by RabidFalcon on 2012-12-31
thankz JiuJitsu500  and Mark Phelps  for your insight and direction . Guess my best option is to look more into getting  an OEM version of " windows vista" back working on HDD then look into a dual boot for Ubuntu. I for see a long hard road, but will get back to where i started eventually, if you happen to see a guy pushing  a jet down express way " it will prob be me" thankz again for your time .):P

---

### Post by JiuJitsu500 on 2013-01-01
True story phelps, but virtualizing can do that. I'm probably aware you know this however. BUT, unless you have an 8-core 3GHz CPU, 4GB of fast video memory, a ton of RAM, and quite fast storage (SSD on host, for example)... AND allocate half of that to a VM with Windows 7 or Vista, even W8... you won't be able to do jack squat with a linux machine or any real VM. That's what I meant in a nutshell I guess :D

Too bad though, I thought the DX guys coded most of their things on a linux machine anyway last I heard. You'd think they'd release some kind of awesome translator to allow full access to the kernel and hardware with the right drivers (if, of course, NVidia and Radeon hopped on board)...

We need more desktop market share... And honestly, I'm doing my part. My girlfriend has been a long-time ubuntu fan now, and quite a few other people I know are quite impressed with it and use it regularly. Games though, for real.... Direct X, drivers, all of it... oh well, I'm fine with what we have :)

Whatever you need too mr. falcon..... I've dual, triple, and quad-booted a whole lot of machines. My experience says install the proprietary OS first, then use a Live environment to shrink the partition, re-format the one you want, make a swap partition (about as much RAM as you have, unless you have a lot of RAM, then you won't need swap), and manually install ubuntu using those created partitions. This way the old bootloader goes away, and GRUB now controls the boot process without manually installing GRUB (also easy, but we can skip a step here). It's all easy with the installer, just ask and I'm sure the forums will be helpful!

You will, though, HAVE to get used to the command line. It can screw your whole life up it seems, but that's part of the fun. Almost everything has a graphic interface now though, most of what you will ever need to do will not require a terminal (command line), but I prefer sometimes to hit a keyboard command and simply type a small, fast command and my password to update my machine or run some things I don't feel like using the mouse for. Or, more powerful tasks requiring it (though very rare)... I still prefer GUI for almost everything, but get comfortable with commands... fraking sudo, apt-get, install, purge, clean, rm, cd, and gksu might be some you'll come to love

---

