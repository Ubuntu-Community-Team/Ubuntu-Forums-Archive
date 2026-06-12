---
title: "[SOLVED] The &amp;quot;GRUB error&amp;quot; appears when I try to boot from Hard Disk."
date: 2008-09-29
forum: New to Ubuntu
---

### Post by NewsAndHistory on 2008-09-29
Earlier today, I was messing with ArchLinux disto, and I stopped mid-way through the installation process because it wouldn't work for me. So, now I want to install Ubuntu.

However, my computer (Dell 9100 with intel Pentium 4 processor) will not allow me to "Boot from Hard Disk" without getting this error-message: "GRUB" with a blinking cursor "_".

When installing Archlinux, the GRUB was installed on the Hard Disk or Hard Drive (which mean the same thing, I guess).

Would any of you please tell me what would happen if I install Ubuntu from my CD-ROM? Would the GRUB-error be fixed if I did that?

---

### Post by OldGrey on 2008-09-29
It sounds like you as you only part installed ArchLinux it messed up your Grub. I think that if you boot from the Ubuntu live disc and then select the install option a clean install should fix it.

---

### Post by kansasnoob on 2008-09-29
> Would any of you please tell me what would happen if I install Ubuntu from my CD-ROM? Would the GRUB-error be fixed if I did that?

Generally yes.

Will this be a single operating system installation? As opposed to dual boot?

---

### Post by NewsAndHistory on 2008-09-29
Yes. I want to dual-boot Ubuntu 8.04 with Windows XP Ultimate. Is that possible to do so even with my GRUB-error (which I caused by partly installing archlinux)?

> **OldGrey said:**
> It sounds like you as you only part installed ArchLinux it messed up your Grub. I think that if you boot from the Ubuntu live disc and then select the install option a clean install should fix it.

Is the Ubuntu Live Disc different than the ISO-disc, which is offered at the official Ubuntu Download page?
[COLOR=Red]
**I downloaded the following ISO from that page:**[/COLOR] **ubuntu-8.04.1-desktop-i386.iso**

---

### Post by OldGrey on 2008-09-29
Yes the ISO is the same. If you are going to dual boot with Windows. Install windows first. If you do it the other way around Windows will over right Grub.

---

### Post by kansasnoob on 2008-09-29
That should be fine. Just be sure it's burned as an ISO image.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Then when installing this part of the same guide is helpful:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by NewsAndHistory on 2008-09-29
I'll go to those web-pages. Thanks for helping me, again.

> **OldGrey said:**
> Yes the ISO is the same. If you are going to dual boot with Windows. Install windows first. If you do it the other way around Windows will over right Grub.
That's nice to know. Thanks. So, I'll follow your instructions, as well: I'll be installing Windows OS before installing Ubuntu.

:guitar: Problem solved!

---

