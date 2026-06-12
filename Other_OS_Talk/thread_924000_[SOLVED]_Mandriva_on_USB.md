---
title: "[SOLVED] Mandriva on USB"
date: 2008-09-19
forum: Other OS Talk
---

### Post by YldGuy on 2008-09-19
hi,

I was planning to install mandriva on a USB stick so wanted to know few things about it.

1) Does the latest Spring 2008 live CD allow install to USB in persistent mode? or do i need to install the ISO to USB myself?

2) Is Mandriva on USB fast enough compared to slax? I was looking at slax and this one looked appealing.. less resource hungry and minimalistic KDE menu (i like GNOME).

any ideas?

---

### Post by pelle.k on 2008-09-19
There is a mandriva sub-forum you know...

1) I'm not quite sure what you mean? I installed mandriva to a 2.5" USB HD though. It's a bit finicky, but it can be done.
In a nutshell, you may have to adjust grubs own hd0/1 syntax to match the drives location (hd0/1/2) upon actually booting from it. But as long as you use UUIDs things should work fine.
You may, or may not, have to adjust fstab since what was considered sdb upon installation, may be sda when booting from it. As I said, finicky.
2) Mandrivas kde is nowhere as fast as the slax kde. Not many are. But it's not as sluggish as kubuntus kde. I find it to be fast enough though.

---

### Post by wolfen69 on 2008-09-21
check out [Mcnlive]("http://www.mcnlive.org/"). it is mandriva made especially for usb.

---

