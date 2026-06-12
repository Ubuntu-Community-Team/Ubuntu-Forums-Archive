---
title: "I need a walkthrough for 11,04 to 11.10 save settings"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by cackerso on 2011-11-27
I tried a simple upgrade from 11.04 11.10.  Now I have a number of problems.  So I'd like to do a clean install.  My /home is on a separate partition and is encrypted.  So how to I do the clean install and minimize all the work of getting my settings, installed applications and so on back to what they were before the install? 

There must be a guide somewhere, I just haven't found it.

---

### Post by Paddy Landau on 2011-11-27
Encrypted /home is poorly documented and a bit tricky to get right. (I have documented the process but even so I still don't understand it well enough to actually do it.)

The absolute easiest way to do this is how I do it:
[LIST=1]
[*]Back up your entire /home directory (unencrypted, of course). You'd have to back up anyway for safety. An external USB hard drive is a good place. Remember to include all the hidden folders (those that start with ".")
[*]Check that your backup, including hidden folders, is sound before continuing.
[*]Do a clean installation, formatting your /home partition.
[*]After booting your computer, selectively restore the files that you want from your backup -- or, if you prefer, just restore the entire thing and log out and in again.
[/LIST]

---

### Post by dniMretsaM on 2011-11-27
> **Paddy Landau said:**
> Encrypted /home is poorly documented and a bit tricky to get right. (I have documented the process but even so I still don't understand it well enough to actually do it.)

Yeah, not the easiest thing to do. I would recommend trying to find someone on here who has done it before and can walk you through it. If you do that, consider helping to improve the documentation on the process.

> **Paddy Landau said:**
> The absolute easiest way to do this is how I do it:
[LIST=1]
[*]Back up your entire /home directory (unencrypted, of course). You'd have to back up anyway for safety. An external USB hard drive is a good place. Remember to include all the hidden folders (those that start with ".")
[*]Check that your backup, including hidden folders, is sound before continuing.
[*]Do a clean installation, formatting your /home partition.
[*]After booting your computer, selectively restore the files that you want from your backup -- or, if you prefer, just restore the entire thing and log out and in again.
[/LIST]


I recommend this method also. It's exactly what I do and it's worked out great so far.

---

### Post by vangop on 2011-11-28
Try to use this [guide]("http://ubuntuforums.org/showthread.php?p=7576717"), it's very detailed.

---

### Post by cackerso on 2011-11-28
Thanks for the input and the links to the guides.

cackerso

---

