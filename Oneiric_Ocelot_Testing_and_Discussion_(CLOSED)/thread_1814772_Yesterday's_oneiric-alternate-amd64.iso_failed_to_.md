---
title: "Yesterday's oneiric-alternate-amd64.iso failed to install"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by canga on 2011-07-30
I decided to try out oneiric using yesterday's daily iso for amd64 by downloading and transferring to a USB stick using UNetBootin.  However the debian-installer failed to complete the install of the base system.

Bug report at [https://bugs.launchpad.net/bugs/818388](https://bugs.launchpad.net/bugs/818388)

I hope this can be diagnosed and fixed before next week's alpha-3 release.

---

### Post by iClouseau88 on 2011-07-30
@canga,

I ran into the same problem not too long ago.  Some member of this forum suggested using the daily-live iso and it works.

---

### Post by drs305 on 2011-07-30
If you don't want to or can't burn a CD/DVD (I think the image is currently too large for a CD), you can install it from an ISO image on your hard drive.

Retrieve the daily build (64-bit in my case):
```
wget http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64.iso
```
I use a custom Grub 2 menuentry which boots the daily build:
> menuentry 'Oneiric Daily' {
isofile=oneiric-desktop-amd64.iso
loopback loop (hd1,6)/iso/$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/$isofile  noprompt noeject
initrd (loop)/casper/initrd.lz
}

The above file is located in sdb6 in the /iso folder.

Once you get it booted to the Desktop, you need to unmount /isodevice and then you can begin the installation to the partition you select.

```
sudo umount -lrf /isodevice
```

I've installed it about 15 times without any installation issues.

---

### Post by jfernyhough on 2011-07-31
You can also try the amd64+mac version which is pretty much the same thing (but with a few tweaks to work nicely on Macs).

For example, I downloaded the 27-Jul Kubuntu daily live and the amd64 version didn't want to boot whereas the amd64+mac booted fine.

In the end though, I had to use the natty release iso then upgrade to oneiric.

Useful tip:

$ sudo do-release-upgrade -d

works on any *buntu platform. It's designed for server upgrades (so is text-based) but it works very nicely on any version.

---

