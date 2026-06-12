---
title: "Dell latitude d800"
date: 2017-04-03
forum: New to Ubuntu
---

### Post by step290 on 2017-04-03
Hi i want to install lubuntu in my dell latitude d800... should i install an older version or the last one is gonna be ok?

---

### Post by mooreted on 2017-04-03
The system specifications for Lubuntu 16.04 are:

System Requirements
Lubuntu is a good operating system for many old computers, but not for all of them. Some computers have too little horsepower or memory. A rule of thumb is that the computer should not pre-date 2000. The desktop images for lubuntu 16.04 requires a DVD / USB device to write it to, the alternate images are for those with have non-standard setups or Low RAM.

Memory (RAM)

For advanced internet services like Google+, YouTube, Google Docs and Facebook, your computer needs about 1 GB of RAM.

For local programs like LibreOffice and simple browsing habits, your computer needs about 512 MB of RAM. See minimal for systems below that RAM.

Processor (CPU)

The minimum specification for CPU is Pentium 4 or Pentium M or AMD K8.

Older processors are too slow and AMD K7 has problems with flash video.

Graphics chip / card

Nvidia, AMD/ATI/Radeon and Intel work out of the box, or the system can be tweaked to work fairly easily. You can get help at the Ubuntu Forums. With such graphics, or if you don't know, try the current Lubuntu version.

---

### Post by RobGoss on 2017-04-03
> **step290 said:**
> Hi i want to install lubuntu in my dell latitude d800... should i install an older version or the last one is gonna be ok?

That would depend of your system specs you can post then so we may give you the best possible advice

I have a Dell Latitude D610 running Fedora 25 like a champ

---

### Post by RobGoss on 2017-04-03
You can also run the live desktop to see how it performs that will let you know what to expect

---

### Post by mörgæs on 2017-04-04
The only older version of Lubuntu with support is 14.04, and support for this one ends this month. This leaves 16.04.2 and the almost-released 17.04 (beta) as the only realistic options. 

I run Lubuntu on a Latitude D610 with good results so I can't imagine that the 800 has problems.

---

### Post by gordintoronto on 2017-04-04
The specs published by Cnet indicate it should run Ubuntu OK, but very slowly. Lubuntu, Xubuntu or Ubuntu Mate are probably better options.

---

### Post by DuckHook on 2017-04-05
Welcome to the forums, step290

As mörgæs notes, your only real option is 16.04. I would not run anything other than an LTS on this thing.

The D800 was only a 32-bit CPU using the infamous Pentium M, so you will need the 32-bit version of Lubuntu and the forcepae parameter, but it works: [https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

The more debilitating restrictions will be your system RAM (most default configs came with only 512 MB) and the sad video (low-powered GPU w/ max 128MB VRAM, in some configs only 64MB). Mine ran Lubuntu okay on 1GB RAM and 128MB VRAM, but I was lucky to have two spare 512 MB RAM modules lying around and maxed out VRAM version. DDR1 is ancient now and hard to find.

Your mileage will depend on your specs. If your machine is at the low end of the specs, then you may be better off running Puppy, Slitaz or Tiny Core. The best use for such old dogs is to get rid of the GUI altogether and use them as a server. Ubuntu server will run well on this thing especially if you add HDD capacity through the USB ports and use as backup/torrent/dhcp/etc server.

---

### Post by mörgæs on 2017-04-05
Pentium M came in two series and it's likely that the D800 uses the latest of them. If so then forcepae is not necessary, and the install is next, next, next, finish.

By the way, is original poster still here?

---

### Post by DuckHook on 2017-04-06
> **mörgæs said:**
> Pentium M came in two series and it's likely that the D800 uses the latest of them. If so then forcepae is not necessary, and the install is next, next, next, finish.

By the way, is original poster still here?True enough. My model had the older Pentium M and required the forcepae parameter.

If OP has abandoned this thread, I'm sure it's still useful to general searchers and lurkers who may come across it.

---

