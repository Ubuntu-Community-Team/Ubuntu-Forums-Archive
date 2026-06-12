---
title: "Are There Any Differences Defraging in Windows To Defraging in Ubuntu?..."
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Foghornleghorn on 2008-06-12
I'm currently Dual Booting XP(not for long) and Ubuntu Hardy. My Defraging process in Windows are usually done using O&O degrag Software. Do i need something Similar for Ubuntu? 

Regards,
Foghornleghorn.

---

### Post by defrex on 2008-06-12
You don't need to defrag Ubuntu. :D Welcome to Linux.

---

### Post by decoherence on 2008-06-12
lifted from wikipedia...

> the Linux System Administrator Guide states, "Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system."

The wikipedia entry goes on to say that you should worry about it in certain use cases such as heavily used servers.

But in most cases the hard drive will probably die before you ever need to defrag it ;)

---

### Post by Foghornleghorn on 2008-06-12
Thanks Guys...This OS is such a Breath of Fresh Air.

---

### Post by Chr0mis on 2008-06-12
It depends on what you're using the computer for. If you plan to run a server of any kind, then you cannot anticipate read/write requests from users that are logged in, meaning that fragmentation is not a concern. If you are the only user on the machine, defragmenting a drive can help by reducing the number of jumps the drive read/write heads have to make to get all your data.

You can try the program defrag. [http://freshmeat.net/projects/defrag/?topic_id=136](http://freshmeat.net/projects/defrag/?topic_id=136)

You can also read this link about wyh you should not have to defrag your linux pc. [http://www.mail-archive.com/expert@linux-mandrake.com/msg17753.html](http://www.mail-archive.com/expert@linux-mandrake.com/msg17753.html)

Or you could use the command "fsck", just don't run it on a mounted partition. 

But long story short, you don't need to defrag, linux partitions dont fragment.

---

### Post by mick222 on 2008-06-12
its great no defraging ,bothering about viruses  having to clean out spyware or worrying that your computer may have been taken over by a trojan. Also doesn't slow to a stop when you install some apps.

---

### Post by mick222 on 2008-06-12
fsck runs roughly every 25th boot of the system effectively defraging your drive but only takes a couple of minutes.

---

### Post by TheWaylander on 2008-06-12
Thank frigging God, man I hate all the maintenance that you have to do with Windows

---

### Post by .Thomas on 2008-06-12
Good Info for new users!:)

---

### Post by aysiu on 2008-06-12
This is the best explanation I've seen:
[Why doesn't Linux need defragmenting?](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

