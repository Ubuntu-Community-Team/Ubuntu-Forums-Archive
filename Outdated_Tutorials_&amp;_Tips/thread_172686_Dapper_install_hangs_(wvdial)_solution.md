---
title: "Dapper install hangs (wvdial) solution"
date: 2006-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by skippy81 on 2006-05-09
Not really a guide, but I wanted to post this so forum searchers can find a quick solution to something that took me a while to work out and broke my system for a few hours. There are references and bug reports to this problem floating about, but none of them seem to explain in plain english how a user who doesnt want to have his system screwed can save himself.  I hope this helps.

Problem: 
Install goes smoothly until at the last stages apt-get attempts to configure "uwdial".  At this point nothing happens, the system doesn't hang or crash, but the install process will not proceed.  If you reboot at this point you will lose your system. 

Solution: 
Open a terminal (if gnome is hanging then you can use cntl-alt and F1 - F6).  Do:

> top

find the uwdial process and get its PID (process ID) number (the leftmost number). Then do:

> sudo kill processid where processid is the correct number.  Your install should now continue, saving your *** :

Unfortunately if you have opted to install from the non-live install disc, and are doing so from a CD-boot this trick will not work since you only have access to the more limited ASH shell - I couldnt find a process killing method in ASH.  Your best bet would be to install breezy and then dapper over it if you dont have the live cd.

---

### Post by vinetu on 2006-05-11
<< SOLVED for me >>

Hi, I had the same problem - I installed Dapper Flight 7 AMD64 from boot CD (non-live install). 

After trying installation couple of times with different language & region settings + saying "no network this time" (who knows, maybe helps...), I reallized that problem happened because serial port was used by the Wacom Intuos tablet - i saw in logs that wvdial scanns all serial ports to find a dial-up modem and hangs already when checking dev/tty0. 

So I temporary disconnected the Wacom Tablet from serial port, rebooted and did Dapper installation again without any hangs. If you have serial devices, maybe the trick works for you as well.

In Breezy and Hoary, developers used another dial-up prog (ppp I think), which didn't produce such hangs. I would suggest this as bug in wvdial !!

It is also strange that for the user who during installation says "no network please", the wvdial is installed anyways. Easy why - with dselect, you can see that essential "ubuntu-desktop" module has declared dependancies with "wvdial". Users who access Internet via DSL Router, don't need this dial-up package either.

regards

---

### Post by SqRt7744 on 2006-05-11
If you only have the ash shell, i.e. you are installing from the install CD, it is most certainly NOT NECESSARY to reinstall everything from scratch.  Ctrl-Alt-F[1,2,3,4,5,6] (pick one) will get you to a terminal, then type

killall uwdial

if you're not sure of the name of process, you can type

ps -e|more

and peruse the output to see all running processes, and kill the appropriate ones. (with kill processid)

---

