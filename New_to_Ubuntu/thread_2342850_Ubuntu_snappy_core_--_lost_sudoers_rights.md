---
title: "Ubuntu snappy core -- lost sudoers rights"
date: 2016-11-10
forum: New to Ubuntu
---

### Post by patdej on 2016-11-10
Hi,

I'm running a raspberry pi with Ubuntu snappy core 16.04. I made a mistake entering the command and I have no sudo rights for the ubuntu user anymore. I tried to boot via Grub holding down the SHIFT-Key. But that is not working. How can i get the sudo rights back for the ubunut user? Thanks!

---

### Post by RobGoss on 2016-11-10
Hello and welcome, This might help you with your login issue follow the instructions in this article [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by patdej on 2016-11-11
Thank you, but at the Boot time with Ubuntu snappy core holding Down the shift-key grub won't appear. Is there another possibility on snappy Ubuntu core?

---

### Post by ian-weisser on 2016-11-11
Can you describe exactly what mistake you made?

---

### Post by patdej on 2016-11-12
I did
"sudo usermod -G dialout Ubuntu"

That whas wrong, I had to do
"sudo usermod -aG dialout Ubuntu"

---

### Post by kingneutron on 2016-11-30
--I know of no easy way to fix this on a Pi without reinstalling the system, but it does make a good case for having "backup" admin-enabled users and enabling root login/password for emergencies... :(  

--On a regular PC, I would have recommended booting with System Rescue CD and doing a chroot, but Pi has no CDROM :(

--What did you do to fix this?

---

