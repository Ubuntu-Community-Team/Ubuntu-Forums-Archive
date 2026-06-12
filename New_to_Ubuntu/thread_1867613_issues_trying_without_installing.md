---
title: "issues trying without installing"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by aloevera on 2011-10-23
Hi there,
I'm new here and I'm looking for some help with Lubuntu. I'm an absolute absolute Ubuntu beginner and no computer whiz ;)

The thing is, I have this 2005 HP laptop (Pavillion dv1250 - don't seem to be able to find the specs anywhere. It used to have 512Mb RAM, I brought it to 1Gb) that my brother-in-law had been using so far, which now I'd use just to check my emails or browse the internet when I'm in bed/sick/tired etc. 
I'm currently running Ubuntu 11.10, but the machine (probably due to the poor specs) tends to be laggy and often overheats. So I've been told to try Lubuntu. I downloaded the ISO and burned the DVD, I rebooted my computer and it prompted the installation screen. I chose *Try Lubuntu without installing*, the loading screen with dots appeared and then got to a black screen with this text:

> Loading the saved-state of the serial devices..
*Starting NTP server ntpd [OK]
*Starting bluetooth [OK]
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic i686)
*Documentation: https//help.ubuntu.com

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$

What should I do? Every time I tried a new distro (tried Kubuntu and Xubuntu too), I'd get to the desktop without issues. What about now? I created the DVD several times, both with 11.10 and 11.04 (as for 11.10, I couldn't check the hashes), nothing worked for me.

Any help is appreciated. 
Thanks in advance from Italy!

---

### Post by ajgreeny on 2011-10-23
I had the same problem with an old laptop of mine.

What you have arrived at is a live command line system, logged in as the live user, but with no GUI (LXDE).

You need to type the command ```
sudo lxdm start
```at the cli prompt you see (ubuntu@ubuntu:~$) which should then startup the lubuntu desktop for you.

I have tried to search for this as a bug but so far without luck, and in fact it only happened on my laptop;  my desktop machine started in LXDE as expected, and an installation from that live CD which I have put on that desktop also starts in GUI.

Incidentally both the md5sum for the iso file and the subsequent burn to CD were good, having been checked before trying the live session.

Another anomaly is that if I use the command ```
startx
``` at the prompt it gives me a standard LXDE desktop, not the Lubuntu desktop, which obviously requires lxdm started to get it up and running.

EDIT:  I have just tried again this morning, twice.

The first boot to live CD went to the command line, and I started lubuntu as I said above, the second boot to live CD (a complete shutdown and reboot) managed to get to the Lubuntu desktop all buy itself, so perhaps my supposition that it is a one time glitch is true.

---

### Post by aloevera on 2011-10-23
Looks like it's working now! Thank you very much!! :KS

---

