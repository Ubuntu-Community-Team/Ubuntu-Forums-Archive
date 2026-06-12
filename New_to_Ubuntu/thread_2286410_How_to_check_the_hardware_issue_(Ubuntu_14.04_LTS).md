---
title: "How to check the hardware issue (Ubuntu 14.04 LTS)"
date: 2015-07-11
forum: New to Ubuntu
---

### Post by wtkmichael on 2015-07-11
Some times my desktop (Ubuntu 14.04 LTS)  itself restart. 
Is there any software/program that can help to identity the hardware  (hard disk, graphic card, RAM,powersupply or motherboard) issue or problem ? So that I can know which part to be replaced.
Thank you.

---

### Post by dino99 on 2015-07-12
as it is a random issue, maybe think about temperature over hitting: is that system dusty (clean the fans); is that system overclocked ? (set back the genuine settings)

ubuntu always logs the system events: glance at Xorg.0.log inside your /home, and/or inside /var/log/ (mainly dmesg & syslog)

---

### Post by coldraven on 2015-07-12
You could look at the temperatures and see if they are getting too high. 
See here: [URL="https://help.ubuntu.com/community/SensorInstallHowto"]https://help.ubuntu.com/community/SensorInstallHowto
[/URL][http://askubuntu.com/questions/15832/how-do-i-get-the-cpu-temperature](http://askubuntu.com/questions/15832/how-do-i-get-the-cpu-temperature)

---

