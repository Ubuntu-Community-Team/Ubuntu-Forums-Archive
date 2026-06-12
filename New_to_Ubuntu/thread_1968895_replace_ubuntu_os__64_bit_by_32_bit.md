---
title: "replace ubuntu os  64 bit by 32 bit"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by hemoeshock on 2012-04-29
i have ubuntu 64 bit and windows in my laptop 
the problem is ubuntu hung a lot and crash.
is 64bit ok ?
if i want to remove ubuntu 64 and reinstall it but 32 can i do that without remove windows os ?

---

### Post by strask on 2012-04-29
As far as I know, the 64 bit version of ubuntu is just as stable as the 32 bit version... if you are having hangs and crashes, I don't think changing this will fix your problem. What kind of crashes are you having? What are you doing when it hangs? Can you provide any error messages? What version of ubuntu are you using, and what kind of laptop do you have?

But if you really want to replace your ubuntu with the 32 bit version, here's what to do:

1) BACK UP YOUR SYSTEM, both linux and windows, just in case.
2) Boot from a 32-bit install CD or USB. 
3) When install asks if you want to install with your other operating systems, replace your other operating systems, or something else, choose the "something else" option.
4) Carefully select your 64-bit linux partition and specify it as the place to install the 32-bit version. Tell it to format the partition. FORMATTING THE PARTITION WILL ERASE ALL YOUR LINUX DATA, so make sure you backed up your linux files first.
5) Proceed with the install. You should end up with 32-bit ubuntu and windows should remain as it was.

---

### Post by hemoeshock on 2012-04-29
when i try open apps it's not open and send a error msg report. i used the last ubuntu version.acer Aspire 4937 with intel centrino 2

---

### Post by mastablasta on 2012-04-29
mqybe the upgrade/install was bad. next what kind of GPU do you have? did you check for any additonal drivers?

lshw 

in terminal to get hardware data.

---

### Post by rgreener25 on 2012-04-29
yes you can just make sure that you backup the files you need on the ubuntu partition and on the installer AT THE PARTITIONING SECTION SELECT MANUALLY PARTITION HARD DRIVES AND MAKE SURE IT ONLY USES THE UBUNTU ONES LEAVE THE WINDOWS ONE UNTOUCHED

---

### Post by cotcot on 2012-04-29
This is not a 32 vs 64 bit problem.
Start your applications in terminal. This might give usefull error messages.
You can install linux after windows. The bootloader will recognize windows and allow you to choose it during startup.
Thing about having /home on a different partition. This makes reinstalling easier.

---

