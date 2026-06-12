---
title: "How to recover mistake in synaptic package manager?"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by zircon_34 on 2014-02-23
I find software center too limited so I started to use synaptic. However, since I am a bit unexperienced, lately I uninstalled the wrong package and my system got almost unusable and had to reinstall Ubuntu. I have Ubuntu/XUbuntu 13.10 installed.

Is there a way to save a recovery point in synaptic? for example in the case I uninstalled the wrong packages, is it possible to go back to a point I save beforehand, a point my system was stable?

---

### Post by r.stiltskin on 2014-02-23
Not really.  Uninstalled means uninstalled.   But can you be more specific?  What does "almost unusable" mean?  Usually a linux system can be repaired without reinstalling the whole thing, especially if all you did was uninstall a package.  As long as you haven't trashed the entire file system you should be able to boot from a recovery disk (or usb stick), chroot into the damaged system and reinstall whatever's missing.

---

### Post by zircon_34 on 2014-02-24
> [COLOR=#000000]But can you be more specific? What does "almost unusable" mean? [/COLOR]

I had Ubuntu 13.10 (Unity desktop) installed and wanted to try xfce desktop so installed that in synaptic. But then decided to deinstall xfce after a while and removed all xfce packages. when applying in synaptic and going back to desktop, I couldnt select any programs anymore (when clickicking on them the icons in the tab disappeared), the log off/restart buttons were gone, I just screwed up...

I installed now XUbuntu, which I prefer, but I just would like to avoid this in future, and thought maybe there is a way to save my current stable system setup, before installing new packages.

---

### Post by Bucky Ball on 2014-02-24
This old chestnut. ;)

If you wanted to try xfce4 that's all you need to install. Find xfce4 in Synaptics>Install>logout>choose 'xfce4 session' from the 'Sessions' menu>login.

Installing *buntu-desktop anything is usually not a great idea unless you are doing for a specific reason (like bloat, redundancy and duplication ... but seriously, unless you have good reason). From your post I'm gathering you installed xubuntu-desktop rather than xfce4. This is like having Xubuntu and all its default packages and apps installed with Ubuntu (and all its packages and apps). ;)

Just a tip for the future.

---

### Post by zircon_34 on 2014-02-24
ok thanks Bucky Ball :). 

Actually when that happened, I tried to only install xfce4 and xfc4-goodies (not the xubuntu-desktop), but this seems to install several packages and sometime it is difficult to grasp which package does what. Anyways, now I have installed Xubuntu after that mess, happy ending cause on this little MBA there is not much space and I prefer that distro!

I guess since it seems not possible to make a recovery point in synaptic, maybe there must be another app to this or I will try the undo button in synaptic in the future.

---

### Post by knpoe on 2014-02-24
i find  apt-get , apt-cache search, and ppa-purge to be most effective over aptitude and software-center.


usually a good recovery point is to simply try to reinstall the *'ubuntu-desktop gnome-shell gdm'* packages after removing the new breaking stuff.. at least then you can start back fresh

---

### Post by r.stiltskin on 2014-02-24
In the "good old days" it was OK to have multiple desktops installed and simply select which one to use when you login.  And it's true that the display managers (gdm, kdm) still allow you to choose your session preference when you login.  But it seems that in recent years the desktop managers fight with each other for control of the desktop and change various settings that can be hard to restore.  I guess the display managers haven't exactly kept up with the desktops in terms of being able to sort out all the settings affected by each desktop.

Long story short, it's not a great idea to install multiple desktops on a single system unless you're looking for a way to kill some time :)  The documentation is out there someplace, but it can take a while to find it.  If you want to try out a different environment it's safer to run it from a usb stick, or install another system on a separate disk partition.

But with most other packages -- i.e., programs that deal with "what you use your computer for" rather than "how your computer works" -- it's generally safe to try things out and then just uninstall them if you don't like them.

---

### Post by Impavidus on 2014-02-24
It seems that Unity and xfce are quite OK, they don't really bite each other. I have them both installed, although in practice I only use xfce. Other combinations may be less fortunate.

Something that could be used as a recovery point for installed packages is this:```
#To create the "recovery point":
dpkg --get-selections >your-recovery-point.asc
#to restore to a recovery point
sudo dpkg --clear-selections
sudo dpkg --set-selections <your-recovery-point.asc
sudo apt-get dselect-upgrade
```where your-recovery-point.asc will be a file in your home directory (or wherever you want to store it). You may want to encode the date in the file name. The only catch is that dependencies may have changed, which has to be handled correctly.

---

### Post by oldos2er on 2014-02-24
Synaptic has an "Undo" option under the Edit menu, although I've never had need to use it myself so I can't tell you how reliable it may be.

---

### Post by zircon_34 on 2014-02-24
Good comments:p,

to Impavidus: this is something I was looking for, I will have to read a little about that, do you generally use these commands before installing a set of new packages?

---

### Post by monkeybrain20122 on 2014-02-24
> **oldos2er said:**
> Synaptic has an "Undo" option under the Edit menu, although I've never had need to use it myself so I can't tell you how reliable it may be.

I think that is just for undoing the selection before clicking "Apply", it doesn't reverse actions that have already been carried out. What is done is done.

---

### Post by Frogs Hair on 2014-02-24
The man page is mainly for terminal use, but worth looking getting familiar with . ```
man dpkg
```

---

### Post by zircon_34 on 2014-02-24
There is a history menu of installed packages in synaptic, its handy, but lets say I choose to install 15 packages I would really enjoy having an option to click in the history and say "roll back" what I did that day.

I also found a command line tool called "Snapper" from LAS they point to it at min~52, see [http://www.jupiterbroadcasting.com/38086/the-arch-way-aas-s27e03/](http://www.jupiterbroadcasting.com/38086/the-arch-way-aas-s27e03/)
anyone tried that tool?

---

### Post by ian-weisser on 2014-02-24
Essentially, you are asking for tools to protect you from making mistakes. Such tools are always limited and fallible.

You may do better by learning the basic apt and dpkg toolset
I find managing packages to be very easy using those tools.

Know how to backup and restore your package settings using dpkg.
Know how to backup and restore your data.
Then almost any damage you do will be trivial to fix.

---

### Post by monkeybrain20122 on 2014-02-24
> **zircon_34 said:**
> 

I also found a command line tool called "Snapper" from LAS they point to it at min~52, see [http://www.jupiterbroadcasting.com/38086/the-arch-way-aas-s27e03/](http://www.jupiterbroadcasting.com/38086/the-arch-way-aas-s27e03/)
anyone tried that tool?

Never heard of it before, it sounds interesting. But I think it is primarily designed and tested for SUSE. Support for ext4 is only 'experimental' and requires special kernel and something called e2fsprogs (no idea what it is), so it sounds too much trouble to be worthwhile. It would be interesting to play with it on a test installation(I have one :)) but I wouldn't count on it.
[http://snapper.io/faq.html](http://snapper.io/faq.html)

---

### Post by Buntu Bunny on 2014-02-25
> **r.stiltskin said:**
> But it seems that in recent years the desktop managers fight with each other for control of the desktop and change various settings that can be hard to restore. 

> **Impavidus said:**
> It seems that Unity and xfce are quite OK, they don't really bite each other. I have them both installed, although in practice I only use xfce. Other combinations may be less fortunate.

Just a cautionary tale - I have Ubuntu and Xfce both installed but had Nautilus and Thunar battling it out awhile back. Nautilus was winning until I got some help from the community.

---

### Post by Impavidus on 2014-02-25
> **zircon_34 said:**
> Good comments:p,

to Impavidus: this is something I was looking for, I will have to read a little about that, do you generally use these commands before installing a set of new packages?

No.

---

### Post by 23dornot23d on 2014-02-27
Something that I have found recently is Timeshift - it backs up only the system files though 

[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)

( keep data / docs / photos on a separate partition and this could be a very useful tool to have on any Linux system )

[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)

I have tried it out - and this is the thing with most backups - you only try them when things go wrong - well this worked
for me and I was happy it was there.

But it has some limitations and some small flaws - these I will explain.

The amount of room for a backup - is often estimated short by around 3 gig ...... ( so on a system that is say 20 gig in size )
You would need a backup area of 23 gig plus leaving space to work in - at least another 10 gig.

Total would be in the region of ( 20 gig + 23 gig + 10 gig ) just as a rough finger in the air for normal use with data files
and documents being in a separate safe partition.

It will overwrite all of the partition you restore it to ...... which should usually only be the one you have backed up.

( but if you have a clean partition with room to spare - you can keep a duplicate system running by doing the backup to it
you need to know what you are doing when using this - it needs to be on something like a external hard drive )

But it is maybe worth having a look at - and while people are learning and only have small OS's its a good thing to have
as a restore tool ....... just thought I would mention it - as I have found its quite a nice thing to have on my own system.

---

