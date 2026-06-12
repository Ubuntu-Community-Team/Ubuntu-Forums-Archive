---
title: "NTFS network share"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by il pepe on 2012-05-07
Hi,

I can't get the following thing working.

I have a dualboot desktop (win7 and Ubuntu 12.04). Both OS have their own partitions, but share a common NTFS partition (called X)

I would like to share this common partition X over the network when using Ubuntu. I have several other ubuntu computers in the network, and when the desktop is booted (in ubuntu) i would like to able to acces this common partition from every other laptop.

The desktop has already a fixed IP. SSH is an option but i would rather like to use Samba as i sometimes also would like to use a windows laptop to acces this partition.

The partition is loaded in boot because of an entry in fstab and is mounted in /windows/sto.
I got the map somehow shared under sudo, but i can't acces it from my laptop...

How do i solve this?

---

### Post by drdos2006 on 2012-05-07
Using Ubuntu, navigate to the folder you want to share.
Right mouse-click, dropdown to "Sharing Options".

Tick "Share this folder", enter a share name.
Tick "Allow others..." and/or "Guest access.."
and save.

Right mouse-click, go to "Properties", "Permissions" add Group account if necessary and Folder access.

regards

---

### Post by il pepe on 2012-05-08
So once i got a group ready with all the users on the different computer it should work?
Then i have only 1 question?
How do i add users from a different computer?

Add user -> username?
But i guess you somewhere have to link it to the other computer?

Kind regards,
Pieter

---

