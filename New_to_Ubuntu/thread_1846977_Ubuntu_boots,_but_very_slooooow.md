---
title: "Ubuntu boots, but very slooooow"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by conkermaniac on 2011-09-20
Hey there,

I posted a couple of weeks back about trying to dual boot Windows 7 and Ubuntu 11.04. I was having problems getting the Live CD to work because the Ubuntu installer refused to see my hard disk (actually, it's an SSD). I ended up using the alternate install with ACPI turned off in order to force the installer to recognize my SSD, but that caused all sorts of other issues.

Well, yesterday, in a moment of inspiration, I decided to turn ACPI off in my BIOS, and now the Live CD works! So if necessary, I can troubleshoot by booting from the Live CD. 

Anyway, my problem now is this: Ubuntu boots fine, but it's slow. And I don't mean ordinary slow. I mean *extremely* slow. As in, it takes half an hour to boot up the kernel from GRUB. And even once the kernel is booted, it responds to commands like molasses. (I'm operating from the terminal here.) For example:

```

login: ...

(2 minutes later)

Password: ...

(2 minutes later)

Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic x86_64)

```

During the booting process, I get several messages of the form: INFO: task so-and-so blocked for more than 120 seconds, and it hangs on "Checking battery state..." for a while before proceeding (I'm using a desktop.)

I should also mention that ACPI 2.0 and ACPI APIC Support are both disabled in my BIOS, and I am booting with the additional commands acpi=off noapic nolapic.

Any ideas what could be causing this or what I can do to troubleshoot? My specs are listed below, and I've attached the output from Boot Info Script (if that's of any use).

Specs:
[LIST]
[*] Asus M4N68T-M motherboard
[*] AMD64 Phenom II processor
[*] OCZ Agility 3 SATA III 2.5'' 120GB SSD
[*] Nvidia GeForce GTS450 graphics card
[*] Patriot Gaming i5 8GB RAM
[/LIST]

Thanks a bunch!

---

### Post by 7cardcha on 2011-09-20
Try using the WUBI installer. Not sure if that would help but it ure can't hurt.

---

### Post by conkermaniac on 2011-09-20
But running Wubi is not the same as dual booting...or am I missing something?

---

### Post by 7cardcha on 2011-09-20
Your right I was just suggesting it.

---

### Post by conkermaniac on 2011-09-20
Anyone else have any ideas?

---

### Post by wildmanne39 on 2011-09-20
Hi, did you try other options before turning acpi completely off? That can cause issue like sometimes your fans will not run with acpi off and other hardware.

Here is a link on nomodeset try it then if boot issues still occur post back.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

### Post by conkermaniac on 2011-09-21
Disabling ACPI is necessary to get Ubuntu to even recognize my hard disk. I've tried booting with nomodeset, it doesn't work.

---

