---
title: "HOWTO: Creative's Jukebox with Gnomad"
date: 2005-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by globalspace on 2005-05-09
First of all thanks to :
- **panickedthumb** to his help ... without his help now i couldn't use my Zen Micro with Linux :)
- This great [Article](http://gnomad2.sourceforge.net/?section=article) 


**With this How To you can :**
- Send/receive Files to/from your Nomad Devices (see the section "Working Devices" for compatibility)
- Manage the playlists (Create, delete, modify ... )
- Manage the files (modify the Mp3's tag of your collection)
- repleace the Creative's Windows Software 
- and so on ...


**How To manage Creative's Jukebox with gnomad to send / receive file **

*Working Devices* 
- Creative Nomad Jukebox 1 (aka D.A.P.)
- Creative Nomad Jukebox 2
- Creative Nomad Jukebox 3
- Creative Nomad Jukebox Zen
- Creative Nomad Jukebox Zen USB 2.0
- Creative Nomad Jukebox Zen NX
- Creative Nomad Jukebox Zen Xtra
- Dell Digital Jukebox ("Dell DJ")
- Creative Nomad Jukebox Zen Touch
- Creative Nomad Jukebox Zen Micro
(Without the 2.x MTP/PlaysForSure upgrade!)
- Second Generation Dell DJ
(Without the MTP/PlaysForSure upgrade!)
- Dell Pocket DJ
(Without the MTP/PlaysForSure upgrade!)




[COLOR=Red]**Let's Go !**[/COLOR]

------------------
**Download libnjb**

> wget [http://prdownloads.sourceforge.net/libnjb/libnjb-2.0.tar.gz?download](http://prdownloads.sourceforge.net/libnjb/libnjb-2.0.tar.gz?download) 

**Unpack the archive**

> tar xvzf libnjb-2.0.tar.gz

**Install libnjb**

> 
sudo -s -H
./configure && make && make install && ldconfig
If you get a compilation error, you might have forgotten to install the developement libraries from libusb, install them.

**You will then have to set up the hotplug and devfs part**

IF you AREN'T root type 

> sudo -s -H 

then

> cat nomad.usermap >> /etc/hotplug/usb/usb.usermap ; cp nomadjukebox /etc/hotplug/usb/ ; chmod a+x /etc/hotplug/usb/nomadjukebox 

**Restart the hotplug system**

> sudo /etc/init.d/hotplug restart 

**Now we need gnomad, as user do**

> wget [http://prdownloads.sourceforge.net/gnomad2/gnomad2-2.6.3.tar.gz?download](http://prdownloads.sourceforge.net/gnomad2/gnomad2-2.6.3.tar.gz?download)

and then as user do :

> 
tar xvzf gnomad-2.x.x.tar.gz
cd gnomad-2.x.x/ ; ./configure ; make ; sudo make install ; sudo ldconfig  
If you get errors use Synaptics to satisfy the dependences.

**Launch gnomad2 as user** 

> gnomad2 

-----------
[COLOR=Red]***Tips***[/COLOR]

**If when you launch gnomad2 you get this error :**

> bash: /usr/bin/gnomad2: No such file or directory 

you need to copy "/usr/local/bin/gnomad2" into "/usr/bin/"

> sudo cp /usr/local/bin/gnomad2 /usr/bin/

**If when you launch gnomad2 it says you that it can't find libnjb-2.0.so into your shared library type **

> sudo cp /usr/local/lib/libnjb-2.0.so /usr/lib/


PS- This isn't the final version of my How to .. but please excuse me this is my first how to and my english is not so good  :roll:

---

### Post by blahrus on 2005-05-23
Thanks!

MOTU should update the drivers ;)

---

### Post by XDevHald on 2005-05-23
Great HowTo!!!

---

### Post by SwanMocker on 2005-05-24
hmmm, I tried this guide a few days back and it worked fine, but now when I open Gnomad 2 It says "couldn't open the jukebox". I have a creative zen touch. Anyone know what is wrong? The player shows up in the device manager

---

### Post by vassie on 2005-05-24
Hello
I am trying to install gnomad2.6.3-1 on Hoary, however it depends on libnjb4, which in turn depends on a newer version of libc6 that is currently install
Can anyone please help me get the latest gnomad2 working, beacuse without it, I cannot get rid of Windows
Thanks
Ben

---

### Post by cdub on 2005-05-24
[QUOTE=SwanMocker]hmmm, I tried this guide a few days back and it worked fine, but now when I open Gnomad 2 It says "couldn't open the jukebox". I have a creative zen touch. Anyone know what is wrong? The player shows up in the device manager[/QUOTE]

it could be permissions; try running gnomad2 as root and if it connects properly, then try this...

sudo gedit /etc/hotplug/usb/nomadjukebox
#change DEVICEPERMS=0600 --> DEVICEPERMS=0666 and reconnect device

i ran into issues when i had the gpilotd daemon running, but my symptoms were different (successful connection, but infintite hang while "scanning songs"), so i doubt that gpilot is the culprit in your case.

anyway, hope that helps

~cdub

---

### Post by SwanMocker on 2005-05-25
That worked,thanks


EDIT: Well it worked for 5 minutes, now the entire program has gone crazy. Oh well

---

### Post by cdub on 2005-05-25
[QUOTE=SwanMocker]
EDIT: Well it worked for 5 minutes, now the entire program has gone crazy. Oh well[/QUOTE]

What's it doing now?  Are you still able to connect and scan songs successfully?  If you get a chance, post your error messages... there's a 99.9% chance that I've seen 'em all :-)

~cdub

---

### Post by judabuddhist on 2005-05-26
Awesome. One less reason for me to have to boot back to windows. thanks

---

### Post by doans on 2005-05-27
[QUOTE=judabuddhist]Awesome. One less reason for me to have to boot back to windows. thanks[/QUOTE]
 I am having problems compiling gnomad. Here is my error message.

checking for pkg-config... /usr/bin/pkg-config
checking for         glib-2.0                    gthread-2.0                 gtk+-2.0                    libgnomeui-2.0         libnjb... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

configure: error: Library requirements (        glib-2.0                    gthread-2.0                 gtk+-2.0            libgnomeui-2.0               libnjb) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

I looked in synaptic and can't find package gtk+-2.0.  Any suggestions?  Thanks.

---

### Post by TravisNewman on 2005-05-27
>  			 				sudo cp /usr/local/lib/libnjb-2.0.so /usr/lib/
THAT's what I was missing. I'd totally ruined it with installing so many different versions. I can now use this instead of neutrino :)

---

### Post by cdub on 2005-05-27
First, you'll need to fully setup your development environment... packages such as libgnomeui2-dev, libgtk2-dev, glibc-dev, etc.

Next you'll need to build libnjb... no big deal once your dev environment is setup.

After that, gnomad2 should build without any issues.

I can post the list of *-dev packages that I used when I get home from work, if you want... just let me know.

Actually, if I get a chance today before I start my holiday w/e, I'll post a script that will do it all.

Cheers!

~cdub

---

### Post by cdub on 2005-05-27
[QUOTE=panickedthumb]THAT's what I was missing. I'd totally ruined it with installing so many different versions. I can now use this instead of neutrino :)[/QUOTE]

Awesome!!  When you get these things working correctly, it kinda makes up for the hours of googling & putzing around that it takes... well, almost!  :-)  Actually, kudos to **globalspace** for the how-to!!  I'd still be googling if not for the running start the guide gave me... thanks!

On a sidenote... chances are, you'll need to build a shared library such as libnjb in the future and since these are many times installed in /usr/local/lib, it's probably better to add this directory to your LD_LIBRARY path rather than have to track-down and copy/link each one after a build.  Just a thought, but running the following once should do the trick:

sudo echo /usr/local/lib >> /etc/ld.so.conf
sudo ldconfig

~cdub

---

### Post by spacemonkey on 2005-05-27
Here's what I did to get my Dell DJ working properly on Ubuntu:

First, in the ubuntu repositories only the old version of libnjb is available, and the version of gnomad in those repositories depends on that, so what I did was temporarily disable the ubuntu repositories, add the debian unstable ones, install gnomad and the newest version of libnjb, change my repos back to the way they were, and everything worked out perfect.  Since a newer version was installed, synaptic didn't try to change libnjb or gnomad back to the ubuntu versions.  I tried compiling from source like this how to suggests,  but I never could get it to work, always some error.

---

### Post by cdub on 2005-05-27
[QUOTE=cdub]First, you'll need to fully setup your development environment... packages such as libgnomeui2-dev, libgtk2-dev, glibc-dev, etc.

Next you'll need to build libnjb... no big deal once your dev environment is setup.

After that, gnomad2 should build without any issues.

I can post the list of *-dev packages that I used when I get home from work, if you want... just let me know.

Actually, if I get a chance today before I start my holiday w/e, I'll post a script that will do it all.

Cheers!

~cdub[/QUOTE]

```
#!/bin/bash
#gnomad2 setup on ubuntu 5.04
#untested; copy-pasted from my main ubuntu setup script which has been
#(i.e. use this at own risk ;-)
#also, please note the last section of the script; a manual edit is required
################################################

#update apt sources
sudo mv /etc/apt/sources.list /etc/apt/sources.list_bak
wget "http://download.ubuntuforums.org/ubuntusetup/sources.list"
sudo cp sources.list /etc/apt/sources.list
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907
sudo apt-key add -
sudo apt-get update

#get dev packages
sudo apt-get install build-essential
sudo apt-get install gcc g++
sudo apt-get install libgtk2.0-dev libgnomeui-dev libxml-perl
sudo apt-get install libusb-dev libid3tag0-dev

#build libnjb
wget "http://easynews.dl.sourceforge.net/sourceforge/libnjb/libnjb-2.1.1.tar.gz"
tar xvfz libnjb-2.1.1.tar.gz
cd libnjb-2.1.1
./configure
make
sudo make install
sudo cp nomadjukebox /etc/hotplug/usb/nomadjukebox
sudo chmod 755 /etc/hotplug/usb/nomadjukebox
sudo cp nomad.usermap /etc/hotplug/usb/nomad.usermap
sudo ldconfig
#cleanup
cd ..
rm -Rf libnjb-2.1.1
#restart usb hotplug service
sudo /etc/init.d/hotplug restart
#refresh shared libraries
sudo echo /usr/local/lib >> /etc/ld.so.conf
sudo ldconfig
#build gnomad2
wget "http://easynews.dl.sourceforge.net/sourceforge/gnomad2/gnomad2-2.6.3.tar.gz"
tar xvfz gnomad2-2.6.3.tar.gz
cd gnomad2-2.6.3
./configure
make
sudo make install
#cleanup
cd ..
rm -Rf gnomad2-2.6.3

#permissions...
sudo gedit /etc/hotplug/usb/nomadjukebox
#change DEVICEPERMS=0600 --> DEVICEPERMS=0666
#ensure gpilotd is paused (if you use this daemon; caused me some issues)
#plugin in device & cross fingers :-)
#eof
################################################
```

---

### Post by doans on 2005-05-27
[QUOTE=cdub]First, you'll need to fully setup your development environment... packages such as libgnomeui2-dev, libgtk2-dev, glibc-dev, etc.

Next you'll need to build libnjb... no big deal once your dev environment is setup.

After that, gnomad2 should build without any issues.

I can post the list of *-dev packages that I used when I get home from work, if you want... just let me know.

Actually, if I get a chance today before I start my holiday w/e, I'll post a script that will do it all.

Cheers!

~cdub[/QUOTE]

I just needed to install the aforementioned dev packages and it works!  Thanks.
I will try out the script later, sounds like it will be easier.

---

### Post by xalphas on 2005-05-28
Well done @cdub... This script works fine and install very well.. But after i run succesfully gnomad 2 and want to transfer only 1 song it gives someth like this. 

```
xalphas@ubuntu:~/temp/$ gnomad2
usb_bulk_read: 
njb3_get_status: I/O failure on USB data pipe
```

And freeze. Any suggestions welcome..

thx.

---

### Post by cdub on 2005-05-28
[QUOTE=xalphas]Well done @cdub... This script works fine and install very well.. But after i run succesfully gnomad 2 and want to transfer only 1 song it gives someth like this. 

```
xalphas@ubuntu:~/temp/$ gnomad2
usb_bulk_read: 
njb3_get_status: I/O failure on USB data pipe
```

And freeze. Any suggestions welcome..

thx.[/QUOTE]

Hmmm... did it "scan songs" successfully?  Check the Device Manager to ensure that the device is being detected/mounted properly by the usb hotplug service before launching gnomad2.  You may want to try launching "sudo gnomad2" to run as root and eliminate permissions as the cause.  Also, ensure that gpilot daemon is not running... that caused me some headaches and it was something that's tough to catch during troubleshooting.

Good luck...

~cdub

---

### Post by xalphas on 2005-05-28
Thx for the reply. I did all of them.. It scans the jukebox. I can transfer songs from nomad to pc but when i want to transfer from pc to nomad it gives the above error. It freezes but i recognize that it puts the song in jukebox. But only one sond  :? 

-->stopped gpilot
-->0666
--> Normal and sudo both the same. 

Also i realize that in the playlist tab on Gnomad it's empty. But when i select i can see my playlist sections.. Looked also nomadnedd forum same situation mentioned as "USB Problem" . I don't think so cause i can transfer songs from nomad and also i can use my other usb machines like Canon Powershot. 

I think this looks like a njb problem. 

Note : I've looked at Breezy repository and saw that libnjb 2.1.1 and gnomad 2.6.3 as deb. Will it be useful just to install it that way. Think we are using debian unstable sid Maybe?

---

### Post by ecoleman on 2005-07-31
Does anyone know how to play a track from the jukebox on the computer without moving the file across ?
tia
edwin

---

### Post by njean on 2005-08-28
thanks it works fine!

---

### Post by ManLord on 2005-08-31
Thanks cdub, that script works fine. I'm not into building thing from source and devel packages and all that "fuzz". Not that smart. But the script did it's job.

But I had to comment out that first part, didn't find the url.

And since i use kubuntu, i changed to kedit.

But then all ran smooth. Thanks again!

---

### Post by cdub on 2005-08-31
[QUOTE=ManLord]Thanks cdub, that script works fine. I'm not into building thing from source and devel packages and all that "fuzz". Not that smart. But the script did it's job.

But I had to comment out that first part, didn't find the url.

And since i use kubuntu, i changed to kedit.

But then all ran smooth. Thanks again![/QUOTE]

Hi ManLord,

Glad the script helped ya out!!

Cheers,
cdub

---

### Post by NMUrugbysteve on 2005-09-04
[QUOTE=cdub]Hi ManLord,

Glad the script helped ya out!!

Cheers,
cdub[/QUOTE]
 Script works great, but your URL for sources is down.

---

### Post by Unit #134679 on 2005-09-13
root@pandoras-box:/home/mark # cat nomad.usermap >> /etc/hotplug/usb/usb.usermap ; cp nomadjukebox /etc/hotplug/usb/ ; chmod a+x /etc/hotplug/usb/nomadjukebox
cat: nomad.usermap: No such file or directory
cp: cannot stat `nomadjukebox': No such file or directory

---

### Post by _jB on 2005-09-19
Thank you VERY much !!

One more reason for booting ubuntu instead of winblows :D

---

### Post by cdub on 2005-09-19
[QUOTE=_jB]Thank you VERY much !!

One more reason for booting ubuntu instead of winblows :D[/QUOTE]

That's what I like to hear!!   ;-)

---

### Post by MBro on 2005-09-19
> **cdub]it could be permissions said:**
> 
Ok, that helped me but I'm trying to edit that file and I receive this error.  
[quote]root@brotheme:/home/matt # gedit /etc/hotplug/usb/nomadjukebox

(gedit:23376): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


---

### Post by cdub on 2005-09-19
[QUOTE=MBro]Ok, that helped me but I'm trying to edit that file and I receive this error.[/QUOTE]

I try not to run as root... I'd recommend a standard user account and sudo.  You could also give the nano editor a try instead of gedit.  Good luck!

--cdub

---

### Post by MBro on 2005-09-20
The file opened with nano but came up as an empty file

---

### Post by cdub on 2005-09-20
[QUOTE=MBro]The file opened with nano but came up as an empty file[/QUOTE]

Going back through the posts from those that ran into problems with the script, the common theme seems to be that they are running as root.  If you have an opportunity, could you run the install script from a regular user account?  I'm just curious about the results.  I never tested the script as root... I also didn't anticipated any problems either, but I'm certainly no guru. :-)  My guess is that necessary files were not copied properly due to this, so maybe I need to modify the script somewhat.

Let me know how you make out... thanks!

--cdub

---

### Post by MBro on 2005-09-20
No dice, still comes up blank

---

### Post by cdub on 2005-09-20
[QUOTE=MBro]No dice, still comes up blank[/QUOTE]

Hmmm... I dunno.  Does the script appear to fail anywhere along the way when you run it?  Instead of running the script, try (if you haven't already) to copy-paste the contents of the script into the terminal window a line or section at a time to see if anything is bombing out.  I just re-ran it on my machine and it seemed OK, so I'm not sure what the problem could be.  Also, run the following to see if the nomadjukebox file was installed somewhere else (?):

sudo updatedb
locate nomadjukebox

~cdub

---

### Post by thomax on 2005-09-22
Fantastic, just what I needed, I just bought a Creative Zen Micro 6GB but in linux it doesn't see the device as mass storage device, so I will need this :) thanx alot ;)

---

### Post by jimbren on 2005-10-11
Excellent!

---

### Post by djpeanut on 2005-11-02
I am getting the following error (at the bottom):

```
root@peanut:/home/tom/libnjb-2.0# ./configure && make && make install && ldconfig
checking for bash... /bin/bash
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
root@peanut:/home/tom/libnjb-2.0#

```

I'm new to this linux business.... any ideas?

TIA!

---

### Post by cdub on 2005-11-02
[QUOTE=djpeanut]I am getting the following error (at the bottom):

```
root@peanut:/home/tom/libnjb-2.0# ./configure && make && make install && ldconfig
checking for bash... /bin/bash
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
root@peanut:/home/tom/libnjb-2.0#

```

I'm new to this linux business.... any ideas?

TIA![/QUOTE]

It looks like your dev environment is not fully setup.  Try the following packages (Note: not all are needed to build libnjb, but certainly won't harm anything):

sudo apt-get install build-essential
sudo apt-get install gcc g++
sudo apt-get install libgtk2.0-dev libgnomeui-dev libxml-perl

Also, you may have better luck using the Gnomad install script posted earlier in this thread.

Good luck,
cdub

---

### Post by ivanhelguera on 2005-11-16
Another big THANK YOU from another happy user! (Zen touch)
After working out the devel dependencies, it worked really well. I was ready to trade my Zen for an Ipod for linux compatibility, but now the problem seems to be resolved. A couple of bucks will stay in my pocket, and I have - as many others - one reason less to boot the MS system. 
What I do not like about the gnomad is the way it organises the music: if you sort by artist, it does not list songs by Artist->album-> track nr. So you have tracks from an album scattered evrywhere. 
Of course it has nothing to do with the GREAT work you provided (and of course I am very grateful to the GNOMAD team).  
Thanks, 
IH

---

### Post by tomwell on 2005-12-12
Thanks it worked fine for me its great to be able to use my Nomad in Ubuntu...

Peace

Tom

---

### Post by simplyw00x on 2006-01-04
> root@pandoras-box:/home/mark # cat nomad.usermap >> /etc/hotplug/usb/usb.usermap ; cp nomadjukebox /etc/hotplug/usb/ ; chmod a+x /etc/hotplug/usb/nomadjukebox
cat: nomad.usermap: No such file or directory
cp: cannot stat `nomadjukebox': No such file or directory
You need to be in the gnomad2-x.x.x directory

> sudo cp /usr/local/lib/libnjb-2.0.so /usr/lib/
It told me it couldn't find libnjb.so.5. The following did the trick:
```
cp /usr/local/lib/libnjb.so.5 /usr/lib/
```

Just to let you guys know that this still works! I'm using Breezy and a Creative Nomad Jukebox 2 (the really huge ugly one) and as far as I can tell it's working fine. Using libnjb-2.2.4 and gnomad2-2.8.2.

I made some .debs ([libnjb]("http://rapidshare.de/files/10412871/libnjb_2.2.4-1_i386.deb.html"), [gnomad2]("http://rapidshare.de/files/10412904/gnomad2_2.8.2-1_i386.deb.html")) using checkinstall for your enjoyment. I hear that CheckInstall packages don't handle dependencies properly, so make sure you have all the aforementioned dev packages installed, as well as libid3tag-dev (as I think it called) before trying them.

---

### Post by painreliever on 2006-01-19
Hey, just a quick one (with a quick answer I hope!) 

I've installed Gnomad and it runs fine as long as I launch it from Terminal as root, as for some reason I don't have the right permissions for hotplug as user. But that's not the real problem - if anyone does know how to sort this, please tell me, but otherwise my problem is thus:

When I try and connect my player (I'm using a Zen Touch), Gnomad crashes and I get the following message in the Terminal window:

gnomad2: symbol lookup error: gnomad2: undefined symbol: NJB_Set_Turbo_Mode

Even if I got into preferences and disable Turbo Mode BEFORE I connect my Zen, it STILL crashes.

Any ideas?

Ta

---

### Post by Talkendo on 2006-04-22
](*,) 

For the life of me, I can NOT get gnomad2 to work.  I've run the script (as provided) twice before realising I had the MTP enabled firmware.  Okay, scrapped that and then started over with the newest versions.  No errors while installing, but it will NOT, absolutely NOT find my Zen Sleek.
[INDENT]
I have done the following things: 
lsusb to make sure I've got the right device (and fixed it when I didn't)
tried multiple usb ports
changed permissions
rebooted
restarted hotplug numerous times
scoured the forums and Google for any other answers
Oh, and ran both as normal user & sudo for both steps.[/INDENT]

Does anyone, anywhere have any ideas?  I'd appreciate it as it's the LAST thing I need (short of Firefox extensions) to get full enjoyment from my Ubuntu install...

---

### Post by kris kincaid on 2006-04-23
I am having the same problem. Any help would be appreciated. :)


[QUOTE=painreliever]Hey, just a quick one (with a quick answer I hope!) 

I've installed Gnomad and it runs fine as long as I launch it from Terminal as root, as for some reason I don't have the right permissions for hotplug as user. But that's not the real problem - if anyone does know how to sort this, please tell me, but otherwise my problem is thus:

When I try and connect my player (I'm using a Zen Touch), Gnomad crashes and I get the following message in the Terminal window:

gnomad2: symbol lookup error: gnomad2: undefined symbol: NJB_Set_Turbo_Mode

Even if I got into preferences and disable Turbo Mode BEFORE I connect my Zen, it STILL crashes.

Any ideas?

Ta[/QUOTE]

---

### Post by bluenova on 2006-04-30
Well everything was going smoothly, I decided to format my xen xtra and start a fresh. I got half way through copying over 20Gb of songs in gnomad2, and it stopped. I've rebooted, and now all I get is it says 'scanning for songs....' and nothing more, Nutrino and Banshee can't connet anymore either. When I run gnomad I get this in the terminal:
```

gnomad2

(gnomad2:12764): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed
ID3v2 TLEN tag time was 0
ID3v2 TLEN tag time was 0
ID3v2 TLEN tag time was 0
ID3v2 TLEN tag time was 0

```
And it just sits there :(  Any ideas?

:Edit: Neutrino is now working after restarting hotplug, but not gnomad2
:Edit2: Don't worry, seems to have sorted itself out.

---

### Post by twiddle87 on 2006-05-07
[QUOTE=kris kincaid]I am having the same problem. Any help would be appreciated. :)[/QUOTE]

all i did to fix this was comment out a check in the source (jukebox.c) before compiling.. not a great solution, but at least it works.


    ```

    /* Set turbo mode according to preferences  
    if (get_prefs_turbo_mode()) {
      NJB_Set_Turbo_Mode(pdedevice, NJB_TURBO_OFF);
    } else {
      NJB_Set_Turbo_Mode(pdedevice, NJB_TURBO_ON);
    }***/**
```

stephen

---

### Post by JanRa on 2006-05-28
[QUOTE=Talkendo]](*,) 

For the life of me, I can NOT get gnomad2 to work.  I've run the script (as provided) twice before realising I had the MTP enabled firmware.  Okay, scrapped that and then started over with the newest versions.  No errors while installing, but it will NOT, absolutely NOT find my Zen Sleek.
[INDENT]
I have done the following things: 
lsusb to make sure I've got the right device (and fixed it when I didn't)
tried multiple usb ports
changed permissions
rebooted
restarted hotplug numerous times
scoured the forums and Google for any other answers
Oh, and ran both as normal user & sudo for both steps.[/INDENT]

Does anyone, anywhere have any ideas?  I'd appreciate it as it's the LAST thing I need (short of Firefox extensions) to get full enjoyment from my Ubuntu install...[/QUOTE]

I've got exactly the same problem. I tried everything (started gnomad as root, checked hotplug, rebooted etc) but Gnomad just does not want to detect my Zen Sleek

Any suggestions ? Otherwise I might have to create a partition to install windows again, which i really don't want to get into.

Thanks,

Jan

---

### Post by kris kincaid on 2006-05-28
I finally got mine to work. I upgraded to Dapper :-D  Works awesome now!

---

### Post by hippomofatumas on 2006-06-01
Hi,

this walkthrough looks great and everyone is having success, except myself. I'm pretty new at linux, but I know some stuff. However, I can't even install libnjb. When I try to do that ./configure thingy, nothing works. What am I missing?

---

### Post by megamania on 2006-06-03
[QUOTE=hippomofatumas]this walkthrough looks great and everyone is having success, except myself. I'm pretty new at linux, but I know some stuff. However, I can't even install libnjb. When I try to do that ./configure thingy, nothing works. What am I missing?[/QUOTE]
When I installed Gnomad (one month ago) I was already using Dapper, so I have no experience of Gnomad running under Breezy. What I can tell you is that all I had to do was to install it from the synaptic manager, and everything worked perfectly.

If you're still using Breezy, my suggestion is to install Dapper and hopefully everything will be much simpler.

---

### Post by cnphch on 2006-06-06
I installed Dapper a week ago. 
Today I installed Gnomad2 from synaptic, but i get the error "No jukeboxes found on USB bus".

Any ideas? Btw the "hotplug" pakkage isn't avaliable in synaptic. It's there but you can't install it. 

Any help?

---

### Post by megamania on 2006-06-07
[QUOTE=cnphch]I installed Dapper a week ago. 
Today I installed Gnomad2 from synaptic, but i get the error "No jukeboxes found on USB bus".

Any ideas? Btw the "hotplug" pakkage isn't avaliable in synaptic. It's there but you can't install it. 
[/QUOTE]You usually get that error if the Zen is not switched on when you run Gnomad.
With the device switched on, try checking if it shows up in the device manager and please report back.

---

### Post by cnphch on 2006-06-08
> You usually get that error if the Zen is not switched on when you run Gnomad.
With the device switched on, try checking if it shows up in the device manager and please report back.

The Zen does show up in device manager. I connect it and then type "sudo gnomad2" i a terminal.

Then i get this error:

(gnomad2:7155): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed

---

### Post by vladdythephotogeek on 2006-06-12
[QUOTE=cnphch]The Zen does show up in device manager. I connect it and then type "sudo gnomad2" i a terminal.

Then i get this error:

(gnomad2:7155): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed[/QUOTE]

Greetings everyone. I'm new to Ubuntu and USING linux, i've used linux programs and used the file structure, but I haven't done anything liek this so far. I am really enjoying it, but this Zen issue is killing me.

I'm getting the same problem as above. I also have noticed I get the following problem when I try to reset hotplug.

 "pjv@pjv-desktop:~$ sudo /etc/init.d/hotplug restart
  touch: cannot touch `/var/lock/subsys/hotplug': No such file or directory"

I do believe that I have everything installed, all the dev packages and the like. Any assistance would be greatly appricated.

Best Regards,
Paul V

---

### Post by nathansnook on 2006-06-14
I have had some of the same issue that you have all had.  Please check the firmware verision of your Zens.  Also please look at the post by following the link below.

[http://ubuntuforums.org/showpost.php?p=1123152&postcount=7](http://ubuntuforums.org/showpost.php?p=1123152&postcount=7)

I have explained what I did in this post and do not want to cross post to much.

---

### Post by msak007 on 2006-06-18
I was considering your solution, nathansnook, but found a better one (no offense intended). You no longer need to downgrade the firmware version to strip MTP (unless you have some moral objection to anything M$ and want to purge your MP3 player from its standards :lol: ). You can now use libmtp to interface with MTP MP3 players, as a new version was just released earlier this month. I worked for several hours last night and finally got my sister's Creative Zen Micro working with Gnomad2. Here's what you need (3 major components):

1. First and foremost, libmtp. You can download it from [here]("http://libmtp.sourceforge.net/") (click on "File releases" to go to the download - latest version as of this writing is 0.0.8 ). The main page pretty much tells you what it's about, but it's an MTP protocol translated for *nix so that you can interface with MP3 players that use the evil MTP protocol. Download, compile, and install. I can't think of any dependencies that I didn't have right off the bat.

2. You also need libnjb. I know the repositories have it, but for some reason when I was installing gnomad it couldn't find the pkgconfig file for libnjb. It just didn't exist anwyhere on my hard drive. Easiest solution was just to download and compile from source. Get it [here]("http://libnjb.sourceforge.net/") (latest version as of this writing is 2.2.5). The only dependency I ran into here was needing the xml parser, so install "libxml-perl" (will also install the needed parser).

3. Last but not least, gnomad2. Even if you have this installed from the repositories, uninstall it and compile from source because the newest version (2.8.5) is needed to support MTP. As with the other 2, download, compile, and install. Make sure you have "libid3tag0-dev" before compiling.

* This is a very important step* Make sure when you configure libnjb and libmtp, use "./configure --prefix=/usr" - otherwise the needed libraries will be installed to a non-default location and you'll get errors launching gnomad. There's ways around it (creating symlinks to the files in their respective directories), but that's the easiest solution. And I know it's a given, but make sure you have installed "build-essential" to get all the needed compilers. You'll get errors early on enough to know if it's missing :) .

One last thing, for some reason gnomad must be launched as root to interface with the USB bus. I'm trying to edit sudoers to make it work so my sis doesn't have to enter the root password everytime, but haven't had any luck. If somebody can figure this part out, I'd appreciate it. If anybody wants to give this a try, I've gotten it working successfully on 2 comps. Try it out and let me know, maybe we can make it a sticky / faq :). If you guys run into any other errors or dependencies, let me know. My desktop has a ton of crap installed, but the above dependencies were the only ones I ran into problems with on a fresh install of Dapper on my sister's laptop.

Edit: sorry, I just realized that this is a Hoary forum. If you are still using Hoary, this solution may not work for you. If you are using Dapper, I've posted this in the appropriate Dapper forum [here]("http://ubuntuforums.org/showthread.php?t=199250").

---

### Post by BigRod on 2006-06-19
I have had no problems installing libnjb and gnomad2 in warty and hoary (following this guide or a similar one), but in dapper for some reason I am missing the /etc/hotplug directory entirely so when I get to the "cat nomad.usermap >> /etc/hotplug/usb/usb.usermap ; cp nomadjukebox /etc/hotplug/usb/ ; chmod a+x /etc/hotplug/usb/nomadjukebox" part it can't find the files in that direcory.  All the libraries are installed that need to be (libusb-dev, etc.).

Any ideas?  I'm gonna try creating the directory manually, but it seems like something is wrong.

---

### Post by BigRod on 2006-06-19
[QUOTE=BigRod]I have had no problems installing libnjb and gnomad2 in warty and hoary (following this guide or a similar one), but in dapper for some reason I am missing the /etc/hotplug directory entirely so when I get to the "cat nomad.usermap >> /etc/hotplug/usb/usb.usermap ; cp nomadjukebox /etc/hotplug/usb/ ; chmod a+x /etc/hotplug/usb/nomadjukebox" part it can't find the files in that direcory.  All the libraries are installed that need to be (libusb-dev, etc.).

Any ideas?  I'm gonna try creating the directory manually, but it seems like something is wrong.[/QUOTE]

Yeah, nevermind.  It's like the hotplug system isn't on my system at all, which doesn't seem to make an ounce of sense.  I tried looking around to see if maybe in dapper it is located in a different directory, but I can't find it.  Is that something I can apt-get (doubtful, but worth asking I guess)?

---

### Post by msak007 on 2006-06-19
Dapper doesn't use hotplug anymore, it uses udev - it's located in /etc/udev.

---

### Post by xyloweb on 2008-01-05
I kept getting this error message when trying to connect to Jukebox 3 via the USB and Gnomad2: "Could not open jukebox: usb_set_configuration: Connection timed out"

First I tried this:
[http://www.void.gr/kargig/blog/2007/06/23/gnomad2-usb_set_configuration-operation-not-permitted-fix/](http://www.void.gr/kargig/blog/2007/06/23/gnomad2-usb_set_configuration-operation-not-permitted-fix/)

Then, by accident, I tried connecting while the jukebox was off.  It worked!
I'm guessing that the manual (which I don't have) tells you to turn off the player when connecting to a computer.
I hope this helps someone else.

EDIT (01/10/2008): I believe that most/all of the problems were caused by totally dead batteries.  Maybe turning it off helped, or maybe I just got lucky.

---

### Post by cub on 2008-01-06
I have a Creative Zen Sleek Photo and been using Feisty and Gnomad 2.8.11 for a while to transfer songs to my Sleek. I'm looking for a way to easily edit my playlists but can't find one. In Gnomad I can choose 'Edit playlist' but all I can do there is rename the list. There is a Shuffle playlist choice as well but I'd like to set the order of the songs myself. Is that not possible? If I open the list I can remove songs but that's it.

---

