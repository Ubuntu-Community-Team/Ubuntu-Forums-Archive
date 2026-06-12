---
title: "[SOLVED] I have a kernal I don't want"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by adamogardner on 2008-05-30
ok so I have an extra version of Ubuntu on my GRUB menu at startup.  Somehow I aquired this parasite when I was trying to install something.  I have uninstalled that something to the best of my knowledge although that something admittedly was never called ubuntu 7.10 (server) kernal.  Rather than the (generic) which is what I wANT to keep.  How do I rid my self of this?  I looked for ubuntu 7.10 in synaptic pacman  to maybe uninstall the server kernal.  It was not to be found.  What next?  I'm not interested in hiding it and it's recovery counterpart.  I want it out of my system. How?

---

### Post by llamakc on 2008-05-30
Bad idea. Having a backup, older version of the kernel that boots is ALWAYS a good idea.

---

### Post by adamogardner on 2008-05-30
no yu missunderstand   I have what is parenthesied (generic, and an alternative recovery kernal thats is also (generic) but somehow this 3rd party (because I already dual boot with Vistard) showed up and it doesn't shut down, the resolution is awful, and it sets off an alarm in my machine!  this third party is labeled (server) as opposed to generic which i started out with and works fine.  So I want to scrap the server kernal and Its recovery counterpart

---

### Post by llamakc on 2008-05-30
Thanks for adding the information.

Run this command in the Terminal. It will output packages installed that have "server" in them.

```

dpkg -l | grep image | grep server

```

Then remove THOSE packages. They'll most likely be named like this—

```

linux-image-2.6.XX-xx-server

```

---

### Post by niteshifter on 2008-05-30
Hi,

> ok so I have an extra version of Ubuntu on my GRUB menu at startup. Somehow I aquired this parasite when I was trying to install something.

And here's how "the parisite" showed up:

> Some error to install something with the kernal (generic) did not work so I tried the "server" package from Synaptic P-mananger and it installed this fuzzy server version of ubuntu that has poor resolution.

From your earlier post, where you had folks engaged and trying to help you. What? You think people can't read?

Do this:

1. Backup your windows installation.
2 .Use Gparted from the LiveCD and delete your current Ubuntu partition(s).
3. Reinstall ubuntu.
4. Search this forum and use google for a wider range search on using your aircard with Ubuntu / Debian Linux.

5. And most important - don't double post and be disingenuous about it.

---

### Post by Oldsoldier2003 on 2008-05-30
> **llamakc said:**
> Thanks for adding the information.

Run this command in the Terminal. It will output packages installed that have "server" in them.

```

dpkg -l | grep image | grep server

```

Then remove THOSE packages. They'll most likely be named like this&#8212;

```

linux-image-2.6.XX-xx-server

```

Even though I do almost every maintenance operation from the command line, I would suggest to the op that it is easier to sort it out using synaptic. Find the image by searching then mark it for complete removal. This will also update your grub automagically.

---

### Post by adamogardner on 2008-05-30
how do I remove them?

---

### Post by Duck2006 on 2008-05-30
Uncheck them in synaptic package manager.

---

### Post by adamogardner on 2008-05-30
what do you mean disengenuous?  Why are you attacking me?  What I can't recollect my situation after a lengthy and useful thread and come back to it with a fresh air and remodeled statement.  It's not like I'm changing my account...so next time you see my screen name (yeah and my real name too)!  just pass me by. I'm fine without your miserable disposition, you.

---

### Post by adamogardner on 2008-05-30
ok!  i'm going to restart my computer  I'll let you know....

---

### Post by adamogardner on 2008-05-30
ALRIGHT!  THAT WAS FAST AND EASY! just in a language I don't yet speak.  Thank you. 10,000x's thankyou.

---

