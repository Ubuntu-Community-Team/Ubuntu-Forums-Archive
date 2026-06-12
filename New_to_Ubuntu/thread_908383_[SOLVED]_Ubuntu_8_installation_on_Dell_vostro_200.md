---
title: "[SOLVED] Ubuntu 8 installation on Dell vostro 200"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by bprof on 2008-09-02
I've installed Ubuntu 8 on Dell vostro 200, and I have problems in making it working normally.

When I turn the machine on, it starts the booting sequence and then hangs or gives me the Debian busybox. I did some search and I was able to make it pass this point by editing the boot command and adding the following to it

all_generic_ide

Without this statement I can't make it work.

I tried to use envy to detect my Nvidia 8400 and it fails, and not sure if this related the other problem or not. (Without the card I have the same booting problem).

Any thoughts?

Thanks

---

### Post by bprof on 2008-09-02
I was able to sovle it using irqpoll instead of all_generic_ide, everything is working fine now.

---

