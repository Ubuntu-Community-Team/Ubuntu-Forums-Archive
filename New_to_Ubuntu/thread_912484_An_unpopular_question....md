---
title: "An unpopular question..."
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Tsurugi13 on 2008-09-06
Before I get started let me say that I love Ubuntu. It's great. However, my pc is several years old and has a billion and a half compatibility issues that I don't have the time or money to deal with, not to mention the intense lag I get starting up programs.
:(
I'm currently dual booting windows XP and ubuntu, with GRUB as my bootloader. Can I use a Gparted live cd to remove my Ubuntu partition and fill its space with XP and still expect GRUB to work? If not, how can I get my windows bootloader back?

---

### Post by technotitclan on 2008-09-06
do you know have your xp cd or do you have that much valuable data?

---

### Post by Tsurugi13 on 2008-09-06
I have my XP CD but I also have crazy lots of stuff on it that I'm not willing to get rid of.

---

### Post by wolfen69 on 2008-09-06
resize the xp partition to take up the whole drive, then boot to the xp cd and choose recovery console. type in fixmbr. you're done.

---

### Post by aysiu on 2008-09-06
> **Tsurugi13 said:**
> I have my XP CD but I also have crazy lots of stuff on it that I'm not willing to get rid of. wolfen69 gives you the correct instructions but any kind of repartitioning should always be preceded by backing up of all important files. Back up.

Back up your files.

Back up all your files.

Do not proceed with repartitioning until you have backed up your files.

> **wolfen69 said:**
> resize the xp partition to take up the whole drive, then boot to the xp cd and choose recovery console. type in fixmbr. you're done.

---

### Post by oilchangeguy on 2008-09-06
> **wolfen69 said:**
> resize the xp partition to take up the whole drive, then boot to the xp cd and choose recovery console. type in fixmbr. you're done.

it's best to follow all of the steps. first boot from the windows cd, not a factory recovery cd. after it loads choose r to enter the recovery console. you'll be asked for the admin password, if there is one type it and press enter. if there's not one just press enter to bypass the prompt. then type fixboot and press enter. then type fixmbr and press enter. then type exit and press enter.

---

