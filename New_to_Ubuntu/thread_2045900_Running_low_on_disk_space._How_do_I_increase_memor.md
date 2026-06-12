---
title: "Running low on disk space. How do I increase memory?"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by mrtn474 on 2012-08-22
Until recently, I did not realize that that root and home folders were located in different partitions. When I installed Ubuntu, it asked me to resize the partition it was creating. So me, thinking I wanted the most space for my storage, slid the divider to give the partition that was shown on the right, only 6gb. Turns out that that is probably the home folder. Now I'm getting notifications that say I'm running low on space.

How can I fix this? Will I have to reinstall my OS or just resize it? When I tried booting from a live USB, my computer wouldn't boot from it. it only showed the copyright information for grub. and nothing more. I tried the live usb on another pc and it worked perfectly. 

I attached a picture of what the Disk Utility program in ubuntu showed me.

---

### Post by c2tarun on 2012-08-22
> **mrtn474 said:**
> Until recently, I did not realize that that root and home folders were located in different partitions. When I installed Ubuntu, it asked me to resize the partition it was creating. So me, thinking I wanted the most space for my storage, slid the divider to give the partition that was shown on the right, only 6gb. Turns out that that is probably the home folder. Now I'm getting notifications that say I'm running low on space.
 
How can I fix this? Will I have to reinstall my OS or just resize it? When I tried booting from a live USB, my computer wouldn't boot from it. it only showed the copyright information for grub. and nothing more. I tried the live usb on another pc and it worked perfectly. 
 
I attached a picture of what the Disk Utility program in ubuntu showed me.
 
 
copy /home/user folder to some other partition. Then you can easily mount the partition on /home by editing /etc/fstab(if I remeber correctly) file. [Here ]("http://www.tuxfiles.org/linuxhelp/fstab.html")is a quick tutorial to edit fstab file.

---

### Post by spjackson on 2012-08-22
That screenshot shows that the 5.4GB partition is mounted as /. We cannot tell whether the 25GB partition is mounted at all. In a terminal, type
```

df -h

```and post the output.

I cannot yet say whether you need to resize the 5.4GB partition. However, as far as I know, you cannot resize the / partition in Ubuntu without using a live CD (or USB).

---

### Post by Sidewinder1 on 2012-08-22
Totally as a side note. If you decide to shrink your 112 GB NTFS, to make some more space for the other partitions, boot to Windows and defragment your C:\ drive, at least twice. It's also strongly recommended that you back up any irreplaceable data on all partitions prior to any partition modifications. Better to be safe..

HTH,
Side

---

### Post by oldos2er on 2012-08-22
Just FYI, hard disk space and memory are two different things:

[http://en.wikipedia.org/wiki/Random-access_memory](http://en.wikipedia.org/wiki/Random-access_memory)

[http://en.wikipedia.org/wiki/Hard_disk_drive](http://en.wikipedia.org/wiki/Hard_disk_drive)

---

### Post by Wim Sturkenboom on 2012-08-22
A trick to regain some space is to clear the cache used by the package manager.
```

sudo apt-get clean

```
And next maintain that after updates. It will help as long as you don't install additional SW.

> **spjackson said:**
> That screenshot shows that the 5.4GB partition is mounted as /. We cannot tell whether the 25GB partition is mounted at all.
Also noticed that.

---

### Post by mrtn474 on 2012-08-23
> **spjackson said:**
> That screenshot shows that the 5.4GB partition is mounted as /. We cannot tell whether the 25GB partition is mounted at all. In a terminal, type
```

df -h

```and post the output.

I cannot yet say whether you need to resize the 5.4GB partition. However, as far as I know, you cannot resize the / partition in Ubuntu without using a live CD (or USB).
Hi! Sorry for the late reply, this is the best time when I can log on.

Here's what I got when I used the df program.

> mrtn@mrtn-HP-Mini-110-3000:~$ df -h
Filesystem       Size  Used Avail Use% Mounted on
/dev/sda6        5.1G  4.4G  388M  93% /
udev             488M  4.0K  488M   1% /dev
tmpfs            198M  852K  198M   1% /run
none             5.0M     0  5.0M   0% /run/lock
none             495M  536K  495M   1% /run/shm


Now, I think I'm getting that the home folder is partition that is mounted on "/" and the 25bg partition is some other thing. Right?

---

### Post by spjackson on 2012-08-23
> **mrtn474 said:**
> Now, I think I'm getting that the home folder is partition that is mounted on "/" and the 25bg partition is some other thing. Right?
Yes, your /home folders are on the 5.4Gb / partition, along with everything else.

I'm not aware of a gui function that will take the contents of /home, put it on a new partition then mount that partition as /home. One option is to scrap your installation and reinstall, selecting /dev/sda5 for the /home mount point.

Also, if you fiddle about with /home when you are logged in to a gui desktop, you can get into difficulties because the desktop has files open in /home. **Make sure you have a good backup of home before doing anything else.**

However, if the terminal is not too scary for you, then the steps are fairly straight forward, and will save quite a bit of time. However, if you mess up, you might have difficulty logging in to your system, so it is a good idea to have a live CD or usb available in case of need.

I realise that this is the Absolute Beginner Talk forum, so you might find this daunting, in which case I suggest the reinstall option.

These instructions are correct if you don't have an encrypted home. If you do have an encrypted home, then I don't know what impact this has.

# This is a temporary place to mount the new partition, so we can check that it is empty and copy the current /home to it.
```

sudo mkdir /media/newhome

```# edit /etc/fstab and add a line to mount the new partition
# we will change this line later.
```

/dev/sda5  /media/newhome ext4    defaults   0   2

``````

sudo mount /media/newhome

```# Can we see the new 25GB partition mounted as /media/newhome  and virtually empty?
```

df -h
ls -l /media/newhome

```# If all looks good, then logout of GUI, and use Ctrl+Alt+F1 to get a terminal session.
# Login to the terminal.

# We take this approach to copy and rename so that it is easier to recover if things go wrong.
# Take extra care from here because getting it wrong will mean you can't login or maybe boot.
# Note that if you forget to rename /home and recreate it, then the rest will work, but you won't be able to reclaim the space used by your old home.
```
 
sudo cp -rp /home/* /media/newhome
cd /
sudo mv home oldhome
sudo mkdir home

```# edit /etc/fstab and change the line we last added to:
```

/dev/sda5  /home ext4    defaults   0   2

```# reboot with
```

sudo shutdown -r now

```# If it reboots OK and all looks good, then tidy up
```

sudo rmdir /media/newhome
sudo rm -rf /oldhome
# See what the disk space situation is now
df -h

```

---

### Post by jemofthewest on 2012-08-23
Perhaps I'm missing something by skimming, but I don't see why all the talk about remounting your home folder somewhere else.  I'd use gparted to find more details on what inside that 25gb partition and resize your current partition, perhaps taking part of the 25gb part.

---

### Post by spjackson on 2012-08-23
> **jemofthewest said:**
> Perhaps I'm missing something by skimming, but I don't see why all the talk about remounting your home folder somewhere else.  I'd use gparted to find more details on what inside that 25gb partition and resize your current partition, perhaps taking part of the 25gb part.
I took the original post to mean that the OP had created 2 partitions, intending them to be / and /home but somehow it just ended up using the small / partition. I could be wrong about that intent, but I don't think it's an unreasonable interpretation.

Your suggestion is fine, if that's what the OP wants. However, you need to boot from removable media to resize / with gparted in Ubuntu don't you? It won't resize a mounted partition, AFAIU. And the OP said
> 
When I tried booting from a live USB, my computer wouldn't boot from it.


---

### Post by mrtn474 on 2012-08-27
I'm not uncomfortable with using the command line. I don't know much, but I've been reading LINUX: Rute User's Tutorial and Exposition (it's free and on that website, for anyone that's interested). Now I know some basic commands such as those used to manipulate files and directories. 

Anyway, problem fixed. I took the easy way out and simply reinstalled the OS. For some strange reason, the live USB worked (even stranger, is that this keeps happening with Ubuntu and me, i.e., problems getting fixed on their own). While installing, I remembered what I did wrong.

The first time I installed it, when I came to the step that dealt with partitions, I chose the "something else" option. That is where I sized the logical partitions in a pretty inconvenient way. So this time, I simply chose the option that let me install Ubuntu next to Windows. This was also my easiest choice (though I don't know if it was the fastest) since I had just installed Ubuntu the previous week, hence, I had no important files (except for some important forms that I later realized I had in that partition :mad: ).

Thank you all for the responses; I really appreciate it :)

---

