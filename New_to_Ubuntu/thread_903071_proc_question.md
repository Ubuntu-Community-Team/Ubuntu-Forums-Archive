---
title: "proc question"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by mike941 on 2008-08-27
As some of you may know the sound, battery monitor, suspend and hibernate features(among others) don't work on my latop. Is the only way to fix them to go into proc and change something?

---

### Post by phidia on 2008-08-27
Suspend-resume is frequently a acpi issue /etc/default/acpi-support is one place scripts and/or edits can be made. 
Are you booting with a kernel option like noapci? Also if you are using the propritary ati driver that could be causing resume issues too. 
There is the ubuntu laptop [testing wiki]("https://wiki.ubuntu.com/LaptopTestingTeam") but maybe the most help is this [here]("http://www.kalaj.org/blog/2008/05/23/solved-suspendresume-to-ram-on-ubuntukubuntu-hardy-heron-and-t60-with-ati-graphic-card/").

---

