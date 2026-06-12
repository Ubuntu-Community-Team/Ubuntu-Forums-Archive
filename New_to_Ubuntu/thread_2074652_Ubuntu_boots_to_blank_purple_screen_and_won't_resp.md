---
title: "Ubuntu boots to blank purple screen and won't respond."
date: 2012-10-22
forum: New to Ubuntu
---

### Post by jerdub93 on 2012-10-22
I'm new to Ubuntu and I recently installed it on my PC. I logged in immediately after installing and it was working okay. I was told (in a beginners guide to Ubuntu) to update packages, so I opened the command line and typed "sudo apt-get update." Soon after, while I was messing around a bit, the screen froze (everything stopped responding, except for the mouse pointer). I force shut-down the computer, restarted, and tried to log on again. This time, before I even got to the login page, the computer displayed only a purple screen and wouldn't respond to anything. This happened two more times and I can't figure out how to fix it. Any suggestions?
EDIT: I forgot to mention it's version 12.10.

---

### Post by 2F4U on 2012-10-22
What is your hardware and graphics card, what graphics driver are you using? From your description it is not clear to me if the problem happens every time you boot or not.

---

### Post by grahammechanical on 2012-10-22
First of all, so that every new Ubuntu users knows, in 12.10 to simplest way to keep Ubuntu up to date is to go to the power menu and click About this computer. That will open the Details page of System Settings.

On the Details page you will see a panel that will say either:

a) System Up-To-Date
b) Checking updates
c) Install updates

or something like that.

Second, the command 'sudo apt-get update' does not update the OS. It does a comparison check between the computer and the repositories to identify which packages need to be updated.

For the update to take place we use the command 'sudo apt-get upgrade.' You do not say if you ran that command. Did you?

Thirdly, you say this:

> Soon after, while I was messing around a bit,

You do not tell us what you were doing? Could your messing around have caused the breakages?

Fourthly, Is 12.10 the only OS on this machine. Do you see a boot menu? If not try this:

> Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu.

Once you get what is called the Grub menu you can select Recovery mode. At the recovery mode screen select Resume. That might get you to a log in screen and from there to a desktop.

Takes notice of what happens. Any errors that you see will help others make a guess as to what the problem is.

Regards.

---

### Post by wildmanne39 on 2012-10-22
Hi, it is a bit unclear what all you did but sounds like you installed a graphics driver that is causing the problem you can boot recovery if possible and remove the driver or try nomodeset.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

