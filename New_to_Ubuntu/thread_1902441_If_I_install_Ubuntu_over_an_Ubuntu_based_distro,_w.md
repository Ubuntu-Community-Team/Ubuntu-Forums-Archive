---
title: "If I install Ubuntu over an Ubuntu based distro, will my home folder stay intact?"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by Scarbird on 2011-12-30
I was just wondering if I installed Ubuntu over something Ubuntu based like Linux Mint and entered the same computer name, username, password, etc. used in the previous installation at the installation prompt, would my Home folder remain intact?

---

### Post by Butthead on 2011-12-30
Probably not. :eek:

I'm sure there's a way you can save your current home directory folder over to a CD (for example) and paste it back after installing the new Linux distro.

I'm not sure if different flavors of Linux work together so well though.  Even though Mint and Ubuntu are both Debian based, I think I remember reading somewhere that they still don't blend so well when mixed together. :confused:

---

### Post by Bucky Ball on 2011-12-30
Home folder, no. /home partition, yes. For the partition you would use manual partitioning during install, UNMARK the /home partition so it doesn't format and your new installation would use it by default.

---

### Post by PhilGil on 2011-12-30
Bucky Ball is correct. If you created a /Home partition during your previous install you can use it again in your new install.

However, always, ALWAYS do a backup of your documents and media (at a minimum) before doing a fresh install. It only takes a couple of wrong clicks to accidentally blow up the /Home partition.

---

### Post by The Cog on 2011-12-31
In the advanced installer partitioning options, when you nominate the partition to install to, you can also choose not to format it. In that case, the installer goes through a process of deleting all the folders it thinks of system folders before it starts installing. Now, I **think** it leaves /home intact, but I only ever did this once by accident and can't guarantee the results. But it mught be worth a try provided that you already have a backup of /home just in case it doesn't go so well.

---

### Post by 3rdalbum on 2011-12-31
It's a good opportunity to backup /home anyway.

But if you use the manual partitioning method in the Ubuntu installer, but do not elect to format the / partition, then your home folders **will** stay intact. Just make sure you DON'T tick the "Format?" checkbox next to the device file name on the partitioning screen.

---

