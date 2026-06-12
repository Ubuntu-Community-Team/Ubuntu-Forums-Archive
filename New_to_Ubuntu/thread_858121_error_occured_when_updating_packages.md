---
title: "error occured when updating packages"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by elliah on 2008-07-13
when i check for upgrades i get this error message

W: GPG error: [http://xnv4.xandros.com](http://xnv4.xandros.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A3CCB76FA8BCF0C9

Before that I followed the instructions below to install the python IDLE

sudo bash
echo "deb [http://xnv4.xandros.com/xs2.0/upkg-srv2](http://xnv4.xandros.com/xs2.0/upkg-srv2) etch main contrib non-free" >> /etc/apt/sources.list
apt-get update
apt-get install idle-python2.5

now, when i select the install all upgrades option i get this error message

E:/var/cache/apt/archives/sysvinit-utils_2.86.ds1-38_i386.deb: trying to overwrite '/usr/share/man/man1/mesg.1.gz', which is also in package sysvutils

what should i do?

*after that i was unable to shut down my computer, so i powered it off.  now i cannot boot up xubuntu at all, after the it says starting up, i get the black screen of booting death.
i can access recovery mode but it stalls at 
/bin/sh: can't access tty; job control turned off
(initramfs) [   8.775041] Clocksource tsc unstable (delta = -740472046 ns)
[   8.779054] Time: acpi_pm clocksource has been installed

is my computer dead?

---

### Post by ChameleonDave on 2008-07-14
This is how to put the list back as it was, if you manage to log in:

Open up your software sources list with *one* of these commands:

```

sudo nano /etc/apt/sources.list
gksudo gedit /etc/apt/sources.list
kdesudo kwrite /etc/apt/sources.list

```Go to the last line (which you added before) and comment it out by placing a hash sign ("#") in front of it, thus:

```

# deb http://xnv4.xandros.com/xs2.0/upkg-srv2 etch main contrib non-free

```Then run this command in the terminal:
```

sudo apt-get update ; sudo apt-get -f install

```

---

### Post by ChameleonDave on 2008-07-14
Looking at your post again, I'd say that your Ubuntu is probably screwed.  There is no telling what damage all those Xandros packages did to the system, and it would be tricky to undo it all without being able to get to the a standard command line.

If you can somehow activate some failsafe option and get the command line, I can help you.

What guide told you to add and use that repo?

---

### Post by elliah on 2008-07-14
Here's the link to the instructions
[http://forum.eeeuser.com/viewtopic.php?pid=315006](http://forum.eeeuser.com/viewtopic.php?pid=315006)

---

### Post by ChameleonDave on 2008-07-14
> **elliah said:**
> Here's the link to the instructions
[http://forum.eeeuser.com/viewtopic.php?pid=315006](http://forum.eeeuser.com/viewtopic.php?pid=315006)
Ah, it's as I expected.  The EeePC runs on Xandros by default, and people giving advice for it assume that you are running Xandros.  If you have Ubuntu and follow the same advice, it may cause problems, much in the same way that following Mac advice for Windows might damage the system.

If you ever add a repo from another Linux distro, just use it to install what you want (no full upgrades!) and then remove the repo from /etc/apt/sources.list.

It looks like some fundamental packages that control the very core of Ubuntu have been replaced by Xandros packages.  Unless you can get to a command line, a fresh reinstallation is the only thing that will fix it.  Sorry!

---

### Post by elliah on 2008-07-15
it's alright...i clean installed xubuntu again...and now everything is running smoothly...thanks for all your advice too...

---

