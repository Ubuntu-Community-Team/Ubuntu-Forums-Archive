---
title: "Hotplug USB under KDE How-To"
date: 2005-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by landotter on 2005-03-10
KDE users--we now get to use the spirit of Ubuntu, by having our friend, Gnome help us. :D

Run "gnome-volume-manager" under KDE and voila!  Run it from the alt+f2 dialog, then make sure to save your session as you exit.

Now USB devices will show up in Konqueror's sidebar.
 
You can have usb show up on the desktop by checking the "show hard drives" box in desktop configuration--pretty ugly with all the drives sitting there.  Or you can just right click and create a device that will be mounted automatically when you plug it in. Look in Konqui for the official location of the device. In my case, for my camera I tell it to create a new hard disk device located at /dev/sdb1. I rename the icon "Camera".
 
To keep the service from opening up a nautilus window when using it, run "gnome-control-center" and open up "removeable storage" to adjust to your heart's desire.

---

### Post by paul cooke on 2005-03-10
Yippee!!!!!

you can probably tell I'm very happy now... :)

---

### Post by landotter on 2005-03-10
[QUOTE=paul cooke]Yippee!!!!!

you can probably tell I'm very happy now... :)[/QUOTE]
 Cool! Did it work as advertised?

:)

I think it's rather funny how the KDE and Gnome folks rewrite code.

Why can't, for example, the excellent Kprinter printing framework be ported to or used with Gnome? That's the reason I booted into KDE in the first place and discovered this--I wanted to print some borderless prints. With Gwenview, no problem. Can't be done with any gnome program!!! I got annoyed that KDE wouldn't mount my camera, so I just ran the gnome-volume-manager on the off chance it wouldn't bork or hand KDE, and guess what? I worked just fine. I even have it running in the background with Blackbox and it works great there too.

I've seen these lengthy discussions about KDE patches and editing mtab/stab, etc...when the solution was right in front of people.

Not seeing the forest for the trees I guess. LOL

---

### Post by paul cooke on 2005-03-10
> "did it work as advertised?"

not quite, I see nothing in Konq's sidebar and when I click on the devices Icon, I get "Protocol not supported
devices"

---

### Post by landotter on 2005-03-10
[QUOTE=paul cooke]not quite, I see nothing in Konq's sidebar and when I click on the devices Icon, I get "Protocol not supported
devices"[/QUOTE]


Does it work under gnome? See if it works there first. ;) I'm no linux guru and gnome-volume-manager may be dependent on some gnome libs that you don't have installed if you're not a regular gnome user. :)

---

### Post by landotter on 2005-03-10
A better way to autostart gnome-volume-manager and gnome-settings-daemon in KDE is to symlink the executables from /usr/bin to ~.kde/Autostart.

Do this by dragging and dropping within Konqueror and choosing "link".

---

### Post by jdong on 2005-03-15
[QUOTE=landotter]Cool! Did it work as advertised?

:)

I think it's rather funny how the KDE and Gnome folks rewrite code.

Why can't, for example, the excellent Kprinter printing framework be ported to or used with Gnome? That's the reason I booted into KDE in the first place and discovered this--I wanted to print some borderless prints. With Gwenview, no problem. Can't be done with any gnome program!!! I got annoyed that KDE wouldn't mount my camera, so I just ran the gnome-volume-manager on the off chance it wouldn't bork or hand KDE, and guess what? I worked just fine. I even have it running in the background with Blackbox and it works great there too.

I've seen these lengthy discussions about KDE patches and editing mtab/stab, etc...when the solution was right in front of people.

Not seeing the forest for the trees I guess. LOL[/QUOTE]

Kprinter is written in qt/kde and relies heavily on the KDE framework, including the I/O slaves library. If it was *that* trivial to port it over to GNOME, it would've been done already...

As far as g-v-m running under KDE, g-v-m generates GNOME-specific events -- it's just lucky that KDE recognizes some of these. Don't always expect it to work flawlessly...

BTW, KDE 3.4 has built-in HAL support, so the media:/ URI is able to see removable drives! Yay!

---

### Post by cong06 on 2009-12-10
As far as I could tell the only dependance on gnome-volume-manager is "gdm" Uninstall it and it doesn't mount. Install it and everything's back together.

Does kde still use the gnome-volume-manager for hotpluging USB?

---

