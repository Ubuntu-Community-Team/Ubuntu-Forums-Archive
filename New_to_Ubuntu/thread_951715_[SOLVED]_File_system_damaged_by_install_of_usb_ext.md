---
title: "[SOLVED] File system damaged? by install of usb ext. drive"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-18
On installation and first run of an external usb 2.0 hard drive (80 gig hdd - used, probably had XP or NTFS on it), no icon was put on the screen. On looking in /media I found the device. It was named: usb

It could not be mounted. I downloaded GParted, ran it on the 80 gig, did not set the "disklabel" at first. I formatted it to Primary and ext3. Came back to /media checked to see if the drive would "mount / unmount". That seemed good.

I then tried to copy my /home to it. The file operation icon appeared in the panel. I was told one file with a . (hidden) would not copy and said "skip". Half an hour later, the copy was complete.

When I tried to use GFM (Gnome File Manager) to see the contents of the disk, it would not open, giving an "unmounted" error. I tried mounting, to no avail. So I rebooted. That brought up the .dmrc incorrect permissions problem. Which I'll deal with in another post. Yet, now, all three of the usb devices, two memory sticks and the 80 gig have no file permissions. 

WTF? How do I fix this and should there be a primer or how-to on installing microsoft hardware that is known to harm computers?

---

### Post by Pro-reason on 2008-10-19
Why would a permissions error come up?  Surely at that point your old home directory was still mounted at /home/.  Did you edit /etc/fstab before even making sure the drive could mount?

---

### Post by Mark_in_Hollywood on 2008-10-19
> **Pro-reason said:**
> Why would a permissions error come up? 

[COLOR="Red"]I have no idea.[/COLOR]

 Surely at that point your old home directory was still mounted at /home/.  

[COLOR="Red"]Correct[/COLOR]

Did you edit /etc/fstab before even making sure the drive could mount?
[COLOR="Red"]
I did nothing except plug in an external usb disk. As I said, it had probably been used in a 'puter with XP on it.[/COLOR]

---

### Post by Pro-reason on 2008-10-19
> **Mark_in_Hollywood said:**
> [COLOR="Red"]
I did nothing except plug in an external usb disk. As I said, it had probably been used in a 'puter with XP on it.[/COLOR]

Are you saying that it is still messed up when you unplug the external drive?

---

### Post by JeeZiTsDave on 2008-10-19
This is actually pretty weird.  I have never even heard of an external USB data hard drive cause a file system to go awry.

However, I don't think that the USB hard drive was the problem because there is a permissions error.  There could be a problem with fstab so I would check that out.

---

### Post by Mark_in_Hollywood on 2008-10-21
I'm not someone who knows computers. I can cut & paste at the terminal within reason. I tried to describe the problem to the best of my understanding of computer terms, such as: fstab, file system, usb, etc.

I didn't convey the problem and I offer an apology to the responders to my post. I didn't mean to confuse. I don't know how to describe some problems.

---

