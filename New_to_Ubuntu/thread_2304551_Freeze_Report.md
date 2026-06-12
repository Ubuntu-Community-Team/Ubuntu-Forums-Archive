---
title: "Freeze Report"
date: 2015-11-27
forum: New to Ubuntu
---

### Post by james173 on 2015-11-27
Hello,
I am new to ubuntu.
I am using a Lenovo think pad. ubuntu 15.10. I get regular (once a day or so) freezes where the system is completely unresponsive. There seems to be no pattern to the tasks i am undertaking that causes the freeze. 
My question is can someone point me in the direction of finding the cause. I am sure there is information out there but its quite overwhelming the various option. 
Worth noting is that i am quite comfortable on the terminal and have used linux in the past but never ubuntu. 
Thanks
James

---

### Post by matt_symes on 2015-11-27
Hi

It could be anything causing the freezes.

First thing i would do is cut the problem in half.

Is it a software or hardware fault ?

Hardware: Are the drives, memory and temps fine before the freeze ? Have you checked them ?

Software: Is it the kernel freezing or X ?

X: Can you get to a different console and restart X ?

Kernel: Can you use the magic key combination to reboot ?

Kernel: Are any of the keyboard LEDs flashing ? If so the which ones ?

General: Can you ssh into the PC from another box or smart phone ? Will require installing openssh-server so use standard precautions.

If software, once you have identified what is freezing, interrogate the appropriate logs to look for clues.

That's where i would start.

Kind regards

---

### Post by buzzingrobot on 2015-11-28
Overheating can cause that. Each time the machine locks up, has it been in use approximately the same amount of time?

What's the specific ThinkPad model and what kind of video card is in use?

What happens to the display?  Does it remain the same, or is it distorted, or does it vanish (go black)?

When the system freezes, what do you do to get out if it?

---

### Post by madmetal on 2015-12-19
I have the same problem on ASUS F571M after upgrading to 15.10 and I have reported the bug here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518566](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518566)
It seems that there is a freezing random bug as some more people report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1514233/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1514233/)
Give a look to the bug reports to see if they are matching and also follow some steps mentioned, like run  ubuntu-bug linux in order to report any bugs. 

ps. Freezes are too annoying and I am thinking to downgrade to 15.04 :/

---

### Post by RobGoss on 2015-12-20
Hello and welcome, I think the first thing you need to do is provide us with the specs for the machine in question it will help others help you ...

---

