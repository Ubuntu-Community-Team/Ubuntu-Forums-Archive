---
title: "/run/udev"
date: 2011-05-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zika on 2011-05-17
This morning I can not start proper session (even tty) with Ubuntu and the only thing I see unusual is some problem with udev (not being able to open /run/udev, respawning)... Am I the only one? Any ideas? Chroot-ed and upgraded, but, no change...

---

### Post by fil0~ on 2011-05-17
Same problem since yesterday.
I cannot log into the session because i have a frozen screen on GDM, no mouse no keyboard.
Removing the mouse and then plugging it in again makes it work, but i cannot do the same for the keyboard because i'm on a laptop.

Maybe related to this: [http://bugs.gentoo.org/show_bug.cgi?id=365679](http://bugs.gentoo.org/show_bug.cgi?id=365679)

---

### Post by zika on 2011-05-17
I'm ashamed to say, but it was, really, time for reinstall on this machine, running in Testing for many months... Lot of stuff gathered and it was time to delete Win partition and make Ubuntu live on the whole disk. So, I'm, currently on Natty, waiting some (new) energy to go to Oneiric back... In a couple of hours, maybe...
I, simply, do not know what made me make a thorough backup yesterday morning, so I was totally ready for this...

Update: wild guess: do You use xorg-edgers ppa?

---

### Post by fil0~ on 2011-05-17
> **zika said:**
> 
Update: wild guess: do You use xorg-edgers ppa?
Why?

What about downgrading udev?

---

### Post by fil0~ on 2011-05-17
BINGO! Removing /run directory worked!

Should we open a bug on launchpad?

---

### Post by zika on 2011-05-17
Problem is reproducible. I tried upgradin Natty install to Oneiric and got at the same position, with a bit different behaviour of OS. Back to Natty, for the first time having Unity to work... (That was one of the reasons I've asked about xorg-edgers/ppa). Once this fog clears i?ll be back with You on this Oneiric journey...

---

### Post by MacUntu on 2011-05-17
Well, I think the switch to /run isn't just a one-package-update. :P

---

### Post by wojox on 2011-05-17
> **MacUntu said:**
> Well, I think the switch to /run isn't just a one-package-update. :P

True I posted a link in the Cafe a while back [Fedora to give /run a run]("http://ubuntuforums.org/showthread.php?t=1718118&highlight=fedora+run")

Ubuntu said they were interested as well for the 11.10 release.

---

### Post by MacUntu on 2011-05-17
Maybe we get a /run/dos/run... oh snap!

---

### Post by 3vi1 on 2011-05-17
Ran into this same thing.  I can only get in if I fall back to the 2.6.39-1 kernel.  I wouldn't panic; I'm guessing they're in the middle of updates and it will be resolved when some additional packages hit.

---

### Post by zika on 2011-05-18
> **3vi1 said:**
> Ran into this same thing.  I can only get in if I fall back to the 2.6.39-1 kernel.  I wouldn't panic; I'm guessing they're in the middle of updates and it will be resolved when some additional packages hit.That is because update-initramfs was performed only on the latest kernel (or the one being used at the moment of upgrade). Keep that kernel in that state until new version of udev is available.

---

### Post by Quackers on 2011-05-18
I'm getting an error at boot, but only on one Oneiric installation (the almost unused one) whilkst the one I use every day is fine.
As the daily-used one is fine I ran all available updates on the largely unused one and now I can't get a usable desktop on it.
The error at startup reads similar to
udevd (66) or (67) error: runtime directories 'run/udev' not writable
defaulting to '/dev/.udev'

It's strange that it's just affecting one installation.

---

### Post by seeker5528 on 2011-05-19
Don't know why people are seeing this. 

There was an issue in Debian unstable with /run.....

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=621036](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=621036)

But the base-files package I'm seeing available on my Ubuntu mirror base-files_6.3ubuntu2 doesn't create a /run directory.

I'm not installing anything from a PPA at the moment, something installed from a PPA could be causing this, but I don't know why a package other than base-files would create the /run directory.

Later, Seeker

---

### Post by Harry33 on 2011-05-20
> **seeker5528 said:**
> Don't know why people are seeing this. 

There was an issue in Debian unstable with /run.....

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=621036](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=621036)

But the base-files package I'm seeing available on my Ubuntu mirror base-files_6.3ubuntu2 doesn't create a /run directory.

I'm not installing anything from a PPA at the moment, something installed from a PPA could be causing this, but I don't know why a package other than base-files would create the /run directory.

Later, Seeker

The issue in Ubuntu is the previous version (base-files_6.2).
Here is a changelog text from the versions 6.3 and 6.2:

> 
Changelog

base-files (6.3) unstable; urgency=low

  * Dropped /run until everything else is ready for it. In particular,
    udev should not blindly assume that it works just because it exists.

base-files (6.2) unstable; urgency=low
  * Added /run. Requested by Roger Leigh. Closes: #620157.


So the version 6.3 should have removed /run.
What is really strange is that neither of the version 6.2 nor 6.3 were in Oneiric official repos.

For those experiencing this bug, the best solution is to remove /run from their systems.

---

### Post by MAFoElffen on 2011-05-20
> **3vi1 said:**
> Ran into this same thing.  I can only get in if I fall back to the 2.6.39-1 kernel.  I wouldn't panic; I'm guessing they're in the middle of updates and it will be resolved when some additional packages hit.
I just got his tonight.  Hmm...

---

### Post by MAFoElffen on 2011-05-20
> **Harry33 said:**
> For those experiencing this bug, the best solution is to remove /run from their systems.
Remove how?  From a line in a file somewhere?

---

### Post by Harry33 on 2011-05-20
> **MAFoElffen said:**
> Remove how?  From a line in a file somewhere?

1) In terminal:
```
sudo rm -rf /run
```

2) with nautilus (root):
```
gksu nautilus
```
and then go to the directory /run and delete it.

---

### Post by Quackers on 2011-05-20
Thanks Harry.
Is that the run directory inside /var ?

---

### Post by tghe-retford on 2011-05-20
> **Harry33 said:**
> 1) In terminal:
```
sudo rm -rf /run
```

2) with nautilus (root):
```
gksu nautilus
```
and then go to the directory /run and delete it.
Using Dolphin on KDE but it's the same concept, I have the same bug, and I ain't seeing no /run directory (see screenshot attachment).

---

### Post by Quackers on 2011-05-20
The only one I can find is inside /var and that won't delete because it's in use.  
!!:confused:

---

### Post by coffeecat on 2011-05-20
> **Quackers said:**
> The only one I can find is inside /var and that won't delete because it's in use.


I don't have a /run directory either, but I do get "udev[101] error: runtime directory '/run/udev' not writeable". But then the system boots up OK. The desktop is a bit odd, but that's a different issue that everyone is seeing. So I intend to try to ride this one out and see what updates bring.

Call me simplistic, but I guess that the reason that the directory /run/udev is not writeable is because it doesn't exist. So I don't see the logic of trying to delete a directory that isn't there. :-k The error says '/run/udev', not '/var/run/udev' and there is no /var/run/udev on my system. Plenty of /var/run/somethings, but no .../udev, so I think I'll leave my /var directory in peace. :)

I see that other(s) did have a /run directory and there was some talk of a ppa. This Oneiric system is a fairly straightforward upgrade from a working Natty with no PPAs enabled.

---

### Post by VinDSL on 2011-05-20
> **Harry33 said:**
> For those experiencing this bug, the best solution is to remove /run from their systems.
That's funny!

This morning, I decided to add /run/udev to my system - just to see what would happen.

Subsequently, I was met with hard-locks on every boot.  Oops!

Removing /run took care of the lock-ups.  Now I'm back to dependency probs.  Heh!

---

### Post by zika on 2011-05-20
> **coffeecat said:**
> I don't have a /run directory either, but I do get "udev[101] error: runtime directory '/run/udev' not writeable". But then the system boots up OK. The desktop is a bit odd, but that's a different issue that everyone is seeing. So I intend to try to ride this one out and see what updates bring.

Call me simplistic, but I guess that the reason that the directory /run/udev is not writeable is because it doesn't exist. So I don't see the logic of trying to delete a directory that isn't there. :-k The error says '/run/udev', not '/var/run/udev' and there is no /var/run/udev on my system. Plenty of /var/run/somethings, but no .../udev, so I think I'll leave my /var directory in peace. :)

I see that other(s) did have a /run directory and there was some talk of a ppa. This Oneiric system is a fairly straightforward upgrade from a working Natty with no PPAs enabled.(SEveral days ago)NN, clean install, no PPA's, 3 minutes old. Upgraded to OO, via sources.list. Locked on the first reboot with kernel that was initramfs-updated. As soon second kernel was initramfs-updated it looked too... Did not have energy to investigate at that moment... Natty reinstalled... Maybe this weekend again in OO testing...

---

### Post by VinDSL on 2011-05-20
> **zika said:**
> (SEveral days ago)NN, clean install, no PPA's, 3 minutes old. Upgraded to OO, via sources.list.[...]
How does your UbuOO sources.list look?

Here's mine:

```

## Main repositories
deb http://archive.ubuntu.com/ubuntu oneiric main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted multiverse universe

## Updates repositories
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main restricted multiverse universe

## Security repositories
deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-security main restricted multiverse universe

## Backports repository
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

## Partner repository
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## Extras repository
# deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main

## Proposed repository
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed restricted main multiverse universe

## Debian 'Sid' repository
# deb http://ftp.de.debian.org/debian sid main
# deb-src http://ftp.de.debian.org/debian sid main

```


I'm using OO right now (as I type).

```

vindsl@Zuul:~$ date && uname -s -r && unity --version && cat /etc/lsb-release && /usr/lib/nux/unity_support_test -p
Fri May 20 02:12:22 MST 2011
Linux 2.6.39-020639rc7-generic
unity 3.8.12
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
vindsl@Zuul:~$ 

```

It's butt fugly, and mad as a wet hornet, but it's working.  :D

---

### Post by zika on 2011-05-20
> **VinDSL said:**
> How does your UbuOO sources.list look?

Here's mine:

```

## Main repositories
deb http://archive.ubuntu.com/ubuntu oneiric main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted multiverse universe

## Updates repositories
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main restricted multiverse universe

## Security repositories
deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-security main restricted multiverse universe

## Backports repository
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

## Partner repository
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## Extras repository
# deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main

## Proposed repository
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed restricted main multiverse universe

## Debian 'Sid' repository
# deb http://ftp.de.debian.org/debian sid main
# deb-src http://ftp.de.debian.org/debian sid main

```I'm using OO right now (as I type).

```

vindsl@Zuul:~$ date && uname -s -r && unity --version && cat /etc/lsb-release && /usr/lib/nux/unity_support_test -p
Fri May 20 02:12:22 MST 2011
Linux 2.6.39-020639rc7-generic
unity 3.8.12
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
vindsl@Zuul:~$ 

```It's butt fugly, and mad as a wet hornet, but it's working.  :DNo OO at this moment, as You could read from my message...
Similar out from my (late) OO install You could find somewhere here...
I've learned, still, a lot from trying to revive that OO when udev stroke. I've barked below udev tree but,... Now, with all that &#8222;knowledge&#8220; it would be easier. But, real life is calling me back. As I said, maybe this weekend, but I would not count on that with this sun lurking through the window shades...
[COLOR=DarkSlateGray]
Little offtopic: FluxBox was a marvel in this speedy transition. Taking with me just 3 or 4 text-ual files, gave me, in seconds, the same environment I'm used to and there were no time needed for getting used to anything... Unity, Gnome, OK, but FB rules...[/COLOR] :)

---

### Post by Harry33 on 2011-05-20
> **coffeecat said:**
> 
...
Call me simplistic, but I guess that the reason that the directory /run/udev is not writeable is because it doesn't exist. So I don't see the logic of trying to delete a directory that isn't there. :-k 
...


If you do not have /run/udev directory in your system, you are not experiencing this lock up bug.
Instead you only see a warning message and then system defaults to /dev/.udev.

Perhaps the message comes from udev.
There is new udev version in Launchpad now.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/udev/170-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/udev/170-0ubuntu1)

---

### Post by MAFoElffen on 2011-05-20
> **Quackers said:**
> The only one I can find is inside /var and that won't delete because it's in use.  
!!:confused:
I got the same error on the /var/run/ when I tried to delte it.  

I booted from a LiveCD > Mounted the sys partition > Mounted the system... Deleted the /var/run/ directory, which returned a message saying it was having a "problem resolving the host"

But after when I went to look for it-- **It is definitely gone now.**

LMAO!  "That" really wasn't such a great idea after all.  Now I get an error on boot saying "The disk isn't ready. Looking for /var/run/.  Press "S" to skip or "M" for manual recovery."  I pressed "S" and it went on to GDM...

Like I thought and asked before. There's seems to be a pointer in "some" config file somewhere, pointing to those directories, right? (in partucular now, thee pointer to /var/run/) Anyone know offhand what file to change that line, to disable that pointer?

---

### Post by Quackers on 2011-05-20
Did you copy /var/run first so you could replace it, if necessary? Or do you have a similar separate installation that you can steal its /var/run file? I did :-) 
I booted into the other installation and ran ```
sudo cp -r /var/run /media/sdb8/var/run
``` where the broken installation (on sdb8) was mounted on /media. I then rebooted and it's back to where it was before -  still borked :-)

---

### Post by seeker5528 on 2011-05-20
> **Harry33 said:**
> So the version 6.3 should have removed /run.
What is really strange is that neither of the version 6.2 nor 6.3 were in Oneiric official repos.

The Ubuntu changelogs include the Debian changes, so it can be a little unclear sometimes which issues actually affected Ubuntu.

Because of the nature of the problem it was dealt with pretty quickly by the Debian maintainers with a relatively low number of users affected and the fix on affected systems is easy once you find out what the problem is, so the Debian maintainer just put the creation of /run on the back burner while other maintainers get their packages ready for it and left it to the affected users to get rid of the /run directory themselves.

Later, Seeker

---

### Post by seeker5528 on 2011-05-20
> **MAFoElffen said:**
> I got the same error on the /var/run/ when I tried to delte it.

You should not delete '/var/run/'.

It sounds like you can still boot, so at the command line you can type ```
sudo mkdir /var/run
``` to see if you can re-create '/var/run/'

I think anything that uses the '/var/run/' directory should recreate their stuff when necessary, in which case it  shouldn't be necessary for you to re-create anything else that existed in '/var/run', not completely sure though.

Later, Seeker

---

### Post by 3vi1 on 2011-05-20
Here's my situation:

I have no /run, have never had /run, and never deleted it.

2.6.39-2 won't work for me because, after the error message about /run/whatever not being writeable, the system tells me it couldn't mount my /home directory (a btrfs partition) and the USB keyboard is totally unresponsive.  So, obviously - it's not falling back and talking to devices in the previous manner.

At that point, I can't 'S'kip or go 'M'anual.  So, I have to use the reset button (no RSEIUB without a keyboard) and resort to the older kernels.  The older kernels mount /home without any issue whatsoever.

Again... I'm not panicking.  But, if you're running 11.04, I would *not* recommend jumping on the pre-alpha wagon at this time.  Give a few more weeks for the packages to settle.

---

### Post by MAFoElffen on 2011-05-20
> **Quackers said:**
> Did you copy /var/run first so you could replace it, if necessary? Or do you have a similar separate installation that you can steal its /var/run file? I did :-) 
I booted into the other installation and ran ```
sudo cp -r /var/run /media/sdb8/var/run
``` where the broken installation (on sdb8) was mounted on /media. I then rebooted and it's back to where it was before -  still borked :-)
LOL-- No I didn't. Thought about it as I hit that enter key.... Doh!!! {hindsight}

And I didn't mention that delighting those directories did nothing with the original text bootup error(?)  It's still there unchanged with those 2 directories gone.

No matters.  It still boots and runs.  If it does turm into anything later-- I still have all my config files backed off for a reinstall if needed.  Did that plany with the last round of tests.

---

### Post by mrfelker on 2011-05-22
> **fil0~ said:**
> BINGO! Removing /run directory worked!

Should we open a bug on launchpad?

I have the same error msg  on booting oneiric but there is not /run directory.  Totally harmless message however.  Only cosmetic.

Marty Felker

---

### Post by grubler on 2011-05-22
No solution for this yet ?

I have try with chroot but no success :confused:

(Oneiric Ocelot - 2.6.39-2)

---

### Post by Quackers on 2011-05-22
> **mrfelker said:**
> I have the same error msg  on booting oneiric but there is not /run directory.  Totally harmless message however.  Only cosmetic.

Marty Felker
Not true here!
No desktop background 
Opened windows won't close
Windows moved around the screen leave snail trails
Poorly rendered fonts on the top panel

Definitely not a harmless message here (unless something else is causing these problems).

The same error message has now start to appear on my gnome3/gnome-shell OO installation too, whereas that had escaped until today.
That one is harmless though as no other effects are shown on the desktop.

---

### Post by VinDSL on 2011-05-22
> **Quackers said:**
> Not true here!

No desktop background 
Opened windows won't close
Windows moved around the screen leave snail trails
Poorly rendered fonts on the top panel

Definitely not a harmless message here (unless something else is causing these problems).[...]
Have you installed the **gtk3-engines-unico 0.1.0+r64-0ubuntu1** package?

I had all of the problems, that you mentioned above.

I hammered away on OO for days, to no avail.

I actually started using 10.10, so I could get some work done. LoL!

Then, after I installed the package above, OO started acting normally - better than Natty, actually.

I've been on this machine for 14h today.  I couldn't stand it for 14m before.

---

### Post by Quackers on 2011-05-22
I don't remember that one :-)
I'll go back in and take a look.
Thanks VinDSL

---

### Post by Quackers on 2011-05-22
Ok done that. Still the same :-(
Maximised windows won't go away, even if I close them.
Can't take a screenshot because it just takes a snap of a blue/green background. I don't have a blue/green background, I have a black one :-)
Still got snail trails from moving minimised windows around.
No good dude, but thanks for the suggestion!

Why would I need to install that package separately, please?

Actually here's a snap of my panel, but with the wrong background colour, of course.

---

### Post by MacUntu on 2011-05-22
...

---

### Post by Quackers on 2011-05-22
All these problems began after running some updates. All at the same time. Why would Nautilus stop drawing my desktop?
Maybe you should change your glasses - that's not the same /run/udev error at all :-)

---

### Post by MacUntu on 2011-05-22
...

---

### Post by Quackers on 2011-05-22
So the updated Nautilus stops drawing the desktop, but only for some users?

I don't even understand your last point, sorry, but nevermind.

---

### Post by matt_symes on 2011-05-22
> **Quackers said:**
> So the updated Nautilus stops drawing the desktop ...

@Quackers. 

Just updated my Oneiric for the first time in a good number of days. My desktop is drawing fine (all be it, a little bit slowly after boot up), however i cannot start nautilus.

Starting it from the command line gives...

```
matthew@matthew-Aspire-7540:~$ nautilus

Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
aborting...
Aborted
atthew@matthew-Aspire-7540:~$ 
```You can see what my problem is. I will not look at this today.

 Is something similar happening on your borked system ? Might be an area to start looking at maybe ?

---

### Post by VinDSL on 2011-05-22
> **Quackers said:**
> Ok done that. Still the same :-(
Maximised windows won't go away, even if I close them.
Can't take a screenshot because it just takes a snap of a blue/green background. I don't have a blue/green background, I have a black one :-)
Still got snail trails from moving minimised windows around.
No good dude, but thanks for the suggestion!

Why would I need to install that package separately, please?

Actually here's a snap of my panel, but with the wrong background colour, of course.
Have you set a background image & color in System Settings -> Personal -> Background ?

The Background Panel looks like this...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-22-may-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-22-may-2011.png")[/INDENT]

---

### Post by Quackers on 2011-05-22
@matt_symes
are you running Unity on that install?

@VinDSL
Do you mean since the updates? All was set ok before them. Haven't set them again since the updates though.
I am using my OO/gnome3 system on a daily basis as the unity system is so borked.

---

### Post by matt_symes on 2011-05-22
> are you running Unity on that install?

Yes.

---

### Post by ronacc on 2011-05-22
desktop icons won't appear and nautilus won't start from panel or menu but will from terminal with errors .

---

### Post by Quackers on 2011-05-22
Thanks, I'll boot back into the unity install and have a look :-)

---

### Post by Quackers on 2011-05-22
Ok, I've set a desktop background again and that's back to normal. No more snail trails or windows that won't close :-)
Starting Nautilus from the terminal produces no errors at all here.It just starts up.
The panel still looks very dodgy though. The icons look normal now but the text is very faded, almost unreadable where the date is.
The theme also seems to have gone for a walk!
But all in all it's much better than it was.
Many thanks all :-)

---

### Post by dino99 on 2011-05-22
> **ronacc said:**
> desktop icons won't appear and nautilus won't start from panel or menu but will from terminal with errors .

get the same errors on i386, "classic" choice

---

### Post by Hanmac on 2011-05-22
i chould be related: i can not change the desktop background, and there are no icons on the desktop, and i cant even open the contect menu of the deskop

other question: why cant i open the nautilus from menu? the LocationsFolder opens gwenview and if i deinstall it i prever Konqueror ... and this on GDM!!

edit:classic amd64

---

### Post by ronacc on 2011-05-22
> **dino99 said:**
> get the same errors on i386, "classic" choice

I'm on classic too , amd64 .

---

### Post by ronacc on 2011-05-22
I figured out how to get nautilus to start from the panel icon in classic , rt click on the icon , select properties and remove --browser from the command line . leave everything else.

---

### Post by MacUntu on 2011-05-22
I really don't wanna poop the party, but can you continue in this thread: [http://ubuntuforums.org/showthread.php?t=1760490](http://ubuntuforums.org/showthread.php?t=1760490)

*This* one is about problems related to the transition from /dev/.udev to /run/udev.

---

### Post by zika on 2011-05-22
> **MacUntu said:**
> I really don't wanna poop the party, but can you continue in this thread: [http://ubuntuforums.org/showthread.php?t=1760490](http://ubuntuforums.org/showthread.php?t=1760490)

*This* one is about problems related to the transition from /dev/.udev to /run/udev.It stopped being about /run/dev after very short time... :)

---

### Post by zoff_ita on 2011-05-23
I get the same error.
I tried to run kernels 2.6.39-1/2/3 and to remove /run folder but problem stand the same, I'm freezed in GDM screen.
I can get mouse to work uplugging and plugging it.

I can fallback to TTY resetting X server with Alt+Stamp+K and pressing Ctrl+Alt+Fx. 
From the TTY i can use keyboard and ran startx by-passing gdm but even if I can load the desktop keyboard stands unresponsive.

I also noticed an error about / not writable, I already checked /etc/fstab and both with UUID and dev name nothing changes.

Any suggestion?

---

### Post by MAFoElffen on 2011-05-23
> **zoff_ita said:**
> I get the same error.
I tried to run kernels 2.6.39-1/2/3 and to remove /run folder but problem stand the same, I'm freezed in GDM screen.
I can get mouse to work uplugging and plugging it.

I can fallback to TTY resetting X server with Alt+Stamp+K and pressing Ctrl+Alt+Fx. 
From the TTY i can use keyboard and ran startx by-passing gdm but even if I can load the desktop keyboard stands unresponsive.

I also noticed an error about / not writable, I already checked /etc/fstab and both with UUID and dev name nothing changes.

Any suggestion?
I successfully removed both the /run/udev and /var/run/.udev folders.  It didn't change that startup error on my box at all!  It still gets it.  (removed the folder in /var by booting off a LiveCD Mounting the drive and sys...)

There's still something somewhere pointing to it.

---

### Post by seeker5528 on 2011-05-23
> **MAFoElffen said:**
> I successfully removed both the /run/udev and /var/run/.udev folders.  It didn't change that startup error on my box at all!  It still gets it.  (removed the folder in /var by booting off a LiveCD Mounting the drive and sys...)

There's still something somewhere pointing to it.

I am assuming when you say '/var/run/.udev' you really meant '/dev/.udev/' since there shouldn't be a '/var/run/.udev/' folder.

I suspect that '/dev/.udev/' will get created again if you delete it since I don't see it in the list of installed files (which includes directories) supplied by the udev package , this is the normal place the udev stuff will get written to until the transition to '/run/' happens, you shouldn't be doing anything to it.

If you see an error message indicating something about '/run/udev/' not being  writable and falling back to '/dev/.udev/', that's not an indication of a problem, it's just telling you what it found and what it's doing as a result of what it found.

Later, Seeker

---

### Post by lidex on 2011-05-24
> If you see an error message indicating something about '/run/udev/' not being writable and falling back to '/dev/.udev/', that's not an indication of a problem, it's just telling you what it found and what it's doing as a result of what it found.

Right. I get that consistently and just leaving it alone, boots into gdm in about 45 seconds.

---

