---
title: "How to remove unused dependencies ?"
date: 2005-03-14
forum: Repositories &amp; Backports
---

### Post by Roman2K on 2005-03-14
Hi,

When I install a program, for example tuxracer, I do "apt-get install tuxracer", it searches for its depencies that are not installed on my computer, then it downloads them and tuxracer works :).

The problem is when I want to remove tuxracer : I do "apt-get remove tuxracer" and then "dpkg --purge tuxracer" but it doesn't remove the dependencies it had installed during the "apt-get install tuxracer" !

So for example, the package "tuxracer-data" is still installed, and I know it has installed other stuff but I don't remember their name so I can't remove them, and it uselessly uses diskspace !

It really annoyes me and I think other people, but maybe I don't do how I would must do.

Can you help me to not have a garbaged disk please ?

Thank you,
Best regards and congratulations for this wonderful Ubuntu Hoary,
Roman,

---

### Post by Roman2K on 2005-03-14
I just found deborphan, what a good software !
aptitude purge `deborphan --guess-all`
dpkg --purge `deborphan --guess-all`
I love it.

---

### Post by A-star on 2005-03-15
But is it safe to use?

---

### Post by mirtux on 2005-03-15
Good question, since i'm also interested in that package but not sure about the results since i can't have my machine blocked...

MC

---

### Post by Roman2K on 2005-03-16
I think it's safe, seeing how it determines if a package is good to remove or not.
Anyway, I removed (and purged) all the stuff it gave me with a "deborphan --guess-all" and I don't see any problem for now, and I rebooted the PC without any problem too.

---

### Post by bernardfrancois on 2006-10-09
I saved 104MB of disk space this way. It doesn't seem much, but it was on an older laptop with only 6GB disk space, so it made a difference.

Rather than directly removing everything, I removed everything manually in synaptic to make sure no other packages were removed. I used the following command to obtain a handy list of the packages: [i]deborphan --guess-all | sort | less
[/i]

A feature should be added to synaptic to show a list with orphaned packages. There is a list with local or obsolete packages, but it doesn't show a lot (only programs I installed manually).

---

### Post by thegsusfreek on 2006-11-18
I've been wanting a tool like this ever since I started using linux. If you keep installing a bunch of junk and its dependencies and then uninstall that same junk, over time you will end up with a pretty bloated HDD.

I really think that package managers should, when you uninstall a package, check all of the dependencies that that particular package has to see if they are required by any other packages. If there are packages that were depended on that are no longer depended on, ask the user if they want to uninstall those packages while leaving the rest alone... sort of like a "Reference Counting" garbage collection algorithm.

I think that is what Windows XP does. I'm pretty sure I've had times where I was uninstalling a package and was asked if I wanted to delete a dll that no longer appeared to be required.

---

### Post by ryu kun on 2006-11-19
Aptitude can remove unused dependencies if depending software installed by  it. So, it's best to use aptitude instead of apt-get or synaptic.

> I think that is what Windows XP does. I'm pretty sure I've had times where I was uninstalling a package and was asked if I wanted to delete a dll that no longer appeared to be required.

When Windows asks you about the dll file, it also warns you that "it may be needed by some other program.", And you can never know which program may need it. So you keep everything or will face unexpected errors when running another program.

---

### Post by savohead on 2006-11-20
windows leaves a lot of rubbish on your hdd but it doesn't tell you where, so you find yourself with a lot of "${34k5jhk3j}" directories and you don't know which one you could delete without screwing the whole thing up.
Anyway, what's the differences between the cleaning process of aptitude and deborphan?! I mean, which one's the safer, the quicker?! Should someone ask for this feature for synaptic in the future Ubuntu release (i'd vote for it!!)?!
thanks

---

### Post by AlanRogers on 2006-11-20
Having read various fora on this subject, but being no expert, I use *aptitude* instead of *apt-get* for any software that I'm just trialing and am likely to want to remove later. I only use *apt-get* or *Synaptic* for packages that I **know** are going to stick around.

---

### Post by thegsusfreek on 2006-11-21
Thanks for the tip. I've been playing around with aptitude and I think that you can still install with Synaptic and just uninstall with aptitude and aptitude will still remove the orphans. That's perfect! :D

---

### Post by RAOF on 2006-11-23
Also, new versions of apt-get also have this capability.  I think Edgy's apt got it.  You can now use **sudo apt-get autoremove** to remove no longer needed dependencies.

---

### Post by savohead on 2006-11-23
> **RAOF said:**
> Also, new versions of apt-get also have this capability.  I think Edgy's apt got it.  You can now use **sudo apt-get autoremove** to remove no longer needed dependencies.

perfect!! thank you!

---

### Post by aysiu on 2006-11-23
> **thegsusfreek said:**
> Thanks for the tip. I've been playing around with aptitude and I think that you can still install with Synaptic and just uninstall with aptitude and aptitude will still remove the orphans. That's perfect! :D
I haven't found this to be the case, actually. 

I just installed *kword* through Synaptic, and when I tried to remove it with *aptitude*, all it removed was *kword* (not *kspread* and all the other dependencies: ```
sudo aptitude remove kword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  kword 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 7066kB will be freed.
Writing extended state information... Done
(Reading database ... 114275 files and directories currently installed.)
Removing kword ...
```

If you want dependencies removed when you remove an application, your best bet is to always install with *aptitude* and always remove with *aptitude*.

---

### Post by aysiu on 2006-11-23
> **RAOF said:**
> Also, new versions of apt-get also have this capability.  I think Edgy's apt got it.  You can now use **sudo apt-get autoremove** to remove no longer needed dependencies.
I never knew that. Is that new as of Edgy? Or was that in Dapper, too?

```
 sudo apt-get autoremove kword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kword-data koffice-data kword kspread libruby1.8 koffice-libs libwv2-1c2
The following packages will be REMOVED:
  koffice-data koffice-libs kspread kword kword-data libruby1.8 libwv2-1c2
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 34.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 114275 files and directories currently installed.)
Removing kword ...
Removing kspread ...
Removing koffice-libs ...
Removing koffice-data ...
Removing kword-data ...
Removing libruby1.8 ...
Removing libwv2-1c2 ...
```

---

### Post by cantormath on 2006-11-23
> **Roman2K said:**
> Hi,

When I install a program, for example tuxracer, I do "apt-get install tuxracer", it searches for its depencies that are not installed on my computer, then it downloads them and tuxracer works :).

The problem is when I want to remove tuxracer : I do "apt-get remove tuxracer" and then "dpkg --purge tuxracer" but it doesn't remove the dependencies it had installed during the "apt-get install tuxracer" !

So for example, the package "tuxracer-data" is still installed, and I know it has installed other stuff but I don't remember their name so I can't remove them, and it uselessly uses diskspace !

It really annoyes me and I think other people, but maybe I don't do how I would must do.

Can you help me to not have a garbaged disk please ?

Thank you,
Best regards and congratulations for this wonderful Ubuntu Hoary,
Roman,

Are they dependencies if they are unused?

---

### Post by RAOF on 2006-11-23
> **aysiu said:**
> I never knew that. Is that new as of Edgy? Or was that in Dapper, too?
...

New as of Edgy.  Oh, and the latest apt upload to Feisty added documentation for it :)

---

### Post by aysiu on 2006-11-24
> **RAOF said:**
> New as of Edgy.  Oh, and the latest apt upload to Feisty added documentation for it :)
Thanks for the information.

---

### Post by Neophile on 2006-11-25
How about "apt-get --purge autoremove thepackage". I've been using this way to uninstall packages. Is there some negative point with this way what I don't know about?

---

### Post by aysiu on 2006-11-25
> **Neophile said:**
> How about "apt-get --purge autoremove thepackage". I've been using this way to uninstall packages. Is there some negative point with this way what I don't know about?
It's available only in Edgy, apparently.

---

### Post by Popoi on 2006-12-15
> **RAOF said:**
> Also, new versions of apt-get also have this capability.  I think Edgy's apt got it.  You can now use **sudo apt-get autoremove** to remove no longer needed dependencies.

YEAH MAN!! THAT'S TOO SEXY!!

---

### Post by jis on 2006-12-15
> **RAOF said:**
> Also, new versions of apt-get also have this capability.  I think Edgy's apt got it.  You can now use **sudo apt-get autoremove** to remove no longer needed dependencies.

Does the autoremove option uninstall the no longer needed dependencies that have been installed by aptitude or Synaptic, as well?

---

### Post by DarkN00b on 2006-12-15
I used ```
aptitude purge `deborphan --guess-all`
dpkg --purge `deborphan --guess-all`
``` and it removed a bunch of old gstreamer libs which were no longer needed as I got rid of gstreamer as soon as I could. It also removed some other libs and configuration files with no effect on my system except more free space.

I then ran **sudo apt-get autoremove** and that removed an additional 20 megabytes that deborphan missed. I'll probably try it the other way around in the future to see what happens, but it looks like **sudo apt-get autoremove** does a better job.

Deborphan should work well for pre-Edgy users though.

---

### Post by AncientPC on 2008-03-18
Sorry for reviving a dead thread, but I ran into this problem again.
sudo aptitude install kword -y:
> Aptitude 0.4.6.1: log report
Tue, Mar 18 2008 00:45:18 -0500

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

**Will install 14 packages**, and remove 0 packages.
50.3MB of disk space will be used
===============================================================================
[INSTALL, DEPENDENCIES] kexi
**[INSTALL, DEPENDENCIES] kghostview**
[INSTALL, DEPENDENCIES] koffice-data
[INSTALL, DEPENDENCIES] koffice-libs
[INSTALL, DEPENDENCIES] kspread
[INSTALL, DEPENDENCIES] kword-data
[INSTALL, DEPENDENCIES] latex-xft-fonts
[INSTALL, DEPENDENCIES] libkscan1
[INSTALL, DEPENDENCIES] libpqxx-2.6.9
[INSTALL, DEPENDENCIES] libruby1.8
[INSTALL, DEPENDENCIES] libwv2-1c2
[INSTALL, DEPENDENCIES] ruby
[INSTALL, DEPENDENCIES] ruby1.8
[INSTALL] kword
===============================================================================

Log complete.

sudo aptitude remove kword -y:
> Aptitude 0.4.6.1: log report
Tue, Mar 18 2008 00:48:30 -0500

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and **remove 13 packages.**
49.5MB of disk space will be freed
===============================================================================
[REMOVE, NOT USED] kexi
[REMOVE, NOT USED] koffice-data
[REMOVE, NOT USED] koffice-libs
[REMOVE, NOT USED] kspread
[REMOVE, NOT USED] kword-data
[REMOVE, NOT USED] latex-xft-fonts
[REMOVE, NOT USED] libkscan1
[REMOVE, NOT USED] libpqxx-2.6.9
[REMOVE, NOT USED] libruby1.8
[REMOVE, NOT USED] libwv2-1c2
[REMOVE, NOT USED] ruby
[REMOVE, NOT USED] ruby1.8
[REMOVE] kword
===============================================================================

Log complete.


sudo apt-get autoremove kword -y:
> Aptitude 0.4.6.1: log report
Tue, Mar 18 2008 00:55:20 -0500

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and **remove 13 packages.**
49.5MB of disk space will be freed
===============================================================================
[REMOVE, NOT USED] kexi
[REMOVE, NOT USED] koffice-data
[REMOVE, NOT USED] koffice-libs
[REMOVE, NOT USED] kspread
[REMOVE, NOT USED] kword-data
[REMOVE, NOT USED] latex-xft-fonts
[REMOVE, NOT USED] libkscan1
[REMOVE, NOT USED] libpqxx-2.6.9
[REMOVE, NOT USED] libruby1.8
[REMOVE, NOT USED] libwv2-1c2
[REMOVE, NOT USED] ruby
[REMOVE, NOT USED] ruby1.8
[REMOVE] kword
===============================================================================

Log complete.

In both cases they missed removing kghostview.

deborphan --guess-all also returned nothing.

deborphan -a --guess-all returned a lot of optional/extra packages that I had installed, but still missed a few.  Off the top of my head, I know it missed kghostview and the Latex packages.  The irony is that it kghostview is listed as an optional package and is not depended upon others (as checked via /var/lib/dpkg/status).

---

