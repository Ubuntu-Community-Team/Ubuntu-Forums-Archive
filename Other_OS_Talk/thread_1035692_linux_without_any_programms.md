---
title: "linux without any programms"
date: 2009-01-10
forum: Other OS Talk
---

### Post by honkey on 2009-01-10
Did anybody of you know if there is a linux distri without any programms?
I heard something of arch-linux. 
Is arch linux good for me?
I work since 1 or 2 years with ubuntu now but i think I dont need all these programs or I have better ones for them.

---

### Post by Peter09 on 2009-01-10
Do you mean the server version which comes with no GUI and just the necessary support programs.

---

### Post by sisco311 on 2009-01-10
You can use the alternate cd to setup a command line system and then install the x server and your prefered applications.
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

If you want to try arch the wiki and the beginners guide is an exellent resource for information:
[http://wiki.archlinux.org/index.php/Arch_Linux]("http://wiki.archlinux.org/index.php/Arch_Linux")
[http://wiki.archlinux.org/index.php/Beginners_Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide")

---

### Post by ugm6hr on 2009-01-10
I think you misunderstand the way that the OS works.

It is entirely possible to install any distro without default applications.

Arch is designed to be configured from the base up.

However, Ubuntu can also be installed that way too:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

---

### Post by cardinals_fan on 2009-01-10
What do you define as a "program"?  If you mean graphical apps, almost any distro can be installed with just a command line.  Arch is a good distro for someone newish to this category of distros.  If, however, you mean all software not directly related to the Linux kernel, you want LFS (Linux From Scratch).  This lets you create your own distribution using the Linux kernel.  It is quite an experience and is not for the faint of heart.

---

### Post by gjoellee on 2009-01-10
If you have a Linux without programs you would just have a bootable computer that does nothing else then using electricity.

However you have a distribution called Arch Linux that comes without a GUI (Graphical User Interface) and you can self decide what to install.

You have Slackware as well, but it is however "harder" to use then Arch Linux which is "harder" to use then Ubuntu.

You can also try installing a Ubuntu Minimal CD (Install command Line). That will give you the basics of a Ubuntu system, and you can self decide what to install later (NOTE: Ubuntu Minimal install is not anything near as flexible as Arch or Slackware are)

---

### Post by cmay on 2009-01-10
what i do is a debian netinstall. that way i can decide what and what not to be isntalled. i start from scratch whit xorg and then from there i alwasys as i love gnome desktop install that. but i can choose more free what should be installed and as example i always remove gnome.games from all distros. and i always install geany and build essentials. the netinstall cd lets me choose what desktop and what programsw to use. that could be lxde ,jwm ,open-box or something lighter than gnome also.

---

### Post by fistfullofroses on 2009-01-11
Umm, an OS is just a collection of programs on top of a kernel, HAL, and API... but anyway, beyond the technical, I did understand your question. You can do this. Debian has netinstall, Ubuntu has Ubuntu minimal, and then there are Arch, Slackware, Draco, and a host of others that always have this in mind. You can install from the ground up, but I do not recommend it. You will end up with this or that missing, and eventually get so frustrated you just "apt-get install ubuntu-desktop"

However, if you really truly feel that this is what you want to do, research each package you are going to install. Make sure that you grab all the deps, and needed libs for what you want the program to do. This will save you a lot of headache in the future.

---

