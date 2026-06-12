---
title: "Can't Boot into Windows after Dual-Boot Install - BitLocker"
date: 2019-03-21
forum: New to Ubuntu
---

### Post by illuminati-tri on 2019-03-21
Here's the boot repair summary:

[http://paste.ubuntu.com/p/mWT4H6JP5F/](http://paste.ubuntu.com/p/mWT4H6JP5F/)

Basically what happens is when I try to boot into Windows 10, it asks for my BitLocker key (which I have), so I enter it and it says it's correct, but then it just asks for it again and eventually reboots (and asks for it again). Not sure what to do here.
Any help is appreciated - thank you!

Let me know if any other information is needed.

Btw, this is on a Dell XPS 13 9360, if that matters.

---

### Post by oldfred on 2019-03-21
Note sure grub can boot encrypted Windows.

Can you directly boot Windows from UEFI boot menu.

Most desktops do not need separate partitions for /boot nor other system partitions other than perhaps /home.

---

