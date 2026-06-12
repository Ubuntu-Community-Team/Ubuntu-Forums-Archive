---
title: "Software installation - more obscure applications. some not so obscure"
date: 2023-04-25
forum: New to Ubuntu
---

### Post by ajohnl on 2023-04-25
I'm thinking of changing distro to Ubuntu. One of the reasons for using my current one was software searches. I could use function or name. Worked well for years and could generally get stable packages. Some applications were not officially supported but were well maintained in the distro's repo's. Just had to find the right one.

So I upgrade and as an example quickly find I can only get an experimental version of The  Gimp. Install it and have update errors a few days later. I've run Ubuntu on a USB stick and the built in search didn't produce any results for some apps i use pretty regularly. Another more obscure one. I have a PC USB oscilloscope that runs under TK TCL Does Ubuntu offer any easy solution to this sort of problem? Or is it apt get etc for all and are they likely to be stable?

I sometime compile from source - is there a simple way of loading all that is likely to be needed. C compiler and various libraries? If any other libs are needed I only take them from stable sources ;) usually causes problems if I don't.

Unusual but have changed the kernel in the past. That needs the headers. Not much of a problem really as would be asking about this aspect on here.

As my PC is a tool I would be running long term releases. That usually means that the latest greatest versions of apps can not be installed as they come out. That's ok but what about stability?

---

### Post by poorguy on 2023-04-25
> **ajohnl said:**
>  I have a PC USB oscilloscope that runs under TK TCL Does Ubuntu offer any easy solution to this sort of problem? Or is it apt get etc for all and are they likely to be stable?


I'm using Lubuntu 22.04 and these two packages are available from the repos using the default Package Manager.

Can't say if they are available in Ubuntu 22.04 although I would think they would be,  Lubuntu 22.04 is an official Ubuntu flavor.

I've never used either one as I have several analog oscilloscopes.

 **Xoscope **
Xoscope is a oscilloscope using input from a sound card or EsounD server and/or a COMEDI hardware. Includes 8 signal displays, variable time scale, math, memory, measurements, and file save/load.


[https://xoscope.sourceforge.net/](https://xoscope.sourceforge.net/)

[URL="https://manpages.ubuntu.com/manpages/bionic/man1/xoscope.1.html"]https://manpages.ubuntu.com/manpages/bionic/man1/xoscope.1.html
[/URL]

**PulseView** PulseView is a GUI for sigrok that supports logic analyzers, oscilloscopes, and MSOs.

 It can acquire samples from a supported device and display them, load and display captures from existing sigrok *.sr files, as well as run protocol decoders and display their annotations.

[https://www.sigrok.org/wiki/Downloads](https://www.sigrok.org/wiki/Downloads)

[https://sigrok.org/wiki/Downloads#Binaries_and_distribution_packages](https://sigrok.org/wiki/Downloads#Binaries_and_distribution_packages)

---

### Post by Impavidus on 2023-04-25
Ubuntu 22.04 has Gimp 2.10 in the official repositories and it appears to work fine. GCC and various libraries with header files are in the repositories; just look for libsomething-dev. Undoubtedly many libraries aren't in the repositories, but I've never needed one of those. If you want to know what version of some software is available from the official repositories of a particular Ubuntu release, have a look at [https://packages.ubuntu.com/](https://packages.ubuntu.com/).

---

### Post by ajohnl on 2023-04-25
> **Impavidus said:**
> Ubuntu 22.04 has Gimp 2.10 in the official repositories and it appears to work fine. GCC and various libraries with header files are in the repositories; just look for libsomething-dev. Undoubtedly many libraries aren't in the repositories, but I've never needed one of those. If you want to know what version of some software is available from the official repositories of a particular Ubuntu release, have a look at [https://packages.ubuntu.com/](https://packages.ubuntu.com/).

Thanks. I tried looking for Viewnor and also TK. No problem or on a plotting package so looks promising, I used the 22.04 repo. I wasn't sure how this aspect was handled.

Wine doesn't look too good but the only win package I will need to run should be ok on the version that is available. WineHQ will sometimes help when packages wont run but only if the latest version is being used, That is currently version 8.01.

Out of interest I looked at GIMP versions. They are using flatpack installations. Sounds like it downloads an entire container so runs on all distro's. It also looks after updates. There appears to be an increase in this sort of approach. ;) Flatpack is available for Ubuntu but not in the repo.

Oscilloscopes - the USB scope I have is way more capable than sound card based ones, Those do have applications in the audio area  with certain packages. One of those is written in Java so not a problem - ;) Other that it needs to be Java and not the OS equivalent. However a 24bit range covering nearly 120db on a decent card.

---

### Post by monkeybrain20122 on 2023-04-25
You can get the flatpak [https://www.gimp.org/downloads/](https://www.gimp.org/downloads/)

Or you can compile from source, which I did. See screenshot

Some dependencies are hard to hunt down but they are optional, mostly python2 stuffs and for help browser (webkit), also see [https://www.linuxfromscratch.org/blfs/view/svn/xsoft/gimp.html](https://www.linuxfromscratch.org/blfs/view/svn/xsoft/gimp.html)

---

### Post by BBQdave on 2023-04-25
> **ajohnl said:**
> As my PC is a tool I would be running long term releases. That usually means that the latest greatest versions of apps can not be installed as they come out. That's ok but what about stability?

I am using Ubuntu 22.04LTS. I installed with minimal applications, no games and such. I added applications with Snap-store, built in Ubuntu (Gnome) Software. I have LibreOffice, Darktable and Gimp - all *snaps* and the most recent stable version of those applications.

I would offer you can have the best of both worlds with Ubuntu LTS and current applications :)

---

### Post by ajohnl on 2023-04-26
For photography I use DispCal on the monitor. Processing, GIMP, Rawtherapee and Fotoxx.  GIMP often gets used for polishing snapshots a bit usually taken in poor conditions and for layer work. . I don't think there will be a problem installing any of those or other packages I use regularly. I do think flatpack like services are useful. For instance dev versions may be available and no harm in installing them. Also sometimes distro packages lag a long way behind latest  releases. These types of installation started appearing some time ago.

Thanks all. I have feel for how this area works now. The question arose as I ran Ubuntu from a USB stick and used the desktop search for certain packages with no results.So this just leaves one question really, Can these repo's be added to that search. My impression was that the desktop search offers a sort of one click install? I'm not adverse to  using the console but do avoid it when ever I can. I just learn the few commands I need. If others are needed I use google to find them and usually promptly forget them when the need passes.

LOL I'll miss KDE after 25+years of use. Could be 30 not sure.

---

### Post by ajgreeny on 2023-04-26
If you're prepared for potential instability and feel you can trust the creator of this ppa you can get the most recent version, 2.10.34 from [https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/gimp-test/+build/25619773](https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/gimp-test/+build/25619773)

I have not tried it so do not know how different it is from the current 2.10.30 build already available in the universe repos nor what possible problems there might be.

---

### Post by Impavidus on 2023-04-26
> **ajohnl said:**
> LOL I'll miss KDE after 25+years of use. Could be 30 not sure.
There's Kubuntu too, which is Ubuntu with KDE. It has the same repositories and the same software available for installation, just a different set of defaults. And only 3 years of support for LTS releases for the stuff not in the main Ubuntu repository.

---

### Post by ajohnl on 2023-04-27
I will be happy with the official releases I can get. Taking GIMP quick work on snapshots just uses it's basic functions. Usually levels, size reduction and sharpening. More detailed work might involve layers and masks etc plus it's various brushes. Then some specific facilities from what could be called GIMPS own repo. One for instance decomposes a shot into layers based on levels of detail. It might be used to enhance some one face to reduce signs of wrinkles or smooth it out etc but can also be used to enhance certain levels of detail. This link covers face enhancement but it can be used for all sorts of things.
[https://patdavid.net/2011/12/getting-around-in-gimp-skin-retouching/](https://patdavid.net/2011/12/getting-around-in-gimp-skin-retouching/)

I could use other package I use for snapshots but find GIMP convenient.

---

### Post by ajohnl on 2023-04-27
Maybe Kubuntu but I am a little tiered of KDE trying to catalogue everything I do and turning off two auto search feature that are built in. Certain applications may turn them back on again. When active I find them more of a hindrance than a help but haven't enabled them for a long time now. For file searches I am inclined to use Linux's own that has been around for ever via catfish. A part file name finds all related pretty quickly but the database needs updating to find newly added files. That doesn't take long either.

I fell out with the KDE arrangement when it popped up part of pdf and other similar I had been reading and also when I realised it was always crawling slowly around my disks to produce an index. A sad aspect was that I was using windows at work when they went in this sort of direction. They warned that it might impact performance however it was possible to build the initial index quickly as a separate operation. Once done no signs of it running this at all. I'd have to say windows in this area was better.

---

