---
title: "HOWTO: ATI fglrx driver *and* suspend to ram"
date: 2005-09-26
forum: Outdated Tutorials &amp; Tips
---

### Post by sjs on 2005-09-26
The problem:
 - with the open source ATI driver, you can suspend to ram, but you can't play 3D games
 - with ATI's proprietary fglrx driver, you can play games, but you cannot suspend to ram.  Mind you, suspend to disk (hibernate) works.

The (kludged) solution:
 - This is courtesy my in-house Linux expert, Mark Lord.  (Any errors in describing the process are entirely mine -- S.J.Skinner's)
 -> Here's the plan: normally run with a driver that works with suspend to ram. Suspend and resume whenever you please.  When you want to run a game, switch to the game driver, run the game & then hibernate.  When you come out of hibernate, use the suspend-to-ram driver again.

 0) go to /etc/X11 and copy your xorg.conf (or XF86config) to xorg.conf.game 
   (XF86config.game) if it's the one you use for gaming or to xorg.conf.good 
   (XF86config.good) if it's the one that works with suspend to ram.   If you
   now have both a .game and a .good file, skip to step 2.

1) If you only have the open source driver version, save it as xorg.conf.good 
   and go and get the fglrx version, following the instructions in the other ATI
   HOWTOs.  If you only have the gaming version, save it as xorg.conf.game and
   then you can use Synaptic to get and install the open source version  You 
   should be able to configure it with:
      dpkg-reconfigure xserver-xorg-driver-at
..... Note that I haven't tried this myself so I'm not positive it'll work......
   Or you can try changing your fglrx driver options to eliminate what causes
   suspend to ram to fail.  In my case, I found that setting
      Option "no_accel"      "yes"
   turned off direct rendering (glxinfo shows its state) and thus killed the
   game, but allowed suspend to ram to work. 

   Once you have an xorg.conf that allows suspend to ram, save it as
   xorg.conf.good.

 2) modify the shell script below to suit you. (I called it gamesxterm.sh)
    #!/bin/sh
    export PATH="/usr/local/sbin:/usr/local/bin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/X11R6/bin:/root/bin"
    export DISPLAY=":1"
    export SHELL=/bin/bash
    # make your xterm bigger for bigger screens: height of 35 is for a 640x480 screen
    exec /usr/bin/xterm -geometry 80x35+1+1 -bg black -fg white

   Modify the shell script below for your system.  (I called it rungamedisplay.sh)
   #!/bin/sh
   xinit -e <full path>/gamesxterm.sh -- /usr/bin/X -config xorg.conf.game :1
   sleep 3
   chvt 12
   sleep 4
   <full path to hibernate script, likely /etc/acpi/hibernate.sh>
   chvt 7

   What does this do and why?
     rungamedisplay.sh starts a new X session using the FGL driver (called by
     your saved xorg.conf.game) and then runs gamesxterm.sh  Then gamesxterm.sh
     sets the DISPLAY variable so that programs will show up in the new X
     session you are running (!) and calls an xterm.  Using the xterm, you can
     call your game(s).  When you are finished, incant
         exit
     This will end gamesxterm.sh and you drop back to rungamedisplay.sh which 
     suspends to disk (hibernate).  Then power-on & you'll be back to normal.
     
     This works because, after the FGL driver has been running, the video card
     is buggered, but everything else is actually working.  So the hibernate
     saves a perfectly valid copy of (essentially) what you were doing before
     you ran rungamedisplay.sh.  When you power-up from the hibernate the first
     part of the boot sequence runs & that gives the video card a hard reset
     which fixes it.  The restore brings back your session and everything is
     perfect.

     You'll notice that, before the hibernate, there are some sleeps & a switch
     to a console session (chvt 12 -- the equivalent of doing
     <cntl><alt><F12>),  then a switch back to X (chvt 7) after the hibernate.
     In theory, all that isn't necessary; however, it is nice to make sure that
     the display has settled down before hibernating and the switch to the
     console lets you see any error messages that get displayed.  -- Just in
     case.

3) Make your new shell scripts executable:
   chmod a+x gamesxterm.sh rungamedisplay.sh

4) Run rungamedisplay.sh to start gaming.

---

