---
title: "Why Mount Extended..?"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by frncheez on 2012-01-02
Trying to find out why my root part was full I started playing with a few things checking/learning about df -h,sudo blkid and UUID's I found out in fstab that the system is mounting the extended, [COLOR="Red"]not External as written before[/COLOR] partition where I installed Ubuntu (10gig root,50gig /home and 3gig Swap) then it mounts /Home and Swap. it is a DualBoot with WinXP and Ubuntu11.10

I don't understand that mounting process at all so if anyone wishes to explain it...

As far as why my / was full or said it was full I should say I have no clue. GParted was telling me one thing then Disk Usage was telling me another. I did get some room back (10%) running "apt-get clean" mind you so...

---

### Post by idoitprone on 2012-01-02
```
du -h /boot/
```

```
du -h /var/log/
```

it might be a good idea and go to the synaptic to delete unused linux kernels

var log might be an offender and i am not sure how safe it is to delete its contents

---

### Post by frncheez on 2012-01-02
I had to get rid of synaptic a while back. It would start then quit on me. I am using Aptitude...
What about the bootup issue (if it is)...is that normal..?

---

### Post by MartijnNL on 2012-01-03
Just to be clear: when you talk about /root do you mean:

/      -> the root of the filesytem   or
/root  -> the home directory of the root user.

The latter normally shouldn't be on a separate partition. If you mean / please write it like that, in order to prevent misunderstandings.

10 GB should normally be enough for a root partition, unless you have a LOT of software installed. You also could have a lot of files in /var (for example the log files idoitprone mentions).

You might want to try installing 'baobab'. This is a graphical disk usage analyser from Gnome. It can show you which directories take a lot of space. Of course the command 'du' works as well like for example:
```
du -xh -max-depth=2 /
```
You can play with the max-depth option to get more or less detail.

---

### Post by frncheez on 2012-01-03
I meant root partition...me and thinking that I'm clear and concise still need improvement ;)
Here is what I did once I found the command(s). I did Linux many years ago but forgot most of it so I am back to basic...

me@Ltop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.2G  5.3G  3.5G  61% /
udev                  984M  4.0K  984M   1% /dev
tmpfs                 397M  1.1M  396M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  991M  512K  991M   1% /run/shm
/dev/sda5              44G  4.9G   37G  12% /home
me@Ltop:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
me@Ltop:~$ sudo apt-get clean
[sudo] password for me: 
me@Ltop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.2G  4.8G  4.0G  55% /
udev                  984M  4.0K  984M   1% /dev
tmpfs                 397M  1.1M  396M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  991M  512K  991M   1% /run/shm
/dev/sda5              44G  4.9G   37G  12% /home

Thanks for taking the time to help me. Like I said in the original post I may be somewhere I have no need to be but to me that booting thing doesn't seem right and I love tinkering...

---

### Post by MartijnNL on 2012-01-04
Why doesn't it seem right? Every partition containing a filesystem can be mounted. And of course partitions which contain relevant data for the OS need to be mounted otherwise the data can't be accessed. So first the root filesystem (/) is mounted. Then the other filesystems (like /home) are mounted on their designated mount points. So the partition containing the data in /home is mounted in de directory /home. (if you would look at the data in that partition on it's own, there would be no /home directory, you would only find the directories inside /home, like the one for your user.

So naturally the root partition needs to be mounted as well, otherwise the kernel couldn't access any configuration files, programs, devices and so on. The type of partition doesn't really matter. But from your df output I would say that the root partition (/dev/sda2) is a primary one, not an extended one. /dev/sda5 is a logical partition inside an extended one.

The command:
```
sudo fdisk -l
```
might show you this. Probably /dev/sda3 is your extended partition, which contains /dev/sda5.

You can read some more on mounting [here]("https://help.ubuntu.com/community/Mount").

---

### Post by idoitprone on 2012-01-04
I think its better if we look at op fstab

```
cat /etc/fstab
```
[IMG]chrome://dictionarytip/skin/dtipIconHover.png[/IMG]

---

