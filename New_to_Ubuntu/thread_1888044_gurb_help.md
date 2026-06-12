---
title: "gurb help"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-11-28
okay really messed up installed linux mint on its own partition. every was fine. then i wanted to tweak the grub menu so ubuntu preceeded linux mint.
i used the program startup up manager while in mint. now grub menu doesnt display and machine boots directly into ubuntu. best way to fix. have tried live cd to fix but to no avail. tks

---

### Post by rburkartjo on 2011-11-28
note when i installed mint i set the "/" to the linux mint partition. get lot of error messages but can still get into ubuntu.

---

### Post by drs305 on 2011-11-28
Did Mint work properly after installing it? Normally Grub 2 will only boot without displaying the menu if it doesn't detect another OS. You might run "sudo update-grub" from your working installation to see if Grub finds the second OS.

I'd recommend installing Boot Repair and allow it to try to fix things. If it doesn't fix the problem, it has an option to run the boot info script. Let it do so and post the link for the RESULTS.txt it generates.

Once you get the system booting, use Grub Customizer to tweak things. StartUp-Manager was good for Grub legacy but not so much for Grub 2. GC was designed for Grub 2 and can safely accomplish a large variety of tweaks.

Both apps are linked in my signature line: "Boot Repair" and "Customizer"

Edit: I can change 'gurb' to 'grub' in the thread title if you would like.

---

### Post by rburkartjo on 2011-11-28
drs already tried the sudo update-grub and didnt work. will try runnin the program you suggested. tks for your speedy reply.

---

### Post by Shmook on 2011-11-28
Easiest solution: download and burn to cd: [boot-repair-disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/") and choose the first "recommended" action to get things back to normal.

---

### Post by rburkartjo on 2011-11-28
cant find the program boot repair in software center or spm.

---

### Post by rburkartjo on 2011-11-28
okay i found it online.

is this right one
[http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html](http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html)

---

### Post by drs305 on 2011-11-28
> **rburkartjo said:**
> cant find the program boot repair in software center or spm.

Go to the link I suggested in my signature line. You have to enable a ppa. There are two commands, one to add the repository and then the next to install the app; the creator combines it all into one line in the first post.

---

### Post by rburkartjo on 2011-11-28
drs installed the program ran repair and gurb was fixed. thanks a millon!!

---

### Post by drs305 on 2011-11-28
> **rburkartjo said:**
> drs installed the program ran repair and gurb was fixed. thanks a millon!!

Great!  :-)

If you don't have any other issues with this, please mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post.

Happy Ubuntu-ing.

---

