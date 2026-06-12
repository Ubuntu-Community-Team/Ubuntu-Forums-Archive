---
title: "options specified in startup-manager are ignored"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by halfbeing on 2011-09-27
When I try to specify the default operating system in startup-manager my choice is ignored and the default when I boot up is always Linux, presumably because it is the first on the list. The same goes for the timeout time which stays at 10s even though I try to specify 8s.

The other week a friend of mine was trying to set up Linux Mint as his default OS and he ran into the same problem of not being able to set Windows as the default OS or to change Linux Mint's default behaviour of not displaying the Grub menu.

Anyone know what is going on?

---

### Post by oldos2er on 2011-09-27
Which version of Ubuntu are you using?

Startupmanager is no longer being developed; it's recommended to use Grub Customizer now. [https://launchpad.net/startup-manager/+announcement/8300](https://launchpad.net/startup-manager/+announcement/8300)

---

### Post by halfbeing on 2011-09-27
I'm using the latest Kubuntu 11.10 beta. It comes with no graphical tool to manage grub.

I ended up renaming /etc/grub.d/30_osprober to 05_osprober and running update-grub. This has put Windows to the top of the list of OS's and therefore made it the default.

I came across another serious issue too when I was installing and, for what my opinion is worth, I would say that Kubuntu is definitely not to be installed alongside other operating systems by any except very experienced users.

---

### Post by Mark Phelps on 2011-09-28
The startup-manager app no longer works properly since recent GRUB updates. You should switch over to Grub-Customizer.

---

### Post by oldos2er on 2011-09-28
> **halfbeing said:**
> I'm using the latest Kubuntu 11.10 beta. It comes with no graphical tool to manage grub.

I ended up renaming /etc/grub.d/30_osprober to 05_osprober and running update-grub. This has put Windows to the top of the list of OS's and therefore made it the default.

I came across another serious issue too when I was installing and, for what my opinion is worth, I would say that Kubuntu is definitely not to be installed alongside other operating systems by any except very experienced users.

You're using the beta, so hopefully you filed a bug for the serious issue.

---

### Post by Elfy on 2011-09-28
Thread moved to Ubuntu +1 (Oneiric Ocelot).

---

### Post by halfbeing on 2011-09-29
> **oldos2er said:**
> You're using the beta, so hopefully you filed a bug for the serious issue.

The issue is that the default installation option is to overwrite all partitions. Unfortunately this probably counts as a design decision rather than a bug, so there's probably not much point in a bug report.

---

### Post by cariboo on 2011-09-29
In order to set boot options, have a look at drs305's excellent [Grub2 GUide]("http://ubuntuforums.org/showthread.php?t=1195275")

---

