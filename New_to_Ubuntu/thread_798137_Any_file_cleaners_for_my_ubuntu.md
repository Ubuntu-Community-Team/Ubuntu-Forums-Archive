---
title: "Any file cleaners for my ubuntu?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-17
I want a cleaner like Ccleaner for windows..and i want it to be free..btw why is it when i put something in my trash it still looks empty??

---

### Post by UnWarierMage224 on 2008-05-17
I've looked... there really aren't many things like CCleaner out there for Ubuntu, mostly because Ubuntu doesn't need it. 

Check out this guide for more tips on keeping ubuntu all pretty and shiny :)
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

As for the trash problem... happens sometimes. I think if you open up the trash the deleted file will be there and be removable. 

-'Mage

---

### Post by nowshining on 2008-05-18
u can try kleansweep - but be VERY VERY careful with it as it can do some major damage, I only do ".tmp, .bak and ~" files. :) yes it's in the repos. U can go to my gutsygibbon site for a pre-compiled deb of a cleaner for the gnome config files.

---

### Post by nicedude on 2008-05-18
Heed nowshinings advice as Kleensweep will find a ton of stuff that you don't want to delete.

You chould also research the apt-get manpage and look at what varations there are for keeping your cached programs clean and keeping everythings dependencies fixed.

If you are using high speed internet all the time and or you don't install and uninstall allot of things then the commands below will clean your package cache ( Cached copies of software installs that is stored locally ) and can remove dependencies that are no longer needed as well as check for missing dependencies

Here are the relevant apt-get command variables examples below this list

check
check is a diagnostic tool; it updates the package cache and checks
for broken dependencies.

clean
clean clears out the local repository of retrieved package files.
It removes everything but the lock file from
/var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
APT is used as a dselect(8) method, clean is run automatically.
Those who do not use dselect will likely want to run apt-get clean
from time to time to free up disk space.

autoclean
Like clean, autoclean clears out the local repository of retrieved
package files. The difference is that it only removes package files
that can no longer be downloaded, and are largely useless. This
allows a cache to be maintained over a long period without it
growing out of control. The configuration option
APT::Clean-Installed will prevent installed packages from being
erased if it is set to off.

autoremove
autoremove is used to remove packages that were automatically
installed to satisfy dependencies for some package and that are no
more needed.

To use these switches you add them to the end of an apt-get command like so 

sudo apt-get check

This will check for missing things

or my favorite

sudo apt-get autoremove

which will look for things installed that are not needed by anything and remove them

Any of the commands in the discriptions above will work when added to the sudo apt-get command so hope this helps you out some.

And everything you ever need is free in linux :-)

---

### Post by hyper_ch on 2008-05-18
what does ccleaner do?

---

### Post by Xiong Chiamiov on 2008-05-18
CCleaner empties out various temporary files in different programs and Windows itself, with options for what you want and what you don't.  For me, it was always most useful in that it emptied my trash.  Just the other day I emptied it on Kubuntu and freed up ~20 gigs...

@nicedude: You can do all of those commands much simpler with aptitude instead of apt-get, eg. sudo aptitude autoclean.  I read [this]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/") recently and have been trying to break myself of the apt-get habit.

---

### Post by Helios38 on 2008-05-18
> **hyper_ch said:**
> what does ccleaner do?

as we all know, windows is horribly inefficent at keeping itself neat, its a slob.


Ccleaner cleans out temp files, cache files, old prefetch files that windows leaves in its wake.


i like ccleaner, and would suggest it to anybody else who has klunky XP running alongside their shiny neat ubuntu :D

---

### Post by hyper_ch on 2008-05-18
there's no real need then for ccleaner on linux ;)

---

### Post by Raineer on 2008-05-18
Thirded for CCleaner, it is a wonderful application which does a wonderful job in Windows and it is constantly updated.

For Ubuntu, utilizing 'make clean' if you install software you have to compile yourself or using apt-get's features for Debian packages usually should get you by just fine.

---

