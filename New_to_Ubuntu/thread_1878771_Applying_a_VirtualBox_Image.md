---
title: "Applying a VirtualBox Image"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by dolphin194 on 2011-11-10
I have created an image of my server in VirtualBox on my desktop computer at home, and would like to apply the image to the hard drives in my server computer. The server computer is at a different house.

The image has Ubuntu 10.04 Server LTS running, and I want to turn my virtual machine into a physical machine.

What would be the easiest way of doing this?

---

### Post by CharlesA on 2011-11-10
Use something like clonezilla to clone the drive onto an image then image that to the physical drive.

You may have to edit the network rules in /etc/udev/rules.d/70-persistent-net.rules

So it knows the network card is eth0.

---

### Post by haqking on 2011-11-10
> **CharlesA said:**
> Use something like clonezilla to clone the drive onto an image then image that to the physical drive.

You may have to edit the network rules in /etc/udev/rules.d/70-persistent-net.rules

So it knows the network card is eth0.

+1

However bear in mind that your VM was running virtualised hardware.

When you put that onto real hardware there may be significant differences (graphics, RAID) etc.

Check for compatability first.

HD to VM works fine, VM to HD not always flawlessly.

Peace

---

### Post by dolphin194 on 2011-11-10
I'll give that a try. I might just install everything manually.

---

### Post by CharlesA on 2011-11-10
> **dolphin194 said:**
> I'll give that a try. I might just install everything manually.
I wrote up a script that does that for me.

But I am lazy..

;)

---

