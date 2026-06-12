---
title: "Installing new fonts in 11.10"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by clivejo on 2011-10-10
In previous versions of Ubuntu installing fonts was as easy as opening the file and clicking install.  What is the procedure in 11.10?  As opening the file doesn't seem to do anything.

---

### Post by Kobalt on 2011-10-10
You can create a .font directory in your Home folder and place your new font files here. 
Update your cache to make them available to your apps, and here you go. 

```
sudo fc-update -fv
```

---

### Post by clivejo on 2011-10-10
I know I can do it manually.  Isnt the point of Ubuntu to make Linux easier?

What happened to the installer program that does it automatically?

---

### Post by Kobalt on 2011-10-10
I think what happened is Gnome 3

---

### Post by castrojo on 2011-10-10
On my machine opening a font opens a window that shows the font and then there's an install button on the bottom right corner.

---

### Post by Mr. Picklesworth on 2011-10-10
Yep, shouldn't be any different than it was last release. ubuntu-desktop has a hard dependency on gnome-font-viewer, so unless you've removed that yourself (or lost it in an update mixup), it's there.

If you right click the font file, there should be an option for Gnome Font Viewer. It's usually the default one. When you open a font file with it, you'll get a dialog like this:
[ATTACH]203954[/ATTACH]

---

### Post by coffeecat on 2011-10-10
@clivejo, do you have gnome-font-viewer installed? It was missing in earlier builds and I don't know whether it would have come in automatically with updates.

Earlier thread:

[http://ubuntuforums.org/showthread.php?t=1839927&highlight=fonts](http://ubuntuforums.org/showthread.php?t=1839927&highlight=fonts)

Bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/839407](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/839407)

---

### Post by clivejo on 2011-10-11
It wasn't installed properly, so reinstalled, seems to be working again. That's better! (big thanks to coffeecat)

Its been missing since I started testing 11.10, I thought its should have been re-installed later on as part of the upgrade process.  

Maybe its worth a full, clean re-install.  Might be best considering I'm seriously not liking Unity, time to bail out me thinks!

---

### Post by coffeecat on 2011-10-11
As Mr. Picklesworth says, gnome-font-viewer is a dependency of ubuntu-desktop and there was an update to ubuntu-desktop around 6th October, so it's curious that gnome-font-viewer wasn't pulled in for you then.

Sorry to hear you're not liking Unity.

---

### Post by clivejo on 2011-10-11
I guess I'm too old school, I like my desktop to bend to my will, not the other way around.

I also like certain information (temperatures, CPU load, other statistics) displayed permanently and dont mind giving up a small bit of viewable real-estate for that.  I also find window management to be a nightmare in 11.10, whereas before the desktop cube would make a bystander dizzy, as I multi-tasked in previous versions.  

I admit its probably brilliant for touch screens and the likes, but for regular mouse and keyboard I just find it "goes against the grain"

---

### Post by grahammechanical on 2011-10-11
I am not complaining as I am testing Oneiric but from alpha 2 down until now when I right click the one true type font that I would like installed I get the message No Applications Available to Open xxxxx.TTF.

I have been able to install the font using the method suggested here. I do not see this as a big problem as I am converting the fonts in my documents to unicode fonts so I will not need this font in future and it is installed in my working Ubuntu (11.04).

Regards.

---

