---
title: "ubuntu doesnt load"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by stubblepoo on 2008-07-27
i got a message saying server x or my desktop compositor or something has failed ( i picked up on it as no programs could save to the desktop) and so rebooted. it said something about inconsistencies and me needing to run fsack in safe mode wih the disk unmounted, i preceded into safe mode and unmounted the disk but cannot run fsack. when i type 'fsack' i get bash command not found(etc)
cheers

---

### Post by lisati on 2008-07-27
If you boot from a  LiveCD you will be able to run the fsck command from there.

---

### Post by Troll_the_Great on 2008-07-27
The command is "fsck" not "fsack".
You could log in in recovery mode (at boot up choose recovery mode from the grub menu), then choose fix X server and log in normally.Tell me if it worked.
Cheers!

---

### Post by sharks on 2008-07-27
i think its **fsck** (file system check or file system consistency check)

---

