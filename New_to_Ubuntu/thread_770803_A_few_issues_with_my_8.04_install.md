---
title: "A few issues with my 8.04 install"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by jimjesus on 2008-04-27
I just installed 8.04 last night from a fresh 6.10 install(I was having problems installing 8.04 directly and had posted about it on here last night) and I'm having a few problems. The first is mounting all my ntfs partitions. They all mount correctly when I select them in the file browser but everytime I reboot I have to mount them again. It's not that difficult but it means I have to reimport all my music to rhythmbox everytime. How would I get them to automatically mount everytime?

My other issue is getting rhythmbox to actually play. When I first tried to import all my songs, it said I needed the codecs and it automatically brought up a synaptic for me to get them. I downloaded them and all my songs imported, but when I tried to play them, I can't hear anything. How should I go about fixing this?

EDIT: My music plays, but only through my integrated motherboard sound card. How do I set it to play through my soundcard?

---

### Post by typal on 2010-07-27
Not sure about the sound-card-bit, but there are a couple options for auto-mounting your ntfs partition. First, use an external program to set it up (simple, but not educational.) Something like [ntfs-config]("http://flomertens.free.fr/ntfs-config/index.html") would do the trick. 
Second, manually edit your /etc/fstab file. For the second option, it's again fairly simple. Follow a guide like the one [here]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29"), and you should be good to go.

Good Luck,
T

---

