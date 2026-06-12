---
title: "[SOLVED] Problems running Ubuntu; Hardware Requirements?"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by deanium on 2008-09-18
Hey,

I have a fully functional Ubuntu cd (which I've used on a previous computer). My problem is that with my current PC (Advent 9315 Laptop) I am unable to run it. When attempting to run it (in live mode, loading it to install it, or even booting it after installing it from within windows) it hangs when loading. I get as far as the graphical "Ubuntu" and the progress-style bar bellow. The bar stops and the PC then has to be cold-rebooted in order to reboot to windows.

I would assuming my hardware was the problem, however I can't see how. Does ubuntu have any specific hardware requirements or restrictions?

My Laptop system is:

Intel C2D @ 1.5GHz
2.0GB RAM
SiS Mirage 3 (~184MB)
Currently Running WinVista Home Prem x86.
Don't know about MoBo etc. as it's a high-street retailer job.


If anyone can shed some light, and even cure my problem I'd be so grateful, as I LOVE ubuntu, and would LOVE to Dual Boot it!

Thank you in advance,
Dean

---

### Post by Tatty on 2008-09-18
First thing to check in this situation is your CD.  Boot to the first menu then run an integrity check.

---

### Post by pytheas22 on 2008-09-18
Your hardware is not the problem.  You have many times the memory and CPU required to run Ubuntu reliably.

Try booting to the installation on your hard drive.  As soon as the orange bar appears, press control-alt-F1, which should bring you to a screen where you can see verbose information regarding the loading process.  Do you see anything that looks like an error?  What's the last message printed on the screen before it hangs?

You might also want to try installing using the alternative CD, which you can download from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box that says "I need the alternative CD" (or something approximating that).  There's a good chance that the alternative installer will work better.

---

### Post by phidia on 2008-09-18
This sounds like it could be a video problem. See if you can open a commandline window when it stalls (Alt+Ctrl+F1) and try either "xfix" or "sudo dpkg-reconfigure xserver-xorg".

---

### Post by jemate18 on 2008-09-18
> **deanium said:**
> Hey,

I have a fully functional Ubuntu cd (which I've used on a previous computer). My problem is that with my current PC (Advent 9315 Laptop) I am unable to run it. When attempting to run it (in live mode, loading it to install it, or even booting it after installing it from within windows) it hangs when loading. I get as far as the graphical "Ubuntu" and the progress-style bar bellow. The bar stops and the PC then has to be cold-rebooted in order to reboot to windows.

I would assuming my hardware was the problem, however I can't see how. Does ubuntu have any specific hardware requirements or restrictions?

My Laptop system is:

Intel C2D @ 1.5GHz
2.0GB RAM
SiS Mirage 3 (~184MB)
Currently Running WinVista Home Prem x86.
Don't know about MoBo etc. as it's a high-street retailer job.


If anyone can shed some light, and even cure my problem I'd be so grateful, as I LOVE ubuntu, and would LOVE to Dual Boot it!

Thank you in advance,
Dean

If the CD integrity fails, download a new one from another mirror and then burn it in a slow speed.

Your hardware specs is GOOD and well OVER the minimum specs to run ubuntu

---

### Post by haydnc on 2008-09-18
I've had a similar problem on one of my laptops. All I had to do was change the boot options to turn apci off (I think that's what it's called).

There's actually a boot option on the live CD gui but I think you can just put noapci in there manually too.

That was all it took for me.

Sorry I'm a bit vague on details, it was a while ago.

---

### Post by deanium on 2008-09-18
Right well I'm not able to access the command-line bit (Ctrl+Alt+F1) as I don't seem to have enough time between the kernel loading and the graphics appearing (and hanging).

I did try an CD integrity check thingy, and again it froze.

I'll try that noapci thing, but I can't see it actually being the disc as I'm using a proper Ubuntu disc (not burnt myself).

---

### Post by deanium on 2008-09-18
Right under Other Options I've tried the following:
ACPI = OFF : Blank Command-Line Screen, and CD stopped spinning.
NOAPIC : Graphics (Ubuntu logo and Orange bar) w/ hang, and CD stopped.
NOLAPIC : Blank Command-Line Screen, and CD stopped spinning.

I also tried under Alternate Startup/Install Options:
Safe Graphics Mode : Graphics w/ hang, and CD stopped.

I still can't get to this command-line view of the hang, as by time I see the orange bar (and logo) it's frozen.

---

### Post by pytheas22 on 2008-09-18
I think using the alternate CD is the next thing to try.  If the problems are arising from something graphical, the alternate installer should help.

---

### Post by haydnc on 2008-09-18
I found one post that suggests you're not alone and the Advent 9315 Laptop has issues running Linux.

It suggests that you need to boot in "Safe graphics" mode with both the noapic and acpi=off options selected. If that still fails try booting into "recovery" mode with the same options selected (noapic and acpi=off).

I don't know if that'll help but hopefully you'll at least be able to boot. It sucks when your laptop does not play well with Linux - I know, I've been there a time or two myself.

---

### Post by deanium on 2008-09-18
OK I managed to run it from the "Instal within Windows" installation by selecting (from the esc menu) "acpi workaround" method. It then configured all nice-nice, and now boots fine, except for some "bios error"... or something along those lines, but it doesn't stop the boot. It does mention something about running linux with a certain script... or something, but I have no idea how, nor is it that big of a problem.

Cheers for your help people.:D

---

