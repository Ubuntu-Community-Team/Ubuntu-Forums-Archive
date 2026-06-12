---
title: "Desktop icons for mounts"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Kissell on 2008-04-22
Can someone please explain whats going on in the mounting and the icons?

I have a few issues related to that.

1) i have manually mounted a raid-6 volume under /mnt/san0 but it doesn't get an icon.  :(

2) I have an icon popping up for a data partition of my hard disk, and it's auto-labelling it by the size of the partition...  i'd like to be able to change the label of that icon.

There are more, but I think if I understood how to deal with these two things then I could figure the others out.

---

### Post by mikeyphi on 2008-04-22
Have a look at this guide - and ask again if necessary!
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by billgoldberg on 2008-04-22
I find it easier to don't let any icons appear on the desktop and open the drives/partition using the file manager.

You'll need to go to the gconf menu( in a terminal type "gksudo gconf-editor" and then go to "apps -> nautilus -> desktop".

There might be a way to change the label somewhere in there to.

---

### Post by Kissell on 2008-04-23
> Have a look at this guide - and ask again if necessary!
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I know how to do the stuff in that guide, I can mount things...  my question is more of how do I get those mounts to show up under the PLACES menu?  and where do the automatically mounted things under the places menu get their names from?

---

### Post by Paqman on 2008-04-23
> **Kissell said:**
> 
1) i have manually mounted a raid-6 volume under /mnt/san0 but it doesn't get an icon.  :(


If you mount it to /media/san0 instead, you'll get an icon for it on the desktop.

---

### Post by Kissell on 2008-04-23
oh, okay...  

so the things in /media auto-iconify?  

I had considered that, and i thought I tried that, but it didn't work...  but I didn't reboot or restart any service either, i simply manually mapped it from the command line and checked immediately...  I'll try it when I get back there and see if it works after a reboot.

at what point does it auto-iconify?  or how long does it take to do it "live", or how can i force it to check the /media folder for things it should make links to?

---

### Post by Paqman on 2008-04-23
Do you really need to mount it from the command line anyway? If you add an entry for it to /etc/fstab it'll mount automatically during boot.

---

### Post by Kissell on 2008-04-23
Yeah, now that it's in fstab it mounts on it's own at boot...  i just did it manually for the first time and while i've been messing with it trying to make an icon automatically show up like it does when I insert a usb drive.

---

