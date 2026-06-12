---
title: "HOWTO:  Old Loki Entertainment Games in Edgy"
date: 2007-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Footissimo on 2007-04-06
Basically, this is an update from my [previous](http://ubuntuforums.org/showthread.php?t=189360&highlight=loki+games) thread (which applied to Dapper).  Again, I'm not a techie person and I'm just sticking together what other people have said on other threads and boards into something that works for me, so I'll apologise in advance when / if I can't help with individual problems.

Again, I'm assuming that:

a) your main CD/DVD drive is mounted on /media/cdrom0
b) you have your graphics drivers set up and are working - direct rendering should say 'yes' if you type the following into the terminal ```
glxinfo | grep direct
```.  If it doesn't then you need to sort those drivers out!
c) that you want everything installed systemwide in /usr/local/games (where they tend to default to anyway)

IMPORTANT:  Whenever any of the installer programs helpfully offer to let you 'play' from the installer itself..say NO or QUIT.  If you do so then you'll create a root-owned game user which will be no fun at all

NOTE: if when starting any of the installers, you get an error like this: ```
setup.sh: 9: function: not found
x86
```Then try changing from dash to bash - type in```
sudo dpkg-reconfigure dash
``` and choose not to, then retry the installer

Covering seven games for this guide:

Civilization: Call To Power
Heavy Gear 2
Heretic 2
Sim City 3000 Unlimited
Heroes of Might and Magic 3
Railroad Tycoon 2
Descent 3

There are plenty more [Loki Entertainment Games](http://www.lokigames.com/products/) but these are the only ones I have - if someone kind wants to send me some others..then please do! ;)

**_Railroad Tycoon 2_**

OK, firstly you need to change to bash rather than dash, if you haven't done this already:
```
sudo dpkg-reconfigure dash
```
..and say no

Stick the disk in, change directory and start installing:
```
cd /media/cdrom0
sudo sh setup.sh
```

The installer comes up and I'll just click to install all the optional extras.  Once that's done, quit out   of there and download / install the patch..
```
 cd  ~/
wget ftp://mirrors.dotsrc.org/lokigames/updates/rt2/rt2-1.54c-unified-x86.run
sudo sh rt2-1.54c-unified-x86.run --keep
```
Type 'rt2' to run. A menu item appeared for me, but only after logging in and out of GNOME. If one doesn't appear then just use menu editor with the command 'rt2'

To clear out the stuff left behind:
```
cd ~/
rm rt2-1.54c-unified-x86.run
sudo rm -rf t2-1.54c-unified-x86
```

Revert to dash if you wish:
```
sudo dpkg-reconfigure dash
```

[B][U]
Heretic 2[/U][/B]

If you haven't done so, change from dash to bash
```
sudo dpkg-reconfigure dash
```
Stick the disk in, change directory and start installing:
```
cd /media/cdrom0
sudo sh setup.sh
```
I pressed on all the options and kept the default locations.  Once it's installed, just quit..don't try to play.  The terminal window window will suggest that a file wasn't found and whatnot.  We'll correct that and create a symlink so that running Heretic is a little easier.
```
sudo cp /media/cdrom0/bin/x86/glibc-2.1/heretic2 /usr/local/games/heretic2/
sudo ln  -s  /usr/local/games/heretic2/heretic2 /usr/local/bin
```
Next we need to download two patches:
```
cd ~/
wget ftp://mirrors.dotsrc.org/lokigames/updates/heretic2/heretic2-1.06b-unified-x86.run
wget ftp://mirrors.dotsrc.org/lokigames/updates/heretic2/heretic2-1.06c-unified-x86.run
```

Before you do anything, we have to patch the patches!
```
sh heretic2-1.06b-unified-x86.run --keep
```

This will cause a fault, but no worries, just change directories:
```
cd heretic2-1.06b-unified-x86/bin/Linux/x86/
```

Delete the borked loki_patch and download the newer one:
```
rm loki_patch
```
```
wget http://www.step-n-up.com/downloads/loki_patch
```

Change the permissions:
```
chmod +x loki_patch
```

Back up a few directories and run the update:
```
cd ../../../
```
```
sudo sh update.sh
```

You need to do exactly the same for the 1.06c patch, summarised:
```
cd ~/
```
```
sh heretic2-1.06c-unified-x86.run --keep
```
```
cd heretic2-1.06c-unified-x86/bin/Linux/x86/
```
```
rm loki_patch
```
```
wget http://www.step-n-up.com/downloads/loki_patch
```
```
chmod +x loki_patch
```
```
cd ../../../
```
```
sudo sh update.sh
```
You can now play the game by typing:
```
heretic2
```

To create a menu item, just load Menu Layout / Editor and use the command 'heretic2'.  The icon is messed up - if you want a better one then:
```
wget http://aslan.homelinux.com/dana/icons/games/heretic2.png
```
```
sudo mv heretic2.png /usr/share/pixmaps/
```

There should now be a slightly better Heretic icon in your default icon directory :)

Lastly, clean up the faff:
```
cd ~/
```
```
sudo rm -rf heretic2-1.06b-unified-x86
```
```
sudo rm -rf heretic2-1.06b-unified-x86
```
```
rm heretic2-1.06b-unified-x86.run
```
```
rm heretic2-1.06c-unified-x86.run
```
..and change back to dash, if you so desire..
```
sudo dpkg-reconfigure dash
```

Sim City / CivCTP next up!

---

### Post by beeldings on 2007-04-06
:) I can once again play Heretic 2 on Ubuntu. I've been at this for about two weeks trying to get the game to update and run under Edgy, and thanks to you it works.

---

### Post by mostholy on 2007-05-19
thanks a bunch for the howto.  Have been away from linux long enough to have forgotten a few things.  One wish I had was to get RT2 working and my initial attempts were laughable.  

Cheers

---

### Post by azador1606 on 2007-05-29
Tried to follow for Railroad Tycoon II in fiesty 7.04 on a Toshiba laptop.

A couple of things happened:

when installing the patch it asked for the installation directory,
for me this was /usr/local/games/RT2 -- or at least it seemed okay with this

running with rt2 spat out some errors - could not create file -- permission denied

creates a .loki directory in your home directory but creates it with owner and group as root

sudo chown -R <username> .loki
sudo chgrp -R <username> .loki

running again no errors

first time I also has a going down hard crash -- seg fault followed by unable to execute loki_qagent

will check this again

---

### Post by Stephen Howard on 2007-05-29
[Here's a link]("http://ubuntuforums.org/showpost.php?p=2740852&postcount=6") to getting Sim City 3000 running under Feisty.

---

### Post by ks1731-26 on 2008-05-10
I just tried to install the patches to Rail Road Tycoon II in Hardy Heron (8.04). I downloaded them from [http://lokifiles.tuxgames.com/updates/rt2/](http://lokifiles.tuxgames.com/updates/rt2/), grabbing the file rt2-1.54c-unified-x86.run

However, the installer script didn't work. I was shocked to discover that the behavior of the UNIX command "tail" had changed. The patch script assumes that, for instance, "tail +6" will return the entire file, starting with line 6. Now that doesn't work, and you need to use "tail -n +6" instead. . . Now, why would you change a basic UNIX utility like that?? Anyway, I digress. 

So I edited the script to use the newer syntax. However, one thing the script does is check the cksum for the installer file. . . and I just changed it, so the numbers don't match.

Well, I know the cksums are supposed to be an integrity check, so doing this really defeats the purpose. But, I replaced the checksum value at the top of the script with the new value that chsum returns, and the installer worked fine. 

I did go back and check that the original file I downloaded had the correct cksum, with tail -n +6 rt2-1.54c-unified-x86.run | cksum
Those numbers matched.

Hope someone finds this helpful.

Mike

---

### Post by notmyidea on 2008-08-16
> **ks1731-26 said:**
> I just tried to install the patches to Rail Road Tycoon II in Hardy Heron (8.04). I downloaded them from [http://lokifiles.tuxgames.com/updates/rt2/](http://lokifiles.tuxgames.com/updates/rt2/), grabbing the file rt2-1.54c-unified-x86.run

Hope someone finds this helpful.

Mike

Thanks!  That was very useful!  Everything works now, except the sound is all choppy (sounds like it is underwater).

Jason

---

### Post by GepettoBR on 2008-08-20
> **ks1731-26 said:**
> I just tried to install the patches to Rail Road Tycoon II in Hardy Heron (8.04). I downloaded them from [http://lokifiles.tuxgames.com/updates/rt2/](http://lokifiles.tuxgames.com/updates/rt2/), grabbing the file rt2-1.54c-unified-x86.run

However, the installer script didn't work. I was shocked to discover that the behavior of the UNIX command "tail" had changed. The patch script assumes that, for instance, "tail +6" will return the entire file, starting with line 6. Now that doesn't work, and you need to use "tail -n +6" instead. . . Now, why would you change a basic UNIX utility like that?? Anyway, I digress. 

So I edited the script to use the newer syntax. However, one thing the script does is check the cksum for the installer file. . . and I just changed it, so the numbers don't match.

Well, I know the cksums are supposed to be an integrity check, so doing this really defeats the purpose. But, I replaced the checksum value at the top of the script with the new value that chsum returns, and the installer worked fine. 

I did go back and check that the original file I downloaded had the correct cksum, with tail -n +6 rt2-1.54c-unified-x86.run | cksum
Those numbers matched.

Hope someone finds this helpful.

Mike

Sorry, but just how did you manage to change the script? Gedit won't open it. I can't update Heroes 3 and I suspect this to be the problem.

---

### Post by corax on 2008-11-07
use an editor that works :) try it with nano
```
nano rt2-1.54c-unified-x86.run
```
It will load a bit slow (~ 5 sec) on my machine because the file is over 7 MB :)

Good luck!

Bence

---

