---
title: "DSL randomly freezes up on USB boot"
date: 2008-09-02
forum: Other OS Talk
---

### Post by demios on 2008-09-02
Hey, the damnsmalllinux board admin is taking forever to activate my account, so I thought I'd ask here:

I can get DSL embedded to boot from my usb key, but it will freeze up randomly (at completely different points) within fiveish minutes. I thought it was a connection problem, but booting within windows via qemu works fine, no freezing. anyone have any ideas of what might be up?

thanks a ton

---

### Post by zmjjmz on 2008-09-02
> **demios said:**
> Hey, the damnsmalllinux board admin is taking forever to activate my account, so I thought I'd ask here:

I can get DSL embedded to boot from my usb key, but it will freeze up randomly (at completely different points) within fiveish minutes. I thought it was a connection problem, but booting within windows via qemu works fine, no freezing. anyone have any ideas of what might be up?

thanks a ton
It could be your USB drive.
Check if it's fragmented badly or something.
(by the way, ask in the IRC channel)

---

### Post by demios on 2008-09-02
how might I check if it's fragmented poorly? I didn't even know that was possible.

---

### Post by Bungo Pony on 2008-09-02
- Try booting it on a different machine and see if the problem follows the USB drive. If not, then it's a hardware problem.

- Try re-formatting the USB drive (you can use Gparted) and re-installing DSL onto it. If the problem persists, try using a different USB drive.

---

### Post by demios on 2008-09-02
Alright, I'll try all that, thanks a ton.

---

