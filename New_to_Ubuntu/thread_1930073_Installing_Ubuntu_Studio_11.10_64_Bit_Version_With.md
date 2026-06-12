---
title: "Installing Ubuntu Studio 11.10 64 Bit Version With 2 Seperate HDD's"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by xAGENTP6x on 2012-02-23
I need some help installing ubuntu studio

I had previously installed regular ubuntu 11.10, then overwrote that now with studio 11.10.
The install UI is completely different for this and im stuck on a certain option, which ill get to in a second.

My first HDD has Windows 7 and A bunch of valuable software that i dont want to mess with at all. That whole HDD is off limits for ubuntu. I want this to be my default operating system to be booted.
My second HDD however, is going to be fully dedicated to ubuntu. I want to be able to only access ubuntu by accessing my bios boot menu and choosing that HDD to boot from

Now back to my problem. In the ubuntu installation menus, ive encoutered an option about how to configure the Ubuntu OS and my master Boot Record. Which option do i choose in this menu to make it so that everything in regards to booting remains the same, with windows as my primary OS, and i access ubuntu only through bios boot menu?

Thanx in advance :)

---

### Post by cariboo on 2012-02-24
You shouldn't have any problems installing grub on /dev/sda, but if you'd rather do it by booting from the bios, put grub on the same drive you install Ubuntu on, in this case it would be /dev/sdb.

---

### Post by HeroOfCanton on 2012-02-24
Another option, unless you are hiding linux for a reason, is to make windows your default selection in grub and set the timer to only a couple of seconds. Unless you are sitting and ready to boot to linux it will just switch quickly to windows, but still easier than changing the boot order each time.

---

