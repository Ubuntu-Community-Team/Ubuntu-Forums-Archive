---
title: "HOWTO: Play Doom, Hexen, and Heretic using Doomsday 1.9 beta-4"
date: 2007-01-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Jivicin on 2007-01-03
What started as a peaceful evening surfing [digg.com]("http://www.digg.com/gaming_news/Play_Doom_Doom_2_Heretic_Hexen_in_Hi_res_on_ANY_computer") developed into an entire night of playing with Doomsday.  This magic little peace of software allows you to play Doom, Hexen, and Heretic on ubuntu, provided you've got OpenGL up and running.

This guide has two parts.  The first being how to install Doomsday and get it up and running, and the second being how to install the hi-res models to give old school Doom a face lift.  :-D

**[SIZE="4"]Installing Doomsday[/SIZE]**

1.  Make sure the following lines are in your /etc/apt/sources.list (they should be if you've ever run Automatix):
```
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
```

2.  Install the Doomsday dependencies and the shareware Doom wad (the -dev packages of the SDL libraries are needed for the source build):
```
sudo apt-get install doom-wad-shareware libsdl-sound1.2 libsdl-net1.2 libsdl-mixer1.2 timidity

```

3.  Build and install Doomsday from source, available [here]("http://prdownloads.sourceforge.net/deng/deng-1.9.0-beta4.tar.gz?download").

3 (alternative). curtis3389 was nice enough to host the compiled package.  Execute the following commands from your home directory:
```
wget http://curtis3389.googlepages.com/deng-1.9.0_beta4-1_i386.deb
sudo dpkg -i deng-1.9.0_beta4-1_i386.deb
```

4.  Now that Doomsday is installed and the libraries are in place, we need to create a directory and a script to execute Doomsday.  First, create a directory that Doomsday will use for save games and configuration files.  I chose to do it from my home directory:
```
mkdir doomsday && cd doomsday/

```

Next we need to create the script.  Open up your favorite text editor and paste in this code:
```
#!/bin/sh
/usr/local/bin/doomsday  -g jdoom -file /usr/share/games/doom/doom1.wad
```
It will be useful to make changes to the script later rather than repeatedly execute it from the command line.  
NOTE:  If you have the commercial versions of Doom or Doom 2, simply replace the path of the shareware WAD file with that of the commercial version.

Save it as doom.

Next, make the script executable:
```
chmod +x doom
```

5.  The moment of truth: execute the script. ```
./doom
```  If everything went ok, you should see a startup screen followed by the Doom main menu.  If it did, congrats!  If by some chance it didn't, post the error your getting and I'll try to help out.

**[SIZE="4"]Installing the Hi-Res Models[/SIZE]**

Following the guide at [http://dengine.net/dew/index.php?title=How_to_load_resources_from_command_line](http://dengine.net/dew/index.php?title=How_to_load_resources_from_command_line) is the simplest way to get it up and running.  After the files for the resource packs are moved to the correct places, simply add ```
-def }Defs/jDoom/jDRP.ded -file }Data/jDoom/jDRP.pk3
``` to the startup script.

**[SIZE="4"]References[/SIZE]**
Addons to Doomsday - [http://forums.newdoom.com/showthread.php?t=11670](http://forums.newdoom.com/showthread.php?t=11670)
DoomsdayHQ - [http://www.doomsdayhq.com/](http://www.doomsdayhq.com/)
Doomsday Wiki - [http://dengine.net/dew/index.php?title=Main_Page](http://dengine.net/dew/index.php?title=Main_Page)

**[SIZE="4"]Troubleshooting[/SIZE]**
Check these sites out for some basic help:
[http://forums.newdoom.com/forumdisplay.php?f=80](http://forums.newdoom.com/forumdisplay.php?f=80)
[http://dengine.net/dew/index.php?title=Category:Troubleshooting](http://dengine.net/dew/index.php?title=Category:Troubleshooting)
[http://dengine.net/dew/index.php?title=Category:HOWTO](http://dengine.net/dew/index.php?title=Category:HOWTO)
[http://dengine.net/dew/index.php?title=Command_line_options_reference](http://dengine.net/dew/index.php?title=Command_line_options_reference)

**[SIZE="4"]Miscellaneous[/SIZE]**
If you want to get crazy, you can install the models, environmental pack, and updated sound files availble under the link at "Addons to Doomsday".  Then you'd have a startup script that looked something like this:
```
#!/bin/sh
/usr/local/bin/doomsday -g jdoom -file /usr/share/games/doom/doom1.wad \
 -def }Defs/jDoom/jDRP.ded \
 -file }Data/jDoom/jDRP.pk3 \
 -file }Data/jDoom/jDEP.pk3.zip \
 -file }Data/jDoom/d1music.pk3  \
 -file }Data/jDoom/d2music.pk3  \
 -file }Data/jDoom/jdui.pk3.zip  \
 -file }Data/jDoom/plmusic.pk3  
```

Enjoy! 8)

---

### Post by curtis3389 on 2007-01-07
I've got Doomsday running, but whenever I try to play a game (Doom, DoomII, Hexen), I get insane amounts of lag. Any ideas on why this would be so?

---

### Post by Jivicin on 2007-01-09
Do you have OpenGL working on your computer?  What kind of graphics card do you have?

Try running "fglrxinfo" in the console and paste the output

---

### Post by curtis3389 on 2007-01-09
I figured it out. I was using the default drivers for my Radeon 9800 Pro. I switched to the ATI Radeon open source driver and everything went swell.

---

### Post by lime4x4 on 2007-01-09
here's the error i'm getting on edgy

checking SDL/SDL_net.h usability... no
checking SDL/SDL_net.h presence... no
checking for SDL/SDL_net.h... no
configure: error: *** SDL_net not found!

---

### Post by curtis3389 on 2007-01-09
Here's how I installed Doomsday on Edgy.

[LIST=1]
[*]Open the terminal (Applications->Accessories->Terminal)
[*]Open /etc/apt/sources.list ```
sudo gedit /etc/apt/sources.list
```
[*]Add the following lines to the end of the file ```
deb http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse
```
[*]Save and close the file
[*]Run the following commands in the terminal (one at a time)
Note: You may have to do this more than once to get the key. It will be confirmed with an "OK"
 ```
gpg --recv-keys 0x4B6E7209
gpg --export -a 0x4B6E7209 > Yagisan.asc
sudo apt-key add Yagisan.asc
```
[*]Now update your repositories ```
sudo apt-get update
```
[*] Open Synaptic Package Manager (System->Administration->Synaptic Package Manager)
[*]Search for the word "doomsday" (no quotes)
[*]Your results **should** contain the package "deng". Just install deng and all the required packages (including SDL) will be installed too.
[*] Enjoy!

Note: Also with those search results will be all the installers for the Doomsday games. If you have the original wads, I highly suggesting installing theses along with some of the other packages related to Doomsday.
All the descriptions of the packages can be found here -> [http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu]("http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu")
[/LIST]

---

### Post by lime4x4 on 2007-01-09
new error now

checking target system type... i686-pc-linux-gnu
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking curses.h usability... yes
checking curses.h presence... yes
checking for curses.h... yes
checking SDL/SDL_net.h usability... no
checking SDL/SDL_net.h presence... no
checking for SDL/SDL_net.h... no
configure: error: *** SDL_net not found!
john@john-edgy:~/Desktop/deng-1.9.0-beta4$

---

### Post by curtis3389 on 2007-01-09
Be sure to install the SDL dev packages also.
EX: libsdl-net1.2 & libsdl-net1.2-**dev**

---

### Post by Jivicin on 2007-01-16
Bumping this up because a source build is no longer required.  Some new people might want to check it out! :-D

---

### Post by Angry penguin on 2007-02-08
I am having dificulty getting heretic to work using these instructions, doom is working fine. What is different with the setup to get heretic running?

---

### Post by stonemethod on 2007-02-13
soz delete this post

---

### Post by stonemethod on 2007-02-13
> **curtis3389 said:**
> Here's how I installed Doomsday on Edgy.

[LIST=1]
[*]Open the terminal (Applications->Accessories->Terminal)
[*]Open /etc/apt/sources.list ```
sudo gedit /etc/apt/sources.list
```
[*]Add the following lines to the end of the file ```
deb http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse
```
[*]Save and close the file
[*]Run the following commands in the terminal (one at a time)
Note: You may have to do this more than once to get the key. It will be confirmed with an "OK"
 ```
gpg --recv-keys 0x4B6E7209
gpg --export -a 0x4B6E7209 > Yagisan.asc
sudo apt-key add Yagisan.asc
```
[*]Now update your repositories ```
sudo apt-get update
```
[*] Open Synaptic Package Manager (System->Administration->Synaptic Package Manager)
[*]Search for the word "doomsday" (no quotes)
[*]Your results **should** contain the package "deng". Just install deng and all the required packages (including SDL) will be installed too.
[*] Enjoy!

Note: Also with those search results will be all the installers for the Doomsday games. If you have the original wads, I highly suggesting installing theses along with some of the other packages related to Doomsday.
All the descriptions of the packages can be found here -> [http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu]("http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu")
[/LIST]

ive done all of this, but where is doom? how do i get it to start?

---

### Post by frankob on 2008-08-13
Well, I got everything up and running just nice. But I can't figure out how to install the resource packages (pk3's)... The link given by Jivicin leads to a "The Doomsday Engine Wiki (DEW) is currently offline while we upgrade. It will be returning soon." message... and it is for days now. And I can't find a tutorial anywhere else. They all talk about installing them in the win32 version... :-/

---

### Post by frankob on 2008-08-14
Please, help! Jivicin, or anybody?

---

### Post by afrodeity on 2010-08-08
deng is installed, now what?

---

### Post by Largaroth on 2011-02-07
Hi all, just reviving this post here, I'm having a little trouble with the sources, when I launch the configure file I get a message (some way in to the configuration) telling me openAl is not available, and that Makefile.in is not available (whereas it is and I don't get ^^).

---

