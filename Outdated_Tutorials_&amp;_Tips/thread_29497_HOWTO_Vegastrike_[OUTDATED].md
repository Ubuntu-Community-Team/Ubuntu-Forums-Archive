---
title: "HOWTO: Vegastrike [OUTDATED]"
date: 2005-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2005-04-24
This is a howto install Vegastrike as Global user and with the bleeding edge of Vegastrike.

First make sure that your repositories are setup. You can read all about it here: [http://ubuntuguide.org/](http://ubuntuguide.org/)

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gcc
sudo apt-get install libjpeg62-dev
sudo apt-get install libopenal0
sudo apt-get install libopenal0-dev
sudo apt-get install libopenal-dev
sudo apt-get install python2.4
sudo apt-get install python-opengl
sudo apt-get install cvs
sudo apt-get install libsdl-mixer1.2-dev
sudo apt-get install libxmu-dev
sudo apt-get install libsdl1.2-dev

```

If you are using Nvidia drivers:

```

sudo apt-get install nvidia-glx-dev

```

I' not sure which one to use if it's ATI card, can I get some feedback on this one. But I think it's *xorg-driver-fglrx-dev*. Then just change *nvidia-glx-dev* with *xorg-driver-fglrx-dev*.

Now there's several choices to install Vegastrike:
(1). Vegastrike without music ~143 mb
(2). Vegastrike with music ~ 204 mb
(3). Vegastrike Developer version ~ varied

--------------------------------------------------------------------

**(1). Vegastrike without music - The script downloads ~143 mb**
*You want music? Go to choice (2).*

Grab **Vegastrike 0.4.3 Download/compile Script** [here](http://vegastrike.sourceforge.net/files/linux_vegastrike-0.4.3.sh) 

Remember where you saved it.

```

cd where/the/file/is
sudo sh linux_vegastrike-0.4.3.sh

```

This may take awhile. Grab a cup of coffee or something ;)

When it's done compiling and installing then:

```

cd
sudo chmod 777 .vegastrike
cd /home/<username>/.vegastrike
sudo chmod 777 vegastrike.config

```

To setup vegastrike type '*vssetup*' in the terminal or make a launcher.

To play vegastrike type '*vegastrike*' in the terminal or make a launcher.

--------------------------------------------------------------------------


**(2). Vegastrike with music**

The base installation [here](http://prdownloads.sourceforge.net/vegastrike/vegastrike-0.4.3-base.bz2.run?download)  ~145 mb

The Music installation [here](http://prdownloads.sourceforge.net/vegastrike/vegastrike-0.4.3-music.bz2.run?download)  ~ 61mb

```

cd /where/you/saved/the/file(s)
sudo sh vegastrike-0.4.3-base.bz2.run
sudo sh vegastrike-0.4.3-music.bz2.run
cd
sudo chmod 777 .vegastrike
cd /home/<username>/.vegastrike
sudo chmod 777 vegastrike.config

```

To setup vegastrike type '*vssetup*' in the terminal or make a launcher.

To play vegastrike type '*vegastrike*' in the terminal or make a launcher.

------------------------------------------------------------

**(3). Vegastrike developers version total bleeding edge.**

Get it [here](http://vegastrike.sourceforge.net/files/linux_vegastrike-cvs.sh) 

```

cd where/the/file/is
sudo sh linux_vegastrike-cvs.sh
cd
sudo chmod 777 .vegastrike
cd /home/<username>/.vegastrike
sudo chmod 777 vegastrike.config

```

To setup vegastrike type '*vssetup*' in the terminal or make a launcher.

To play vegastrike type '*vegastrike*' in the terminal or make a launcher.

Just run the script again to update the developer version

------------------------------------------------------------------------


If I missed something eg. dependency etc. etc. please let me know.



.:=The AI Dude=:.

---

### Post by Burgundavia on 2005-04-24
Please note, this is packaged and in the repos as well, for those who don't want to break their box.

Corey

---

### Post by Perfect Storm on 2005-04-24
Yes it's in the package but it's 0.4.2
But there's a huge diffrent between 0.4.2 and 0.4.3 The animation, the gameplay etc. have been considerable improved.

---

### Post by poofyhairguy on 2005-05-13
bump

---

### Post by qrazi on 2005-05-15
[QUOTE=poofyhairguy]bump[/QUOTE]
 i installed vegastrike, but it didnt install in /home/<usr>/.vegastrike directory, but in /usr/local/games

also, vssetup doesnt work. vegastrike does work, but i only got the setup screen the first time i installed it.

---

### Post by equilibrium on 2005-05-16
hmm this is very annoying :(

downloaded and installed the game using the .run files but there's no vssetup and if I run vegastrike the game loads but in some stupidly low resolution.

If I run vsinstall.sh --setup

I get

/home/user/vegastrike/bin/setup: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I tried manually editing the vegastrike.config but it's just stupidly complex.

Might go back to playing vendetta  :???:  :roll:

---

### Post by qrazi on 2005-05-17
"vegastrike setup" gives me a setup screen to change resolution and detail settings...

however, i cannot get the launcher to work, only start vegastrike with "vegastrike". i cant save games, and cant gcreate pilots....

---

### Post by mike998 on 2005-05-17
I tried this with the cvs version and got :
```
checking for python... configure: error: *** Python version 2.2 or later not found!
Error running ./configure
``` 
I tried installing python 2.2 as well, but got the same error.

---

### Post by Perfect Storm on 2005-05-22
You should take these errors to the Vega Strike >Forum, I know the guys over there really wants inputs, bugs reports etc.

---

### Post by AndyAWS on 2005-05-25
You missed a dependancy - Glut 3.7 or greater required...

Trying packages glutg3 and glutg3-dev...

Also had a warning that sdl-config could not be found

Trying package libsdl1.2-dev

---

### Post by AndyAWS on 2005-05-25
Still says glut is too old...as far as I can tell I have 3.8

---

### Post by AndyAWS on 2005-05-25
I see they have 0.4.3 binaries for download...I'll try that.

---

### Post by AndyAWS on 2005-05-25
Installed libxmu-dev ... now it compiles

---

### Post by AndyAWS on 2005-05-25
One more thing, if you want audio support you need package libsdl-mixer1.2-dev...so to recap I had to install 3 packages other than what you listed:

libsdl-mixer1.2-dev
libxmu-dev
libsdl1.2-dev

The GLUT packages I tried weren't needed although I suspect the latest freeglut is a requirement.

Letting it recompile...will try it tomorrow.

---

### Post by Perfect Storm on 2005-07-14
Updated the howto.

---

### Post by AndyAWS on 2005-07-14
I did manage to get this compiled, works great, thanks AI.

The 0.4.3 binaries also work well...they use a Loki installer.

BTW anyone who tries VS and likes it should also checkout Privateer:Remake and Wing Commander Universe (Mods to VS). Both are still heavy in development.

For more info go to Vegastrike's Forums.
[http://vegastrike.sourceforge.net/forums/](http://vegastrike.sourceforge.net/forums/)

---

### Post by Perfect Storm on 2005-07-22
Aye, tried it. It takes me back to the good old days ^^

---

### Post by neurosion on 2005-08-03
[QUOTE=equilibrium]If I run vsinstall.sh --setup

I get

/home/user/vegastrike/bin/setup: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
[/QUOTE]I found the package you need through synaptic.  It's called libstdc++-2.10-glibc2.2.  That will allow you to run "vegastrike setup" and get the game running.

---

### Post by duan on 2005-09-04
[QUOTE=neurosion]I found the package you need through synaptic.  It's called libstdc++-2.10-glibc2.2.  That will allow you to run "vegastrike setup" and get the game running.[/QUOTE]
 sudo apt-cache search libstdc++* shows the following package available. 
libstdc++2.10-glibc2.2

I think it is just a typo from neurosion, because 
libstdc++-2.10-glibc2.2 (with the hyphen before the 2) doesn't exist.

This fixed the libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory complaint and now
sh vegastrike setup brings up the setup box.

Thanks.

---

### Post by nsa_767 on 2005-11-26
Hi there,

Tow things, one a little update and the other a question.

[LIST=1]
[*]***vssetup*** no longer works, you have to us ***vegastrike setup*** to get setup.
[*]I downloaded "Privateer: Gemini gold", but I'm having difficulties getting it installed properly... tried using the same commands for it as described in this guide for vegastrike, and I got it installed, but when I type "privateer" in the terminal it states "command not found". 
[/LIST]

I think my problem has to do with the setting up of symbolic links, but that's something I know too little about... Guess I'll have to Google it.

AI, since you've installed Gemini before, it might be a useful addition to this How-To.

Anyway, thanks for a great HOWTO!

---

### Post by demonhunter on 2006-12-20
> **equilibrium said:**
> hmm this is very annoying :(

downloaded and installed the game using the .run files but there's no vssetup and if I run vegastrike the game loads but in some stupidly low resolution.

If I run vsinstall.sh --setup

I get

/home/user/vegastrike/bin/setup: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I tried manually editing the vegastrike.config but it's just stupidly complex.

Might go back to playing vendetta  :???:  :roll:

See if you have /usr/lib/libstdc++.so.6. If not, install package called "libstdc++6" which should give you that lib. Then you need to do a symlink for it to work: "ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++-libc6.2-2.so.

:cool:

---

### Post by Sitenl on 2007-02-19
```
# vssetup
Unable to read from setup.config

```

Err... where should be this file?

---

### Post by Perfect Storm on 2007-02-19
This howto is old and not supported anymore (gonna, shut it down). If you use one of the newer Ubuntu releases you can find it in the repo.

If you want the newest SVN version - [http://vegastrike.sourceforge.net/wiki/HowTo:Compile_from_CVS](http://vegastrike.sourceforge.net/wiki/HowTo:Compile_from_CVS)

---

