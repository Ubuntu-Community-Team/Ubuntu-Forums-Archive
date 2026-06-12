---
title: "Ubuntu freezes when loading"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by ImTroyMiller on 2013-11-04
I did a OS update of Ubuntu 12.04 and I install these packages for the Android Open Source Project(plus a rename in there)...

[COLOR=#000000]$ sudo apt[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000088]get[/COLOR][COLOR=#000000] install git gnupg flex bison gperf build[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]essential [/COLOR][COLOR=#666600]\[/COLOR]
[COLOR=#000000]  zip curl libc6[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]dev libncurses5[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]dev[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#000000]i386 x11proto[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]core[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]dev [/COLOR][COLOR=#666600]\[/COLOR]
[COLOR=#000000]  libx11[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]dev[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#000000]i386 libreadline6[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]dev[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#000000]i386 libgl1[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]mesa[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]glx[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#000000]i386 [/COLOR][COLOR=#666600]\[/COLOR]
[COLOR=#000000]  libgl1[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]mesa[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]dev g[/COLOR][COLOR=#666600]++-[/COLOR][COLOR=#000000]multilib mingw32 tofrodos [/COLOR][COLOR=#666600]\[/COLOR]
[COLOR=#000000]  python[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]markdown libxml2[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]utils xsltproc zlib1g[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]dev[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#000000]i386
$ sudo ln [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]s [/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]usr[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]lib[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]i386[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]linux[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]gnu[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]mesa[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]libGL[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]so[/COLOR][COLOR=#666600].[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]usr[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]lib[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]i386[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]linux[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]gnu[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]libGL[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]so[/COLOR]

Now Ubuntu boots to the tty1 screen.  I can login, but typing startx gives me...

etc/X11/xinit/xserverrc: 3: exec: /usr/bin/X: not found
xinit: giving 
up
xinit: unable to connect to X server: No such file or directory
xinit: 
server error

What can I do?

---

### Post by ImTroyMiller on 2013-11-05
How can I reinstall the whole graphical interface via the command line?

sudo apt-get NVidia?
sudo apt-get .....?

I'd like to save the system.  My files are there, it must be the graphics driver or something...

---

### Post by newb85 on 2013-11-05
This doesn't appear to be driver-related.  Perhaps
```
sudo apt-get install xorg
```
will do the trick.

---

### Post by ImTroyMiller on 2013-11-05
That almost worked.  Afterwards, I gave the startx command and it took me into the GUI but all of my files were gone.  I clicked "logout" and it took me back to the command line.  I rebooted, went to recovery from the GRUB menu, hit ESC(I believe, maybe ENTER), got to the command line, and my files were all there.  Then I tried 'startx' and got

xauth:  error in locking authority file /home/user/.Xauthority
xauth:  error in locking authority file /home/user/.Xauthority

Fatl server error:
Server is already active for display 0
      If this server is no longer running, remove /tmp/.X0-lock and start again.

Please consult the The X.Org Foundation support
      at [http://wiki.x.org](http://wiki.x.org)
  for help.

  ddxSigGiveUp: Closing log
No protocol specified
No protocol specified
xinit: giving up
xinit: unable to connect to X server: Resource temporarily unavailable
xinit: server error
xauth: error in locking authority file /home/user/.Xauthority

Should search for /tmp/.X0-lock and delete it?

---

### Post by hansdown on 2013-11-05
Hi ImTroyMiller.

Please save your data to a usb, etc., and try this.

[http://askubuntu.com/questions/69896/cant-run-x-configure-server-is-already-active-error](http://askubuntu.com/questions/69896/cant-run-x-configure-server-is-already-active-error)

---

### Post by ImTroyMiller on 2013-11-06
^That link is about screen brightness.

The .X0-lock file has a four digit number inside of it.

Is there a way to install my Nvidia drivers from the command line?

---

### Post by ImTroyMiller on 2013-11-06
This is a video I made of the error that I am having now.  I sign on, the screen blinks, and then it goes right back to the sign in.  The strange thing, is that I just got a Raspberry PI and it was having the same issue.  The only way to get it to boot with a GUI is to 'apt-get update' and then 'startx'.

[http://www.youtube.com/watch?v=ozMc-tBgBxU](http://www.youtube.com/watch?v=ozMc-tBgBxU)

---

### Post by ImTroyMiller on 2013-11-06
This here seems to have fixed the problem...

[http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest](http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest)

---

