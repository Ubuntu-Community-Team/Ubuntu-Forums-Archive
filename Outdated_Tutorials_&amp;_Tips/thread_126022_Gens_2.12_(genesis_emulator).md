---
title: "Gens 2.12 (genesis emulator)"
date: 2006-02-05
forum: Outdated Tutorials &amp; Tips
---

### Post by chronusdark on 2006-02-05
This is my first contribution to the linux community and i would like to thank cdhotfire for helping me out with this

this is a Gens deb file i have seen many people who want this so i figured i would just make it myself

just install like this 
```

unzip gens.zip
sudo dpkg -i gens_2.12a-i386.deb
```

and there you go just type gens to launch or make a launcher for it

please tell me if you have any problems

---

### Post by MighMoS on 2006-02-05
Thanks for the deb file, but could we also have a source?  (AMD64 user here)

---

### Post by chronusdark on 2006-02-05
i just got the source from CVS
```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gens login
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gens co -P GensForLinux
```

make sure you do 

```
export CC=/usr/bin/gcc-3.4
```

or else the compile wont work

---

### Post by majikstreet on 2006-02-05
genesis as in sony genesis, the game system? how do you get games for it? I never got the game system emulator thing, like gameboy advance emulators and stuff...

---

### Post by chronusdark on 2006-02-05
like sega genesis but im not allowed to tell you where to get roms....you can do that on your own but it works great on my system and its easy to use

---

### Post by mustang on 2006-02-05
Interesting--I didn't even know gens existed for linux. 

I tried running it but it crashes hard (can't even go back to gdm) when I go into fullscreen mode. Looked okay otherwise.

---

### Post by darrenrxm on 2006-02-06
Thank you for making this howto. If you need roms you can get them on usenet. Or you used to be able to get them. Haven't checked in a few years... Another place you might be able to get them is irc. Also, I hear their is this search engine called "google". With this search engine you might be able to find some. 

Anyway, I do know for sure they are much harder to find then they used to be.

---

### Post by Jengu on 2006-02-06
Generally ROMs are *easier* to get nowadays through normal search engines. The games are so old Nintendo and Sega don't care to go after people over NES and SNES titles anymore I think.

---

### Post by LordBug on 2006-02-06
Actually, they do care.  Nintendo is VERY agressive about protecting their systems' ROMs.  Sega isn't so much.  Probably because they have no good games...  :)

Anyway, thanks for the quick-and-easy DEB file for Gens.

---

### Post by chronusdark on 2006-02-06
nintendo is so protective because roms are their backup plan whenever they need a lil cash they re-release super mario brothers with "new features" and make millions

---

### Post by saVTRonic on 2006-02-09
Thanks :)

---

### Post by MighMoS on 2006-02-13
I was able to build this in a 32-bit chroot, but for some reason it wont build AMD64 natively.  Anyone know why?

---

### Post by chronusdark on 2006-02-13
this emulator requires nasm to compile therefore it may be doing some code down on the machine code level stuff that is very arch dependant

---

### Post by Cesium on 2006-02-13
[QUOTE=LordBug]Actually, they do care.  Nintendo is VERY agressive about protecting their systems' ROMs.  Sega isn't so much.  Probably because they have no good games...  :)[/QUOTE]

I know you're being a smart ***, but BS.  SEGA has many great games and was one of the best producers of arcade games.

---

### Post by MighMoS on 2006-02-13
[QUOTE=chronusdark]this emulator requires nasm to compile therefore it may be doing some code down on the machine code level stuff that is very arch dependant[/QUOTE]
I've been trying to get it to at least compile (working would also be great), but I can't get it to work, and I haven't gotten some vague message about compatible libraries, but ```
gens_core/cpu/68k/cpu_68k.c:27: warning: initializer element is not computable at load time
gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for `M68K_Fetch[1].offset')
gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for `M68K_Fetch[1]')
```

Frustrating.  I've tried changing the hex values and adding some leading zeros, but I think AMD64 is less lax about *something* I don't know about.

---

### Post by Morbett on 2006-04-10
Does anyone here know what extension the roms for Gens usually are?

I found a Genesis rom with the zip extension .7z, but Gens won't load it.  So I assume I have the wrong file type.

Thanks.

---

### Post by escape on 2006-04-10
.7z is like .zip. I don't know if linux handles 7-zip.

---

### Post by zi99y on 2006-04-10
Yes you'll have to unpack the 7z files, but gens does support zipped files (.zip). 

The roms should be in .SMD or .BIN format if memory serves!

There is also DGen which is a pretty good genesis emulator if anyone has trouble with this - I installed it through synaptic but I think it's in universe - let me know if you need help finding.

---

### Post by badrad on 2006-06-04
[QUOTE=chronusdark]This is my first contribution to the linux community and i would like to thank cdhotfire for helping me out with this

this is a Gens deb file i have seen many people who want this so i figured i would just make it myself

just install like this 
```

unzip gens.zip
sudo dpkg -i gens_2.12a-i386.deb
```

and there you go just type gens to launch or make a launcher for it

please tell me if you have any problems[/QUOTE]

Sweet, thank you so much. I could not get the damn thing to compile, but this works like a charm!

The sound is delayed for me, the effects happen about .5 secs after the action. Any know how to fix?

Just one more issue - and its probably related to me using compiz. If I say fullscreen the window just moves to the center of the screen - it doesnt get any larger. Would really like to fullscreen it, and any help is appreciated.

---

### Post by GuitarHero on 2006-06-28
how do i get it in the applications menu?

---

### Post by j5tixc on 2006-07-03
Honestly thank you! I was struggling with Gcc-3.4 etc. to do this with dapper but your packet worked perfectly!

---

### Post by denisesballs on 2006-07-05
[QUOTE=GuitarHero]how do i get it in the applications menu?[/QUOTE]

First, copy [this]("http://jessejoe.com/~jesse/gens.png") image to /usr/share/pixmaps, then do

```
sudo gedit /usr/share/applications/gens.desktop
```

and put this in the file:

```
[Desktop Entry]
Type=Application
Version=1.0
Encoding=UTF-8
Name=Gens Sega Emulator
Comment=A Sega Genesis Video Game Emulator
Icon=gens.png
Exec=gens
Terminal=false
StartupNotify=false
Categories=Application;Game;ArcadeGame
```

PS, has anyone found a way to connect to someone else and play gens networked?

---

### Post by patrick295767 on 2006-07-08
> **escape said:**
> .7z is like .zip. I don't know if linux handles 7-zip.

to unpack p7zip:
```
sudo apt-get -f -y install p7zip

7z e thepackage7zpacked.7z   
# to unpack the 7z pack
```

---

### Post by HAARP on 2006-07-27
Did anyone get a newer version to compile andcan provide me with it?
2.14 is the newest.

---

### Post by -DarkMind- on 2006-08-26
thanks :D

---

### Post by goph-R on 2007-06-09
=D>
Thanks for it! I couldn't compile this stuff on my ubuntu, but with this .deb my problem is solved!

---

### Post by overlord_david on 2007-08-04
T_T Um, why doesn't it work? I installed it but it doesn't appear to do anything when I do. Where did it go? It doesnt appear to be in the wine folder or anything like that.

---

### Post by ciper on 2007-08-04
There is a tool that helps to find and label the correct roms. A version exists for all of the popular emulated home systems. Even bad dumps are identified as such. As of now all officially licensed games for the system have been dumped and are available in multiple formats (country, hacked, prototypes etc)

I seem to remember a non dos version but at the moment I couldnt find it. In the meantime here is the download page for the GoodGen application from its homesite. [http://www.allgoodthings.us/mambo/index.php?option=com_simpleboard&Itemid=42&func=view&id=1691&catid=4](http://www.allgoodthings.us/mambo/index.php?option=com_simpleboard&Itemid=42&func=view&id=1691&catid=4)

---

### Post by nickdr on 2007-10-29
what is the CVS password?

---

### Post by Dirkomatic on 2007-10-31
Can anyone figure out how to get gens to allow you to map a space bar to a game pad button?  I'd really like to use my MAME control panel for gens, but button three (maps to space) is useless.  It just shows -1 in the gens.cfg

---

### Post by kundalinikat on 2008-01-05
Yeah, what is the CVS password?

---

### Post by sargetech on 2008-03-27
OH SHIZZLE!!!
thanks my Ubuntu Roasted Brother
Worked great and the sounds are
on point!!!!

L L & P:popcorn::guitar:

---

### Post by anonanonanon on 2009-01-11
I'm a ubuntu noob and i manged to install it ok but when i try to configure a gamepad it scrolls through all the options in turbo speed and i can't change them. Any ideas?

---

### Post by Puzzlenoise on 2009-01-11
> **LordBug said:**
> Actually, they do care.  Nintendo is VERY agressive about protecting their systems' ROMs.  Sega isn't so much.  Probably because they have no good games...  :)
SEGA had many good games... they almost made only good games in the old days. 
The problem isn't that the games lack in quality... they had some games which were even better than what you'd find on the NES or SNES.

The problem is the management departement at SEGA today... but this is not the right place to be talking about this now.

My gens works perfectly. ^_^

---

### Post by thidenthi on 2009-04-09
thanks :)

it's work very good ;)

---

### Post by KiDDO646 on 2009-06-13
ive tried to install this but i have the wrong architecture 

this is what it says 

" Error: Wrong architecture 'i386' "

---

### Post by dark magshin on 2009-06-30
does any 1 know the cvs pass???

---

