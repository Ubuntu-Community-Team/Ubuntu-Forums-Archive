---
title: "telinit S GDM locked keyboard and monitor shutoff"
date: 2006-02-03
forum: Programming Talk
---

### Post by Pragmatist on 2006-02-03
I posted this bug in bugzilla awhile ago, but nobody seems to be able to explain it.
[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/29175](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/29175)

Basically, I can do "telinit S" in the following cases:

1.) switch consoles and /etc/init.d/gdm stop  followed by startx
2.) switch consoles and type "telinit S"
3.) on my Fedora box which doesn't start gdm as a daemon
4.) on Ubuntu when I don't start gdm as a daemon
5.) I can always get to single-level user mode by "telinit 1" 

When I type "telinit S" on the regular Ubuntu Breezy system, my terminal receives continuous prompts (carriage returns) and I get a locked keyboard (caps lock doesn't light, nothing works).  I can use "xset r off" and not get the repeated prompt, but the keyboard is still dead.  Sometimes my monitor shuts off, especially when I change consoles, even when I don't do telinit S  Also, when I use chvt I get the repeated carriage returns when I return to vt7 but no locked keyboard.  Also, when I would shutdown using "shutdown -h now" from an xterm I'd get these carriage returns as it was shutting down.

I can get "telinit S" to work when I start GDM like Fedora does.  I start via a script (like Fedora's /etc/X11/prefdm) which, in turn, starts GDM with the --nodaemon option.  Also, in all these cases where it works, X and/or GDM are subprocesses under /bin/sh  Here are some different process trees:

Default version in Breezy
/usr/sbin/gdm
 \_ /usr/sbin/gdm
     \_ /usr/X11R6/bin/X :0 -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

With GDM started via a script with --nodaemon option (like in Fedora)
/bin/sh /etc/X11/prefdm -nodaemon
 \_ gdm -nodaemon
      \_ gdm -nodaemon
          \_ /usr/X11R6/bin/X :0 -audit 0 -auth / var/lib/gdm/:0.Xauth -nolisten tcp vt7

switch console, stop GDM, startx method:
/bin/login --
 \_ -bash
     \_ /bin/sh /usr/bin/startx
         \_ xinit /etc/X11/xinit/xinitrc -- /etc/X11/xinit/xserverrc -auth /root/.serverauth.13269
            \_ /usr/bin/X11/X -dpi 100 -nolisten tcp


In all cases where it works, GDM/X are started under shell rather than directly branching off init

So really, from a practical point of view (don't let the handle fool you :) ) this isn't a problem.  However, from a programming point of view, at a minimum, this isn't a graceful response to "telinit S" which is a reasonable command to type in a terminal.  Also, I think the monitor and other problems are related.  My vague guess is that this has something to do with the console, control of the display and the shell :)

I've spent a huge amount of time on this and despite that I still don't really understand what is going on!  I'm in the process of studying for my Linux certification (believe it or not) and am trying to learn all that I can about Linux.  None of my books discuss consoles, X, virtual consoles, GDM, or even login shells, in sufficient detail.  Please can somebody show me the way!  Thank you.

---

