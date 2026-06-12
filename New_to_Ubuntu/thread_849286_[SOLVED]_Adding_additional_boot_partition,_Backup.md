---
title: "[SOLVED] Adding additional boot partition, Backup"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by Dr_Bop on 2008-07-04
I have searched but can't find an exact answer to my question so, sorry if I missed something...

What I have:
Good sized drive, partitioned with 1 boot partition with Ubuntu 8.04.  Works great.  Don't want to break it.

What I want:
I would like to install Ubuntu server in a second partition on the same drive so I can dual boot.  There is plenty of space.  Can I just do an install and will the server install leave my workstation as a good boot too?

What I did:
I hear about Mandriva so I installed it as a dual boot (as above).  It took over the boot screen but I was still able to boot either.  I then loaded Fedora and it messed up the boot and I could not boot anything other than Fedora.  No problem as I was playing.  So I went back to "What I want" and it is just fine.  I would like to get to "What I want:

Second question:
Is there a physical disk backup?  I have a Ubuntu backup running every day and it works fine.  If I lost the disk (it is new, so not likely yet), I would be fried.  Any thoughts?

Sorry for the long post, but details help derive answers.  Thanks so all..

scott

---

### Post by milosz.galazka on 2008-07-04
1. Yes, but I am not sure about grub. It will be probably reinstalled with only choice of new system. 

The easiest way to do this will be to use *kvm* to install it on second drive. It will need some tweaking...

2. Yes, there are many tools... You could start [here]("http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html")

---

### Post by ZabiGG on 2008-07-04
Hi there ;)

To learn all about partitioning, so you can use different parts of your disk without affecting others, read this great Psychocats guide:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

To learn all about the MBR and Grub boot loader, go here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Scroll down a bit, and you'll find sections on MBR, Grub and uninstalling (where you'll find tips on reorganizing your OSes in the Grub launcher).

Hope this helps,

Z.

---

