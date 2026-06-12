---
title: "Howto use Creative Zen Mirco in Hoary"
date: 2005-05-07
forum: Outdated Tutorials &amp; Tips
---

### Post by tora201 on 2005-05-07
After lots of searching, I finally got it going. Here is a short and very simple  How To. Believe me, you wife will thank you for having the time to spend more time with your family. ;-) That is until my next project....

1)Importan: First, **DO NOT** install gnomad2 from the Ubuntu depositories, instead go to:

[http://packages.debian.org/unstable/x11/gnomad2](http://packages.debian.org/unstable/x11/gnomad2)

Get the i386 version, download, and install from a terminal:

sudo dpkg -i gnomad2_2.6.3-1_i386.deb

You may have other dependencies that need to be installed before it will let you install gnomad. If that is the case, install the files as needed. I had to install libnjb4_2.0-1_i386.deb

(which is available from: [http://packages.debian.org/unstable/libs/libnjb4](http://packages.debian.org/unstable/libs/libnjb4))

Note: maybe the depositories could be updated with the relevant files?


2) Once you have gnomad2 installed, just connect your Zen, fire up gnomad from a terminal:  :grin: sudo gnomad2

You can then make an icon for it in your menu, but unfortunately you will need to run it as as a superuser: Since I use Xfce, I just made a launcher in the menu, and in the Command line put: gksudo gnomad2

That should be it! (Unless somebody can CLEARLY tell me how to solve the problem of the thing absolutely wanting to run as a superuser! -- not that I really care anymore, but it would be nice if it could be solved in a simple way)
:wink:

Edit: Apparently  this works for most other Creative Jukebox players etc. Just remember to get the latest files, as described above.


A few sources:
[http://ubuntuforums.org/archive/index.php/t-2700.html](http://ubuntuforums.org/archive/index.php/t-2700.html)
[http://blog.clurrcache.me.uk/index.php/archives/2004/12/15/zens-on-linux/](http://blog.clurrcache.me.uk/index.php/archives/2004/12/15/zens-on-linux/)
[http://www.nomadness.net/modules.php?name=Forums&file=viewforum&f=2](http://www.nomadness.net/modules.php?name=Forums&file=viewforum&f=2)

---

### Post by poofyhairguy on 2005-05-13
Great howto. Glad I dug it out.

---

### Post by xalphas on 2005-05-14
I followed the steps and thank you i had success opening gnomad2 as root. I don't know if this is a problem with my zen xtra but in gnomad i can't see my playlists. When it opens it scans all the songs.. that's ok.. but couldn't transfer any song and see my playlist. 

I rebuild the library of nomad by resetting and holding the play button. but no difference. I was not able to use my player for 2 weeks. If someone knows my issue and write something here i would be really glad. 

thx.

---

### Post by tora201 on 2005-05-14
[QUOTE=xalphas]I followed the steps and thank you i had success opening gnomad2 as root. I don't know if this is a problem with my zen xtra but in gnomad i can't see my playlists. When it opens it scans all the songs.. that's ok.. but couldn't transfer any song and see my playlist. 

thx.[/QUOTE]

hmm... it works for me! Here is list of players that are supported by Gnomad2:

Creative Nomad Jukebox 1 (aka D.A.P.)
Creative Nomad Jukebox 2
Creative Nomad Jukebox 3
Creative Nomad Jukebox Zen
Creative Nomad Jukebox Zen USB 2.0
Creative Nomad Jukebox Zen NX
Creative Nomad Jukebox Zen Xtra
Dell Digital Jukebox ("Dell DJ")
Creative Nomad Jukebox Zen Touch
Creative Nomad Jukebox Zen Micro
(Without the 2.x MTP/PlaysForSure upgrade!)
Second Generation Dell DJ
(Without the MTP/PlaysForSure upgrade!)
Dell Pocket DJ
(Without the MTP/PlaysForSure upgrade!)

Yours seems to be there.... so I have no idea why it does not work for you. What you could do is post your problem in the Gnomad forums and see if that helps. I am pretty sure it is a problem with your particular model, and not the instructions I gave here. Try the following forum and see if any others have having similar problems: 

[http://www.nomadness.net/modules.php?name=Forums&file=viewforum&f=4](http://www.nomadness.net/modules.php?name=Forums&file=viewforum&f=4)

Best of luck! If you find success, please do post your results here as to help others who might be in a similar situation.

---

### Post by Josh M on 2005-05-14
I installed Gnomad2 a while back by apt. It works great with my Creative Zen Touch. I have to run this program as root for it to recognize and scan the mp3 player.

---

### Post by xalphas on 2005-05-14
@Tora201 thnx for the reply and effort. My Player is in the list. Zen Xtra 60Gb. I was using it 6 months ago with FC3. Then with warty with no problem. And also with Hoary 1 month ago.I reinstalled Hoary and started to have this problem. 

Today i did a try again. Your guide is helpful and it installs those packages for njb and gnomad. Np. Today i connected again to my jukebox and can transfer files from jukebox to pc. But still can't transfer from pc to jukebox. I've already left a post to nomadness but nothing.. 

Anyway i will work on this in my free times. Hope i figure it out. Again thank you for writing.

---

### Post by vassie on 2005-05-19
Help
I cannot install libnjb4 as it depends on a newer libc6, thus meaning I cannot install the latest gnomad2
Someone please help, as there is no point in me using Ubuntu if I cannot copy music to my Zen Micro
Ben

---

### Post by Joey911 on 2005-06-01
Yes - I had this problem, too. But you can download the files you need from the server mentionnend in the first post.
There you'll get the libc6 and the libusb (I needed it too)

Then you install these files and after that you can install the remaining files and use gnomad2

It works

---

### Post by Joey911 on 2005-06-01
But be careful - Now I have problems with installing other programs.. 

I hope I'll find a solution for it

---

### Post by dodongo on 2005-06-07
> **tora201]After lots of searching, I finally got it going. Here is a short and very simple  How To. Believe me, you wife will thank you for having the time to spend more time with your family.  said:**
> http://packages.debian.org/unstable/x11/gnomad2[/url]

Get the i386 version, download, and install from a terminal:

sudo dpkg -i gnomad2_2.6.3-1_i386.deb

You may have other dependencies that need to be installed before it will let you install gnomad. If that is the case, install the files as needed. I had to install libnjb4_2.0-1_i386.deb

(which is available from: [http://packages.debian.org/unstable/libs/libnjb4](http://packages.debian.org/unstable/libs/libnjb4))

Note: maybe the depositories could be updated with the relevant files?


2) Once you have gnomad2 installed, just connect your Zen, fire up gnomad from a terminal:  :grin: sudo gnomad2

You can then make an icon for it in your menu, but unfortunately you will need to run it as as a superuser: Since I use Xfce, I just made a launcher in the menu, and in the Command line put: gksudo gnomad2

That should be it! (Unless somebody can CLEARLY tell me how to solve the problem of the thing absolutely wanting to run as a superuser! -- not that I really care anymore, but it would be nice if it could be solved in a simple way)
:wink:

Edit: Apparently  this works for most other Creative Jukebox players etc. Just remember to get the latest files, as described above.


A few sources:
[http://ubuntuforums.org/archive/index.php/t-2700.html](http://ubuntuforums.org/archive/index.php/t-2700.html)
[http://blog.clurrcache.me.uk/index.php/archives/2004/12/15/zens-on-linux/](http://blog.clurrcache.me.uk/index.php/archives/2004/12/15/zens-on-linux/)
[http://www.nomadness.net/modules.php?name=Forums&file=viewforum&f=2](http://www.nomadness.net/modules.php?name=Forums&file=viewforum&f=2)
 There is an issue with libnjb I've just discovered... what I think you've bumped into with the "you have to run this program as root" issue.

The problem is that there's a hotplug.sh script that comes with the libnjb package that (may | does) not get run when installing the .deb package.  The script chmod's the USB devices for user-level access.  Is this a security issue?  I don't know... but there's an easy workaround for it.  I wrote a quick shell script:

> #!/bin/bash

gksudo "chmod -R a+w /proc/bus/usb"
gnomad2

This is the workaround suggested in the libnjb documentation.  There, they suggest you have to run the chmod line every time you reconnect the jukebox to the USB bus.  However, by using this script, you get the chmodding automatically (still have to type your password), and then runs gnomad2 as a normal user.

To get this to work, copy the above text into a file named [whatever].sh, then run chmod +x on that file.

---

### Post by mstralka on 2005-06-17
I just followed these directions and gnomad2 works great.  The problem is, installing these non-Ubuntu packages broke a ton of other packages on my system and now, Synaptic reports 3 broken packages and  wants to remove a ton of packages.  I can't figure out how to remove gnomad2 without removing all of these packages.  Does anyone know how I can forcefully remove gnomad2 without breaking my system?

```

mstralka@ubuntu:~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  build-essential dbus-glib-1-dev g++ g++-3.3 libart-2.0-dev libatk1.0-dev
  libaudiofile-dev libbonobo2-dev libbonoboui2-dev libc6-dev libc6-i686
  libdbus-cil libesd0-dev libexpat1-dev libflac-dev libfontconfig1-dev
  libfreetype6-dev libgconf2-dev libgcrypt11-dev libglade2-dev libglib2.0-dev
  libgnome2-dev libgnomecanvas2-dev libgnomeui-dev libgnomevfs2-dev
  libgnutls11-dev libgpg-error-dev libgtk2.0-dev libice-dev libid3tag0-dev
  libidl-dev libjpeg62-dev libmono-dev libmusicbrainz4-dev libncurses5-dev
  libogg-dev liborbit2-dev libpango1.0-dev libpopt-dev libsm-dev
  libstdc++5-3.3-dev libtunepimp2-dev libvorbis-dev libx11-dev libxext-dev
  libxft-dev libxi-dev libxml2-dev libxrender-dev locales lsb nvidia-glx-dev
  ubuntu-base xlibmesa-gl-dev xlibmesa-glu-dev zlib1g-dev
0 upgraded, 0 newly installed, 56 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 118MB disk space will be freed.
Do you want to continue [Y/n]?

```

Thanks

---

### Post by dodongo on 2005-06-17
[QUOTE=mstralka]I just followed these directions and gnomad2 works great.  The problem is, installing these non-Ubuntu packages broke a ton of other packages on my system and now, Synaptic reports 3 broken packages and  wants to remove a ton of packages.  I can't figure out how to remove gnomad2 without removing all of these packages.  Does anyone know how I can forcefully remove gnomad2 without breaking my system?

```

mstralka@ubuntu:~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  build-essential dbus-glib-1-dev g++ g++-3.3 libart-2.0-dev libatk1.0-dev
  libaudiofile-dev libbonobo2-dev libbonoboui2-dev libc6-dev libc6-i686
  libdbus-cil libesd0-dev libexpat1-dev libflac-dev libfontconfig1-dev
  libfreetype6-dev libgconf2-dev libgcrypt11-dev libglade2-dev libglib2.0-dev
  libgnome2-dev libgnomecanvas2-dev libgnomeui-dev libgnomevfs2-dev
  libgnutls11-dev libgpg-error-dev libgtk2.0-dev libice-dev libid3tag0-dev
  libidl-dev libjpeg62-dev libmono-dev libmusicbrainz4-dev libncurses5-dev
  libogg-dev liborbit2-dev libpango1.0-dev libpopt-dev libsm-dev
  libstdc++5-3.3-dev libtunepimp2-dev libvorbis-dev libx11-dev libxext-dev
  libxft-dev libxi-dev libxml2-dev libxrender-dev locales lsb nvidia-glx-dev
  ubuntu-base xlibmesa-gl-dev xlibmesa-glu-dev zlib1g-dev
0 upgraded, 0 newly installed, 56 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 118MB disk space will be freed.
Do you want to continue [Y/n]?

```

Thanks[/QUOTE]
 It looks like you're only removing -dev packages (in general, not necessary for system operation unless you're compiling stuff yourself) and the ubuntu-base, which is a meta-package specifying what other packages constitute ubuntu-base, along with some other meta-packages.

As far as I can tell, allowing apt-get to do what it wants here isn't going to hurt a thing.  You may have to reinstall the -dev packages if you want to compile something later, but none of that looks to me like it will "break" your system.

PLEASE PLEASE get a second opinion before going thru with the uninstall -- but I think you're safe.

---

### Post by mstralka on 2005-06-17
Thanks for your super-fast response and insight.  I didn't notice that it was just DEV packages.  I'm going to let it do its thing and then just reinstall it all... Even if I break something I'll probably be able to boot to the command line and fix everything..  I'll let you know if it works

---

### Post by dodongo on 2005-06-17
[QUOTE=mstralka]Even if I break something I'll probably be able to boot to the command line and fix everything..  I'll let you know if it works[/QUOTE]

Ah, there's the ambitious spirit!  :)  Good luck!

---

### Post by mstralka on 2005-06-17
alright so I removed them all and nothing seems broken.  I haven't rebooted yet though.

I reinstalled Gnomad2 again and don't have the broken package issues now, but Gnomad2 doesn't have a sync feature so I'm going to try to install nomadsync.  Thanks again

---

### Post by vassie on 2005-06-17
Now that gnomad2.7.0 is out, it's very easy to install, here's how I got it working....

```
wget http://kent.dl.sourceforge.net/sourceforge/gnomad2/gnomad2-2.7.0-1.FC3.i386.rpm
```
```
wget http://kent.dl.sourceforge.net/sourceforge/libnjb/libnjb-2.1.2-1.FC3.i386.rpm
```
```
sudo alien gnomad2-2.7.0-1.FC3.i386.rpm
```
```
sudo alien libnjb-2.1.2-1.FC3.i386.rpm
```
```
sudo dpkg -i libnjb_2.1.2-2_i386.deb
```
```
sudo dpkg -i gnomad2_2.7.0-2_i386.deb
```

Thats it :)

Ben

---

### Post by xalphas on 2005-06-22
@vassie Thank you very much. Latest package of njb and gnomad2 works great. I want to ask about listening music from gnomad. I select play track in Gnomad. But no sound comes. I also asked this to nomadness forums but i really need a detailed answer of what i am missing. 

Thx.

---

### Post by weeroona on 2005-07-12
Has anyone gotten Gnomad 2.8 working yet? I'm trying to download the right libraries to compile it but I keep getting MD5Sum mismatch on a bunch of the library packages needed to install libgnomeui2.0.

---

### Post by dodongo on 2005-07-12
[QUOTE=weeroona]Has anyone gotten Gnomad 2.8 working yet? I'm trying to download the right libraries to compile it but I keep getting MD5Sum mismatch on a bunch of the library packages needed to install libgnomeui2.0.[/QUOTE]

We're slowly wending this thread off-topic, but I'll bite :)  Yes, I do have Gnomad 2.8 working, though I've compiled the 2.2 libnjb by hand and symlinked as necessary, and I have Gnomad 2.8 compiled locally as well.  I'm still getting odd errors; it's very picky about when it likes to run and when it doesn't.  However, the 2.8 series adds some nice functionality, so as soon as I can  track down some sort of bug, I'll toss a report into the hopper.

---

### Post by vassie on 2005-07-13
2.8 works fine too, make sure you download the FC3 packages and not FC4

Ben

---

### Post by Lord Illidan on 2005-07-21
10x vassie!!

---

### Post by tUrtleAE86 on 2005-08-18
I installed according to Vassie's instructions, modified to install gnomad2-2.8.0.2 instead. But, I get the following error when I try to run using "sudo gnomad2".

```
gnomad2: error while loading shared libraries: libnjb.so.5: cannot open shared object file: No such file or directory
```

I already have libnjb installed though.... any ideas?

---

### Post by vassie on 2005-08-18
Try these two debs's

[http://195.153.177.76/upload/ben/deb/gnomad2_2.8.0-2_i386.deb](http://195.153.177.76/upload/ben/deb/gnomad2_2.8.0-2_i386.deb)
[http://195.153.177.76/upload/ben/deb/libnjb_2.2-2_i386.deb](http://195.153.177.76/upload/ben/deb/libnjb_2.2-2_i386.deb)

I noticed version 2.2.1 of libnjb is available, but there is only an FC4 rpm, and the last time I tried the FC4 ones, it didn't work

Ben

---

### Post by tUrtleAE86 on 2005-08-18
[QUOTE=vassie]Try these two debs's

[http://195.153.177.76/uploads/ben/deb/gnomad2_2.8.0-2_i386.deb](http://195.153.177.76/uploads/ben/deb/gnomad2_2.8.0-2_i386.deb)
[http://195.153.177.76/uploads/ben/deb/libnjb_2.2-2_i386.deb](http://195.153.177.76/uploads/ben/deb/libnjb_2.2-2_i386.deb)

I noticed version 2.2.1 of libnjb is available, but there is only an FC4 rpm, and the last time I tried the FC4 ones, it didn't work

Ben[/QUOTE]

Works great! Thanks!

---

### Post by Royal2000H on 2005-11-26
I installed from Adept (Kubuntu's Synaptic), and I can't get it running...

When I was using Windows, I put the PlaysForSure firmware so that I can use in on windows media player, instead of the standard creative firmware. Is that the problem?

Also, most my files are licensed with msn music because my friend somehow got me over 1000 codes for songs on msn music.... any way to play those songs in linux? and do i need the creative firmware for gnomad2 to recognize my creative zen micro?

---

### Post by dodongo on 2005-11-26
[QUOTE=Royal2000H]I put the PlaysForSure firmware so that I can use in on windows media player, instead of the standard creative firmware. Is that the problem?

Also, most my files are licensed with msn music because my friend somehow got me over 1000 codes for songs on msn music.... any way to play those songs in linux? and do i need the creative firmware for gnomad2 to recognize my creative zen micro?[/QUOTE]

To the first question, the answer is YES.  To my knowledge, the PFS firmware is unsupported in Linux.  If you re-flash the unit with the Creative firmware, you'll have better results.

As for the songs on MSN music...  I can't speak to that with any authority, but my guess is that you're going to have problems with that, as they're tethered to Windows Media Player and MSN.

---

### Post by dmartin on 2006-01-28
As for the root issue, I followed the instructions here: 
[http://www.linuxquestions.org/questions/showthread.php?p=1184427#post1184427](http://www.linuxquestions.org/questions/showthread.php?p=1184427#post1184427)

You won't have the two files mentioned.  Create them, and make their contents what is posted.

They worked perfectly for me, and I no longer need to be root to access my Micro.

As for the prior instructions, yes, making usb a+w is not a good idea at all, in terms of security.  There's very little (maybe nothing) on a Linux system that should be writeable by everyone.  At the very least, you should have made it writeable by a certain group (maybe a "usb" group) and then add users to that group.  Still, I'd recommend the instructions on the page provided, as they work very well.

---

