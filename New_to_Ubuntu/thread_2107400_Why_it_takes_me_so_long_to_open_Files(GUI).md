---
title: "Why it takes me so long to open Files(GUI)"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by rolandluo on 2013-01-21
OS: Ubuntu 12.10
GNOME 3
Problem: It takes me a lot of time (about five minutes) to open the Files(GUI) in the left panel. Can anyone tell me the reason? And sometimes the Ubuntu just died and gave me no response(more frequently than windows 7 I used before).

I have another windows 7 installed on the C disk and my ubuntu is on E disk.

Thanks!

---

### Post by elgordodude on 2013-01-21
Welcome to the forums,

Could be lots of things so more information would help. First, E:\ drive? You aren't running a live cd are you, or worse a live wubi?That's not the most responsive way to run a system.

Second it would be a good idea to take a look at what's running. I like htop and it's easy to get without using compiz. First open a terminal with Ctrl+Alt+T

Then:

```
sudo apt-get install htop
```

Then:

```
htop
```

to get a list of processes in order of cpu use. That will give you an idea of where to go next.

---

### Post by rolandluo on 2013-01-21
Thanks for your advice. Of course the Ubuntu has already been installed on the E partition. 
Actually when the GUI is open finally, then it will be normal when I use it to go to other directories. So it is just the first open of it. Very weird.

It seems that the problem doesn't exist when I didn't install Gnome 3. So it could the problem of that?

---

### Post by elgordodude on 2013-01-21
Possibly, compiz has been known to cause some problems from time to time. Htop will tell you if it's the offender, and it is a very quick program to install and run, if compiz is acting up, you can switch to gnome classic. The short way is
> 
sudo apt-get install gnome-panel

at reboot click the ubuntu icon in the logon screen, select gnome 2d (no effects)

login

reboot again

and login again, you'll now be running classic gnome, minus the buttons on the left, but with handy drop down menus up top.

There are many tutorials on google that will walk you completely through this.

---

### Post by mysteriousdarren on 2013-01-22
What hardware are you using?

---

### Post by audiomick on 2013-01-22
> **mysteriousdarren said:**
> What hardware are you using?

Yes, good question. Particularly, how much RAM? Since you said that Win7 was or is also on the machine, I expect it is enough, but please post how much it is. The CPU and perhaps the graphics card might also be interesting.

---

### Post by rolandluo on 2013-01-22
CPU: Intel Core 2 Duo processor T6400(2M Cache, 2.00 GHz, 800 MHz FSB)
RAM: 2GB DDR3
Graphics card: NVIDIA GeForce 9600M GS

actually, I think it's enough :)

---

### Post by audiomick on 2013-01-22
Yes, that should run ok.

---

### Post by rolandluo on 2013-01-22
Yes, when I switched to the gnome classic, the problem disappears. But I love the style of the previous gnome, it's so cool! 
Is there any method to let me keep the previous one and solve the problem?:)

---

### Post by audiomick on 2013-01-22
I can't say anything for sure, as I haven't looked at Gnome 3 at all. It does sound like it is something to do with that, though.

---

### Post by rolandluo on 2013-01-22
Actually, gnome classic just likes windows 7 :(

---

