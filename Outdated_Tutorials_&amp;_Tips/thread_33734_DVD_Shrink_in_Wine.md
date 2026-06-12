---
title: "DVD Shrink in Wine"
date: 2005-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by aragorn2909 on 2005-05-12
Sorry if I'm beating a dead horse here, but I JUST got DVD Shrink to work under Wine.  I would encounter either aspi errors, or Shrink just wouldn't recognize the drive, but its all figured out now.  For those also encountering these errors, hope this helps.  

Before running winetools, configure your DVD drive for scsi emulation:
[http://www.ubuntuforums.org/showthread.php?t=27369&highlight=scsi+decrypter](http://www.ubuntuforums.org/showthread.php?t=27369&highlight=scsi+decrypter)

Run winetools, and when asked for the mount point of your drive, enter:
"/media/cdrecorder".  Finish installing Wine.  Install DVD Shrink

This will enable DVD Shrink to see your drive, however, you'll still encounter aspi errors (at least I did, anyways).  To take care of that, you need to edit the ~/.wine/config file

sudo gedit ~/.wine/config

Under the [Version] heading, you'll find a line that says:
"Windows" = "win98"
this needs to be changed to 
"Windows" = "winxp"
save ~/.wine/config, and your ready to go.

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=aragorn2909]Sorry if I'm beating a dead horse here, but I JUST got DVD Shrink to work under Wine.  I would encounter either aspi errors, or Shrink just wouldn't recognize the drive, but its all figured out now.  For those also encountering these errors, hope this helps.  

Before running winetools, configure your DVD drive for scsi emulation:
[http://www.ubuntuforums.org/showthread.php?t=27369&highlight=scsi+decrypter](http://www.ubuntuforums.org/showthread.php?t=27369&highlight=scsi+decrypter)

Run winetools, and when asked for the mount point of your drive, enter:
"/media/cdrecorder".  Finish installing Wine.  Install DVD Shrink

This will enable DVD Shrink to see your drive, however, you'll still encounter aspi errors (at least I did, anyways).  To take care of that, you need to edit the ~/.wine/config file

sudo gedit ~/.wine/config

Under the [Version] heading, you'll find a line that says:
"Windows" = "win98"
this needs to be changed to 
"Windows" = "winxp"
save ~/.wine/config, and your ready to go.[/QUOTE]


Thank you very much. I will try this soon.

---

### Post by darkaudit on 2005-05-12
I've been having issues lately where:

a) The screen will blank just before DVD Shrink runs. As I do other operations, blank parts will come back.

b) In GNOME, KDE, and XFCE, the left side menu is blank. I can only select parts to omit from the main movie. I cannot do anything to the extras or menus. If I'm in Fluxbox, all operations and menus are available. BUT...

c) In Fluxbox, when the operation is over, and I return to the main screen, CPU use pegs at 100% and stays there, even after I've shut down DVD Shrink. I have to kill WINE to get the resources back.

Even the .debs from the Sourceforge repo are a month behind the current WINE version. Any word on when they'll catch up?

---

### Post by Heliode on 2005-05-12
I can report that DVD Shrink also works with Crossover Office 4.2.
Just make sure that, in the screen where you select the setup file, you specify 'Windows XP' or else you'll get  aspi errors.

Tnx Aragorn! Now I need Windows even less!

---

### Post by mrbass on 2005-05-12
Also make sure to throw in the quartz.dll if you wish to view playback video in dvdshrink's preview window (no sound though).  You can download it from my dvdshrink ubuntu guide.
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

---

### Post by mrbass on 2005-05-12
[QUOTE=darkaudit]I've been having issues lately where:
b) In GNOME, KDE, and XFCE, the left side menu is blank. I can only select parts to omit from the main movie. I cannot do anything to the extras or menus. If I'm in Fluxbox, all operations and menus are available. BUT...
[/QUOTE]

Resize it or easier just Maximize and UnMaximize the window (yes each and every time).

---

### Post by aragorn2909 on 2005-05-13
As a sidenote, Shrink will work without scsi emulation, as long as ~/.wine/config indicates xp

---

### Post by poofyhairguy on 2005-05-13
This thread is awesome.

---

### Post by mrbass on 2005-05-13
True DVDShrink doesn't require scsi emulation.   Note though in linux without dvd decrypter you couldn't backup The Grudge, Spanglish, Little Black Book, Resident Evil Apocolypse just to name a few.  All have ARcoSS protection which dvdshrink can't handle.

---

### Post by Patrick on 2005-05-14
this reply is not to kick the ts for posting this, but if you are going to install Wine and use dvdshrink to ripp dvds, why not use VMware to install windows and then use dvd rebuilder so you can use the cce

---

### Post by poofyhairguy on 2005-05-14
[QUOTE=Patrick]this reply is not to kick the ts for posting this, but if you are going to install Wine and use dvdshrink to ripp dvds, why not use VMware to install windows and then use dvd rebuilder so you can use the cce[/QUOTE]


Cause VMware costs money if you have any respect for copyright and fairness....

---

### Post by Heliode on 2005-05-14
[QUOTE=Patrick]this reply is not to kick the ts for posting this, but if you are going to install Wine and use dvdshrink to ripp dvds, why not use VMware to install windows and then use dvd rebuilder so you can use the cce[/QUOTE]

Because then you would need a license for VMWare, and a license for Windows.
With Wine you can do it for free (as in beer) with free (as in liberty) software. 

You shouldn't need Windows when you run Linux ;)

---

### Post by aragorn2909 on 2005-05-14
[QUOTE=Heliode]You shouldn't need Windows when you run Linux ;)[/QUOTE]

Exactly.  Personally, the 2 reasons why I run a Linux system are:
1 the fun of learning something new
2 to break my dependency on M$

The whole point to this thread is to get a nice little free app to work in Linux, nothing more, nothing less.

---

### Post by poofyhairguy on 2005-05-14
[QUOTE=aragorn2909]Exactly.  Personally, the 2 reasons why I run a Linux system are:
1 the fun of learning something new
2 to break my dependency on M$
[/QUOTE]

Here here!!!

I couldn't have said it better myself.

---

### Post by aragorn2909 on 2005-05-14
[QUOTE=mrbass]True DVDShrink doesn't require scsi emulation.   Note though in linux without dvd decrypter you couldn't backup The Grudge, Spanglish, Little Black Book, Resident Evil Apocolypse just to name a few.  All have ARcoSS protection which dvdshrink can't handle.[/QUOTE]
I know dvdbackup will handle css, will it handle ARcoSS?  The only reason I lost scsi emulation was an issue w/ synaptic asking for ubuntu install disk in "cdrom0", and wouldn't recognize "cdrecorder".

---

### Post by aragorn2909 on 2005-05-14
Another sidenote; instead of sudo gedit ~/.wine/config, you can also change "win98" to "winxp" from Winetools main menu by clicking "Edit the Wine configuration file" and making the appropriate change.

---

### Post by mrbass on 2005-05-15
[QUOTE=aragorn2909]I know dvdbackup will handle css, will it handle ARcoSS?  The only reason I lost scsi emulation was an issue w/ synaptic asking for ubuntu install disk in "cdrom0", and wouldn't recognize "cdrecorder".[/QUOTE]

Yeah same thing happened to me. 
sudo gedit /etc/apt/sources.list

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog blah blah blah
change to 
deb cdrecorder:[Ubuntu 5.04 _Hoary Hedgehog blah blah blah

Does this work?

Rippers that deal with ARcoSS (fake errors on .vobs protection)
Windows (DVD Decrypter, DVD43, AnyDVD)
Mac (MacTheRipper)
Linux (none that I'm aware of)

---

### Post by mrbass on 2005-05-15
[QUOTE=poofyhairguy]Here here!!!

I couldn't have said it better myself.[/QUOTE]

I have about 5 things I need to do before I wipe my windows 2000 and kiss it goodbye.  One is show a friend Battle for MiddleEarth game..already finished it just wanted to briefly show him since he's a big LOTR fan.  Others include write a couple dvd guides.  Other is try out irfanview in wine (think I tried long time ago it was a no go)  If not then find replacement or collection of image manipulation programs to fill the need.  Anyway I figure in the next week I'll be 100% on ubuntu, other linux distros, and mac tiger.

---

