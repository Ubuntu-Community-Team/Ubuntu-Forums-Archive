---
title: "how to install Ubuntu from the Windows Startup Screen?"
date: 2015-05-14
forum: New to Ubuntu
---

### Post by owen8 on 2015-05-14
I had an old unused laptop and I decided to try and install ubuntu in it  
but the thing is that it was in this startup loop thing running on windows 7
So basically I can't open Windows 7 , but the thing before windows launches looks fine
Is there a way to install it without going to windows?

I'm new with Ubuntu so I'm sorry if this is obvious , or not clear enough but I can provide more information

---

### Post by kagashe on 2015-05-14
You need to have Ubuntu on DVD or USB stick and you should set the Boot priority in the BIOS to boot from the DVD/USB stick before hard disk.

Kamalakar

---

### Post by newb85 on 2015-05-15
> **owen8 said:**
> 
Is there a way to install it without going to windows?

Yes, that's actually the preferred method.  It's possible to run Ubuntu in VM software from inside Windows, but that means your machine has to run both platforms.

How old is the laptop, and what are the specs?  Some older machines aren't powerful enough to run regular Ubuntu, and need a lighter variant, like Lubuntu.  The nice thing is you can test it out without installing, because the install media has a "Try Ubuntu" option, where you can run from the install media.

Another important question is whether or not you wish to preserve Windows.  Ubuntu installs on it's own HDD partition (ext4 format), so if you keep Windows, you'll need to at least shrink it's partition to make room (or get another HDD).  If you want to do away with Windows (if for example, you have another machine you use as your primary, and this is an extra), it makes installing Ubuntu simpler, because the installer can simply reformat the entire HDD.

There are plenty of instructions out there for installing Ubuntu.  Just make sure you're not using the Windows Ubuntu installer, a.k.a. Wubi (which isn't supported anymore, and would require you to install from within Windows).  Installing from a USB will be faster than a CD/DVD, assuming your BIOS will support booting from a USB.  If you have any questions, this is a great place for them!

---

