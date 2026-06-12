---
title: "Rootkits?"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by Foobarz on 2011-11-15
All right, so my friend and I were arguing that a Linux is more vulnerable to a virus because it does not implement the same security restrictions to the main system components, boot sector, and BIOS that a Windows does. I said that you can detect a virus easily unless you were dumb enough to make a weak sudo password. Even still, a sudo password has its limitations, so a hacked sudo does not guarantee system privileges to everything. Is this true?

---

### Post by Dangertux on 2011-11-15
> **Foobarz said:**
> All right, so my friend and I were arguing that a Linux is more vulnerable to a virus because it does not implement the same security restrictions to the main system components, boot sector, and BIOS that a Windows does. I said that you can detect a virus easily unless you were dumb enough to make a weak sudo password. Even still, a sudo password has its limitations, so a hacked sudo does not guarantee system privileges to everything. Is this true?

I'm not sure what exactly this has to do with rootkits.

Viruses and rootkits are not the same thing. By definition a virus is a self propogating piece of code, that may or may not do anything malicious in nature other than self propogate. A rootkit on the other hand is something entirely different, it is a hook or set of hooks (usually to the kernel, however under Windows lots of stuff gets hooked, Firewalls are pretty commonly hooked, as well as antivirus and windows logon.) designed to allow a malicious individual to maintain access to a system, either by harvesting credentials, creating a backdoor , or any combination of the two and anything else that can allow someone to have continued access to a compromised machine. 

As far as detecting a virus easily, it depends, if the virus is well profiled, meaning the AV vendor has a valid signature than yes it is easily detected. Since you probably don't run AV you may be able to detect a virus easily if you religiously audit your logs.

A rootkit is something entirely different again, its designed not to be detected, and the likelyhood of you detecting an unsignatured rootkit (on either Windows or Linux) is EXTREMELY unlikely as an average end user. Now of course if you want to sit there with unhide and a debugger hooked up to your kernel, sure you might notice some pretty suspicious activities, however removing a root kit is a royal PITA that is best reserved for systems where it ABSOLUTELY needs to be removed, as opposed to just a reinstall.

BIOS rootkits : these fall under the same category as the hypervisor rootkit boogie men of the world. While they do exist they are highly targeted, and unlikely to affect you. 

Bootkits && Boot sector malware : Generally small pieces of code, not the full payload, designed to grab the remainder of a payload in order to bypass AV and survive a reboot, these are detectable relatively easy with live media based anti-malware tools.


As far as the "strong sudo password" deal goes, remember you can be keylogged without root permissions, so in the case of a compromised linux box, you would likely be keylogged when you entered your sudo pasword if your machine was compromised. Additionally some forms of compromise, SSH bruteforce have your sudo password at the same time they have your authentication credentials. Sudo and UAC are not the end all be all.
Hope this helps.

---

### Post by Foobarz on 2011-11-15
Could a rootkit keylog the sudo password and install itself?

---

### Post by Kaboom3009 on 2011-11-15
> **Dangertux said:**
> ...

A rootkit is something entirely different again, its designed not to be detected, and the likelyhood of you detecting an unsignatured rootkit (on either Windows or Linux) is EXTREMELY unlikely as an average end user. Now of course if you want to sit there with unhide and a debugger hooked up to your kernel, sure you might notice some pretty suspicious activities, however removing a root kit is a royal PITA that is best reserved for systems where it ABSOLUTELY needs to be removed, as opposed to just a reinstall.

....

I spent 2 weeks removing a rootkit and I still cant install Windows because of it. I spent over 100 hours just getting any version  of Linux to install. I finally had to use an Archaic partition manager to finally remove the main  rootkit install to allow an OLD version of Linux to repartition the drive to allow Ubuntu 11.10 to REpartition the drive which then allowed the software to install. 

It doesn't matter WHAT OS you run what matters is who is writing code that is trying to access a system and WHAT OS they are expecting to find there. How many power users of Linux could slap a script  together that would fix someones troubles and give them access to that persons linux because they felt the other person wasnt using it the way they think they should ? ANY OS can be hacked in anyway .. it's JUST how many people are using that OS that determines who is programming for it and why they want it. MAC and Windows are the most common OS around so you hear alot about  virus and other things; ONCE Linux is more widely used you will see and hear more about people being hacked and getting viruses and so on. The real trouble will be the first power users that get smacked because they say "Linux doesnt have any known viruses"  when the answer is Linux doesnt have any known viruses YET.

---

### Post by Foobarz on 2011-11-15
Oh my, so a rootkit can affect manifest itself on the hard drive and take complete access!?

---

### Post by Dangertux on 2011-11-16
By definition a rootkit is a kit designed to maintain root access. If you need proof or just want to learn more about rootkits, how they are installed, how they affect Ubuntu I put together two articles recently about an older, but still useable rootkit that circulates in the wild from time to time (in fact its strikingly similar to the one found on the kernel.org servers)

here : [http://dangertux.wordpress.com/2011/09/27/a-look-at-root-kits-as-they-apply-to-ubuntu/](http://dangertux.wordpress.com/2011/09/27/a-look-at-root-kits-as-they-apply-to-ubuntu/)
and here : [http://dangertux.wordpress.com/2011/11/08/umm-yeah-so-i-think-i-got-owned/](http://dangertux.wordpress.com/2011/11/08/umm-yeah-so-i-think-i-got-owned/)

Hope this helps.

---

### Post by SheaMan on 2011-11-16
[quote=Kaboom3009, edited]
It doesn't matter *what* OS you run what matters is who is writing (the) code  that is trying to access a system and *what* OS they are expecting to find  there.
[/quote]

Exactly. :guitar:

---

### Post by lolpenguin on 2011-11-16
A rootkit hides itself in the system directories and hijacks OS calls made by AV utilities to give a false negative. Removing rootkits usually requires the computer to be booted into safe mode.
You really don't have to worry about malware in GNU/Linux, because, UNIX being a hostile environment for malware due to the superuser required to actually *do* much. As a precaution, scan downloaded executables with a virus scanner (ClamAV is great) before you run them.

---

### Post by Dangertux on 2011-11-16
> **lolpenguin said:**
> A rootkit hides itself in the system directories and hijacks OS calls made by AV utilities to give a false negative. Removing rootkits usually requires the computer to be booted into safe mode.
You really don't have to worry about malware in GNU/Linux, because, UNIX being a hostile environment for malware due to the superuser required to actually *do* much. As a precaution, scan downloaded executables with a virus scanner (ClamAV is great) before you run them.

That's not necessarily true. If an unprivileged user has access to a compiler and privileges to execute code (which by  default they do) than they can escalate.

---

