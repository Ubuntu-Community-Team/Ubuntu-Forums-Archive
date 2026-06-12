---
title: "Need Grub help - Urgent!! - Grub rescue."
date: 2012-08-17
forum: New to Ubuntu
---

### Post by Baldrick_NZ on 2012-08-17
Hi all,

I installed Ubuntu on my work PC, but needed to remove it ASAP, so I inserted a live CD and used gparted to remove all my Ubuntu partitions.

Now I get a message upon boot saying "Unknown file system. Grub rescue", and it does nothing more.

What must I do in order to make the PC load windows as it did before?

I need the PC for work tomorrow...

Any help would be very much appreciated!

---

### Post by sandyd on 2012-08-17
> **Baldrick_NZ said:**
> Hi all,

I installed Ubuntu on my work PC, but needed to remove it ASAP, so I inserted a live CD and used gparted to remove all my Ubuntu partitions.

Now I get a message upon boot saying "Unknown file system. Grub rescue", and it does nothing more.

What must I do in order to make the PC load windows as it did before?

I need the PC for work tomorrow...

Any help would be very much appreciated!
Grub replaces the windows MBR
boor from a Windows 7/vista/xp restore disc (any will be fine)

Open a command prompt and type
```

bootrec /fixmbr
bootrec /fixboot
```

---

### Post by Ravi5kumar on 2012-08-17
This article will help you : [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/).

---

