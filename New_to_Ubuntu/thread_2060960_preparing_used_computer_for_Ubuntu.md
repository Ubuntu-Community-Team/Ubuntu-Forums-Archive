---
title: "preparing used computer for Ubuntu"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by john18 on 2012-09-21
I recently bought a used pentium 4 computer ($100) with microsoft xp home edition for the sole purpose of installing and learning Linux using Ubuntu.  Since I already have a windows computer for my routine use while getting familiar with Linux, I think I would like to remove windows completely from the recently aquired machine (call it my Linux computer).  Is this a good idea?  Will I be able to do it if I don't know window administrator's password (or even if one is necessary)?  Will Ubuntu automatically overwrite windows as suggested in a book on Ubuntu which I borrowed from the library and would this be equivalent to removing windows alltogether?  I would like as clean a slate as possible.

Thanks,
John

---

### Post by Mark Phelps on 2012-09-21
> **john18 said:**
> ... I would like as clean a slate as possible.

Thanks,
John

OK, then boot from an Ubuntu LiveCD (or USB) and use GParted to remove ALL the partitions from the hard drive.  That will give you an empty drive to start with for Ubuntu.

---

### Post by irv on 2012-09-21
> **Mark Phelps said:**
> OK, then boot from an Ubuntu LiveCD (or USB) and use GParted to remove ALL the partitions from the hard drive.  That will give you an empty drive to start with for Ubuntu.

Can I ask a question. If you just install Ubuntu and chose the option to use the entire drive doesn't the install do the same thing as you suggested in this post? I am not trying to get smart, I always thought that is what it did.

Also before installing Ubuntu I would run the live OS to make sure all the hardware will work with it. Like Video, wifi if it has a wifi card, network card etc.

---

### Post by Sidewinder1 on 2012-09-21
Might I suggest that you first md5sum the ubuntu ISO and make sure the output matches exactly the hash that is usually provided at the site in which you downloaded the ubuntu ISO? Even if you acquired it via torrent/peer to peer protocol that does have error checking built in, when installing an entire operating system, it's best to be absolutely certain that everything is exactly correct.
Oh, and, Welcome to Ubuntu!

Side

---

### Post by clive littlewood on 2012-09-21
Hi

When you go through the installation process from the live CD (DVD)

You will be given the options to install alongside windows or remove windows and use the whole drive for Ubuntu.
 
Chose the whole drive for Ubuntu option and you will be good to go.

Regards

Clive

PS. It is always a good policy to run the live CD first to make sure that all equipment is recognised, then use the install now icon on the desktop.

---

### Post by daslinkard on 2012-09-21
> **john18 said:**
> I recently bought a used pentium 4 computer ($100) with microsoft xp home edition for the sole purpose of installing and learning Linux using Ubuntu.  Since I already have a windows computer for my routine use while getting familiar with Linux, I think I would like to remove windows completely from the recently aquired machine (call it my Linux computer).  Is this a good idea?  Will I be able to do it if I don't know window administrator's password (or even if one is necessary)?  Will Ubuntu automatically overwrite windows as suggested in a book on Ubuntu which I borrowed from the library and would this be equivalent to removing windows alltogether?  I would like as clean a slate as possible.

When you run the CD you will be able to select Linux as your only OS on the PC.  You will not need to know the administrator password for windows as you will be able to bypass the log in. 

Personally I think this is a great idea for you as my family and I moved away from windows about a year ago and have not looked back.  Any questions you have just know there are a ton of people here to help you.

---

### Post by snowpine on 2012-09-21
With such an old computer, you should definitely audition the Live CD before committing to an install. I think you may end up with something lighter like Xubuntu or Debian for your old Pentium 4. Also if you are concerned about removing all traces of the previous owner (for security/privacy reasons), you can completely wipe the drive using an application such as dban: [http://www.dban.org](http://www.dban.org)

---

### Post by cmcanulty on 2012-09-21
also look at lubuntu the lightest ubuntu desktop

---

