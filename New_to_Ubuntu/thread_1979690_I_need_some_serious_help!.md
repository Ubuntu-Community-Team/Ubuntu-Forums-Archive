---
title: "I need some serious help!"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by missrachel on 2012-05-13
Okay.. I am having some issues with my desktop I think.  My windows started flickering, and were becoming invisible until selected or text was highlighted etc. The tool bar is see-through most of the time and everything.  When I reboot, its FINE until the launch bar loads which is what I think is causing the problem.  so I tried "$ sudo apt-get install ubuntu-desktop", but I ran out of space so it wouldn't continue and my problem still persists. 

So... I tried to delete things I don't need, such as games etc, but I got the error saying something about needing special permission or something like that. So I typed: "sudo dpkg --configure -a" as I always had before,

: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
So I did this: "sudo dpkg --configure -a" and this is where I am stuck so far:

Setting up libsgutils1 (1.24-1) ...

Setting up gnome-cards-data (1:2.22.3-0ubuntu2netbook5) ...
Setting up ttf-kochi-mincho (1.0.20030809-4ubuntu2) ...
/usr/bin/defoma-font -vt reregister-all /etc/defoma/hints/ttf-kochi-mincho.hints
Registering /usr/share/fonts/truetype/kochi/kochi-mincho-subst.ttf..
Registering -kochi-mincho-medium-r-normal--0-0-0-0-c-0-iso10646-1..
Registering -kochi-mincho-medium-r-normal--0-0-0-0-c-0-jisx0212.1990-0..
Registering -kochi-mincho-medium-r-normal--0-0-0-0-c-0-jisx0201.1976-0..
Registering -kochi-mincho-medium-r-normal--0-0-0-0-c-0-jisx0208.1983-0..
Registering -kochi-mincho-medium-r-normal--0-0-0-0-c-0-iso8859-1..
Updating fontconfig cache for /usr/share/fonts/truetype/kochi
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.

Setting up language-selector (0.3.4netbook1) ...

Setting up libexchange-storage1.2-3 (2.22.3-0ubuntu3netbook1) ...

Setting up libmtp7 (0.2.6.1-2ubuntu1) ...

Setting up python-brlapi (3.9-6ubuntu1) ...

Setting up libtotem-plparser10 (2.22.3-0ubuntu2) ...

Setting up libelfg0 (0.8.6-4) ...

Setting up libkpathsea4 (2007.dfsg.1-2ubuntu0.1) ...

Setting up libotr2 (3.1.0-2) ...

Setting up gimp-data (2.4.6-1ubuntu1~hardy1netbook1) ...
gtk-update-icon-cache: Failed to write hash table
WARNING: icon cache generation failed for /usr/share/icons/hicolor

Setting up ttf-kochi-gothic (1.0.20030809-4ubuntu2) ...
/usr/bin/defoma-font -vt reregister-all /etc/defoma/hints/ttf-kochi-gothic.hints
Registering /usr/share/fonts/truetype/kochi/kochi-gothic-subst.ttf..
Registering -kochi-gothic-medium-r-normal--0-0-0-0-c-0-iso10646-1..
Registering -kochi-gothic-medium-r-normal--0-0-0-0-c-0-jisx0212.1990-0..
Registering -kochi-gothic-medium-r-normal--0-0-0-0-c-0-jisx0201.1976-0..
Registering -kochi-gothic-medium-r-normal--0-0-0-0-c-0-jisx0208.1983-0..
Registering -kochi-gothic-medium-r-normal--0-0-0-0-c-0-iso8859-1..
Updating fontconfig cache for /usr/share/fonts/truetype/kochi
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.

Setting up bluez-audio (3.36-1ubuntu2netbook1+really3.26-0ubuntu6netbook2) ...
Setting up python-gnome2-desktop (2.22.0-0ubuntu1) ...

Setting up alacarte (0.11.5-0ubuntu1.1) ...
gtk-update-icon-cache: **
** Gtk:ERROR:(/build/buildd/gtk+2.0-2.12.9/gtk/updateiconcache.c:1100):write_bucket: assertion failed: (*offset == ftell (cache))
Aborted
WARNING: icon cache generation failed for /usr/share/icons/hicolor

Setting up gnome-media (2.22.0-0ubuntu3) ...

Setting up gcalctool (5.22.3-0ubuntu0.1netbook1) ...

(gconftool-2:9073): GConf-WARNING **: Failed to write "/var/lib/gconf/defaults/%gconf-tree.xml": Error writing file "/var/lib/gconf/defaults/%gconf-tree.xml.new": No space left on device

Error syncing configuration data: Failed to write some configuration data to disk
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 1
Setting up bug-buddy (2.22.0+dfsg-2) ...
dpkg: error processing bug-buddy (--configure):
 unable to fill /var/lib/dpkg/updates/tmp.i with padding: No space left on device
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted

Please please help me.  I am so frustrated.

---

### Post by bodhi.zazen on 2012-05-14
> 
(gconftool-2:9073): GConf-WARNING **: Failed to write "/var/lib/gconf/defaults/%gconf-tree.xml": Error writing file "/var/lib/gconf/defaults/%gconf-tree.xml.new": [size=2]**[color=darkred]No space left on device**[/size][/color]

Your hard drive is full. Free up some space.

---

### Post by missrachel on 2012-05-14
Okay, how can I delete programs, games, etc manually?  Synaptic wants me to run dpkg before I use it, and I already showed you what happened when I ran it.. I don.t have much on my harddrive other than what ubuntu installs there.  I think its because someone else owned this computer before me, and even though I deleted their account, its taking up space.

So deleting all those games and things I don't use would really help!

---

### Post by coffeecat on 2012-05-14
As a start, you could try emptying the package cache - all the downloaded deb files which are sitting there taking up space and only needed for re-installing things.

```
sudo apt-get clean
```

The system might just refuse to co-operate with that seeing as your partition is so full, in which case I can give you a rm command that does the same job. See if that works first.

**EDIT**: By the way, don't try to delete applications manually. You need to use the package manager. Hopefully, freeing a bit of space will allow that.

---

### Post by rai4shu2 on 2012-05-14
You might try a:

```
sudo apt-get clean
```

and see if that helps.

EDIT: Ninja'd. :D

---

### Post by forrestcupp on 2012-05-14
For one thing, it looks like you're using Ubuntu 8.04 (Hardy Heron), which hasn't been supported for a long time.

---

### Post by matt_symes on 2012-05-14
Hi

Also


```
sudo apt-get autoremove
```


to remove libraries that are no longer dependencies.


Also remove old kernels you don't need


```
dpkg -l | grep linux-image-[0-9]
```


You can uninstall any old ones you don't need. That will free up move space.


Clean out the trash folder.


After that, look for large files in your home directory.


After that uninstall, any applications you don't use.


Kind regards

---

### Post by missrachel on 2012-05-15
Thanks! I did everything but deleting the kernals because I don't know what those are, so I have no idea if I need them or not.  I was able to free up 628 MBs and complete 'dpkg --configure -a'.. however, my original flickering problem still persists.

---

### Post by matt_symes on 2012-05-15
Hi

I had something that sounds like your problem after an update in Precise development version. Resetting Unity fixed it for me.

```
unity --reset
```

I cannot guarantee this will work for you though.

Kind regards

---

### Post by Derek Karpinski on 2012-05-15
It's probably time to start fresh, and install 12.04.

---

### Post by missrachel on 2012-05-17
> **matt_symes said:**
> Hi

I had something that sounds like your problem after an update in Precise development version. Resetting Unity fixed it for me.

```
unity --reset
```I cannot guarantee this will work for you though.

Kind regards

I tried, it only said command not found!  But thank you!

Is there any way to disable the desktop launcher?

---

### Post by matt_symes on 2012-05-17
Hi


> **missrachel said:**
> I tried, it only said command not found!  But thank you!

Is there any way to disable the desktop launcher?

What *buntu are you using ?


Kind regards.

---

### Post by missrachel on 2012-05-17
It says I am using Hardy Heron.

---

### Post by matt_symes on 2012-05-17
Hi


> **missrachel said:**
> It says I am using Hardy Heron.

That's ancient (I assume it's Ubuntu ?). No wonder unity --reset did not work :D.


Have you considered backing up and upgrading ?


Kind regards

---

