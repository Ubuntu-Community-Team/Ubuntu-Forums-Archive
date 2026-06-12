---
title: "Hard drives not spinning back up"
date: 2021-08-29
forum: New to Ubuntu
---

### Post by ustunt8008 on 2021-08-29
Hi,
I have installed current ubuntu and have setup a Plex server.
I also used hdparm to have my hard drive spin down after being idle for a few minutes.
hdparm -S 48 /dev/sdb

This works great. the drive spins down after the set time.

if i access the drive locally it spins back up and i can view my media.
I can also play media from other devices when the drive is spinning. 

Unfortunately if the drive spins down and i try to access media from another device, the drive doesn't spin back up !


Wake on Lan is set but im assuming thats for waking the OS (which isnt asleep anyway)


Any ideas

---

### Post by guiverc on 2021-08-29
It sounds like your system is setup as a desktop, and not server (*thus why it wakes on local use; ie. acting like a desktop, and not a server which remains awake always*).

However you've not provided any OS & release details.  A "*current Ubuntu*" doesn't really help.

Is this a Ubuntu Core product?  A Ubuntu Server? or Ubuntu Desktop? what release? and which kernel stack choice (LTS releases have two stack choices).  We have been given none of this detail.

Plex server implies to me it's a Ubuntu Server install; but your description sounds like it's not a server install, or you've added a desktop & turned your server into a desktop (*intended to be operated locally - after all it's a desktop*).

---

### Post by ustunt8008 on 2021-08-30
Apologies,
The OS is Kubuntu 21.04 Hirsute Hippo, and yeah its a desktop setup, with a Plex install on there.

Is there a way to get this operating how i need or do i need to install the server variant of ubuntu ?

regards

---

