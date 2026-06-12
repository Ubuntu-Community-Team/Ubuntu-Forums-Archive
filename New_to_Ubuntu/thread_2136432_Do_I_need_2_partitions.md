---
title: "Do I need 2 partitions?"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by Malmberg on 2013-04-17
Greetings from The Newbie!

Being fairly new to Ubuntu, I want to be sure not to miss any docs/music/files, when I mess up my Ubuntu 12.04 :-)
I’m quite good at keeping my Win7 computers alive - but have absolutely no idea how to rescue a broken Ubuntu installation!

So Im think it would give me a "life-line," if I could have 2 partitions on my favourite laptop with Ubuntu!

Can I use a "partition tool" to create a "safe-area" for my docs? - and if (when), I get my OS fuxx-up, then I can reinstall Ubuntu on "the OS partition" - right??????

Thanks in advance!
Steen

---

### Post by Vaphell on 2013-04-17
during installation in manual partitioning mode you can create separate partition for /home, which is where all userspace stuff is. It allows for easy reinstallation of the core system parts in 10 minutes without touching user data. During reinstall you simply point /home to the partition in question and that's it, just make sure 'format' checkbox is disabled.
Another quite common setup that allows for easy sharing between windows and ubuntu in dual boot setup is to create an ordinary NTFS partition where all the good stuff goes.
That said, always have a backup of things you can't afford to lose. Simple hardware failure can happen too.

---

### Post by Krextyl on 2013-04-17
> **Vaphell said:**
> 
That said, always have a backup of things you can't afford to lose. Simple hardware failure can happen too.

Second That!

---

### Post by audiomick on 2013-04-17
Yes, maintain backups. And yes, a separate partition for your /home directory will achieve what you want. I set up my installs that way, and it has helped me immensely.

What a separate /home partition will not do is keep track of programs you have installed manually after setting up the system. What it does do is retain the configuration files, so if you have to re-install, when  you re-install a program, the config file for it should still be there.

---

### Post by Malmberg on 2013-04-19
Gents - Thanks,
Ill start with a back-up :-), and then give GParted a try!
Cheers

---

### Post by rewyllys on 2013-04-19
> **Malmberg said:**
> Gents - Thanks,
Ill start with a back-up :-), and then give GParted a try!
Cheers
Malmberg, I can assure you that you'll be glad you set up a separate partition for your /home directory.  

The adoption of a separately partioned /home directory is, IMHO, the best single piece of advice I received after I first started experimenting with Linux 10 years or so ago.

Good luck with your installation!

---

### Post by Malmberg on 2013-04-19
Well, I did something stupid (again) :)
I did try to follow one of the very good instructions How To Move Your /Home Folder To New Partition!

This went just so wrong / I ended up with having a problem when the laptop boots - cant find my /home folder :(

So I think I need to start all over again!

Cheers

---

