---
title: "Running Kohan and Sid Meier's Alpha Centauri on 9.04 64-bit"
date: 2009-07-07
forum: Outdated Tutorials &amp; Tips
---

### Post by overridex on 2009-07-07
I recently had a craving to play some of my older Loki games, but I quickly found that games made for Linux distributions from 2001 or so don't work so easily on modern distributions.  Here's a quick run down on how to get these native Linux ports working again.  You should be able to apply the basics of this to other Loki games as well.

For both of these games you will need the following files:

[http://www.overridex.net/files/loki_compat_libs-1.3.tar.bz2]("http://www.overridex.net/files/loki_compat_libs-1.3.tar.bz2")
[http://www.overridex.net/files/loki_patch]("http://www.overridex.net/files/loki_patch")

[SIZE="4"]Sid Meier's Alpha Centauri[/SIZE]

In addition to the files above, you will also need this patch:

[http://www.overridex.net/files/smac-6.0b-x86.run]("http://www.overridex.net/files/smac-6.0b-x86.run")

**Step 1: Install the game**

Insert your game cd and run the following commands, assuming the game is in your first cdrom:

```

cd /media/cdrom
linux32 /bin/bash setup.sh

```

Cancel or press Ctrl-C for the Loki Update and Loki Uninstall setups, then install Alpha Centauri - I installed everything, and I installed to ~/games/smac with the symlinks in ~/bin.  If you want to install somewhere system wide, you will need to run the install as root with sudo.

**Step 2: Update the game**

Run the following commands in the directory where you downloaded the game patch and loki_patch to:

```

chmod +x smac-6.0b-x86.run
_POSIX2_VERSION=199209 linux32 ./smac-6.0b-x86.run --keep
cp loki_patch ./smac-6.0b-x86/bin/Linux/x86/loki_patch
cd smac-6.0b-x86
mv patchdata data
linux32 ./update.sh

```

**Step 3: Install the Loki Compatibility libraries**

Extract the loki_compat_libs-1.3.tar.bz2 file somewhere - I put it in ~/games/ since I planned to use them for more than one game, and my games are installed in sub directories there.

```

tar xvjf /path/to/downloaded/loki_compat_lib-1.3.tar.bz2

```

**Step 4: Update Compiz settings (Optional)**

If you want to run the game with Compiz, you'll need to make a small change so that the game doesn't play with it's window mostly transparent.  Open CompizConfig Settings Manager under System -> Preferences -> CompizConfig Settings Manager.  If you don't already have this, you can install the package "compizconfig-settings-manager".

Find and enable the Window Rules plugin under Window Management.  If you do not have this plugin, you may need to install the "compiz-fusion-plugins-extra" package.

Add the following string to the "No ARGB Visuals" setting:

```

(title=Sid Meier's Alpha Centauri) | (title=SMAC Planetary Pack)

```

**Step 5: Running the game**

You can now run the game by changing to the game's directory, and running one of the following commands:

Alpha Centauri on 64-bit:

```

LD_PRELOAD=../Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/lib32/libX11.so ./smac.dynamic

```

Alien Crossfire on 64-bit:

```

LD_PRELOAD=../Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/lib32/libX11.so ./smacx.dynamic

```

If you're on a 32-bit install, simply switch /usr/lib32/libX11.so for /usr/lib/libX11.so in each command.  Also, keep in mind you may need to change the command if you installed Loki_Compat somewhere other than the directory above your game directory.

**Step 6: Running the game from smacpack**

Alpha Centauri came with a neat frontend called 'smacpack' for choosing to launch the original game or the expansion.  In order for this to work, we need to make a few changes which will help automate running the game.  From the game's directory, run these commands:

```

mv smac smac.real
mv smacx smacx.real

```

Next, recreate the 'smac' file as a text file with this content:

```

#!/bin/sh
# A simple shell script to launch SMAC on a modern Linux distribution

SCRIPTLOC=$0
DIRNAME=""

# Step through symlinks to find where the script really is
while [ -L $SCRIPTLOC ]; do
    SCRIPTLOC=`readlink $SCRIPTLOC`
done

# Get the directory the script is in, then change to it
DIRNAME=`dirname $SCRIPTLOC`
cd $DIRNAME

# Run the game
LD_PRELOAD=../Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/lib32/libX11.so ./smac.dynamic

```

Again, keep in mind you may need to change the last command slightly if you're on a 32-bit system, or if you installed the Loki_Compat libraries somewhere different.

Repeat the above steps recreating the smacx text file with the above script, just change the last line to use "smacx.dynamic" instead of "smac.dynamic".

Now, make both scripts executable:

```

chmod +x smac
chmod +x smacx

```

**Ready to play!**

You should now be all set to play by running 'smacpack'.  You may want to create a new entry in your menu to launch this, which you can do under System->Preferences->Menu Editor. You can find an icon to use attached to this post.

[SIZE="4"]Kohan: Immortal Sovereigns[/SIZE]

In addition to the files above, you will also need this patch:

[http://www.overridex.net/files/kohan-1.2.0-x86.run]("http://www.overridex.net/files/kohan-1.2.0-x86.run")
[http://www.overridex.net/files/kohan-1.3.1-x86.run]("http://www.overridex.net/files/kohan-1.3.1-x86.run")

**Step 1: Install the game**

Insert your game cd and run the following commands, assuming the game is in your first cdrom:

```

cd /media/cdrom
linux32 /bin/bash setup.sh

```

Cancel or press Ctrl-C for the Loki Update and Loki Uninstall setups, then install Kohan - I installed everything, and I installed to ~/games/smac with the symlinks in ~/bin.  If you want to install somewhere system wide, you will need to run the install as root with sudo.

**Step 2: Update the game**

Run the following commands in the directory where you downloaded the game patches and loki_patch to:

```

chmod +x kohan-1.2.0-x86.run
_POSIX2_VERSION=199209 ./kohan-1.2.0-x86.run --keep
cp loki_patch ./kohan-1.2.0-x86/bin/Linux/x86/loki_patch
cd kohan-1.2.0-x86
linux32 ./update.sh
cd ..
chmod +x kohan-1.3.1-x86.run
_POSIX2_VERSION=199209 ./kohan-1.3.1-x86.run --keep
cp loki_patch ./kohan-1.3.1-x86/bin/Linux/x86/loki_patch
cd kohan-1.3.1-x86
linux32 ./update.sh

```

**Step 3: Install the Loki Compatibility libraries**

Extract the loki_compat_libs-1.3.tar.bz2 file somewhere - I put it in ~/games/ since I planned to use them for more than one game, and my games are installed in sub directories there.

```

tar xvjf /path/to/downloaded/loki_compat_lib-1.3.tar.bz2

```

**Step 4: Running the game**

Change to the game's directory and run the following command:

```

LD_PRELOAD=../Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so ./kohan.dynamic

```

Keep in mind you may need to change the command if you installed Loki_Compat somewhere other than the directory above your game directory.

I also found that sound got distorted and crackled sometimes right at the main menu, sometimes after playing for a bit.  This is fixed by using the following command to run the game instead:

```

LD_PRELOAD=../Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:../Loki_Compat/libSDL-1.2.so.0 SDL_AUDIODRIVER="dsp" SDL_PATH_DSP="/dev/dsp" ./kohan.dynamic

```

Of course, this requires either OSS sound drivers or ALSA's OSS emulation.  Change /dev/dsp to your actual sound card.

**Step 5: Scripting running the game**

You can automate starting the game by creating the following script in your game directory.  I named mine runkohan.sh:

```

#!/bin/sh
# A simple shell script to launch Kohan on a modern Linux distribution

SCRIPTLOC=$0
DIRNAME=""

# Step through symlinks to find where the script really is
while [ -L $SCRIPTLOC ]; do
    SCRIPTLOC=`readlink $SCRIPTLOC`
done

# Get the directory the script is in, then change to it
DIRNAME=`dirname $SCRIPTLOC`
cd $DIRNAME

# Run the game
LD_PRELOAD=../Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:../Loki_Compat/libSDL-1.2.so.0 SDL_AUDIODRIVER="dsp" SDL_PATH_DSP="/dev/dsp" ./kohan.dynamic

```

Remember, if you don't want the sound fix or have Loki_Compat installed somewhere else, you'll need to update the last command of the script.

You should also symlink runkohan.sh into your PATH somewhere - ~/bin is in my PATH, so I created a symlink there.

**Ready to play!**

You should now be all set to play by running 'runkohan.sh'.  You may want to create a new entry in your menu to launch this, which you can do under System->Preferences->Menu Editor. You can find an icon to use attached to this post.

Have fun, let me know if you run into any problems following this tutorial.

---

### Post by jpeddicord on 2009-07-11
Excellent tutorial. Approved, and thank you for contributing to Tutorials & Tips!

---

### Post by Johnny B on 2009-07-11
after running
 > chmod +x smac-6.0b-x86.run
_POSIX2_VERSION=199209 linux32 ./smac-6.0b-x86.run --keep
cp loki_patch ./smac-6.0b-x86/bin/Linux/x86/loki_patch
cd smac-6.0b-x86
mv patchdata data
linux32 ./update.sh
update.sh gives the error: 
> Performing update:
ERROR: No matching delta for /home/j/games/data/tutor.txt
edit: tried a different iso, same error

i cant figure this one out, any ideas?

---

### Post by overridex on 2009-07-18
> **Johnny B said:**
> after running
 
update.sh gives the error: 

edit: tried a different iso, same error

i cant figure this one out, any ideas?

Where is the game installed?  Did it get installed to /home/j/games/ and get moved or was it originally installed to /home/j/games/smac ?

If the game is really installed in /home/j/games/smac but it's looking in the directory above it, try editing ~/.loki/installed/smac.xml and change the root attribute of the product tag to the correct directory.

By the way, sorry for taking a bit to reply to you on this - I hadn't subscribed to the thread when I first submitted it and didn't see that it had been approved yet.  I should be much quicker to respond now. :)

---

### Post by slamelov on 2009-08-23
I have followed the steps using planetary pack, but after starting a game, the game crashes after acepting the first city name:

> X Error:  BadMatch
  Request Major code 66 ()
  Error Serial #677
  Current Serial #680


 Any help?

---

### Post by overridex on 2009-08-23
> **slamelov said:**
> I have followed the steps using planetary pack, but after starting a game, the game crashes after acepting the first city name:




 Any help?

This is caused by not preloading libX11.so and using the dynamic executable.  Make sure that you're preloading /usr/lib/libX11.so if you're on a 32-bit system as described in the tutorial, or if you're on a 64-bit system preload /usr/lib32/libX11.so -- you should make sure that file exists, if it doesn't, install the ia32-libs package to get it.

Hope this helps,

---

### Post by slamelov on 2009-08-23
Finally, it works adding this:

```
Section "Extensions"
Option "Composite" "Disable"
EndSection
```

To Xorg file and restarting X. 

Thanks for the help

---

### Post by overridex on 2009-08-24
> **slamelov said:**
> Finally, it works adding this:

```
Section "Extensions"
Option "Composite" "Disable"
EndSection
```

To Xorg file and restarting X. 

Thanks for the help

Interesting, what video card and driver are you using?  On my Nvidia card with the proprietary drivers I play with composite enabled and compiz.

---

### Post by slamelov on 2009-08-24
nVidia 7900 Ultra, drivers 180.44.

also, I had the same problem about tutor.txt, but still works with these options in xorg.

I don't use compiz.

do you know is there is any way to change game resolution?.

---

### Post by overridex on 2009-08-26
> **slamelov said:**
> do you know is there is any way to change game resolution?.

I'm pretty sure those games only supported 1 resolution.

---

### Post by slamelov on 2009-08-31
> **overridex said:**
> I'm pretty sure those games only supported 1 resolution.

I think in Windows Release you could change resolution adding a line in ini file: directdraw=0 (or 1, not sure). Something like this:

[PREFERENCES]
directdraw=1

But I don't know in Linux.

---

### Post by vafnord on 2010-03-18
I am also getting the error Johnny B got:
```
va@feynman:~/Downloads/smac-6.0b-x86$ sudo linux32 ./update.sh 
=============================================================
Welcome to the Sid Meier's Alpha Centauri 6.0b Update
=============================================================

Would you like to read the README for this update?  [Y/n]: n

=============================================================
Would you like to apply this update? [Y/n]: y

Please enter the installation path: [/usr/local/games/smac]: 

=============================================================
Performing update:
ERROR: No matching delta for /usr/local/games/smac/data/tutor.txt
va@feynman:~/Downloads/smac-6.0b-x86$ ls /usr/local/games/smac/data/tutor.txt 
/usr/local/games/smac/data/tutor.txt

```

I checked ~/.loki/installed/smac.xml and the root attribute of the product tag is /usr/local/games/smac. Any suggestions?

---

### Post by overridex on 2010-03-18
> **vafnord said:**
> I am also getting the error Johnny B got:
```
va@feynman:~/Downloads/smac-6.0b-x86$ sudo linux32 ./update.sh 
=============================================================
Welcome to the Sid Meier's Alpha Centauri 6.0b Update
=============================================================

Would you like to read the README for this update?  [Y/n]: n

=============================================================
Would you like to apply this update? [Y/n]: y

Please enter the installation path: [/usr/local/games/smac]: 

=============================================================
Performing update:
ERROR: No matching delta for /usr/local/games/smac/data/tutor.txt
va@feynman:~/Downloads/smac-6.0b-x86$ ls /usr/local/games/smac/data/tutor.txt 
/usr/local/games/smac/data/tutor.txt

```

I checked ~/.loki/installed/smac.xml and the root attribute of the product tag is /usr/local/games/smac. Any suggestions?

Hmm...  I didn't run into this problem myself, but looking around that error basically just means that the file is not what it expects it to be before patching it - either it's corrupt, already patched or something similar.  I wonder if any of the smac discs came with a later update than mine?

Out of curiosity if you skip patching it, does the game work? And if so what version does it say it is?

If it's any help, the md5sum of my tutor.txt after running the patch is:

9ef29da9ba1edbeb89ae00447d71cbe8  data/tutor.txt

-Dan

---

