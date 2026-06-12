---
title: "HOWTO: LOW LATENCY AUDIO the easy way"
date: 2005-12-01
forum: Outdated Tutorials &amp; Tips
---

### Post by mathieujohnson on 2005-12-01
Hi,
after a couple requests I have come to make this how to.
This is primarly for musicians, recording studios or basicly anyone who really cares about their audio performances under linux.

This how to is based on the great work of the Demudi/agnula distro.

first step to get a patched kernel for audio work is to add this line to your sources.list file :deb [http://demudi.agnula.org/packages/demudi](http://demudi.agnula.org/packages/demudi) stable main

sudo gedit /etc/apt/sources.list
or sudo kwrite /etc/apt/sources.list

and copy past the line: deb [http://demudi.agnula.org/packages/demudi](http://demudi.agnula.org/packages/demudi) stable main

then save the file
and 
sudo apt-get update
sudo apt-get install kernel-image-2.6.12-3-multimedia-k7   (you can replace the last part with your appropriate architecture)
then when they ask if you want to stop now answer no
apt should resolve any dependencie problems, but in theory everything you need to make this kernel work is in the repo.
once this install is done, reboot and when grub menu appears choose the multimedia kernel and see wether jack can connect in realtime or not.
*****you can also update your version of jackd with that repository and a lot of other good stuff is on there*****

Thats it.

I got this working pretty good at 2.9ms latency without any problems.

my only concerns are to make amarok work with jack and basicly every app that uses audio to be routed to jack. still haven't got that going!

let me know if this is incorrect, doesn't work for you or if there are any mistakes.

and tell me how much you like it if it works.

---

### Post by 23meg on 2005-12-02
With what audio device did you get the 2.9ms latency?

---

### Post by mathieujohnson on 2005-12-02
with the hammerfall dsp
RME multiface no problems at all and I don't have such a fast computer.
1.4ghz athlon XP 1600+
768mb ram DDR 266
40gb ata 100 7200rpm
160gb ata 100 7200rpm
matrox G450 16mb dual head (also have a Nvidia 64mb geforce 3 card but it only has one head, though I am trying it out as I was having display problems when too much eye candy was activated mainly with e17)

Haven't toyed with midi yet.
don't have any midi devices. mainly use virtual stuff like synths and drum machines and obviously plugin effects (I used to have a lot of outboard gear but I got rid of it, they didn't get any use)

---

### Post by johannes on 2005-12-02
Nice tutorial, thanks.

> my only concerns are to make amarok work with jack and basicly every app that uses audio to be routed to jack. still haven't got that going!
I guess you have seen [this]("http://gentoo-wiki.com/HOWTO_Jack") Gentoo howto on Jack/ALSA stuff? I tried to do that in Ubuntu, but soon discovered that I would probably have to recompile ALSA, and I haven't got the time or patience to do that... If you get it to work, please write a tutorial!

Oh, I don't know if you already know this, but to be able to use Jack in realtime,

apt-get install realtime-lsm module-assistant
build the module with module-assistant
modprobe realtime gid=29

That should improve the audio in some cases.

---

### Post by mathieujohnson on 2005-12-02
I had already seen that how to for jack, though it is a good idea to post it in this thread so people have it in one simple place.
about the realtime-lsm module, there is a version in the demudi repo though I was never able to get it to work through module-assistant.
I beleive that it was allready loaded in the system if you used the demudi version AFAIK

---

### Post by foxy123 on 2005-12-03
a stupid question: what is it for? I mean is it only for some professional needs or it will mprove sound quality in Ubuntu overall?

---

### Post by 23meg on 2005-12-03
[QUOTE=foxy123]a stupid question: what is it for? I mean is it only for some professional needs or it will mprove sound quality in Ubuntu overall?[/QUOTE]
For audio production software only. It won't improve sound quality; it will only improve the responsiveness of the audio device to instructions.

---

### Post by foxy123 on 2005-12-03
[QUOTE=23meg]For audio production software only. It won't improve sound quality; it will only improve the responsiveness of the audio device to instructions.[/QUOTE]
oh, I see, thanks...

---

### Post by mathieujohnson on 2005-12-03
yeah basicly, if you don't have professionnal needs (or amateur, you know) well, this how to is not for you as this kernel is built for multimedia production hence is slower for other things like compiling (well, if you don't set the priority higher that is!)

---

### Post by reet on 2005-12-03
This sounds interesting, however with a different kernel I run into problems with my video drivers (Nvidia). I am told something about the Nvidia kernel module cannot be loaded because it hasn't been compiled for the new kernel. Am I going to have to abandon the .deb package for my video drivers and manually install them for this to work?

System Specs:
Athlon 2400+
768MB RAM
Geforce 6600GT
M-Audio Audiophile 2496

---

### Post by 23meg on 2005-12-03
As an alternative, you can install the corresponding linux-restricted-modules package for your new kernel, assuming there is one.

---

### Post by reet on 2005-12-03
It doesn't look like there is any :(

---

### Post by yaaarrrgg on 2005-12-04
thank you! This howto helped out a lot!!! I wouldn't have know where to start otherwise. 

 I just tried the realtime-lsm module and it has improved my audio responsiveness ... here is a list of everything I did.  A word of warning ... I am still new to Ubuntu so all these steps may not be needed :)

-----

HOWTO SETUP REALTIME-LSM FOR BREEZY (DEFAULT KERNEL)

EDIT: BEFORE TRYING THIS, SEE POST #18 IN THIS THREAD ... WHICH SHOWS A BETTER APPROACH USING RTLIMITS.  I'D RECOMMEND USING REALTIME-LSM AS YOUR LAST OPTION.  ANYWAYS:

1. first, I configured Breazy to use alsa for input and output.  In Gnome, this is set at:
System -> Preferences -> Multimedia Systems Selector

2. I added universe repository to Synaptic Package Manager...

If you're not sure how to do this, see

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo](https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo)

3. then i installed the realtime module

```

#switched to super user for convenience .. always use care as superuser
sudo -i

# you'll need to install headers for your version of linux
# you can do:
apt-get install linux-headers-$(uname -r)

# you'll need the module-assistant too
apt-get install module-assistant

# install jack tools
apt-get install jackd libjack0.80.0-dev qjackctl

#get and build realtime-lsm
# note: i got an error at this step saying roughly
# some kernel sources are unconfigured.
# i figure this was from something else I caused.  I ignored.

m-a update
m-a prepare
m-a get realtime-lsm
m-a get realtime-lsm-source
m-a build realtime-lsm-source
m-a install realtime-lsm

```

4. reboot the computer.  you may get error if you try to do a modprobe.  i don't know why, and thougth it would take more time to figure out than to reboot.  the module should be loaded when the computer restarts.

5. create a start script for loading jack. i called the file 'jackstart' ... you can of course name yours anything.  note: this might not be needed, but i didn't see anything in /etc/init.d that was related to jack

--start script--
```

#!/bin/bash

/usr/bin/jackd --realtime -d alsa -d hw -r 44100 -p 2048 -n 2 &

```
--end script--

# also changed group to audio for this script
chgrp audio jackstart

6. now almost done.  i tried starting jack using this script, and then ardour, but it still didn't seem to be  in realtime.  so i opened up the jack control panel:

```

qjackctl

```

go to Settings.  check the "realtime" option.  if jackd is running it will tell you to restart jack,  you can stop jack and restart with:


```

killall jackd

```

and then use the custom script to restart (assuming you are in the same directory):

```

./jackstart

```

then i tested ardour and hydrogen.  both had improved audio performance. no xruns.  

7. Ardour notes:

ardour is a multitrack recording package.  I tested ardour a bit more with multitracking.  I could still hear a bit of latency (like one beat of delay) when recording.  but after thinking about it, i realized the sound was delayed because it was taking a long path: 

(a) going from the instrument into (b) the mixer, then (c) going into the computer, (d) then processed, (e) then be returned to the mixer, and (f) sent to my ear.  

i assume this is unavoidable?  (I've never used a computer to record before)  a simple trick to eliminate this is to always click 'record' and 'mute' for the track you are currently working with.  i use a mackie mixer, so i can hear the sound from the source directly, rather than piping through the computer.  in other words, suppose I record track 2, while listening to track 1.

1. i hear track 1 coming from the computer, into the mixer
2. i record and mute track 2.  so, i hear track 2 (what I'm playing) straight from the mixer
3. when i playback, I unmute track 2.  the two tracks are synced up perfectly.  

hope this is helpful...  it is late now, so i'll work on this some more later.

edit:
by default realtime-lsm should start automatically when the computer boots.  To disable realtime-lsm, edit the file:

```

/etc/default/realtime

```

and change 'yes' to 'no', at:

```

# enable loading of module at startup
ENABLE=yes

```

---

### Post by maruchan on 2005-12-05
I would love to see this howto integrated into something like the Automatix script. This would be a good way to troubleshoot the methodology, too.

---

### Post by mathieujohnson on 2005-12-07
--start script--
```

#!/bin/bash

/usr/bin/jackd --realtime -d alsa -d hw -r 44100 -p 2048 -n 2 &

```
--end script--

nope, this is your problem here -p 2048 by setting the period to 2048 that gives you a latency of probably 92ms wich is horrible if you need to hear what you record WITH plugins.
basicly try and lower the period to 64 if it works ok, then you've got yourself a 2.9ms latency wich is amazing. if jack doesn't start, then raise the period to 128 wich is still a good 5.6ms. If you still get problems, try raising the latency again. I find it easier to start jack via the qjackctl app wich has a great configuration setup.
anything under 10ms should be reasonably "good" you probably will hear a delay if you are close or over 10ms!
the lower the better!
I'm glad that people enjoy this how-to and even happier that people add their insights to this particular task.

thanx

---

### Post by Sanne on 2005-12-07
Cheers mathieujohnson, thanks for this HOWTO, it's good to know you can run a Demudi low latency kernel on Ubuntu. :)

However, I  didn't understand everything yet, but from what I read, it seems that realtime-lsm is deprecated and there's something new built into the kernel already, it's called rtlimits. If anybody wants to look into it, here's a [description of this approach]("http://tapas.affenbande.org/?page_id=22").

It is mentioned that there's a tool called set_rtlimits that can help in reaching realtime mode for specified applications. I tried it, and it seems to work with the standard breezy kernel, but I still have to test it thoroughly.

If anybody else has experiences with this, I would be interested to hear about it. Maybe this is another option to achieve low latency on Ubuntu.

---

### Post by reuben on 2005-12-10
I'm having problems with this.

1) The low-latency kernel doesn't work for me (the nvidia drivers apparently are the problem; it also complains about the s20powerd startup script.)

2) I installed set_rtlimits, which don't work for me -- I tried 
set_rtlimits -d -r=1 /usr/bin/jackd -dalsa -dhw:1 -r44100 -p1024 -n2 
...
set_rtlimits -d -r=100 /usr/bin/jackd -dalsa -dhw:1 -r44100 -p1024 -n2 

...and got xruns in every case.

3) m-a get realtime-lsm-source

...failed until I had installed realtime-lsm and realtime-lsm-source using synaptic. From what I understand in the above, it should work without that step. I do have multiverse & universe enabled.

4) Even after installing realtime-lsm & realtime-lsm-source, m-a build realtime-lsm-source fails to build.

5) Using qjackctl or the commandline, --realtime fails.

6) The only sweet spot for me is -p2048, which isn't exactly instantaneous (but is OK). I'd expect better though -- I have an AMD 3400, with 1GB RAM, outputting to an M-Audio Delta 44. 

So, what can I do to reduce latency?

Thanks
Reuben

---

### Post by yaaarrrgg on 2005-12-11
Ahhh, thank you all for the replies... corrected some of my notes too.  My frame buffer was way too large.  Makes more sense now. :)

I just tried the rtlimits solution too.  For me, this seemed to be a lot easier to work with than realtime-lsm.  Also, it is already merged in the kernel, so makes more sense to use it.  More details on how I set mine up:

note: The computer I'm testing this on is nothing special...just a basic t2682 emachine: 2.6 Ghtz with 256 MB of memory, running Ubuntu 5.10 with very few modificatons.  Couple things I already have setup:

1. first, I configured Breezy to use "alsa" for input and output. In Gnome, this is set at:
System -> Preferences -> Multimedia Systems Selector

2. Also I added universe repository to Synaptic Package Manager... and I have previously installed: 

build-essential, linux-headers-2.6.12-9-386, jackd, libjack0.80.0-dev, qjackctl, and ardour  

If you're not sure how to do this, see:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[https://wiki.ubuntu.com/AptGetHowto?...ct=AptGetHowTo](https://wiki.ubuntu.com/AptGetHowto?...ct=AptGetHowTo)

3. Also, if you have installed realtime-lsm, it is probably a good idea to deactivate it.   Not sure what would happen if you run both these at the same time.  

-----

HOWTO SETUP RTLIMITS (FOR BREEZY DEFAULT KERNEL)

```

#switching to superuser... working in tmp directory
sudo -i
cd /tmp

#get and unpack set_rtlimits program
wget http://www.physics.adelaide.edu.au/~jwoithe/set_rtlimits-1.1.0.tgz
tar xvzf set_rtlimits-1.1.0.tgz
cd set_rtlimits-1.1.0

# this should compile the program and install
# note though... 
# i've already installed linux-headers and build-essential with apt-get
make
make install

```

For me, this compiled and installed without any errors.  To configure it now, you'll need to add the programs you'll invoke in the config file /etc/set_rtlimits.conf

For me, the file looks like this (my username is kevins)
```

# Configuration file for set_rtlimits.  Format is:
#
#   username   program   max_nice_priority  max_realtime_priority

kevins  /usr/bin/jackd  -1  100
kevins  /usr/bin/ardour -1  100

```

Now you are ready to go.  I wrote a quick script to launch jackd and ardour, (although there are probably countless better ways to do this).

```

#!/bin/bash
# this is a simple script for starting jack and ardour
# i usually don't have jackd running so i kill it after exiting

# NOTES ON THE OPTIONS:

# 1. the jackd "-n" option:
# determines the number buffers your hardware supports
# my cheap card supports "2" ... left and right channels?

# 2. the jackd "-p" option:
# determine the period  (or frame size...must be a multiple of 2).
# the smaller, the less latency. although if it's too small, you'll get 'xruns'
# (meaning your hardware can't keep up). possible values, for example, are:
#       64  (excellent)
#       128 (good)
#       256 (ok)

# 3. the set_rtlimits "-r" option:
# sets the priority "-r" for jack and ardour between 1 (low) and 100 (high)
# 30 seems to be a good choice for jack, with ardour slightly smaller

# start the apps in realtime mode
killall jackd
set_rtlimits -r=30 /usr/bin/jackd -R -d alsa -d hw -r 44100 -p 256 -n 2 &
set_rtlimits -r=25 /usr/bin/ardour
killall jackd

```

This should launch ardour and jack in realtime.  If you get xruns, then you might experiment with different priorities and frame size.  For me, ardour reports having 5.6 millisecond latency, and is very solid.  Tried 2.9 millisecond delay, but occasionally there was an xrun with the default breezy kernel.

-----

SUMMARY OF THE 3 METHODS LISTED IN THIS HOWTO, RANKED BY PERFORMANCE

1. demudi kernel:  Very solid! for me, Ardour reports 1.5 ms latency (since using two buffers).  Of course with a different kernel, there's a chance a few things could need to be recompiled to run.  For example, my system seems to work perfectly except my wierd wireless internet card.

2. rtlimits: For me, ardour reports 5.6 ms latency.  Works with default breezy kernel (not as fast as demudi though). also, this is already integrated into the kernel, and a good choice if you don't use the demudi kernel.

3. realtime-lsm:  Ardour reports 5.6 latency.  Also works with default breezy kernel.  A bit harder to set up than rtlimits.  Also, seemed like something was a bit flakey a few times.  For best results, start jackd from the control panel qjackctl, and be sure to check setup.  be sure to check "realtime", and try setting the priority to "30".

-----

yeah.. it would be nice if automatix had a sound studio package that included things like ardour, rosegarden, and hydrogen.  Incredible apps, but setting them up can be difficult.  Intially I almost gave up on Ardour.

---

### Post by Sanne on 2005-12-11
Ha, yaaarrrgg, thanks for the detailed description how to use set_rtlimits. I was prepared to do this to help reuben, but you beat me to it and saved me some work. :)

reuben, can you test yaaarrrgg's way for set_rtlimits? It should work then, I'm doing the same and getting jack to run in realtime mode.

Remember that you need to start every application via set_rtlimits -r..., not only jackd, and that every such application needs a corresponding entry in /etc/set_rtlimits.conf.

Edit: yaaarrrgg, why do you "killall jackd" at the very last line in your jack/ardour starter script? Wouldn't this kill jack after you just started it?

---

### Post by yaaarrrgg on 2005-12-11
[QUOTE=Sanne]Edit: yaaarrrgg, why do you "killall jackd" at the very last line in your jack/ardour starter script? Wouldn't this kill jack after you just started it?[/QUOTE]

I start jackd as a background process  (with the '&' at the end), but not ardour.  So, the last line is not executed until after ardour is closed.   For now, I don't use jackd for anything other than ardour.  Not sure how other people use jack though ...

---

### Post by Sanne on 2005-12-12
[QUOTE=yaaarrrgg]I start jackd as a background process  (with the '&' at the end), but not ardour.[/QUOTE]
Ahh yes, should have seen that, thanks for the clarification.

---

### Post by Doughsay on 2005-12-12
Hello, and thanks alot for this great howto.  But I'm having some problems.  I get xruns no matter what I do...

I haven't tried the demudi kernel yet, but I've followed yaaarrrgg's howto with the standard ubuntu kernel.  It seems that jack starts with no problems with realtime and everything (using realtime-lsm) , but no matter what settings I use, I stilll get xruns (alot of them), unless I go up to 2048 for the period setting.  What could be the problem?

```

jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
23:41:50.649 Server configuration saved to "/home/doughsay/.jackdrc".
23:41:50.650 Statistics reset.
23:41:50.654 Client activated.
23:41:50.654 Audio connection change.
23:41:50.656 Audio connection graph change.
**** alsa_pcm: xrun of at least 12.255 msecs
**** alsa_pcm: xrun of at least 13.117 msecs
**** alsa_pcm: xrun of at least 12.124 msecs
23:41:52.713 XRUN callback (3 skipped).
**** alsa_pcm: xrun of at least 3.234 msecs
**** alsa_pcm: xrun of at least 2.464 msecs
23:41:53.814 XRUN callback (5).
23:41:54.724 XRUN callback (1 skipped).
**** alsa_pcm: xrun of at least 2.346 msecs

```

Simply running from console gives the same output:

```

$ jackd -d alsa
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
**** alsa_pcm: xrun of at least 9.143 msecs
**** alsa_pcm: xrun of at least 10.184 msecs
**** alsa_pcm: xrun of at least 9.112 msecs
**** alsa_pcm: xrun of at least 10.069 msecs
**** alsa_pcm: xrun of at least 9.164 msecs

```

I never quite figured out how to configure or control alsa in any way.  Is this an alsa driver related issue?  How can I check?

---

### Post by fp-www.tonepad.com on 2005-12-12
I tried Yaaarrrgg's "HOWTO SETUP REALTIME-LSM FOR BREAZY (DEFAULT KERNEL)" and it worked great on my Dell laptop's onboard sound card. The Realtime checkbox works now. I now can set it up for 2.9mSec latency. I get some xrun messages on qjackctl mssg window but there are no audible dropouts, so I figure it's ok, right?

THANKS YAAARRRGG!

Now, having had such success with this, I tried it with my Tascam US-224 usb sound card... which was giving me 42mS prior to the realtime-lsm setup.

Sadly, even though I can select the Realtime option and lower the Frames/period, there is choppy sound with anything under 1024 (42mS latency). Any idea on how I could get the $$ USB tascam card to work as fast as the onboard laptop card?

Fp

---

### Post by Doughsay on 2005-12-12
Hello again,  I just tried installing the demudi kernel image and wanted to point out that it doesn't come with LVM support compiled into it, which makes it useless for me, as ubuntu set up the root filesystem in an LVM group by default on my machine.  There's no way around this unless I compile a kernel myself right?

---

### Post by yaaarrrgg on 2005-12-13
First, I'd recommend trying set_rtlimits (see post #18 ) before using realtime-lsm.  Sanne pointed out that realtime-lsm is deprecated, whereas set_rtlimits uses something already built into your breezy kernel.  I've gotten both to work, although I think realtime-lsm adds more complexity, and is probably more prone to having problems.  

Doughsay: if you start jack from the command line, be sure to add the realtime flag ( "--realtime" or "-R" ). 

fp-www.tonepad.com: i am using jack and ardour, and I figured that both should run in realtime.  In your case, your usb device might be the bottleneck because it might not have a realtime priority (I'm guessing).  The software driving it (and I'm not sure what that would be) may need to be started in realtime as well.  In other words, a chain will only be as fast as it's slowest component.

---

### Post by Doughsay on 2005-12-15
Hi,

Thanks for the reply.  I can't reproduce it right now, but I did try set_rtlimits and got the same results...  I don't think that's the problem, regardless of which way I give the application realtime privelages, it should still get them.  When running it through qjackctl, it *says* it's running in realtime, but it just doesnt seem like it, since I still get tons of xruns.  But I notice that even without jack running and just using the alsa driver directly, Hydrogen gives me the same thing, a lot of xruns.  So it doesn't seem to be jack's problem, it's alsa.  The problem is I can't uninstall alsa to reinstall it myself (from source maybe) because if I try to remove the package, it wants to remove half of my system with it.  Not just meta packages like ubuntu-desktop, but packages like gedit too!  I don't know why, it's really frustrating.  I wish I could uninstall everything alsa jack and realtime related, and start fresh installing things myself.  Anobody have any ideas on how I can do that?

I might try getting the source for the demudi low latency kernel and recompile it with LVM support.  Or I might re-install ubuntu without logical partitions...  I tried the demudi livecd, and everything worked perfectly...I got 5.6ms latency, I couldn't go down to 64 on the frames setting, so I stuck with 128.

Anyway, I'll post my results back after I try some more experiments...

---

### Post by yaaarrrgg on 2005-12-19
hmm... 5.6 latency for the demudi kernel is not very good.  Makes me think you might have a problem related to your hardware, bios, or something eating your resources.  Not sure what kind of machine you are using.  

1. You might try stripping out any unneeded services.  This thread has more info on disabling unneeded services:
[http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

2. Also this link has some info about hardware tuning:
[http://ccrma.stanford.edu/planetccrma/software/installtwosix.html#SECTION000201400000000000000](http://ccrma.stanford.edu/planetccrma/software/installtwosix.html#SECTION000201400000000000000)

----- 

I tested hydrogen with set_rtlimits and had very good results...

First, i edited /etc/set_rtlimits.conf and added an entry for /usr/bin/hydrogen.  

Then i wrote a quick script to launch it:

```

#!/bin/bash

# start a clean instance of jack
killall jackd
set_rtlimits -r=30 /usr/bin/jackd -R -d alsa -d hw -r 44100 -p 256 -n 2 &

# start hydrogen
sleep 1
set_rtlimits -r=30 /usr/bin/hydrogen

# clean up
killall jackd

```

without doing this, hydrogen was just too sluggish to be useful.  You may need to experiment with the priorities though.  Setting too high will cause the gui to be slugish.

---

### Post by 23meg on 2005-12-20
I'm having trouble installing rtlimits; it fails to create the documentation folder. It seems to be looking in the wrong place. Did you modify the makefile in any way to make it work in Breezy?

```
Copying documentation directory...
test -d /usr/local/bin || mkdir -p /usr/local/bin
test -d /usr/local/man/man8 || mkdir -p /usr/local/man/man8
mkdir: cannot create directory `/usr/local/man': File exists
make: *** [install] Error 1

```
The symlink /usr/local/man points to /usr/local/share/man , which doesn't exist.

---

### Post by yaaarrrgg on 2005-12-20
[QUOTE=23meg]I'm having trouble installing rtlimits; it fails to create the documentation folder. It seems to be looking in the wrong place. Did you modify the makefile in any way to make it work in Breezy?
[/QUOTE]

That's odd.  I hadn't modified the MakeFile in any way for breezy.  For me it compiled and installed without a hitch.  I'm using:

```

     GNU Make 3.80
     gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

```

If the directory /usr/local/share/man/ doesn't exist on your system, you can try recreating it.  Really it shouldn't matter where the man file goes, as long as your $MANPATH contains the directory.

Although, the installation is pretty simple to do by hand if "make install" doesn't work...it just copies three files.  You can manually copy these files: 

```

     set_rtlimits         can go in /usr/local/bin/
     set_rtlimits.conf    goes in /etc/
     set_rtlimits.8       can go in your man dir /usr/local/man/man8/

```

also it sets some permisions:

```

sudo     chown root.root /usr/local/bin/set_rtlimits
sudo     chmod u+s /usr/local/bin/set_rtlimits

```

---

### Post by fp-www.tonepad.com on 2005-12-22
I have tried set_rtlimits, but when I input the command:

set_rtlimits -r=30 /usr/bin/jackd -R -d alsa -d hw -r 44100 -p 256 -n 2 & sleep 3

I get the following error:

set_rtlimits: no permission to run /usr/bin/jackd with realtime priorities
[1] 8870
[1]   Exit 255                set_rtlimits -r=30 /usr/bin/jackd -R -d alsa -d hw -r 44100 -p 256 -n 2

how can I change permissions or what can I do to make it work?

Fp

EDIT: I used the following commands:

sudo     chown root.root /usr/local/bin/set_rtlimits
sudo     chmod u+s /usr/local/bin/set_rtlimits

and now I can run jack, but I keep getting xruns. What can I do? when I use demudi the latency can go really low. I want that in kubuntu :)

Fp

---

### Post by reuben on 2005-12-22
According to the linux audio mailing list (if I understood them correctly), 2.6.14 (and on) kernels have some nicety in them which almost preclude the necessity of playing with the RT stuff. Has anybody tried the dapper kernel yet? If so, can you verify? 

(I tried to install the dapper kernel, but I guess I forgot to include the modules for the kernel, or similar, and brought my system to its knees ;/)

---

