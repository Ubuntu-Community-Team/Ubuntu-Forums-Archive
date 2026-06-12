---
title: "How can I turn off the graphical desktop in Ubuntu 18.04 LTS?"
date: 2018-08-15
forum: New to Ubuntu
---

### Post by fallesafe on 2018-08-15
[SOLVED] For some reason, the commands that ended up working were **sudo telinit 3 **(to turn the graphical desktop off) and **sudo telinit 5** (to turn it back on). I'm not sure why that is... since systemd is supposed to be the new startup system. But it worked for me. Thanks to everyone for the help!

Hi Everyone,

I'm new to these board (and to Linux). And I'm having a bit of difficulty with the command line. I'm currently taking an "Introduction to Linux" course from the Linux foundation. And it uses Ubuntu 16.04. But that's (apparently) an old version that isn't available for download anymore. So I installed Ubuntu 18.04; and nothing I'm studying is really working at all. So, my latest difficulty is trying to figure out how to turn off and turn back on the graphical desktop. The course recommends **sudo systemctl stop gdm , **and**sudo systemctl start gdm. **But the first command does nothing to the graphical desktop. And the second one (to undo the first) puts me into a looping login screen like the one I see to unlock my user session (or just glitches my desktop completely).

So I went online to see what others recommend. And I read that the way to do this is to enter **systemctl disable gdm.service** and **systemctl enable gdm.service. **But these commands don't do anything at all to the graphical desktop (even though I'm able to confirm that gdm.service is shut off and then turned back on after each command. And I feel like I'm stuck here. Because I cant just plow through this whole course and learn nothing. If this is the thing that I'm on, in this chapter, I need to figure this out before I can move on. Anybody have any thoughts about what I may be doing wrong here? Thanks!

---

### Post by wildmanne39 on 2018-08-15
16.04 is still available here:

[https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)

---

### Post by fallesafe on 2018-08-15
Thanks! I might just switch over to that version if I keep having difficulties with this material. I don't want to quit just yet though.;)

I found out that **sudo telinit 3 **and **sudo telinit 5 **do what I was expecting the other commands to do (turn off and turn on the graphical desktop). And this may be really dumb question. But I was surprised to see that I couldn't open any programs from the non-graphical desktop (gedit, firefox, etc). I was kind of expecting that it would still do all the things the normal command line does. What's the purpose of turning it off? Is it just for scripting?

---

### Post by TheFu on 2018-08-15
telinit really doesn't make sense since systemd took over the init system. Most Linuxen don't have "runlevels" anymore.

If you don't run a GUI (display manager like X11), then no GUI programs can be run.
Linux servers don't have GUIs, so learning to work without it means learning to manage servers.
In Unix, a GUI is just another program, not the OS.

You really should load up 16.04, since many things have changed in 18.04 which will be confusing.

You can run scripts with or without the GUI.  What you can put into the scripts and how they are started can change if you have a GUI running or not.   And don't forget that you can run programs over a network either with a shell or GUI interface.  ssh is a way of life for me. I'm logged into 6 other computers through ssh right now and I'm running libreoffice on 1 of those other computers, but showing the window for it on my current laptop.  X/Windows can do some amazing things.
[https://en.wikipedia.org/wiki/X_Window_System](https://en.wikipedia.org/wiki/X_Window_System) has a good diagram which explains the client-server architecture.  The OS and GUI are loosely tied together, unlike other OSes.   This applies to all Unix and Linux systems.

To get an overview of Linux, start here: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)  You need this primer.
After that, there are some Linux-culture things that are important to understand. Understanding "why" things are done so differently from Windows or OSX will help you better understand Linux too. That will reduce surprises.

---

### Post by fallesafe on 2018-08-15
> **TheFu said:**
> telinit really doesn't make sense since systemd took over the init system. Most Linuxen don't have "runlevels" anymore.

If you don't run a GUI (display manager like X11), then no GUI programs can be run.
Linux servers don't have GUIs, so learning to work without it means learning to manage servers.
In Unix, a GUI is just another program, not the OS.

You really should load up 16.04, since many things have changed in 18.04 which will be confusing.

You can run scripts with or without the GUI.  What you can put into the scripts and how they are started can change if you have a GUI running or not.   And don't forget that you can run programs over a network either with a shell or GUI interface.  ssh is a way of life for me. I'm logged into 6 other computers through ssh right now and I'm running libreoffice on 1 of those other computers, but showing the window for it on my current laptop.  X/Windows can do some amazing things.
[https://en.wikipedia.org/wiki/X_Window_System](https://en.wikipedia.org/wiki/X_Window_System) has a good diagram which explains the client-server architecture.  The OS and GUI are loosely tied together, unlike other OSes.   This applies to all Unix and Linux systems.

To get an overview of Linux, start here: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)  You need this primer.
After that, there are some Linux-culture things that are important to understand. Understanding "why" things are done so differently from Windows or OSX will help you better understand Linux too. That will reduce surprises.

Yea, I'm not sure why those telinit commands did the trick. Because I also had the impression, from this course, that systemd was the new startup system (like you said). I didn't mean to dual-boot windows with Linux. But I ended up doing it somehow. Could that have something to do with it? (just taking guesses here)? And thank you for such a detailed answer! It's very much appreciated. I'll check out those resources you linked!

---

### Post by mörgæs on 2018-08-15
Thanks for an attempt at marking the thread solved but please note that Wildmanne has a note in the signature about how to do.

---

### Post by Holger_Gehrke on 2018-08-15
'telinit' does not exist on systemd based systems. '/sbin/telinit' is a symbolic link to '/bin/systemctl'. systemctl checks how it is called and if it's called as 'telinit' with a runlevel '**n**' it will  behave as if it was called as 'systemctl isolate runlevel**n**.target' for **n** between 2 and 5, as 'systemctl poweroff' for n=0, as 'systemctl reboot' for n=6 and as 'systemctl rescue' for n=1. Source: 'man telinit'

Holger

---

### Post by fallesafe on 2018-08-15
> **Holger_Gehrke said:**
> 'telinit' does not exist on systemd based systems. '/sbin/telinit' is a symbolic link to '/bin/systemctl'. systemctl checks how it is called and if it's called as 'telinit' with a runlevel '**n**' it will  behave as if it was called as 'systemctl isolate runlevel**n**.target' for **n** between 2 and 5, as 'systemctl poweroff' for n=0, as 'systemctl reboot' for n=6 and as 'systemctl rescue' for n=1. Source: 'man telinit'
Holger

Ok, I do see those folders. And I think that I mostly follow your explanation. Thank you!

> **mörgæs said:**
> Thanks for an attempt at marking the thread solved but please note that Wildmanne has a note in the signature about how to do.

Noted, thanks!:p

---

