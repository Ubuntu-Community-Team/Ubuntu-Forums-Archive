---
title: "Fresh Install and Dual Boot"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Horomancer on 2008-11-01
Hey there. I've decided that my beligerant upgrading, installing, and uninstalling of software has left my Ubuntu distro in a less than ideal state.
I'm downloading the .iso for 8.04 as I've seen that some people are having troubles with nvida cards in 8.10 (that could effect me) and have dug up my old XP discs for making a dual boot system.

My questions are
1. Is there anything special i need to do for a dual boot system when I install Ubuntu?
2. Is there anyway to strip down my XP install so i don't need firewalls and virus scanners running around the clock? It's only for running games and using the printer.
3. I normally install any and all updates that pop up from the update manager. I'm not really certain if i need them since i don't do alot with my lInux except surf the net and watch movies. Is there a way to set up the updates so only vital security fixes show?

---

### Post by diablo75 on 2008-11-01
1.  Not really, but you should install Windows first and then Ubuntu (it's the easiest way to setup dual-booting).

2.  I'd use AVG anti-virus, stick with the firewall that's included with XP SP2 or better, and install Firefox (just incase you need to browse the web).  Avoid using IE.

3.  Yes.  Have a look at System>Administration>Softare Sources, and in that, click on the Updates tab.

---

### Post by Horomancer on 2008-11-01
Will I set up the boot options from XP of Ubuntu? Or from somewhere else?
I know what to do to run XP well, I just don't want to deal with the firewalls and anti-viruses. Is there anyway to strip away sections of XP so that even i it does gt infected there isn't really anything to infect. i want to stream line it down for gaming as best as possible since i've had mixed results from Wine.

Thanks for all th help.

---

### Post by ksamanta on 2008-11-01
> **Horomancer said:**
> Will I set up the boot options from XP or Ubuntu? Or from somewhere else?

It's preferable to install Ubuntu on XP (not the other way around) for a dual boot system as somebody else has already pointed out. Now when you install Ubuntu using the installation CD (containing the ubuntu ISO), choose the option for guided partitioning scheme (if you don't want to   play with the partitioning!) and let it use the freed up space to install Ubuntu. After installing Ubuntu when you reboot, you'll see an option to boot to either XP or Ubuntu (scroll using up and down arrow).
> 
I know what to do to run XP well, I just don't want to deal with the firewalls and anti-viruses. Is there anyway to strip away sections of XP so that even i it does gt infected there isn't really anything to infect. i want to stream line it down for gaming as best as possible since i've had mixed results from Wine.

Who does want to mess with crapwares called antiviruses??:) So my suggestion is if you are not plugged in to the internet while playing games in XP, you should be fine without them. If you want to play it that way you can just uninstall (from XP control panel) the crapwares that you don't need. And by the way, even if your windows partition gets 'infected' by a windows virus, the Ubuntu partition should still be fine.

---

### Post by Horomancer on 2008-11-02
Yay i got a snazzy dual boot system!
What I did-
Took my existing WinXP cd and used another computer running windows to us nLite and make a very stripped down version of XP.
Installed my XPLite and got the drivers updated.
Installed Ubuntu 8.04 from CD.
Total install time for XP- about 5 hours including nLite stripdown.
Ubuntu install time was about 30 minutes.
<3 ubuntu !

Now to remember all those repositories for synaptic.

---

