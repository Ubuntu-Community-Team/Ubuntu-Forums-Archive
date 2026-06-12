---
title: "Nexuiz doesn't open"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-09
I didn't know how to install the current version from the website (2.4.2), so i installed that one that was available in repos, hoping that'd there'd be some in-game update. well i installed whatever version is in the repos (2.3.1, i think), and when i try to open it, nothing happens.

--edit--

i did 
```

sudo aptitude reinstall nexuiz

```

and it was reinstalling nexuiz 2.4.1, so that's the version I got. there's a patch on the website on how to update 2.4.1 to 2.4.2, but i don't get what it means at all.
completely lost ><

---

### Post by ChameleonDave on 2008-07-09
> **adobrakic said:**
> 
and it was reinstalling nexuiz 2.4.1, so that's the version I got. there's a patch on the website on how to update 2.4.1 to 2.4.2, but i don't get what it means at all.
completely lost ><

The instructions there are not too hard to follow.  I can't translate them into more specific steps to follow without installing the game myself, and it is several hundred megabytes.

If you are not enough of an advanced user to install such things manually, you should probably stick with the version available in the Ubuntu repositories, which will doubtless be updated soon.

---

### Post by ChameleonDave on 2008-07-09
> **adobrakic said:**
>  i installed whatever version is in the repos (2.3.1, i think), and when i try to open it, nothing happens.

To see what has gone wrong, open a command-line terminal and run the game from it.  I imagine that the command is "nexuiz".  Then paste the output here.

---

### Post by adobrakic on 2008-07-09
> **ChameleonDave said:**
> To see what has gone wrong, open a command-line terminal and run the game from it.  I imagine that the command is "nexuiz".  Then paste the output here.

Yeah, I just did that before coming here, and i get the following:

```

ado@ado-desktop:~$ nexuiz
Nexuiz Linux 09:18:31 Mar 23 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data20080229.pk3 (3982 files)
Added packfile /usr/share/games/nexuiz/data/music20080229.pk3 (10 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libOffscreenGecko.so" "/usr/lib/games/nexuiz/libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
couldn't exec config.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 1024x768: Couldn't find matching GLX visual

```

---

### Post by ChameleonDave on 2008-07-09
> **adobrakic said:**
> ```

Failed to set video mode to 1024x768: Couldn't find matching GLX visual

```
It looks like there is a problem with 3D acceleration.

Can you run other 3D programs (e.g. compiz, amoeba, neverball, sauerbraten...)?

If you've never tried, try now.

---

### Post by adobrakic on 2008-07-09
i know i cant run compiz, but ill try the others

---

### Post by ChameleonDave on 2008-07-09
> **adobrakic said:**
> i know i cant run compiz, but ill try the others

Aha!  You probably haven't set your video card up properly.

Do you want help with that, or is your card too old for such things?

If your card is incapable of making Compiz work, then you cannot play Nexuiz.

---

### Post by aktiwers on 2008-07-09
Can you post the output of:
```
glxinfo | grep rendering
```

---

### Post by adobrakic on 2008-07-09
> **ChameleonDave said:**
> Aha!  You probably haven't set your video card up properly.

Do you want help with that, or is your card too old for such things?

If your card is incapable of making Compiz work, then you cannot play Nexuiz.

idk if my card's too old or not, it's a S3 Prosavage8 DDR

and for 'glxinfo | grep rendering' i get:

```

ado@ado-desktop:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
ado@ado-desktop:~$ 

```

---

### Post by aktiwers on 2008-07-09
Oh noes.. That card is not well supported. Are you on an IBM laptop?

I have never installed this card, but we could give it a try if you want?

---

### Post by adobrakic on 2008-07-09
nah, i'm on a compaq desktop, heh. and yeah, i know my graphics card sucks, not even the manfacturer updates the drivers anymore. :/

but sure, i wouldn't mind trying to install it, if you don't mind that is.

---

### Post by aktiwers on 2008-07-09
Okay - sure  :)

First I want to make sure you have been to System = Administration = Hardware drivers

Else try install this package:
```
sudo apt-get install xserver-xorg-video-savage
```

Please report back if it was already installed  (it was on my PC) and if you did look in "hardware drivers" already.

Then I go see if I can find some stuff on Google ;)

---

### Post by adobrakic on 2008-07-09
Yeah, it's already installed on my computer.
And yeah, I've been in hardware drivers, but it says like "no proprietary drivers found on this system" or something. 
(i tried running compiz, and failed miserably, lol :x)

---

### Post by ChameleonDave on 2008-07-09
> **adobrakic said:**
> Yeah, it's already installed on my computer.
And yeah, I've been in hardware drivers, but it says like "no proprietary drivers found on this system" or something. 
(i tried running compiz, and failed miserably, lol :x)
I don't hold out much hope for you, with that hardware.

I've just installed it from the repos and had a play.  You are seriously missing out, dude.  Heh-heh.  Sorry.

---

### Post by adobrakic on 2008-07-09
> **ChameleonDave said:**
> I don't hold out much hope for you, with that hardware.

I've just installed it from the repos and had a play.  You are seriously missing out, dude.  Heh-heh.  Sorry.

:(

i figured i could play it, cause i played Unreal Tournament on my windows.
the graphics and stuff looked the same, so i figured i'd give it a try

---

### Post by aktiwers on 2008-07-09
- Updated -

Lets make sure you have the compiling tools. Im not sure if you really need this, but hey they are nice to have anyways.
```
sudo aptitude install libc6 libc6-dev
```
```
sudo aptitude install build-essential linux-headers-$(uname -r);
```

Okay..  here we go (again)! I cross my fingers :)

Start by downloading the drivers for savage and the commen. (to desktop)
```
cd Desktop
wget http://dri.freedesktop.org/snapshots/savage-20060403-linux.i386.tar.bz2
wget http://dri.freedesktop.org/snapshots/common-20060403-linux.i386.tar.bz2
```Have a look on your desktop.. there are 2 new files. Right-click them both and pick "extract here".

2 new folders should show up.

Okay back to terminal.
```
cd ~/Desktop/common-20060403-linux.i386/
sudo sh install.sh
```And run through the installer.

Then we do the same with the next package:
```
cd ~/Desktop/savage-20060403-linux.i386/
sudo sh install.sh
```and follow the stuff on screen again.

After this, reboot, cross fingers and report back. We might need to edit X.org manually too.

---

### Post by adobrakic on 2008-07-09
when installing the first one, i got:

```

Installing files:
        GL & GLU libraries...install.sh: 707: Syntax error: Bad fd number
done
        core libraries...install.sh: 707: Syntax error: Bad fd number
ado@ado-desktop:~/Desktop/common-20060309-linux.i386$ 

```

at one instance. i'm not sure if that's bad or not, though.

and for the second one, i got:

```

Compiling...[: 695: ==: unexpected operator
install.sh: 695: Syntax error: Bad fd number
ado@ado-desktop:~/Desktop/savage-20060309-linux.i386$ 

```

but i'll reboot now

---

### Post by aktiwers on 2008-07-09
I just found out I did not grab the latest packages (the latest seams to be from April 2006 and I got the onces from Marts 2006). Let me know if you want me to change the guide to the "newest" ones. ;)

I dont want to edit it, if you are in the middle of using it.

---

### Post by adobrakic on 2008-07-09
sure, you can, if you don't mind it that is haha.

---

### Post by aktiwers on 2008-07-09
Okay hold on, I will edit the post..  I will report back when it has Im done.

---

### Post by aktiwers on 2008-07-09
Okay I updated it :)
Lets hope it works. Like I said this is new stuff to me too

---

### Post by adobrakic on 2008-07-09
for the first one i got:

```

Installing files:
        GL & GLU libraries...install.sh: 708: Syntax error: Bad fd number
done
        core libraries...install.sh: 708: Syntax error: Bad fd number
ado@ado-desktop:~/Desktop/common-20060403-linux.i386$ 

```

and second one:

```

Compiling...[: 696: ==: unexpected operator
install.sh: 696: Syntax error: Bad fd number
ado@ado-desktop:~/Desktop/savage-20060403-linux.i386$ 

```

:/!

---

### Post by aktiwers on 2008-07-09
urgh! LOL

What if you use 
```
sudo ./install.sh
```in both cases?

Or
```
sudo bash install.sh
```

I think has something to do with the replacement of sh with bash..  donno.. it runs fine on my computer.
You are on Ubuntu 8.04 Hardy, right? :)

---

### Post by aktiwers on 2008-07-09
Okay if non of that work, it looks like must peoples solution to this is:
```
sudo rm /bin/sh 
sudo ln -s /bin/bash /bin/sh
```

Then try the guide I made again :)

---

### Post by ChameleonDave on 2008-07-09
> **aktiwers said:**
> Okay if non of that work, it looks like must peoples solution to this is:
```
sudo rm /bin/sh 
sudo ln -s /bin/bash /bin/sh
```

Then try the guide I made again :)
All that will do is make "sh" be a synonym for "bash".  It won't solve anything that won't be solved simply by doing "sudo bash install.sh".  The script declares itself as requiring bash at the top, so "sudo ./install.sh" is equivalent.

---

### Post by aktiwers on 2008-07-09
Okay thanks..  I am not that good with Bash, dash and sh (yet)
But I guess this problem is because the driver is old (2006) and from Edgy they started using dash instead of bash for /bin/sh. 

Well lets see what happens :)
Thanks again for clearing it out

---

