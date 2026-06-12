---
title: "Ububntu 8.04 AMD64 Fails to Install"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Ubangi on 2008-04-24
1) I have burnt the 8.04 desktop installation image but the install failed while trying to bring up Ubuntu for the first time (frozen dead).

2) There aren't any MM5SSD codes to check the image integrity (I can only find ones for previous Ubuntu releases).

3) Your servers are grinding to a halt.

4) Alltogether a "balls-up".

---

### Post by Ubangi on 2008-04-24
I found the checkcode at last, totally by chance in a forum: 
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso

It checks out, so I don't know what is failing.

I guess I will have to play a detective for a day or two, as always with Ubuntu.

---

### Post by tribaal on 2008-04-24
Try to select "check CD for errors" when booting from the CD - this will check against a bad burn.

If you get errors here, make sure to re-burn a CD with a lower speed (I use the slowest available burning speed).

Hope this helps.

- Trib'

---

### Post by Ubangi on 2008-04-25
Thanks tribaal, I thought of that. It hangs up also while checking for errors. I burnt another CD, using an external burner, and the same thing happens.

I then tried wubi and found that there is a bug in GRUB which writes wrong disk numbers to the MBR. I manually changed it and wubi, at least, now comes up. Could this have something to do with not being able to do CD install?

I really want to have Ubuntu on its own disk, which is sitting there empty at the moment but I cannot either upgrade to it from wubi, or do a CD install, so I am stuck.

---

### Post by Joeb454 on 2008-04-25
I install from an amd64 disc with no issues. I'm typing this from the install right now.

No issues with grub that I've seen, it's even added the 2 others OS's installed on here just fine as well :)

---

### Post by philinux on 2008-04-25
Yep always burn at 4x. I always use cdrw's now, been using them for months - no more coasters. Always check cd for defects, it checks all the md5sums.

Could be be bad cd's. It's happened before.

---

### Post by kesman on 2008-04-25
Also consider using the alternate install cd, it's text-based but nearly as simple as the graphical one, and it's a lot faster. Some would think that the resulting installation would differ with alternate install or the desktop install, but it's absolutely the same with Gnome and compiz and all.

---

### Post by Ubangi on 2008-04-25
I might try the text install, though I have trepidations about being faced with a blank screen and a prompt, just as happened in the middle of this installation.

By the way, I did use 4x burning speed onto a cdrw. 

Those of you who had the GRUB working must have been incredibly lucky.

---

### Post by Ubangi on 2008-04-27
Well, you were all off the mark but thanks for trying.
I have now played the detective for a few days and discovered the secret incantation that is necessary to get UBUNTU installed:

"F6, all_generic_ide floppy=off irqpoll"

---

### Post by Ubangi on 2008-04-27
PS. I don't think I ever want to do another Ubuntu installation again, I don't have time for this...

---

### Post by Ubangi on 2008-04-27
The above F6 magic will get Ubuntu installed but it won't work afterwards! It was dreadfully slow, to the point of freezing totally and having to pull the power plug to get out.

I reinstalled with just "all_generic_ide floppy=off" but WITHOUT "irqpoll" and it now finally appears to be OK.

---

