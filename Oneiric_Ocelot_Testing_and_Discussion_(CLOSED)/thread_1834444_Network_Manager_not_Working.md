---
title: "Network Manager not Working"
date: 2011-08-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Mars11 on 2011-08-27
I just updated my Ubuntu 11.10 install and the Network Manager stopped working. When I open it up it says, "The system network services are not compatible with this version." This makes my computer practically useless. Is anyone else having the same issue?

---

### Post by coffeecat on 2011-08-27
Network manager upgraded to the new 0.9.0 version here a day or so ago and is working fine. There has been some discussion in another thread about some of the mirrors being out of date or possibly inconsistent. Perhaps your NM dependencies were not updated. Which repository mirror are you using?

Try changing the repository to the main server. Then, to get around NM not working, you could chroot in from a live CD and do a "sudo apt-get update" and "sudo apt-get dist-upgrade". Use dist-upgrade, not upgrade, to get intelligent dependency resolution. **EDIT**: um - will that latter work? Chroot-ing to get networking, that is. :? Anyone know?

---

### Post by Mars11 on 2011-08-27
I've never chrooted before. Could you please explain how to do so?

---

### Post by coffeecat on 2011-08-27
> **Mars11 said:**
> I've never chrooted before. Could you please explain how to do so?

No problem. However, as you can see from my edit I'm not sure whether networking will work inside the chroot environment in your situation.

Whatever, try this. Use Synaptic in your broken Oneiric (or however you want) to change your download server to the main server. Then reboot up with the live CD, open a terminal, and:

```
sudo mount /dev/sdaX /mnt
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /sys /mnt/sys
sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt /bin/bash
```

Substitute whichever is your Oneiric root partition for /dev/sdaX in the first command. After the chroot command you will be presented with a '#' root prompt. You are "in" your Oneiric system. Now:

```
apt-get update
apt-get dist-upgrade
```

No sudo - you are root.

**If** that works, reboot into Oneiric and let us know how things are.

---

### Post by Mars11 on 2011-08-27
Upgrading right now, I'll let you know if it works.

Edit: It does, THANK YOU! :D

---

