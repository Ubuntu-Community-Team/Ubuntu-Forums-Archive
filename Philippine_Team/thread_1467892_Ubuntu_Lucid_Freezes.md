---
title: "Ubuntu Lucid Freezes"
date: 2010-05-01
forum: Philippine Team
---

### Post by vaikz on 2010-05-01
Hi, I'm not new to ubuntu and i'm using it since hardy pa. I have 2 pc, one is an intel graphics and the other is a via graphics both are on board. 

Tried to run live on a vm and on my intel w/o problems but when i run it on my pc w/ on board via graphics, then there is a problem. it booted fine and it displays the desktop. But after awhile, the screen display turns into a garbage display. Parang walang signal na TV. and at the same time mouse and kb freezes.

Experience this problem from the past version of ubuntu. and really don't have any idea how to fix this.

PS. Run with puppy on this same computer, but no problem.

---

### Post by loell on 2010-05-01
model specific  of the graphics?

---

### Post by vaikz on 2010-05-01
it's an on-board via graphics from this motherboard: [ASUS K8V-VM]("http://www.asus.com.ph/product.aspx?P_ID=IQoVElAYUAC4aAz3").

---

### Post by loell on 2010-05-01
Oh :(

the progress is not promising accroding to  [https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-openchrome/+bug/377402](https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-openchrome/+bug/377402)

puppy most probably used the Vesa driver, you could achieve the same in ubuntu (supposedly automatic) but there will be no video acceleration.

---

### Post by vaikz on 2010-05-01
That's bad news. 

By the way, how to boot livecd using vesa driver on boot options?

---

### Post by loell on 2010-05-01
press any at the start of the boot, then see boot options, there a safe mode option in there.

---

