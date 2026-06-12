---
title: "[SOLVED] Installing, partitioning questions"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by The Protagonist on 2008-07-21
Hey, I've decided to install Ubuntu and just wanted to know some things first.
My first question is, how big should I make the partitions? I know I need to have a / partition, and /home partition, and a swap partition. I have a 455 gig hard drive and my Windows install is taking up 119 of that. That's with about 30 recorded TV shows. I plan to do some gaming, so I'd like some room for that. I want to use Ubuntu for as much stuff as possible, and just use Windows for games and whatever I need to use Windows for.

I also have a big (465 gig) portable hard drive, I was wondering if it would be at all feasible to run Ubuntu off that? Or would it be too slow?

Also, how easy is it to remove? If I decide I absolutely can't stand it, what do I have to do to get rid of it?

---

### Post by iaculallad on 2008-07-21
Try relating to this forum thread on [Partitioning]("http://ubuntuforums.org/showthread.php?t=282018").

---

### Post by Niniel on 2008-07-21
> **The Protagonist said:**
> Hey, I've decided to install Ubuntu and just wanted to know some things first.
My first question is, how big should I make the partitions? I know I need to have a / partition, and /home partition, and a swap partition. I have a 455 gig hard drive and my Windows install is taking up 119 of that. That's with about 30 recorded TV shows. I plan to do some gaming, so I'd like some room for that. I want to use Ubuntu for as much stuff as possible, and just use Windows for games and whatever I need to use Windows for.
Give Ubuntu 100 GB,that should be plenty.
And you don't *need* a /home partition. Some people argue for it (safe/r from OS screw-ups), some against it (might run out of space)... might be best to not do that until you get more familiar with Ubuntu/Linux.

> **The Protagonist said:**
> I also have a big (465 gig) portable hard drive, I was wondering if it would be at all feasible to run Ubuntu off that? Or would it be too slow?
It can be done, but it requires a bit of work. Search the forum for how it's done.

> **The Protagonist said:**
> Also, how easy is it to remove? If I decide I absolutely can't stand it, what do I have to do to get rid of it?
By "it" you mean Windows, right?
Well, it'll be just as any other OS - delete the partitions and you're done. :)
In the unlikely case that you were talking about Ubuntu, removing the partitions (can be done from within Windows) will leave the boot manager behind, but you can get rid of that too (Windows recovery CD, boot to prompt, run the "fixmbr" command, and that's it).

---

### Post by dave.com on 2008-07-21
I adopted the Gentoo Partition scheme of installing /boot on its own partition. Their reasoning was sensible, something about security, any corruptions elsewhere, and choice of dividing the partitions (original Gentoo installation manual uses ext2 for /boot as an example) as an added precaution. You're going to have to read up in any event, so don't overlook the gnu.org documentation site: 
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

---

### Post by Dutch70 on 2008-07-21
1. /root needs to be between 10 and 20GiB, /home depends on how much stuff you want to put on it. 

2. swap should typically be twice the size of the physical RAM you have. I have 2 GB of RAM, and it never uses any of the swap file that I have noticed. and I do look. 

3. dont know about the portable hard drive.

4. To remove it, all you have to do is delete the partitions it is installed on, and grow the windows partition back to full size. you also have to reconfigure your boot manager to remove grub.


also check this site...its great!
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Rolcol on 2008-07-21
> **Dutch70 said:**
> 1. /root needs to be between 10 and 20GiB, /home depends on how much stuff you want to put on it. 

2. swap should typically be twice the size of the physical RAM you have. I have 2 GB of RAM, and it never uses any of the swap file that I have noticed. and I do look. 

3. dont know about the portable hard drive.

4. To remove it, all you have to do is delete the partitions it is installed on, and grow the windows partition back to full size. you also have to reconfigure your boot manager to remove grub.
(I hope I said that right).

also check this site...its great!
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Without using a windows disk, can't you make a backup of the MBR with dd and restore it without having to write to the rest of the disk?

---

### Post by candtalan on 2008-07-21
You might find that after you begin to get used to Ubuntu you may want to make different decisions about partitions, so go gently at first. 

I have usually found that accepting the default /home directory (not making a separate partition) is perfectly ok.

Hopefully you do backups regularly? Installing a new operating system will include a partition editing activity - which will carry a (small) risk of major data loss.

After you are up and running with Ubuntu, the useful stuff to back up is mostly the /home directory.

Are you aware that the latest Ubuntu (8.04) includes a facility to install -inside- windows as a windows application? this is easy, and avoids any partition changes. However it is a bit vulnerable to sudden power loss, so you might want to use it just initially to try things out.

---

### Post by The Protagonist on 2008-07-21
Thanks everyone. I ended up installing within windows. Everything went smoothly at first, until I restarted after installing updates and a video driver. Then it hung up at the loading screen. I eventually had to hard reset. It started hanging up at a black screen then. So I tried uninstalling and reinstalling. Now I have two Ubuntu options at start up, one of which hangs at the loading screen again, the other I haven't tried. Help?

---

### Post by Dutch70 on 2008-07-21
That is an entirely different problem. mark this thread solved if it is.
And start a new thread with your new problem.

Dutch

---

