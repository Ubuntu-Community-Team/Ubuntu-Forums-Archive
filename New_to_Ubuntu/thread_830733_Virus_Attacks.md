---
title: "Virus Attacks"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by jotnarta on 2008-06-16
Hi
Isn't true that Ubuntu and Linux based Operation System can't be attack by viruses? and if yes, why?

Thanks
Jotnarta

---

### Post by iaculallad on 2008-06-16
No. Because, like windoze - not all Operating System are full proof. Each has its own vulnerability. But the fact that Ubuntu (Linux in general) is Open Source, it has a lower risk of being infected or "hacked" due to the fact that "bugs" are detected and reported right away, patches are created and ready for user download/auto-installation on updates.

---

### Post by nothingspecial on 2008-06-16
Also, unlike windows you need to be root to do anything to your system. If the virus hasn`t got your password it can`t do anything.

---

### Post by nvteighen on 2008-06-16
GNU/Linux systems are can be vulnerable to rootkits (but Windows and Macs also are) and other cracker attacks. To protect yourself, don't open ports (which is the default in Ubuntu, so relax!) or, if you open them, configure your firewall.

Other issues are related to application security-flaws. But those are easily patched through updates and are not the OS's fault (the same goes for Windows and Macs again...).

Mainly, a great protection is not to run anything with sudo if you don't really know if it actually needs root privileges. If you're beginning with Ubuntu, it's always safe to type the command **without** sudo at the first time, see if it worked or not and only if it didn't work because it needed more privileges, run it with sudo. (After some time, you'll have experience on what things need sudo and which not... and you'll have no need to do that sort of checks).

---

### Post by skymera on 2008-06-16
> **nothingspecial said:**
> Also, unlike windows you need to be root to do anything to your system. If the virus hasn`t got your password it can`t do anything.

That is the most important thing.

If you do download a malicious file, god knows why, dont sudo it.
Dont even run stuff without checking the file.

---

### Post by hyper_ch on 2008-06-16
Have a read here:  [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

