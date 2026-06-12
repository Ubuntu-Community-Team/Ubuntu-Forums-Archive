---
title: "Noob"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Vato1982 on 2008-05-02
Hi I want to install linux in my machine, i have a copy of sussy.

OK here it goes:

I have a hard drive and i partitioned in 3:
1. WINDOWS 20GB
2. EMPTY 20GB
3. STUFF 200 +/- GB

so i have Windows XP installed in the windows partition, I have my files in STUFF, and i tried to run the installation on the EMPTY drive, and I get error messages.

Can somebody give me a tutorial on "how to install Linux"

If anyone willing to help me needs screen shots I'm more than happy to do it.

PS: if possible i don't want to lose any of my files in my STUFF drive.

Thanks!!!!

---

### Post by mano cazalet on 2008-05-02
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

I've learned a lot with the psychocats pages, take a look, I'm sure it will help you to

---

### Post by drsox1899 on 2008-05-02
Hi there.

What's sussy ?

An easy way to install is to use the 7.10 live CD and do the following :

1. Install the / partition to your EMPTY partition (will need to be formatted)
2. Install a SWAP partition in the same partition (install might do this for you)
3.  Install /home in your STUFF partition WITHOUT formatting the partition.

What's the format of the STUFF partition ? It will need to be a Linux format. So you may have to backup and restore.

This way you can change installs and reinstall without losing your data etc.

Here's a good HowTo guide : [http://ubuntuforums.org/showthread.php?t=706813](http://ubuntuforums.org/showthread.php?t=706813)

Luck

---

### Post by tango_ninja on 2008-05-02
What's sussy? Is this Suse (never heard this term).  If you're going with Ubuntu, download the liveCD from ubuntu.com, burn the image to disc and you can do a test boot from the CD. Check out the OS, see how you like it, and if you like it you can install for real. Just boot from the CD and follow the instructions. 

You will be able to keep your stuff partition + xp partition, just make sure you select the free one when you install. Are you looking for a step-by-step guide or does this suffice?

---

### Post by bjm1904 on 2008-05-02
Your 'empty space' can be formatted to ext3 during an Ubuntu installation - it will be (if your partition table is accurate) either hda2 or sda2 (depending on if you have an IDE or SATA/SCSI hard disk). Just choose 'manual setup' during installation and you'll get the GNOME paritioner, gparted (which is pretty easy to use)

---

### Post by kingpoiuy on 2008-05-02
Sussy = Sue-se = Suse

I've heard people call it that before, but never spell it out that way.

---

### Post by bigken on 2008-05-02
sussy is one half of sussies somthing my missus used to wear many moons ago memory's :lolflag:

---

### Post by Vato1982 on 2008-05-05
Thank u everyone!!!
and YES I did make a spelling mistake.  =P
Thanks everyone for the help, what im going to do i will try and install linux tonight and i will make a new thread with screenshots and everything.
Thanks again

---

