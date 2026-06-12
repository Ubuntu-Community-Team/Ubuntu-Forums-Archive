---
title: "Weird Vertical colored lines on boot up!"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by mrdosa on 2008-05-01
I use Ubuntu 7.10
This problem has been recurring for quite a while now. Out every approx., 30 boots, I get weird vertical colored lines, and everything comes to a standstill...this happens immediately after boot up, after the ubuntu icon closes...
I then have to perform a hard restart, and the next boot up goes well..
Can any one explain whats going on?
I have a P4 2.8Gigs
intel i845g 
I have not attached any graphic card.
Thanks!

---

### Post by mk4umha on 2008-05-04
I get the same thing with my D630, after 10 hard power shutdowns it usually gets into the login manager OK, very annoying.

---

### Post by reg2117 on 2008-05-06
I have been experiencing the same problem intermittently.
Running Kubuntu 7.10
with the following hardware:
processor   Intel(R) Pentium(R) 4 CPU 2.80GHz
memory      8KB L1 cache
memory      512KB L2 cache
bridge      82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
display     82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device


I followed the advice at the following link:

[[COLOR="RoyalBlue"]Problem with Kubuntu startup[/COLOR]]("http://ubuntuforums.org/showthread.php?t=110195")

> Try to start in recovery-mode (press escape when grub loads!)

Then run "sudo dpkg-reconfigure xserver-xorg", and choose the right resolution! (It asks a lot of other questions, but the "right" answer is those per default!)

The next boot went right to the login, but it is unclear whether the reconfiguration worked or if the reboot cleared the problem.

*Note: I could not find the file ~/.kde/config/kcmrandrrc to play with the startup settings. Is there a similar file in kde 3?*

---

