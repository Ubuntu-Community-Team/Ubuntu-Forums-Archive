---
title: "[SOLVED] Unlocking Partitions"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Nazty_Nayt on 2008-10-01
Hey all, I'm trying to dual boot Ubuntu, and Vista (yuck).  I don't want Vista really, but need it for very few programs.  Anyways, I'm following a guide [here](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=3) but I get stuck at this part...

[img]http://apcmag.com/images/apcapc/howto/Dualboot_-_Vista___Ubuntu__Ubuntu_first__images/ubuntu_gparted_02.jpg[/img]

This part here loses me, it says to click resize/move, but mine is locked, and I don't get that option.  Can someone just simply tell me how to unlock this?

---

### Post by iaculallad on 2008-10-01
The partition you're trying to resize could be active. Try to boot from your Desktop LiveCD and from there, use GParted to resize/move that partition.

---

### Post by Paqman on 2008-10-01
The problem is that you swap is in use, and therefore locked. Since your swap is inside your extended partition it also locks that.

I believe you can issue the swapoff command from a right click in Gparted? If that's the case you should be able to resize your extended partition then swapon when you're done. Otherwise it's:

```

sudo swapoff -a

```
 to disable swap, then to restore it:
```

sudo swapon -a

```

---

### Post by Nazty_Nayt on 2008-10-02
Paqman, upon doing that it unlocked 2 of the drives, but not the main partitions.  And iaculallad, I tried your method, was able to unlock them, but when I went to resize the partition it was taking forever, and not showing any progress, I gave it about an hour with no progess till I switched back to my initial install.

---

### Post by Paqman on 2008-10-02
> **Nazty_Nayt said:**
> Paqman, upon doing that it unlocked 2 of the drives, but not the main partitions.

Ah right, I thought that screenshot was of your system, but I see now that it isn't.

You can't alter any partition which is mounted. Your root partition will be mounted, because you're running from it. Iaculallad's method was correct. Resizing/moving partitions can take a long time, so stick with it.

---

### Post by Nazty_Nayt on 2008-10-02
Thanks Paqman, I'm retrying it again, here.  I shortened it this time to only a 25 Gb partion to be left over, how long do you think that'll take roughly?

---

### Post by Paqman on 2008-10-02
Impossible to say. It depends on how much data the system has to shift around to create the free space.

If you want to see the progress in more detail, you can click on the "details" button and see Gparted completing each stage of an operation.

---

### Post by Nazty_Nayt on 2008-10-02
Alright, it's all done thanks again guys.  Appreciate the help, didn't want Vista anywhere near my machine, but unfortunately since Microsoft runs the country I need it for school.  Thanks again guys.

:guitar:

---

