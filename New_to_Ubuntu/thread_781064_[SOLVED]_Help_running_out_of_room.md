---
title: "[SOLVED] Help running out of room?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Jimtuv on 2008-05-04
My /home/ says it has only 50mb left. How can I make this larger? I have 145 gigs left on the drive

Ubuntu 8.04 intel pentium 4 2.8 hypertheading. 2.5 gig mem c:=50gig 33 free D:=250 gig 145 free also running windows xp home edition sp2

Edit: I ended up making a dedicated partition. (I should have done this the first time) No longer a problem.

---

### Post by master5o1 on 2008-05-04
Care to explain how large the Ubuntu partition is (unless you used wubi - yuk yuk yuk). C: and D: aren't good measures if you made partitions.

---

### Post by Jimtuv on 2008-05-04
You gonna love this one. I have no clue how this was partitioned. Or if wubi was used. how can I find out?

---

### Post by SlappyPappy on 2008-05-04
Type: 

df

In a terminal.

---

### Post by Jimtuv on 2008-05-04
ok this is what I got:

Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      13563852  12330472    549788  96% /
varrun                 1297056       104   1296952   1% /var/run
varlock                1297056         0   1297056   0% /var/lock
udev                   1297056        64   1296992   1% /dev
devshm                 1297056        12   1297044   1% /dev/shm
lrm                    1297056     38176   1258880   3% /lib/modules/2.6.24-16-generic/volatile
df: `/home/james/.gvfs': Transport endpoint is not connected
/dev/scd0               358540    358540         0 100% /media/cdrom0
james@james-desktop:~$

---

### Post by Jimtuv on 2008-05-04
I went into windows xp and it shows up under add remove programs so I figure it is a wubi install of 15 gigs

---

### Post by Jimtuv on 2008-05-04
For right this moment I set up a folder called /host/shared and dumped most of my documents,video,music, etc.. there I figure if this is done as a wubi install that soon I will repartition and do a full install. By putting all my stuff in one folder it should make backup easy. I have been looking up wubi and found the following link. 

[LVPM: Upgrades Wubi 7.10 installs to real Ubuntu installs with dedicated partitions]("http://ubuntuforums.org/showthread.php?t=438591")

is this the right way to preceed? or should I try to add another virtual drive?


I ended up doing a dual boot.

---

