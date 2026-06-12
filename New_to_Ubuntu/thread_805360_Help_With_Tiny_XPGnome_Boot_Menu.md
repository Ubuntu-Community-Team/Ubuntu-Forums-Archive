---
title: "Help With Tiny XP/Gnome Boot Menu"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by monkserpent on 2008-05-23
Ok, I have Vista and Ubuntu (8.04) installed on my computer. I wanted to install Tiny XP on it to so that i'd have some version of XP. However, when I installed it on another partition, it somehow became the default OS. Now when I start up my computer, it boots straight into it! Without showing me the Boot Menu. How do I fix this??? (P.S. When I booted into a Ubuntu installation disk, (where I am now) and tried to edit my boot menu, I still had all the information. Except tiny xp was no where to be found on the list. But I still can't edit it, since i'm on a startup cd.

---

### Post by stalkier on 2008-05-23
> **monkserpent said:**
> Ok, I have Vista and Ubuntu (8.04) installed on my computer. I wanted to install Tiny XP on it to so that i'd have some version of XP. However, when I installed it on another partition, it somehow became the default OS. Now when I start up my computer, it boots straight into it! Without showing me the Boot Menu. How do I fix this??? (P.S. When I booted into a Ubuntu installation disk, (where I am now) and tried to edit my boot menu, I still had all the information. Except tiny xp was no where to be found on the list. But I still can't edit it, since i'm on a startup cd.

The reason yo don't see the GRUB menu is because TinyXP overwrote the MBR. You need to reinstall GRUB. Not sure where you can get it. I know most of the installers I have seen have been from floppies. You remember those square things that no one uses now. ;) Anyhow someone will come on here in a few seconds and post somthing even more useful than I posted. The forums are full of great people like that.

---

### Post by sam_delta on 2008-05-23
use supergrub to fix your grub,
download it @ [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


sam

---

### Post by Maestro23 on 2008-05-23
Super Grub: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by FuturePilot on 2008-05-23
+1 for Supergrub. Fixed my MBR when I overwrote it once. :shock:
Now it's a must have utility in my toolbox. ;)

---

### Post by Maestro23 on 2008-05-23
> **FuturePilot said:**
> +1 for Supergrub. Fixed my MBR when I overwrote it once. :shock:
Now it's a must have utility in my toolbox. ;)

Agree. It is a life-saver.:)

---

