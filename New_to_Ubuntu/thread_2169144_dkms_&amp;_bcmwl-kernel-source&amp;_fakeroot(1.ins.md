---
title: "dkms &amp; bcmwl-kernel-source&amp; fakeroot(1.installed itself on usb and I cant find it"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by mccannarchy on 2013-08-20
My friend was recently hacked by some kind of replicator that messed his system up. I let him use my ubunto usb live to check his files. when I get it back I load it onmachine to check and this is on it. Very windows literate but poor linux understand of commands and terminal. Dont know what to do. Please help.:(

---

### Post by VMC on 2013-08-20
Since you don't know what was done with your usb, anything could be written to it. I would suggest re-install ubuntu onto the usb device from your iso source.
That's the easiest and fastest solution, unless of course I'm missing your concerns.

---

### Post by mccannarchy on 2013-08-21
I have done that. I took my ssd out of my machine because of this. Its now in my ssd too, I did reload usb after I did a full format then a quick format. I loaded it from usb & I went to software center & looked at history & there it is again. I am very frustrated cuz I can't seem to even find it. Whatever it is its migrating across all our computers.

---

### Post by mccannarchy on 2013-08-22
Ok I have discovered that when I allow the modem to load the bcmwl-kernel-source thats when the fakeroot is also loaded. Is this a way to hack this system? How was that put in the programming for wireless? How do I remove it too? Is there a way to get to root@root to remove it? I have been trying to learn to use terminal too. I have just been using the live usb try ubuntu cuz I want to figure out how to get this off my ssd too. AGGRAVATING!!!!](*,)

---

### Post by ibjsb4 on 2013-08-22
The package "bcmwl-kernel-source" depends on "dkms" which recommends "fakeroot".  Its all good :)

[http://packages.ubuntu.com/precise/bcmwl-kernel-source](http://packages.ubuntu.com/precise/bcmwl-kernel-source)

---

