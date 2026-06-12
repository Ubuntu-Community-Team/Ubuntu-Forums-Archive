---
title: "[SOLVED] no graphical login"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by ExpressTrain on 2008-11-27
I've had Hardy Heron working for about a month, but this morning when I tried to turn on the computer, it showed the normal Ubuntu splash screen with the progress bar, but instead of the default graphical login screen, I was presented with a command-line login prompt.  From GRUB, I tried to boot into recovery mode, and I tried the option "xfix  Try to fix X server" (because I know enough to realize that graphical display problems probably have to do with the x server) but it just said 

[FONT="Courier New"]overwriting possibly-customized configuration file; backup in /etc/X11/org.conf.20081127133720[/FONT]

but then, back in the recovery menu, when I select "resume", it just dumps me back at the command-line prompt.

right above the login prompt I see now, it says something like
[FONT="Courier New"]
trying to resume from /dev/disk/by-uuid/b077bfcc-6842-4088- . . .
no resume image, doing normal boot...

ubuntu 9.04.1 for tty1

login:[/FONT]


Does anyone have any suggestions for how to figure out what's wrong with the graphical display?  Are there X11 log files I can look in? or am I barking up the wrong tree?

---

### Post by overdrank on 2008-11-27
Hi and is that a typo 
>  ubuntu 9.04.1 for tty1
Did you mean 8.04

---

### Post by ExpressTrain on 2008-11-27
Yes, that was a typo.  I'm running 8.04

---

### Post by stevek123 on 2008-11-28
have you tried control+alt+F7 ??? I know that you can run mult logins with F1 -> F6 being command line and F7 for graphical... not sure but hope this helps....

---

### Post by bcd87 on 2008-11-28
The graphical login is provided by GDM. If you can get gnome started with startx that could indicate there's no problem with X, but with GDM. Maybe the GDM daemon isn't started during bootup?

---

### Post by ExpressTrain on 2008-11-28
Tried the Cntl-Alt-F7, and that had no effect.  I tried Cntl-Alt-F2 and Cntl-Alt-F3 out of curiosity, and those gave me additional prompts that look like the first one, except they say tty2 and tty3.  So the console-switching stuff seems to be working.  Learned something new there. 


bcd87, I think that's what I was looking for, I'll try xstart at the prompt, and report back.  Assuming that works, I'll do my due-diligence and research GDM to try to figure out what's wrong with it.

Thanks everyone for the responses.

---

### Post by ExpressTrain on 2008-11-28
I tried bcd87's suggestion of entering startx, which resulted in a blank screen :( but then used Stevek123's suggestion of switching back to the original console with Cntl-Alt-F1.  I saw some errors, which I assume are from startx.  So I re-ran it, piping the error output to a file, and here's the pertinent part:
[FONT="Courier New"][INDENT]
(==) Log file: "/var/log/Xorg.0.log"
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "i2c" already built-in
(II) Module "ddc" already built-in
(II) Module "ramdac" already built-in
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

expected keysym, got XF86KdbLightOnOff: Line 70 of pc
expected keysym, got SF86KDBBrightnessDown: line 71 of pc
. . . 
Set ClientVersion: 0 9
Waiting for X server to shut down
xinit: unexpected signal 2.[/INDENT][/FONT]

I looked at the log file referenced above at /var/log/Xorg.0.log and it had a LOT of stuff that looked pretty low level, but nothing stood out as an error that I could see.  Only at the end It said something like "Trying load detection on VGA1, nothing" and a few lines down from that "Trying load detection on VGA2, nothing".

Could the reference above to the NVidia drivers be a clue?  This particular system had the drivers for Nvidia installed (the ones that are not part of Ubuntu because they are proprietary).  They worked for a few weeks until now.  Is it possible these are causing a problem?

Also, I'm wondering if I should take this thread to a more graphics-centered forum instead of the Absolute Beginner Talk.

---

### Post by bcd87 on 2008-11-28
Hmm, maybe you could try
```
sudo nvidia-xconfig
``` and see if that helps?

---

### Post by taseedorf on 2008-11-28
no graphical login...could be a lot of things...

first off...
sudo /etc/init.d/gdm stop
(this stops any cases of your display manager)
than type
sudo /etc/init.d/gdm start

and see if it brings up a login window

or try this

log in...
type
'startx'
it should work, if it gives you an error about no suitable screens than you need to reconfigure your xserver

type in terminal
'sudo dpkg-reconfigure xserver-xorg'
and choose what fits you best
than after that, type
startx
and see if it works

otherwise..... try

well, first off, it looks like you don't have the proper nvidia drivers...

go to nvidia.com and download the drivers for your machine, and install them at command line.....

it will do it automatically for you...

once downloaded, change the file name to nvidia
and than at prompt type

sudo sh nvidia.run (i think .run is the extension of the file, not sure).


please let us know if we helped solve at all

---

### Post by ExpressTrain on 2008-11-29
> **bcd87 said:**
> Hmm, maybe you could try
```
sudo nvidia-xconfig
``` and see if that helps?

nvidia-xconfig reported an error about a missing device line, but also said it wrote a new x configuration file, so I tried startx again, and I now have a desktop running with my menus and everything :) .  It also got a message about updates, being available, so I downloaded those.  Then when I tried to restart the machine, I only saw things like "Hibernate" and "logout".  I assume this is because I didn't start my x session through GDM.  So it looks like x is working now, I just have to work on GDM.

I'll try Taseedorf's suggestion about restarting GDM now.

---

### Post by ExpressTrain on 2008-11-29
I tried sudo /etc/init.d/gdm stop  but it said "command not found".  Just to verify, I checked in /etc/init.d myself and sure enough, no gdm.  I think there has to be a reference in that folder in order for it to be run at startup, right?  So it must have been removed.

I did a search in Synaptic for GDM and it showed up as not even installed.  So I marked it for installation and applied that change.  Then I restarted the machine, and GDM is working again.

So we can call this issue resolved.  However, I don't know how this issue came up in the first place.  The day before I encountered it, I was tyring to resolve some sound issues, and re-installed the ALSA libraries based on this post: [http://ubuntuforums.org/showthread.php?t=661102]("http://ubuntuforums.org/showthread.php?t=661102")
Could that have caused a problem?

---

### Post by ExpressTrain on 2008-12-05
I found a helpful guide for this particular scenario.  If other people experience this problem, try this guide:
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

