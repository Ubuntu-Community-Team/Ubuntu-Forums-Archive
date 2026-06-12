---
title: "Old DELL P3 Latitude CPx"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by dristan24 on 2008-11-16
This is my first venture into Linux territory, and I am failing miserably so far. I am trying to install Ubuntu v8.10 on a 6GB Linux ext3 partition, on this older laptop, but it keeps generating errors, and the install continually fails. I was told that unlike an MS Windows XP\Vista install, the hardware requirements are minimal. Any thoughts on where I am going wrong?

[SIZE="3"]This is a sample of what is on the screen;[/SIZE]

[  497.388518] aufs au_xino_do_write:280:S99acpi-support[7268]: I/O Error, write failed (-5)

[  497.412542] aufs au_xino_do_write:242:S99acpi-support[7270]: I/O Error, write failed (-28)

[  497.412626] aufs au_xino_do_write:280:S99acpi-support[7270]: I/O Error, write failed (-5)

[  497.436779] aufs au_xino_do_write:242:S99acpi-support[7272]: I/O Error, write failed (-28)

[  497.436863] aufs au_xino_do_write:280:S99acpi-support[7272]: I/O Error, write failed (-5)

Linux Ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686

**[SIZE="3"]The system is:[/SIZE]**

Dell Latitude CPx PIII
128MB of RAM
6GB Hard Drive

---

### Post by chrisod on 2008-11-16
What version of Ubuntu are you trying to install? Standard Ubuntu with the Gnome desktop ain't gonna happen with 128MB of memory. 256MB is the minimum with the alternate installer, 384MB with the Live CD/DVD. You could try Xbuntu, which is designed to be less resource intensive. It's Ubuntu with a lightweight GUI. You also might try Puppy Linux, with is based on Ubuntu and designed for really minimal environments.

---

### Post by snowpine on 2008-11-19
Hi Dristan,
My first Linux computer was a Dell Latitude Cpx, just like yours! So hopefully I can help you out.

The first thing you need to do is upgrade your ram. Very few Linux distros will run well with only 128mb. The Cpx maxes out at 512mb; that would be my recommendation.

Next, you need to choose an appropriate distro for older hardware. Ubuntu/Xubuntu will install with 512mb of ram, but is one of the slower options. The best performance I've found on my Cpx is SliTaz linux; very highly recommended! I've also had pretty good luck with Debian Etch and Sidux Xfce. The only Ubuntu-based distro I've tried that ran well on the Cpx is Crunchbang. It is slow to boot (about 2 1/2 minutes) but runs well once it gets going.


Rehabilitating old hardware is lots of fun, but there can be a lot of trial and error. Please ask me if you have any questions, maybe I can save you some time. :)

---

