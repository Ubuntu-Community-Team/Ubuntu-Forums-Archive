---
title: "[SOLVED] Problem syncing ipod with Amarok"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-11
I have a second gen 8 GB iPod Nano, Amarok 1.4.10, Kubuntu 8.04, KDE 4.1.1.  I'm trying to mount my iPod with PnP functionality.  How do I do this?  I haven't been able to sync my iPod since switching from Mandriva 2008.1 to Kubuntu two weeks ago.  I don't have any problem reformatting my iPod if I need to; all my music is backed up.  

I created a mount point at /media/ipod.

I have created a fstab entry like this (admittedly I don't entirely understand this entry, but it seems to be the one commonly used by people as I've been googling how to solve this problem): 
/dev/ipod /media/ipod vfat user,noauto 0 0 

I created a symlink at /etc/udev/rules.d/30-ipod.rules with this in the file:

BUS=="scsi", SYSFS{serial}=="000A2700196FBEE1", KERNEL=="sd?2", SYMLINK=="ipod" 

The symlink isn't detecting my ipod.  Plugging it in does not create the device "ipod" in /dev.

I can physically mount the ipod like this:

tarahmarie@tarahmarie-desktop:/dev$ sudo mount /dev/sdc2 /media/ipod/
tarahmarie@tarahmarie-desktop:/dev$ cd /media/ipod/
tarahmarie@tarahmarie-desktop:/media/ipod$ ls
Calendars  Contacts  iPod_Control  Notes

So it IS mounted.  When I try to connect to my ipod in Amarok, I get this error message:

Media Device: failed to create lockfile on iPod mounted at /media/ipod: Permission denied.  

How can I fix this?  First priority: get Amarok to sync with my iPod.  Second priority: enable some kind of PnP functionality like that in iTunes so I can plug the iPod in and have it mount and be recognized in Amarok, and use the disconnect command in Amarok to have it unmount.

Also, when I try to autodetect new devices in Amarok, I get this error message:
No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window.

---

### Post by DFlame on 2008-09-11
My understanding says you've had to use sudo to make the /media/ipod directory so it will be owned by the root user. Try a chown on that directory changing the permissions to you:

```
sudo chown -hR <yourusername> /media/ipod
```

That should allow Amarok access to the ipod, though I'm afraid I can't help with the PnP aspect of the problem.

DFlame

---

### Post by tarahmarie on 2008-09-11
[http://ubuntuforums.org/showthread.php?p=5768591#post5768591](http://ubuntuforums.org/showthread.php?p=5768591#post5768591)

This is the post that helped me; the long fix worked perfectly, and now my second generation ipod nano is mounted.  Now to figure out the PnP aspect!

---

### Post by tarahmarie on 2008-09-12
Does anyone know how to modify the ipod fstab entry to make it automount?

---

