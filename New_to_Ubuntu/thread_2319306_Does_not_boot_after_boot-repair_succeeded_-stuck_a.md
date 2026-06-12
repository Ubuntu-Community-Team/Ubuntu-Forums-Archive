---
title: "Does not boot after boot-repair succeeded -stuck at initramfs"
date: 2016-04-02
forum: New to Ubuntu
---

### Post by tejal2 on 2016-04-02
Hello all,

Totally new to Ubuntu/Linux and this is my first post. Installed and running Ubuntu 15.10 on a desktop for a few weeks.  Today, I suddenly lost connection to my wireless *Logitech* keyboard and decided to reboot. Got stuck at initramfs. Tried boot-repair via Live USB-boot, and it said boot-repair was succesful. Upon reboot, I am  still stuck on initramfs and it wont go any further.

Launched Gparted and Flags on /dev/sda1 are boot,esp.  No flags on /dev/sda2 and /dev/sda3.


Installed Citrix receiver a couple of days back, and it seems to be fine. Don't know if it has anything to do with it.


Tried previous posts on similar topic but saw none on 15.10 

From boot-repair>  [http://paste.ubuntu.com/15594023](http://paste.ubuntu.com/15594023)

Any help would be appreciated.
   
Tejal

---

### Post by oldfred on 2016-04-03
You have UEFI boot with full drive LVM & encryption.
I do not know either LVM nor encryption.

But LVM requires regular maintenance on housecleaning kernels.
And full drive encryption requires you to have really good backups as any drive corruption may make any drive repairs difficult or impossible.

For Boot-Repair to work you have to mount the encrypted partition. It should be asking for passphase to mount it. Then Boot-Repair cna fully run.

Your sdb2 partition also shows as full or 97%. Anything over about 80% is starting to get full and you need more space or major housecleaning.

---

