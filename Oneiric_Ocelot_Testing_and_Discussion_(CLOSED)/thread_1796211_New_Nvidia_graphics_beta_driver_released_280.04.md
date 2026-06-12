---
title: "New Nvidia graphics beta driver released 280.04"
date: 2011-07-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-03
Nvidia has released a new beta driver 280.04.
This one has already the preliminary support for Xserver 1.11 rc1.

---

### Post by w3rt on 2011-07-04
Is this available in Oneiric yet?

---

### Post by Harry33 on 2011-07-04
> **w3rt said:**
> Is this available in Oneiric yet?

Not in Oneiric repos nor in any PPA yet.
Only by installing from Nvidia site. That is not recommended, however.

---

### Post by VinDSL on 2011-07-05
> **Harry33 said:**
> Not in Oneiric repos nor in any PPA yet.
Only by installing from Nvidia site. **[COLOR="Red"]That is not recommended, however[/COLOR]**.
Thus, I must install the .run file... LoL!  :D

I've installed nVidia .run files many, many, times, but not with lightdm.

Hrm...

Stopping lightdm is simple enough...

```
$ sudo service lightdm stop
```

...but no matter what I do, I can't stop the X server.

I tried...

```
pkill -9 /usr/bin/X
```

... to no avail.

Anybody got a clue how to stop X?!?!?

---

### Post by lucazade on 2011-07-05
> **VinDSL said:**
> Thus, I must install the .run file... LoL!  :D

I've installed nVidia .run files many, many, times, but not with lightdm.

Hrm...

Stopping lightdm is simple enough...

```
$ sudo service lightdm stop
```

...but no matter what I do, I can't stop the X server.

I tried...

```
pkill -9 /usr/bin/X
```

... to no avail.

Anybody got a clue how to stop X?!?!?

just start in recovery mode to avoid X starting?

---

### Post by Harry33 on 2011-07-05
> **VinDSL said:**
> Thus, I must install the .run file... LoL!  :D

I've installed nVidia .run files many, many, times, but not with lightdm.

Hrm...

Stopping lightdm is simple enough...

```
$ sudo service lightdm stop
```

...but no matter what I do, I can't stop the X server.

I tried...

```
pkill -9 /usr/bin/X
```

... to no avail.

Anybody got a clue how to stop X?!?!?

Yes that's it. From recovery mode drop to shell.
Remember though that the .run file may not work.
Oneiric's nvidia-current is patched to work with the latest mesa.

---

### Post by VinDSL on 2011-07-05
> **lucazade said:**
> just start in recovery mode to avoid X starting?
> **Harry33 said:**
> Yes that's it. From recovery mode drop to shell.
Good idea(s) but, no soap...  ;)

Heh!  I posted this thread, before going to bed. I hate to sleep (it's a waste of time, albeit necessary) and succumb to "the first death" only when my body/brain is shutting down.  I rate it second, only to defecation, in the disgusting things we must do, to stay alive.  I would choose to do neither, given the choice.  LoL!

Normally, I'm more garrulous in my descriptions, and of the fixes I've tried, but... I was too tired.  Sorry!

Yes, I went down the recovery path, before posting the OP, and... no, that didn't work either.

Here is a more complete description...  :D

> **Harry33 said:**
> Remember though that the .run file may not work.

Oneiric's nvidia-current is patched to work with the latest mesa.
True, but...

I can't remember a nVidia .run file not working, if you will.

The only 'problem' I've run across with .run file installs (vs. nvidia-current) is, many times ,run installs won't recompile properly when doing subsequent updates to the kernel, system files, et cetera, from the Ubu  repos.  Soooo, many times you end up having to re-install the .run file after an update/upgrade to the system files.  Then, again, many times we need to do this with nvidia-current, yes?

Back to the REAL problem...

The nVidia .run file installer *thinks* that X server is running (even on a cold boot, recovery & drop to root shell) so it won't complete the install.

I judge that it's seeing something - a remnant of X - and it *thinks* that X is running, even though it is not.  Something is lingering around, somewhere - probably a runtime file in /tmp or whatever.

My best guess is... 

Lightdm is not erasing ALL remnants of X, when you stop the service (or even do a reboot) and that remnant is what the nVidia .run file installer is seeing, e.g. giving you the middle finger.

Put another way, the process goes fine, until the installer gets down to point of actually writing the files to disk, then it *thinks* X is still running - gives you a warning dialogue about X still running - then backs out of the install, with a wave of a hand, and goodbye.

Make more sense now?  :)

A bug, perhaps?!?!?!?

I'll search for a workaround...

---

### Post by dnewkirk on 2011-07-06
Maybe this is a stupid suggestion, but couldn't you type "e" at the Grub loader and add "init 3" to the boot params? You should be able to boot without X starting at all...

---

### Post by Harry33 on 2011-07-06
One possibility would be to purge nvidia installation first.
Then a could boot, recovery mode and drop to shell.

---

### Post by zero2xiii on 2011-07-06
> **VinDSL said:**
> 
Back to the REAL problem...

The nVidia .run file installer *thinks* that X server is running (even on a cold boot, recovery & drop to root shell) so it won't complete the install.

I judge that it's seeing something - a remnant of X - and it *thinks* that X is running, even though it is not.  Something is lingering around, somewhere - probably a runtime file in /tmp or whatever.

My best guess is... 

Lightdm is not erasing ALL remnants of X, when you stop the service (or even do a reboot) and that remnant is what the nVidia .run file installer is seeing, e.g. giving you the middle finger.

Put another way, the process goes fine, until the installer gets down to point of actually writing the files to disk, then it *thinks* X is still running - gives you a warning dialogue about X still running - then backs out of the install, with a wave of a hand, and goodbye.

Make more sense now?  :)

A bug, perhaps?!?!?!?

I'll search for a workaround...

I can only comment on how I have installed nvidia drivers many times before. Do the recovery console thing, login and all that, then do a "telinit 3" and run the *.run file... It should enquire if it may disable x for you (by changing some other config file) accept this and bob's your uncle, just reboot (graphics should have changed now) back into the recovery console and re-run the script.. Remember to sudo ;)

This is how I install all the nvidia drivers.. maby you just missed something.. lolz.. but it might be a bug, esp on some screens.. nvidia still doesnt support linux the way it can... 

cherios

---

### Post by VinDSL on 2011-07-06
> **zero2xiii said:**
> I can only comment on how I have installed nvidia drivers many times before. Do the recovery console thing, login and all that, then do a "telinit 3" and run the *.run file... It should enquire if it may disable x for you (by changing some other config file) accept this and bob's your uncle, just reboot (graphics should have changed now) back into the recovery console and re-run the script.. Remember to sudo ;)

This is how I install all the nvidia drivers.. maby you just missed something.. lolz.. but it might be a bug, esp on some screens.. nvidia still doesnt support linux the way it can... 

cherios
Thanks!

I do a "telinit 3".  If I don't, the installer backs out with a suitable tongue-lashing.  :)

I've also been deleting X0-lock:

```
$ sudo rm -f /tmp/.X0-lock
```

No matter what I've tried, nvidia-installer *thinks* X is running.


Here's the result of my most recent attempt:
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jul  6 04:24:28 2011
installer version: 280.04

PATH:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

option status:
  license pre-accepted               : false
  update                             : false
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : ftp://download.nvidia.com
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your
       kernel.  This may be because it is in use (for example, by the X
       server), but may also happen if your kernel was configured without
       support for module unloading.  Please be sure you have exited X before
       attempting to upgrade your driver.  If you have exited X, know that your
       kernel supports module unloading, and still receive this message, then
       an error may have occured that has corrupted the NVIDIA kernel module's
       usage count; the simplest remedy is to reboot your computer.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

Weird, eh what?

I'll try it again, later tonight...  ;)

EDIT

Whoa, baby!

I just noticed that "no X server check" line, while I was checking this post for typos.

Must be a switch, to turn it off, yes?

BBL

---

