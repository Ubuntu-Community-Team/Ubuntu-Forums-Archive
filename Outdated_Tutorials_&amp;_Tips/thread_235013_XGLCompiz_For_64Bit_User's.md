---
title: "XGL/Compiz For 64Bit User's"
date: 2006-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by John.Michael.Kane on 2006-08-12
[COLOR="Red"]**Note: This Guide As Of Now Does Not Work With The Latest Compiz/Csm**[/COLOR]


[CENTER][COLOR="Navy"]**Listed is the method that has worked for my setup. The kernel used was linux-amd64-k8 Non generic kernel Desktop used Gnome**[/COLOR]

[COLOR="Red"]**Note:You are free to try this method at your own risk**[/COLOR][/CENTER]

**Install the Nvidia driver:**
```
sudo apt-get install nvidia-glx
```

**Enable the driver in your xorg:**
```
sudo nvidia-xconfig
```

**Create a link to the “Nvidia-Settings”**
```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```
**Add The Following:**
```
[Desktop Entry] Name=NVIDIA Settings Comment=NVIDIA X Server Settings Exec=nvidia-settings Icon= StartupNotify=true Terminal=false Type=Application Categories=Application;System;
```
Save the edited file.Press CTRL+ALT+BACKSPACE (To restart the xserver). 


Step2:**Edit your sources.list**
```
sudo gedit /etc/apt/sources.list
```
**Add these lines to your sources.list**
```
deb http://www.beerorkid.com/compiz dapper stable
```
```
deb http://www.beerorkid.com/compiz dapper main
```

[COLOR="DarkOrange"]**Packages in this repository are gpg authenticated**[/COLOR]
**Run These Commands in the terminal:**
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

**Setup your gnome login to load Xgl instead of Xorg**
```
sudo gedit /etc/gdm/gdm.conf-custom
```
**Add this to the bottom of the file:**
```
0=Xgl

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl -fullscreen -br -accel xv:fbo -accel glx:pbuffer
flexible=true

```
**Save the file**

**Install Xgl and Compiz. Type the following in your terminal**
```
sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes libglitz-glx1
```


Download compiz-start.py and logo24.png from the link:
[**compiz-start.py**]("http://www.compiz.net/viewtopic.php?id=1615")

Once you have downloaded the file you will have to edit it. 
1: **Replace all the occurences of [COLOR="Red"]gnome-window-decorator[/COLOR] with [COLOR="DarkRed"]cgwd[/COLOR] in the compiz-start.py file**

2: **Search for [COLOR="Red"]def configure_menu_activate(widget):[/COLOR] in the script**

**Replace:**
[COLOR="DarkOrchid"]**gobject.spawn_async(['gset-compiz'], \**[/COLOR]
**With:**
[COLOR="RoyalBlue"]**gobject.spawn_async(['gconf-editor', '/apps/compiz'], flags=gobject.SPAWN_SEARCH_PATH)**[/COLOR]

**To install the script:**
```
chmod 755 compiz-start.py
sudo mv compiz-start.py /usr/bin/
sudo mv logo24.png /usr/share/compiz/
```

[B]To start compiz on login. In gnome, go to 
System --> Preferences --> Sessions --> Startup --> Add and add a line that says:[/B]

```
compiz-start.py
```

**Note before re-booting run:**
```
sudo aptitude update
```
**[COLOR="Red"]followed by[/COLOR]**
```
sudo aptitude upgrade
```

**[COLOR="Purple"]Reboot the machine your done[/COLOR]**

**Screenshot of finshed product**.
[[IMG]http://img75.imageshack.us/img75/8416/screenshotvg3.th.jpg[/IMG]](http://img75.imageshack.us/my.php?image=screenshotvg3.jpg)

[CENTER]**Credit:**
**[COLOR="Blue"]Thanks to Tseliot for the nvidia howto[/COLOR]**
[COLOR="Red"]**Thanks to Beamerboy for the 32bit version which lead to this[/COLOR]**
[B][COLOR="Indigo"]Thanks to g14 for the compiz-start.py and logo
[/COLOR][/B][/CENTER]

---

### Post by AndyW on 2006-08-13
If I used automatrix to install nvidia drivers, do I have to edit anything else or just go from the xgl/comprise section?

::EDIT:: I ran
```
 sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes libglitz-glx1
```
and I get this
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package cgwd

```
did I do something wrong?

---

### Post by John.Michael.Kane on 2006-08-13
AndyW this has not been tested with automatix, and cgwd is listed in the repo's,and i just reinstalled it from the repo's. so i'm not sure what to tell you.

---

### Post by factor on 2006-08-13
I get this error, any idea?

tito@tito:~$ /usr/bin/startcompiz &
[1] 6583
tito@tito:~$ compiz.real: No XKB extension
*** glibc detected *** free(): invalid pointer: 0x0000000000420684 ***
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.

---

### Post by AndyW on 2006-08-13
sorry I just needed to run apt-get update

---

### Post by Hg80 on 2006-08-13
hmm i get the same error but updating doesnt work

---

### Post by John.Michael.Kane on 2006-08-13
AndyW i'm glad it worked out. enjoy.



@factorand Hg80 thats an unkown error to me.what is system spec's? is this a fresh install of ubuntu or have you customized it before using this guide.

---

### Post by aceracer24 on 2006-08-13
well, It's working but it's not, I have no title bars which is an indication something is working. No special effects though.

---

### Post by AndyW on 2006-08-13
> **aceracer24 said:**
> well, It's working but it's not, I have no title bars which is an indication something is working. No special effects though.

That is exactly what I have :???:
cant see windows in panel either and cant move windows. Program windows not the operating system:p

---

### Post by aceracer24 on 2006-08-13
found a fix, well at least for my problem. Remove the reflection plugin from compiz as per this link [http://www.compiz.net/topic-2-38.html](http://www.compiz.net/topic-2-38.html). This will probably only work if you are getting the same error which you can check by looking in your /home/username/.xsession-errors

---

### Post by AndyW on 2006-08-13
ok but how do I remove it?

---

### Post by mattlach on 2006-08-13
Is anyone else having libpango dependancy issues?

```

root# apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes libglitz-glx1
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  cgwd: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
  compiz-gnome: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
                Depends: compiz (= 0.0.13-0quinn31) but it is not going to be installed
E: Broken packages
```

It seems it depends on libpango >= 1.12.3, but even with my up to date system the latest version I have is 1.12.2-0ubuntu3.

Is there a newer experimental version of libpango somewhere I need to install?  Where would I find it, and how would I do that?

Much obliged,
Matt

---

### Post by John.Michael.Kane on 2006-08-13
I don't understand why you all are having dependency issues. the only modifications made with this howto over this one [**NEW UPDATED HOWTO : XGL+Compiz (32bit) (Nvidia)**]("http://www.ubuntuforums.org/showthread.php?t=222034&highlight=updated+xgl%2Fcompiz") is the fact that you need to use **beerorkid** for **[COLOR="Red"]cgwd-themes[/COLOR]**,and the addition of the **libglitz-glx1** which does not get installed automatically.

---

### Post by mattlach on 2006-08-13
> **SD-Plissken said:**
> I don't understand why you all are having dependency issues. the only modifications made with this howto over this one [**NEW UPDATED HOWTO : XGL+Compiz (32bit) (Nvidia)**]("http://www.ubuntuforums.org/showthread.php?t=222034&highlight=updated+xgl%2Fcompiz") is the fact that you need to use **beerorkid** for **[COLOR="Red"]cgwd-themes[/COLOR]**,and the addition of the **libglitz-glx1** which does not get installed automatically.

Well,  what version of libpango do you have installed?

apt-get keeps telling me that I require 1.12.3 for compiz, but the latest version I have installed is 1.12.2-0ubuntu3.

I'd be really curious to see which version you have installed.  From what I can tell 1.12.3 isnt marked stable for AMD64 yet...

---

### Post by John.Michael.Kane on 2006-08-13
1.12.3-ubuntu3
[[IMG]http://img139.imageshack.us/img139/1921/pangoku1.th.jpg[/IMG]](http://img139.imageshack.us/my.php?image=pangoku1.jpg)

---

### Post by Humin12 on 2006-08-13
Does anyone know how to do this with an x86 processor. Please help ive been trying for days to find out how
sorry found the link from above

---

### Post by mattlach on 2006-08-13
> **SD-Plissken said:**
> 1.12.3-ubuntu3
[[IMG]http://img139.imageshack.us/img139/1921/pangoku1.th.jpg[/IMG]](http://img139.imageshack.us/my.php?image=pangoku1.jpg)

Thats really strange.  I have updated the list and I still get 1.12.2-0ubuntu3 as the latest version.   Maybe you have some sort of repository on your list I don't?

---

### Post by mattlach on 2006-08-13
> **Humin12 said:**
> Does anyone know how to do this with an x86 processor. Please help ive been trying for days to find out how
sorry found the link from above

Humin,
Try this guide:
[http://ubuntuforums.org/showthread.php?t=225141](http://ubuntuforums.org/showthread.php?t=225141)

--Matt

---

### Post by John.Michael.Kane on 2006-08-13
No i'm using the standard sources.list

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.systemadministrator.org dapper eyecandy

```

---

### Post by mattlach on 2006-08-13
> **SD-Plissken said:**
> No i'm using the standard sources.list

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.systemadministrator.org dapper eyecandy

```

Well  I don't know what happened, but I just messed around with the GUI repository editor and chenged a bunch of settings, and suddenly its updating TONS of packages (probably unstable ones?).

It may make my system less stable, but libpango is one of the updated packages, so I am happy about this! 

I'll let you all know how it goes.

---

### Post by S01932 on 2006-08-13
Well apparently Quinn is not updating the 64bit versions of compiz and so if you try to install from his repositories will not work on Dapper 64bit, i had to force install older dpkg packages from someones post within the compiz.net forums [here]("http://www.compiz.net/topic-2402-more-amd64-updatedness")

---

### Post by mattlach on 2006-08-14
> **mattlach said:**
> Well  I don't know what happened, but I just messed around with the GUI repository editor and chenged a bunch of settings, and suddenly its updating TONS of packages (probably unstable ones?).

It may make my system less stable, but libpango is one of the updated packages, so I am happy about this! 

I'll let you all know how it goes.

Well, that was fun.   Whatever I did to my sources.list to get the 1.12.3 version of libpango I needed for compiz also upgraded my nvidia drivers to unstable ones (or something to that effect)   After the upgrade OpenGL rendering doesnt seem to work anymore, which caused XGL to behave very strangely :(  (No title bars, couldn't move windows, etc.)

Now I have to try to fix my Nvidia problems before continuing!

---

### Post by mattlach on 2006-08-14
> **aceracer24 said:**
> found a fix, well at least for my problem. Remove the reflection plugin from compiz as per this link [http://www.compiz.net/topic-2-38.html](http://www.compiz.net/topic-2-38.html). This will probably only work if you are getting the same error which you can check by looking in your /home/username/.xsession-errors

I now get the same symptoms you do (no titlebar, and no effects), but I can't figure out how to fix it from that link you posted...

My console outputs the following when I run compiz:
```

** (cgwd:5305): WARNING **: Cannot open pixmap: menu

** (cgwd:5305): WARNING **: Cannot open pixmap: shade

** (cgwd:5305): WARNING **: Cannot open pixmap: /home/matt/.cgwd/theme/buttons.inactive_glow.png
compiz.real: No XKB extension
*** glibc detected *** free(): invalid pointer: 0x0000000000420684 ***

```

Any suggestions?

All help appreciated!

---

### Post by awaken on 2006-08-14
mattlach

I was getting that error as well after installing the latest compiz.  I fixed it by changing my startcompiz script to:

```
awaken@nox:~$ cat /usr/bin/startcompiz 
#!/bin/sh
cgwd --replace &
compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &
```

---

### Post by awaken on 2006-08-14
> **awaken said:**
> mattlach

I was getting that error as well after installing the latest compiz.  I fixed it by changing my startcompiz script to:

```
awaken@nox:~$ cat /usr/bin/startcompiz 
#!/bin/sh
cgwd --replace &
compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &
```
After a little more research, I found that in my case it was the "gconf" plugin that was causing the "*** free(): invalid pointer: 0x0000000000420684 ***" error.

Anyone know how to see what settings the gconf plugin uses?

-Awaken

---

### Post by mattlach on 2006-08-15
> **awaken said:**
> After a little more research, I found that in my case it was the "gconf" plugin that was causing the "*** free(): invalid pointer: 0x0000000000420684 ***" error.

Anyone know how to see what settings the gconf plugin uses?

-Awaken

Thank you for that suggestion!

I loaded the plugins manually in the start script, and left out gconf and this time it started.

It replaced my initial errors with a whole new set of errors though :(

I could use the cool looking alt-tab window switching, and had animated menus, but still no title bars, and the graphics was buggy as all hell.

```

cgwd: Connection Error (No reply within specified time)
6846: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4628.
This is normally a bug in some application using the D-BUS library.
6846: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4592.
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
compiz.real: No XKB extension
```

I still have no idea what the No XKB extension means, and I'm not entirely certain what DBUS is, what it has to do with compiz, and why I am running out of memory.  My box has a gig of ram with 230megs free...

```

Mem:   1028444k total,   796356k used,   232088k free,   119740k buffers
Swap:  2096472k total,        0k used,  2096472k free,   368092k cached

```

Are they referring to graphics ram?   In that case my Gefore 6800GT has 256megs of ram which ought to be enough for just about everything...

Any ideas?

---

### Post by mattlach on 2006-08-15
I fixed most of my problems (yay!)

Turns out the reason compiz was failing was due to fbo.  I read the gentoo forums (my old distribution) and decided to replace ```
"-accel xv:fbo"
``` with ```
"-accel xv:pbuffer"
``` in /etc/gdm/gdm.conf-custom and now compiz loads with no error messages.

I have a new problem though.

compiz RUNS, but there seems to be a terrible screen refresh problem of sorts.   When I move windows everything around them turns white (and sometimes at random EVERYTHING turns white.

Again, I get no error messages from compiz, so I am not sure what the problem could be.

Does anyone know what might be causing this?

Thanks,
Matt

---

### Post by awaken on 2006-08-16
mattlach,

I'll take a guess that your video card driver does not support pBuffer, so effects are being rendered in software.

What video card / X11 driver are you using?

-Awaken

---

### Post by mattlach on 2006-08-16
> **awaken said:**
> mattlach,

I'll take a guess that your video card driver does not support pBuffer, so effects are being rendered in software.

What video card / X11 driver are you using?

-Awaken

Thanks.

It should support pbuffer.

I have a Geforce 6800GT, and I am running the latest nvidia driver (don't have the version now as I am at work)

---

### Post by bender[OO] on 2006-08-16
Hey I keep getting this 

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xserver-xgl

Whenever I get to this part 

save the file and go back to the terminal, it is time to download and install Xgl and Compiz. Type the following in your terminal:

sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes libglitz-glx1

What should I do?

---

### Post by mattlach on 2006-08-16
> **'bender[OO] said:**
> Hey I keep getting this 

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xserver-xgl

Whenever I get to this part 

save the file and go back to the terminal, it is time to download and install Xgl and Compiz. Type the following in your terminal:

sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes libglitz-glx1

What should I do?


Did you edit your sources.list as in the tutorial?   Also you may want to add the ubuntu universe and multiverse.

---

### Post by bender[OO] on 2006-08-16
Yes, I edited the source.list as it showed in the tutorial in this thread.  What is ubuntu universe and multiunivserse, and how would I add them?

(I'm very new to linux)

Thank you.

---

### Post by mattlach on 2006-08-16
> **'bender[OO] said:**
> Yes, I edited the source.list as it showed in the tutorial in this thread.  What is ubuntu universe and multiunivserse, and how would I add them?

(I'm very new to linux)

Thank you.


Universe and multiverse are packages that have not been built by the ubuntu team.

[This](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html) shows you how to enable them.

Once enabled you should run:
```
apt-get update
```
again before trying to get the packages.

---

### Post by bender[OO] on 2006-08-16
Hmm..I enabled those two things, but now when I write in apt-get update into the terminal I get this:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Thanks again.

Edit:  Hmm LOl I don't know why but I retried after Ubuntu got some updates as it does regularly and it worked, I installed Xgl and Compiz.

---

### Post by mattlach on 2006-08-16
> **'bender[OO] said:**
> Hmm..I enabled those two things, but now when I write in apt-get update into the terminal I get this:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Thanks again.


Sounds like you have something else open (Like synaptic or something like that) that uses the list directory.   You can only use one package management tool at the time.   Try closing anything that might be related to packages and trying again.  If this doesnt work, give it a reboot, something might have crashed and kept the list directory locked.

--Matt

---

### Post by bender[OO] on 2006-08-16
Thanks Mattlach it worked now and Im at this step


Now you need to make it exectuable so type the following from the terminal:
Code:

sudo chmod 755 /usr/bin/startcompiz

Whenever I paste that in the terminal nothing happens.  Im getting so close.

---

### Post by mattlach on 2006-08-16
> **'bender[OO] said:**
> Thanks Mattlach it worked now and Im at this step


Now you need to make it exectuable so type the following from the terminal:
Code:

sudo chmod 755 /usr/bin/startcompiz

Whenever I paste that in the terminal nothing happens.  Im getting so close.

Hey.

Don't worry about that.   All that command is doing is making the script you wrote executable.  There is no confirmation message.  It would only give you a message if something went wrong.

---

### Post by bender[OO] on 2006-08-16
So I finished everything in the tutorial rebooted, and everything looked the same besides one thing when i open any new window i can't drag it anywhere its simply stuck.  Is there a way to set up xgl now or something im so lost.

Edit:  I believe the correct term for what I don't have is a user interface.  Im not sure though.

---

### Post by mattlach on 2006-08-16
> **'bender[OO] said:**
> So I finished everything in the tutorial rebooted, and everything looked the same besides one thing when i open any new window i can't drag it anywhere its simply stuck.  Is there a way to set up xgl now or something im so lost.

Edit:  I believe the correct term for what I don't have is a user interface.  Im not sure though.

Do your windows have title bars?

compiz may be failing on start, like it did for me.

disable the start script in sessions that you created and reboot.

next try running the start script you created manually from the console. ```
 /usr/bin/startcompiz
```

It should give you some error messages.  Copy and paste them here.

Chances are you have to alter your start script like Awaken did on page 3 of this thread.

---

### Post by bender[OO] on 2006-08-16
My windows had no title bars.

I disabled the start script and my title bars came back on reboot.

I tried running the start scrip manually from the terminal and my title bars disappeared.

I enetered that code and this was the message
compiz.real: no XKB extension
***glibc detected*** free(): invalid pointer: 0x0000000000420684***

---

### Post by mattlach on 2006-08-16
> **'bender[OO] said:**
> My windows had no title bars.

I disabled the start script and my title bars came back on reboot.

I tried running the start scrip manually from the terminal and my title bars disappeared.

I enetered that code and this was the message
compiz.real: no XKB extension
***glibc detected*** free(): invalid pointer: 0x0000000000420684***

Yep..  Thats the exactly smae problem that awaken and I had.

By default compiz loads plugins through gconf, but that seems to not work on many peoples systems, so instead you can manually specify which plugins you want to run on startup.   Look at what awaken did on page 3 of this thread, and alter your /usr/bin/compizstart appropriately.

I did all that and mine loads without error messages now, but instead I ahve a strange white refresh problem which I ahve been researching to death without being able to solve.  I hope you have better luck than I do.

Once you get it working by starting it from the command line, just go back and enable the startup in sessions again to get it to load on boot.

(I feel silly giving advice since I havn't been able to get mine to work yet, but such are forums :p )

---

### Post by bender[OO] on 2006-08-16
Thank you so much for the help.  I really appreciate it!

---

### Post by mattlach on 2006-08-16
> **'bender[OO] said:**
> Thank you so much for the help.  I really appreciate it!

any time :p

---

### Post by John.Michael.Kane on 2006-08-16
Mattlach there seems to be an issue with the compiz part of guide i just did a reinstall,and have had it not work even changing fbo to pbuffer. will have to further test my setup.

---

### Post by bender[OO] on 2006-08-16
Holy momma hahahaha I finally got it. The first time I noticed my window was all floppy I was like xgl Yahhhhh...then my computer crashed.  But I rebooted again and now it works flawlessly..for now at least.  Heehe I love this eye candy/4 desktops!!

Thank you so much SD-Plissken for writing up the tutorial!

And thank you Mattlach for helping moi!

---

### Post by John.Michael.Kane on 2006-08-16
Bender you got it to working thats good. the new packages don't seem to be working for my setup,however. i'm glad someone was able to use this guide.

---

### Post by awaken on 2006-08-17
> **mattlach said:**
> Thanks.

It should support pbuffer.

I have a Geforce 6800GT, and I am running the latest nvidia driver (don't have the version now as I am at work)


Hmm..  That's the same card I'm using (XFX Version).  I wonder why it wouldn't work with fbo for you.

I'm using the 1.0.8762 driver.

-Awaken

---

### Post by awaken on 2006-08-17
> **SD-Plissken said:**
> Bender you got it to working thats good. the new packages don't seem to be working for my setup,however. i'm glad someone was able to use this guide.

Heya SD-Plissken -- thanks for the howto

To solve your problem, did you try not running gconf by replacing the text in your startcompiz script with the text below?

```
#!/bin/sh
cgwd --replace &
compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water reflection &

```

-Awaken

---

### Post by John.Michael.Kane on 2006-08-17
awaken that script command worked. I have been trying of ways to get this sorted out. where did you find that script/command?

thanks will update the guide.


awaken i will try to retest this on a fresh install,however.I think you hit the nail on the head with that command.


@mattlach i did not have to replace "-accel xv:fbo" as you did. this may be dependant on the card type,however.i'm not sure.

---

### Post by bender[OO] on 2006-08-17
I used his script.  Thats what made it work for me.

---

### Post by John.Michael.Kane on 2006-08-17
@mattlach bender[OO] awaken i have updated the guide. the skydome/cube issues seem to have been fixed. 



Thanks for testing,and helping.

---

### Post by awaken on 2006-08-17
> **SD-Plissken said:**
> awaken that script command worked. I have been trying of ways to get this sorted out. where did you find that

I picked up the basic idea from reading the compiz forums and got the list of modlues from Wikipidia of all places. [[http://en.wikipedia.org/wiki/Compiz]("http://en.wikipedia.org/wiki/Compiz")]

It should be noted that gconf would be a good module to have, but even after today's update, it still doesn't work for me.

I'll keep trying to load it after each update.  If anyone one knows how to get gconf working, please post.

-Awaken

---

### Post by mattlach on 2006-08-18
> **awaken said:**
> I picked up the basic idea from reading the compiz forums and got the list of modlues from Wikipidia of all places. [[http://en.wikipedia.org/wiki/Compiz]("http://en.wikipedia.org/wiki/Compiz")]

It should be noted that gconf would be a good module to have, but even after today's update, it still doesn't work for me.

I'll keep trying to load it after each update.  If anyone one knows how to get gconf working, please post.

-Awaken

What does the Gconf module do anyway?   Is it just a module that allows compiz to use the gconf gui to select which plugins get loaded at startup?

---

### Post by mattlach on 2006-08-18
> **awaken said:**
> Hmm..  That's the same card I'm using (XFX Version).  I wonder why it wouldn't work with fbo for you.

I'm using the 1.0.8762 driver.

-Awaken

Interesting...

I have the XFX card as well.   Maybe its a motherboard chip issue?  There are really so many variables that it would be hard to tell..

I'm willing to wager that its more likely a software glitch somewhere.   Maybe I wound up with an older version of some library or other, or have a slightly different config file somewhere...

I'm still researching it!

--Matt

---

### Post by John.Michael.Kane on 2006-08-18
.....

---

### Post by John.Michael.Kane on 2006-08-22
Guide has been updated. for those who whish to try it you can.

---

### Post by holmes on 2006-08-23
Just tried it on a clean install.


```

The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-core (= 0.0.13.37-0ubuntu1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:~#

```

---

### Post by holmes on 2006-08-23
All fixed.

I think it had to do with a broken package, or just got a bad install. I removed all the packges included and ran the install again. No problems now.


Edit :
Great guide. The startup script did not work for me, but I have my own.

I think you left this part out your guide when updating you guide though?

```
use compiz-start.py to start compiz whenever you login to gnome. In gnome, go to 
System --> Preferences --> Sessions --> Startup --> Add and add a line that says compiz-start.py.
```

---

