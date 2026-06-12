---
title: "[SOLVED] Installation query"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by spocksbeard on 2008-10-18
Hey, I'm currently part way through the installation of Hardy alongside XP, I've resized my XP (ntfs) partition and created 3 more, one 20gb for Ubuntu to live in (ext3, mount point / ),one just over 2gb swap and another which I want to share with Windows (currently ext3 mount point /home ). 

I would ideally like the shared parition to be ntfs as I know XP will definitely work properly and be able to read and write  to it, but the option to create it is not there. If I go ahead and create it as ext3 will I be able to use another partition manager to change it to ntfs after installation?

Also, do I need to set a mount point for the windows partition? I have the options /windows and /DOS.

Help greatly appreciated as I would love to be able to get this done before i fall asleep (I will never start messing around with OSes at 11.30 PM ever again)

---

### Post by beno1990 on 2008-10-18
> **spocksbeard said:**
> Hey, I'm currently part way through the installation of Hardy alongside XP, I've resized my XP (ntfs) partition and created 3 more, one 20gb for Ubuntu to live in (ext3, mount point / ),one just over 2gb swap and another which I want to share with Windows (currently ext3 mount point /home ). 

I would ideally like the shared parition to be ntfs as I know XP will definitely work properly and be able to read and write  to it, but the option to create it is not there. If I go ahead and create it as ext3 will I be able to use another partition manager to change it to ntfs after installation?


Install this after Ubuntu is set up:

```

sudo apt-get install gparted

```

It can format to NTFS

> 
Also, do I need to set a mount point for the windows partition? I have the options /windows and /DOS.

Help greatly appreciated as I would love to be able to get this done before i fall asleep (I will never start messing around with OSes at 11.30 PM ever again)

I don't think NTFS partitions can be given a Unix mount point. If you don't specify a mount point, it should normally be mounted under /media/.

---

### Post by spocksbeard on 2008-10-18
> **beno1990 said:**
> Install this after Ubuntu is set up:

```

sudo apt-get install gparted

```

It can format to NTFS



Ok thanks, I shall do this

> **beno1990 said:**
> 
I don't think NTFS partitions can be given a Unix mount point. If you don't specify a mount point, it should normally be mounted under /media/.

Will I still have the option to boot XP if I don't choose a mount point? It gives me the options to mount it to /windows or /DOS in the drop down menu.

Sorry if this is a stupid question but i'm new to this and tired as hell :(

---

### Post by WelshChris on 2008-10-18
Linux compatability with ntfs has progressed leaps and bounds in recent years - previously I had to create a dos partition to share if I was dual booting.

I've had no problems with dual booting Ubuntu and Vista, and reading/writing to my Windows ntfs partition under Ubuntu.

The ntfs partition is mounted automatically, and an icon placed on the desktop.  No futzing around with /etc/fstab these days.  The only time I haven't been able to access it is when I've closed down Vista via hibernate which saves the box's state to disk.  Makes sense..

(Disclaimer!  I said 'no problems' there - remember, ymmv, and I'm not sure, but they may still be describing ntfs compatability as 'beta'.)

---

### Post by Sef on 2008-10-18
> Hey, I'm currently part way through the installation of Hardy alongside XP, I've resized my XP (ntfs) partition and created 3 more, one 20gb for Ubuntu to live in (ext3, mount point / ),one just over 2gb swap and another which I want to share with Windows (currently ext3 mount point /home ).1) Make Ubuntu 8 - 10 GB.

2) 1 GB swap should be fine.   How much ram do you have?  

3) There is a program that can get Windows to read ext3.  However, most people just make a NTFS partition and use NTFS-3g, so GNU/Linux can read it.

>  Also, do I need to set a mount point for the windows partition? I have the options /windows and /DOS.4) Make sure that Windows is on the first primary partition.

> Help greatly appreciated as I would love to be able to get this done before i fall asleep (I will never start messing around with OSes at 11.30 PM ever again)5) Sometimes best to leave it until morning when you are awake and less likely to make mistakes.

>  Sorry if this is a stupid question but i'm new to this and tired as hell :sad:     6) Asking proves intelligence.  Not asking for help when needed is not smart.

7) Read #5 in this post.

---

### Post by spocksbeard on 2008-10-18
Woo! Install is finished, XP booted fine on 2nd attempt (1st try brought a BSOD telling me to restart, which I did. Checkdisk did its thing and now it works :D) Ubuntu booted first and second time without any problems, other than the wireless card not working.

A strange thing is that I can't seem to find my shared partition on either OS, yet Ubuntu can access my XP system, although XP can't see Ubuntu. Sorting that out is a matter for later however as I'm now off to sleep.

A MASSIVE thankyou to everyone who helped out, I'm looking forward to my new learning curve and hopefully eventually getting rid of Windows altogether.

Thanks again

Spocksbeard

---

