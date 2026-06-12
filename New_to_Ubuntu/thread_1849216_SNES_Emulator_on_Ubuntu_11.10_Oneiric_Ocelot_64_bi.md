---
title: "SNES Emulator on Ubuntu 11.10 Oneiric Ocelot 64 bit?"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by gdbutcher on 2011-09-24
Can anyone recommend a SNES Emulator for Ubuntu 11.10 Oneiric Ocelot 64 bit?

For some reason the excellent SNES9x-gtk has been removed from the repos.
ZSNES wont install from the Ubuntu software Centre on 64 bit Oneiric either. :confused:

---

### Post by MarblePanther on 2011-10-14
I'm wondering the same thing.

Just installed Kubuntu 11.10, and lo and behold my beloved snes9x is missing!

When I try to install zsnes (no 64 bit version for some reason) it says it has to remove some of my applications that I wont part with, like Audacious music player for instance.

Does anyone know why snes9x has been removed?  It was great in 11.04.

---

### Post by Zayteph on 2011-10-15
I installed Znes in Ubuntu 11.10 64 bits using these packages:

Depedence: [URL="http://www.linuxtotal.org/download/file.php?id=10"]lib32ao.deb
[/URL] 
Zsnes: [URL="http://www.linuxtotal.org/download/file.php?id=9"]zsnes_1.510-2.1ubuntu1.1_amd64.deb
[/URL] 
Enjoy.

---

### Post by dawnclover on 2011-10-16
> **Zayteph said:**
> I installed Znes in Ubuntu 11.10 64 bits using these packages:

Depedence: [URL="http://www.linuxtotal.org/download/file.php?id=10"]lib32ao.deb
[/URL] 
Zsnes: [URL="http://www.linuxtotal.org/download/file.php?id=9"]zsnes_1.510-2.1ubuntu1.1_amd64.deb
[/URL] 
Enjoy.

Thank you, I've been looking for this for the last few hours!

---

### Post by mister_playboy on 2011-10-16
I think bsnes is available in the repos now... definitely the way to go if you have a recent computer.

---

### Post by frankob on 2011-10-17
Yes, but it doesn't recognize any roms... Or am I missing something? I am clickin on System > Load cartridge... Then I browse to the folder where I keep my roms, and it shows non of them. :-(

---

### Post by galacticaboy on 2011-10-17
Zsnes should be in the repos, check Synaptic for it. If not, playdeb.net has it!

---

### Post by frankob on 2011-10-17
It is there, but it is a i386 package... If I try to install it, it removes loads of my regular 64 bit packages, including ubuntu-desktop. :-/ And installing 32 bit packages the old way just doesn't work anymore... This multiarch "feature" is a complete mass. At least at this moment. Hope there will be improvements in the future...

---

### Post by frankob on 2011-10-19
Oh, you're talking about Snes9x, but I was referring to Zsnes in my last post...
But it's a good advice, anyway.

---

### Post by frankob on 2011-10-20
I DID IT! :-D

I managed to install a functional ZSNES on Oneiric 64, without losing my regular 64 bit software. Yay! :-D

What I did?

I found in my home this deb package ([http://www.mediafire.com/file/xqc9fwvp0d2uum6/zsnes_1.510-2.2ubuntu5_amd64.deb](http://www.mediafire.com/file/xqc9fwvp0d2uum6/zsnes_1.510-2.2ubuntu5_amd64.deb)) I downloaded somewhere from the internet some time ago, which seems to be newer than the one linked above by Zayteph. BTW, Zayteph's package did install on my computer, but the executable just wouldn't work for some reason... So I installed this package I found, which basically just installs a 32 bit version od zsnes adapted to 64 bit Ubuntu. I did ```
sudo dpkg -i zsnes_1.510-2.2ubuntu5_amd64.deb
```. The installation went well.
But when I tried to run it (from terminal, to test it out) it said > zsnes: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directorySo I searched my system for that lib on my hard drive first, I did:
```
sudo updatedb
locate libGL.so.1
```And I found out that I already have that lib, in both 32 and 64 bit versions on my system... After an hour or so of research around the internet and of try-and-fail, I finally decided to try to softlink the 32 bit version of the lib (which in my case is placed at /usr/lib32/mesa/libGL.so.1.2) to /usr/lib/ folder. So I did:
```
cd /usr/lib/
sudo ln -s /usr/lib32/mesa/libGL.so.1.2 libGL.so.1
```Then I retried to run zsnes, and it finally worked! :-)

I guess the location of libGL.so.1.2 depends on the driver used or something. So before linking check out where the lib is located on your computer, first. And it has to be the 32 bit version of it, zsnes is 32 bit sofware.

I hope this is of some help. :-)

---

### Post by BigSilly on 2011-10-21
> **Chauncellor said:**
> seems Debian removed it intentionally: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=617588](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=617588)

Since they are not willing to keep it in the repos it is up to Ubuntu to host it.

I have submitted a report [_here_]("https://bugs.launchpad.net/ubuntu/+bug/877073"). Please confirm/me too it!

SNES9X-Gtk is different to regular old SNES9X. You're much better off with SNES9X-Gtk, and luckily the developer Brandon Wright has provided a new update to his PPA for the app so it's now available for Oneiric on both 32 and 64 bit. [Get it here]("https://launchpad.net/~bearoso/+archive/ppa"). Thank God too, I couldn't live without this brilliant emulator.

Hope this is of some use to you Ubuntu-loving SNES fans. :)

---

### Post by thepisu on 2011-10-25
> **BigSilly said:**
> SNES9X-Gtk is different to regular old SNES9X. You're much better off with SNES9X-Gtk, and luckily the developer Brandon Wright has provided a new update to his PPA for the app so it's now available for Oneiric on both 32 and 64 bit. [Get it here]("https://launchpad.net/~bearoso/+archive/ppa"). Thank God too, I couldn't live without this brilliant emulator.

Hope this is of some use to you Ubuntu-loving SNES fans. :)

+1 for [Brandon Wright Snes9x PPA]("https://launchpad.net/~bearoso/+archive/ppa")!

---

### Post by Sionek on 2011-10-31
Thanks! Creating the link on the /usr/lib/ folder solved my problem too!

I was having problem playing Humble Bundle games on Oineric Ocelot, but I was getting the same error on all games. Now everything runs fine! :)

---

### Post by dasnk on 2012-01-08
I wanted to install Zsnes..


So I opened ubuntu software center and typed "zsnes" in the search box. 

Sure enough there it appears in the list "ZSNES emulator". So i click the "More info" button.. only to get a "NOT FOUND, There isn't a software package called zsnes in your software sources".

I thought that is a bit silly to show me packages that cannot be installed. So anyway I closed the ubuntu software center.. Don't know why I bothered trying to use it anyway.

I proceeded to type 'sudo apt-get install zsnes" in the terminal.
This command proceeded to remove Ubuntu-desktop, Virtualbox, VLC ... and a load of other things.

Great stuff.

---

### Post by frankob on 2012-01-10
Try what I did above. I had exactly the same experience as you. That is how I solved it.

---

### Post by Syntrel on 2012-02-15
Here's a direct link to the deb package for Snes9x-GTK Oneiric amd64 PPA.

[https://launchpad.net/~bearoso/+archive/ppa/+build/2860375/+files/snes9x-gtk_1.53.81-1%7Eoneiric1_amd64.deb](https://launchpad.net/~bearoso/+archive/ppa/+build/2860375/+files/snes9x-gtk_1.53.81-1%7Eoneiric1_amd64.deb)

Have fun =)

---

### Post by Syntrel on 2012-02-15
> **dasnk said:**
> I wanted to install Zsnes..


So I opened ubuntu software center and typed "zsnes" in the search box. 

Sure enough there it appears in the list "ZSNES emulator". So i click the "More info" button.. only to get a "NOT FOUND, There isn't a software package called zsnes in your software sources".

I thought that is a bit silly to show me packages that cannot be installed. So anyway I closed the ubuntu software center.. Don't know why I bothered trying to use it anyway.

I proceeded to type 'sudo apt-get install zsnes" in the terminal.
This command proceeded to remove Ubuntu-desktop, Virtualbox, VLC ... and a load of other things.

Great stuff.


You can't just click download & install for whatever you want.  Like every other brand and distro, you have to make sure whatever you are trying to install is compatable with your version of Ubuntu.  Zsnes does not have a version that is suited for 11.10 amd64/x86_64.  You need to "shop around before you buy."

---

### Post by Chronon on 2012-02-16
> **dasnk said:**
> I wanted to install Zsnes..


So I opened ubuntu software center and typed "zsnes" in the search box. 

Sure enough there it appears in the list "ZSNES emulator". So i click the "More info" button.. only to get a "NOT FOUND, There isn't a software package called zsnes in your software sources".

I thought that is a bit silly to show me packages that cannot be installed. So anyway I closed the ubuntu software center.. Don't know why I bothered trying to use it anyway.

I proceeded to type 'sudo apt-get install zsnes" in the terminal.
This command proceeded to remove Ubuntu-desktop, Virtualbox, VLC ... and a load of other things.

Great stuff.

When you saw the packages that were going to be removed you could have said no.

---

### Post by mastergkage on 2012-02-16
Is there any automatic search like when we are using 64bit it will only give us 64bit software? Compatible to our system setting and version of ubunutu right?

---

### Post by misterbk on 2012-03-09
Maybe the Windows version of zsnes (or some other Windows snes emulator) could be made to run in Wine?

I do not see bsnes in the repos.  Do you have to add something special to get it in there?  (I've enabled everything standard in 11.10 x64 except for source.)

Zsnes so far is not running for me.  I get the following:

```

$ zsnes 
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Segmentation fault

```

[EDIT]
If I add permission for myself:

sudo chgrp me /dev/input/event? mouse?
sudo chmod g+r /dev/input/event? mouse?

I still get a segfault, just without those errors.
```

$ zsnes 
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 4 mice detected.
Using ManyMouse for:
Mouse 0: iMON Panel, Knob and Mouse(15c2:ffdc)
Mouse 1: HID 1241:1111
Segmentation fault


```

---

### Post by misterbk on 2012-03-09
Woot!

After some experimenting I got it running.  I was trying the 32-bit-forced-to-x64-install version and that didn't work for me, but Zayteph's installer did!

I guess the secret is to just try everything until something works.

I believe giving my user permission to directly read those input devices helped.  If I set things back the way they were, the "working" install of zsnes gives those input errors and can't find mice etc.

Yay for still trying to use software developed in the late 90's, several distros, a CPU architecture and a full change in programming paradigms removed from the original authoring!

Is there a MODERN snes emulator for Linux? I'd love to know.

---

### Post by misterbk on 2012-03-09
> **Parrish416 said:**
> <snip>Just installed Kubuntu 11.10, and lo and behold my beloved snes9x is missing!

There ARE only 3 pages in this thread...  :p

snes9x was removed because it hadn't been maintained in years and could not satisfy its dependencies in modern ubuntu.  Then it sounds like the developer may have updated it, but not soon enough to prevent its removal.  I believe someone posted a link where to get a new version.


As far as my adventure in zsnes, starting to think it may bee too old.  I used to prefer zsnes because it had flawless sound support, but I'm getting frequent hiccups on a system that is many, many times more powerful than needed to run snes games.

(Core i3, plenty RAM, no blending modes enabled.)

```

ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.

```

I'll see if I can fix it by upping the minimum clock on the process scheduler...  we'll see how this goes.

---

### Post by pootan on 2012-03-09
Zsnes was the king of snes emulation 5 years ago but it has now been passed by the likes of Bsnes and Snes9x. If you can get either one of those then you will be better off.

---

### Post by misterbk on 2012-03-09
> **pootan said:**
> Zsnes was the king of snes emulation 5 years ago but it has now been passed by the likes of Bsnes and Snes9x. If you can get either one of those then you will be better off.

I would believe it.  Zsnes definitely shows its age.

Any idea what might have been wrong for that guy who couldn't get bsnes to recognize his roms?  I have lots of emulators to get working (mame, atari2600, nes) so some advice which to try would help.  (snes9x vs. bsnes)

I do have Google I suppose...  I'll see if anyone else is talking about snes emulators these days.

---

### Post by pootan on 2012-03-09
Bsnes was considered the best when I was looking it it about 7 months ago. Bear in mind though that the discussions were about the windows versions of both software. I have no idea on how Bsnes works on Linux but I do know Snes9x works almost on par with it's windows counterpart and will be all you need.

---

### Post by Shazzner on 2012-04-14
> **Syntrel said:**
> Here's a direct link to the deb package for Snes9x-GTK Oneiric amd64 PPA.

[https://launchpad.net/~bearoso/+archive/ppa/+build/2860375/+files/snes9x-gtk_1.53.81-1%7Eoneiric1_amd64.deb](https://launchpad.net/~bearoso/+archive/ppa/+build/2860375/+files/snes9x-gtk_1.53.81-1%7Eoneiric1_amd64.deb)

Have fun =)

Don't mean to bump an old thread, but for me and others looking for snes emulation in Precise this worked great!

(zsnes had audio issues, bsnes doesn't support .smc roms)

---

### Post by Cookyt on 2012-08-15
> **misterbk said:**
> I would believe it.  Zsnes definitely shows its age.

Any idea what might have been wrong for that guy who couldn't get bsnes to recognize his roms?  I have lots of emulators to get working (mame, atari2600, nes) so some advice which to try would help.  (snes9x vs. bsnes)

I do have Google I suppose...  I'll see if anyone else is talking about snes emulators these days.

I was shopping around for a snes emulator, and wound up with bsnes installed, but unable to play anything.  The reason is because bsnes doesn't support .smc files; it only supports .sfc.  

The difference between the two is a trivial 512 byte header in the smc file, so I wrote a python script which cuts out the first 512 bytes of the file.  Works like a charm under bsnes, here's the script:

```

#!/usr/bin/env python
import sys
import re

if (len(sys.argv) < 2 or sys.argv[1] == "-h" or sys.argv[1] == "--help"):
    print "A tool for converting .smc SNES ROM files to .sfc format."
    print "Unless specified it creates a new file of the same name as the"
    print "orginal, but with a .sfc extension, overwriting any old file in the"
    print "current directory."
    print "Usage: \n\t" + sys.argv[0] + " input_file [output_file]"
    sys.exit(1)

if (sys.argv[1][-3:] != "smc"):
    userinput = "none"
    while (userinput.lower() != "y" and userinput.lower() != "n"):
        userinput = raw_input("file does not end in .smc, proceed? (Y/n)")
    if (userinput.lower() == "n"):
        sys.exit(2)

fin = open(sys.argv[1], "rb")

i=0
while (i < 512):
    c = fin.read(1)
    if ((i == 8 and c != "\xaa") or (i == 9 and c != "\xbb")):
        print "input file does not seem to be in SMC format, ending..."
        sys.exit(3)
    if (c == ""):
        print "file too short"
        sys.exit(4)
    i += 1

if (len(sys.argv) == 3):
    newname = sys.argv[2]
else:
    newname = re.sub(r"\..*$", r".sfc", sys.argv[1])
fout = open(newname, "wb")

while (c != ""):
    c = fin.read(1)
    fout.write(c)

```Save it to a file or download it from below, and run it as so (assuming you named it smc2sfc.py):
```
./smc2sfc.py input_file.smc
```It'll create another file called input_file.sfc in the working directory.

---

### Post by jhscheer on 2012-12-22
> **Cookyt said:**
> I was shopping around for a snes emulator, and wound up with bsnes installed, but unable to play anything.  The reason is because bsnes doesn't support .smc files; it only supports .sfc.  

The difference between the two is a trivial 512 byte header in the smc file, so I wrote a python script which cuts out the first 512 bytes of the file.  Works like a charm under bsnes, here's the script:



    Actually, there's a small tool coming with bsnes (v084) called snespurify which does exactly this.

---

