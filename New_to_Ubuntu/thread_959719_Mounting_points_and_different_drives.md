---
title: "Mounting points and different drives"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by technosinner on 2008-10-26
This might be a strange question but I didn't find an answer yet, and I can't get my head around it.

Like most Windows users I have a hard time getting used to the tree-style Unix file system compared to the drives and letters.  I got it down enought to get around, except one thing:

Let's say I have two seperate HDD with one partition each (sda1 & sdb1).  If I have sda1 mounted as /MyFirstMount, is it possible to mount sdb2 as /MyFirstMount/Subdir?  I'm worried it might screw up because the parent directory of one drive would be on another one...?

Does this make sense at all?
Thanks
ts

---

### Post by redseventyseven on 2008-10-26
Theoretically, yes it is. In fact that's (sort of) how it's done by default. Just not (usually) with those particular folder names.

One of your hard drives will be mounted as "/" (i.e. the root directory) and the other will be mounted as "/media/sdb1", which is essentially a sub-folder of the first drive.

This is what happens with all partitioning systems. For example, my partitioning system has one partition which is mounted as "/", and all the others "hang" off of that one. In this case, my partitions are set up to mount to specific points related to the system, each with a particular function, rather than as generic storage. Here are details of that mounting system that I use: [http://www.linuxmint.com/wiki/index.php/How_to_partition#An_elaborate_scheme](http://www.linuxmint.com/wiki/index.php/How_to_partition#An_elaborate_scheme)

Does this help to visualise what's going on? It's a more flexible system than the Windows/DOS way of using drive letters, though admittedly this flexibility can seem a little daunting.

---

### Post by technosinner on 2008-10-26
Makes complete sense!  

That's what I had figured out, but I really wasn't sure if I was right or just confused ;)

Now this does bring another question: is there still a purpose in having partitions in Linux?

Thanks!

---

### Post by JohnFH on 2008-10-26
> **technosinner said:**
> Makes complete sense!  

That's what I had figured out, but I really wasn't sure if I was right or just confused ;)

Now this does bring another question: is there still a purpose in having partitions in Linux?

Thanks!

I thought about this as well and decided not to have too many partitions.  I have one for root, one for swap and one BIG one for home.  Usually a lot of the reasons for using partitions is ease of use, eg. makes it easier to upgrade, offers better protection against accidents ('rm -rf /' will not affect data on an unmounted partition), but there is little NEED for partitions.  However one need comes to mind - to hibernate your PC, the swap area needs to be on its own partition, but if you never hibernate, you don't even need a swap partition at all, just use a swap file instead.

---

### Post by technosinner on 2008-10-26
> but if you never hibernate, you don't even need a swap partition at all, just use a swap file instead.

I didn't know that...  I thought the swap partition was a necessity in Linux..!

I finally split up my partitions/mounts in a way that makes sense, but like JohnFH mentioned, I really didn't see too much of a point for partitions like I did in Windows.

Man I like this linux thigamagig :P

---

### Post by Xiong Chiamiov on 2008-10-26
You don't need partitions simply for organization.  I have many, many partitions on my hard drive atm, because I have different linux distros installed on each one.  I keep my /home on a seperate partition so that I can share it between them all easily.

---

### Post by redseventyseven on 2008-10-27
> **Xiong Chiamiov said:**
> You don't need partitions simply for organization.  I have many, many partitions on my hard drive atm, because I have different linux distros installed on each one.  I keep my /home on a seperate partition so that I can share it between them all easily.

I agree with this, and I think it highlights the difference between Windows and Linux in terms of the philosophy behind partitioning and filesystem-mounting. In Windows, the system is geared up as an organisational system. Everything is set up to appear as separate drives with distinct drive letters. In Linux, it's more functional than organisational. Different partitions (or disks) can be assigned different jobs depending on where on the file system it's mounted. Thus all the individual disks become integrated into the file system as a whole.

I wouldn't necessarily advocate a partitioning system as complex as the one I use (see earlier post). I use it because I like the idea of different disk partitions having different jobs. But one aspect I would definitely recommend: giving "/home" a separate partition. This means you can easily try new distributions out (a process which usually wipes out the partition that your system files are on) without taking all your documents and personal content with it.

---

### Post by JohnFH on 2008-10-27
I have no partitions set aside for testing other distros.  I use VirtualBox for that - a lot more flexible and a lot more convenient.  I'm one who believes your main PC should be kept free of testing - either use another machine(s) or use virtual machines.  I hate repartitioning - time consuming and risky (consequence of a slight user error here can be disastrous).

---

### Post by technosinner on 2008-10-27
I'm getting to really like this file system... once you get over the initial daunting appearence it's actually much more logical!

---

### Post by redseventyseven on 2008-10-30
> **technosinner said:**
> I'm getting to really like this file system... once you get over the initial daunting appearence it's actually much more logical!

I agree with that.

---

### Post by hyper_ch on 2008-10-30
if you have a drive full with yuor music you could for example mount it as "Music" folder on your desktop...

Instead of mounting you could also just make symlinks that go the mounted drive :)

You have many, many possibilities. Instead of mounting a whole partition, you could also just mount a subfolder somewhere else on your system :)

---

