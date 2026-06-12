---
title: "No Boot Device. Halp PLZ asap"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by alexander21778 on 2012-09-21
I decided to wipe my drive of windows 7 and go Ubuntu 100%, but after doing so using the install CD I get No Boot Device Available every time. The Install seemed to go well but it just wont start up.

I have tried everything I can think of. Here's the log I got from the boot repair utility. Hoping someone can help me soon. As of now I only have the live boot.

[Http://paste.ubuntu.com/1218215/](Http://paste.ubuntu.com/1218215/)

---

### Post by alexander21778 on 2012-09-21
I don't believe it's a hardware problem. I removed the drive and tried to install on another smaller drive. Same thing happens. So, I've gone back to the big drive and am hoping someone can help me.

---

### Post by arochester on 2012-09-21
Have you changed the BIOS/Boot Order so that it boots from the CD-Rom first and not the Hard Drive?

---

### Post by Deepak A on 2012-09-21
Can u boot from CD ROM?

---

### Post by YannBuntu on 2012-09-21
@alexander: Boot-Repair indicates:
> The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


Quick solution:
via Gparted, reduce your sda1 partition from 995GB to 100GB. (reduce it from the right-side so that it still begins at the start of the disk).
Then reboot the PC and tell us if better.
If not, run Boot-Repair's Recommended repair and tell us the new URL that will appear please.


> **arochester said:**
> Have you changed the BIOS/Boot Order so that it boots from the CD-Rom first and not the Hard Drive?

that's not the point, because he already could boot the CD and install Ubuntu.

---

### Post by alexander21778 on 2012-09-21
> **arochester said:**
> Have you changed the BIOS/Boot Order so that it boots from the CD-Rom first and not the Hard Drive?

I did, I thought. I used the the (f2) setup options to set my boot device order and I assumed it was the same menu. It has the boot list priority set as should be and all. However, hitting f12 for actual boot options (same menu) different taste. Turns out they are not the same.

Had you not made me think twice (or fifty) times about it I'd never have bothered. So thank you VERY MUCH arochester.

---

### Post by alexander21778 on 2012-09-21
PS thanks everyone ;)

---

### Post by alexander21778 on 2012-09-21
Update: Though my drive was appearing in the bios and working for install it was actually "disabled"! I hate being a noob. Thanks again everyone.

---

### Post by daslinkard on 2012-09-21
We were all noobs at one time.  Please mark this thread as solved!

---

