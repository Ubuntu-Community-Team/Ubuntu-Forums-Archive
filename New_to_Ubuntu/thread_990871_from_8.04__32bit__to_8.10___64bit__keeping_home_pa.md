---
title: "from 8.04  32bit  to 8.10   64bit  keeping home partition"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Harisz750 on 2008-11-23
Hi  !!!!  i want to install from scratch ubuntu 8.10  64bit  but keeping the home partition from the previous installation of 8.04  32bit..  is that possible or i'll experience broblems in configuration files???

---

### Post by beno1990 on 2008-11-23
It is possible to do it; in the partition manager during the install process, choose a manual partition setup. Then set your home partition to the /home mount point and **un**tick the format option, but let it format the other partitions.

Just one snag: Make sure your UID and GID are the default 1000 settings which is what Ubuntu will make your newly created account when you install, otherwise you won't be able to access your home directory and its contents.

---

### Post by Paqman on 2008-11-23
> **Harisz750 said:**
> is that possible or i'll experience broblems in configuration files???

The config files are just plain text, so they're exactly the same for 32-bit and 64-bit.

Regarding UIDs, if you set up your users in exactly the same order, they'll end up right. Otherwise take note of the current settings and make sure you set them that way when you set the users up on the new system. Even if you do muck it up, just issue this command to have the user take full ownership of their home folder:

```

sudo chown -R *username* /home/*username*

```

---

### Post by philinux on 2008-11-23
I done this many times with my /home on it's own partition. As mentioned above choose manual to edit the partition to set the mount points. The format box is default set to not format. Just dont tick it for the /home partition but do tick it for /.
I just reinstalled this morning as opensuse 11, installed to second hard drive, ate grub and gave error 15 which supergrub could not fix.

---

### Post by Harisz750 on 2008-11-23
I'm not completely noob!!!!!!!  I'm not asking about home partition....  but for 32bit  to 64bit keeping old home from 32bit..  anyway, config files are just text... so it can be done...

---

### Post by Paqman on 2008-11-23
> **Harisz750 said:**
> I'm not completely noob!!!!!!!

Ok, but this _is_ the completely noob forum. Glad we could help, though!

---

