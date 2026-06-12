---
title: "Partition table"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by narendra4 on 2013-10-05
Hello friends,
      I want to install Ubuntu 13.04. I have dell Inspiron 1545 320Gb HDD. I want perfect Partition table that will help to efficient performance.
how should i allocate 320 gb 
boot swap home root and remaining for own use

---

### Post by ian-weisser on 2013-10-05
"Efficient performance" depends upon how you intend to use it.

Some people swear that a separate /home is great.
Some people swear that a separate /boot is great.

Personally, I do neither.
I have used the installer's default for years, and it's been great.

---

### Post by oldfred on 2013-10-05
> "Efficient performance" depends upon how you intend to use it.
+1

But each of us have different ways we use computer. 

I like to experiment with different installs so I have many 25G partitions for extra installs. And because of that I have data in a separate partition so I can mount it into every install. I also prefer smaller / (root) partitions and most desktops do not need a separate /boot. Servers or desktops with server type configurations (RAID or LVM) may need a separate /boot.
Also with the new multi-TB hard drives smaller / and some separation of system and data makes more sense. When I first started with Ubuntu I only had / & swap  but that was only a 160GB drive.

And even my own optimum partitioning is usually obsolete a couple of years later as what I am doing it then different. If just starting out, simple is probably better and then down the road you can see what works best.

---

### Post by heir4c on 2013-10-05
When you don't have a dual boot with Windows but you use the whole disk for Ubuntu and you use for the first time Ubuntu, than let the installer use the whole disk. Than you get this:

sda1   /       (all the space minus the swap)
sda2  swap   (1 to 3 GB)

If you want a separated partition for Data than you must make the partitions manual. (Select the option: "Something else" (I don't now what it is in English, I use the Dutch Language for install).
Than you have this:

sda1  /           (20 to 25 GB)
sda2  /DATA    (rest minus / and swap)
sda3  swap

When you want more distro's on it, than you need a Extended partitions for the different installs but only 1 swap and 1 /DATA partition (so you can use it for al the distro's) Than you have this:

sda1 /DATA                      (rest minus sda5 to sdax and swap)
sda2 Extended partition
----sda5  /                       (first distro) (20 to 25GB)
----sda6  /                       (second distro)
----sda7  /                       (third distro)
--etc--
sda3  swap


Dualboot with Windows:

sda1 Windows
sda2 Windows
sda3 /
sda4 swap

If windows had already 4 partitions than you need to empty the DATA partition of Windows (don't forget to Backup the data) and make that a Extended partition. And than make in that partition Logic Partitions for / and a swap: (Don't let Windows make the partitions but use gParted (PartitionManager) to create the Extended and Logic Partitions because that is different. Windows used Dynamic Drives or something, One link with problem with the Dynamic Drive method: [http://ubuntuforums.org/showthread.php?t=2178216](http://ubuntuforums.org/showthread.php?t=2178216))

sda1 Windows
sda2 Windows
sda3 Extended
----sda5 /
----sda6 swap
sda4 Windows

Or with /DATA partition:

sda1 Windows
sda2 Windows
sda3 Extended
----sda5 /
----sda6 /DATA
----sda7 swap
sda4 Windows


(Or for the /DATA use a second or external Hard Drive).

---

### Post by heir4c on 2013-10-05
Double post (problem whit internet connection, slow upload to the forum)

---

