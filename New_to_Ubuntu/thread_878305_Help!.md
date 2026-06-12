---
title: "Help!"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by c-man01 on 2008-08-02
I have a problem.  Every time I start up Ubuntu, It freezes up on me.  The startup screen comes up and it starts to load but then it freezes on me and I have to restart the computer.  I'm not sure what to do.

---

### Post by jamesrfla on 2008-08-02
Are you using a SATA hard drive? Dose it freeze up after you login?

---

### Post by c-man01 on 2008-08-02
No I can't even get to the login screen.

---

### Post by hubie on 2008-08-02
When it freezes can you get to a non-GUI TTY by hitting CTRL-ALT-F1 (or F2, F3, etc.)?

---

### Post by c-man01 on 2008-08-02
I'll try that thanks!

---

### Post by c-man01 on 2008-08-02
It won't let me do anything.  It is completely locked up.

---

### Post by sdowney717 on 2008-08-02
at the grub menu when it first boots, does it have a recovery option?
try that and it might have an option like xfix or fix x.

I was wondering if it is a video issue.

or if all you can get it a command prompt type this in and then restart.
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Polish Rifle on 2008-08-02
I actually helped C-man install Ubuntu and after he selects Ubuntu in Grub it shows the Ubuntu logo with the load bar.  The load bar gets about an 1/8th loaded and the system freezes.  

I haven no idea how to solve this problem.

---

### Post by Polish Rifle on 2008-08-02
Report:  I guess Ubuntu starts 1 out of every 10 times for him.

---

### Post by jamesrfla on 2008-08-03
When he boots and get the options for booting Ubuntu he need to press F6 twice and add select acpi=off, noapic, and nolapic. Just hit enter to select them and then press Esc or b. Then try booting Ubuntu.

---

### Post by gjoellee on 2008-08-03
this may be the last kernel for pre released kernel for Hardy....kernel 2.6.24-20, it seams like this never should have been released yet...use one other kernel if that is your problem

---

