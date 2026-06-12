---
title: "Having trouble picking a suitable OS"
date: 2008-03-17
forum: Other OS Talk
---

### Post by alexj.powell on 2008-03-17
Hi,

I use Ubuntu on most of my PC's / Laptops and was about to install Xubuntu on an old pc, but then i realized, ah, it's a 4GB install.

Heres the system Specs:

```
200mhz Celeron Processor
128MB RAM
4MB VRAM
**Most importantly: 5gb hard drive.**

```

What is a suitable Linux OS for me to use? Or should I just forget it and live with 512MB hard disk space. Which is not alot, considering I will be using it for programming and as a general workstation.

---

### Post by heartburnkid on 2008-03-17
I'm kind of new to the whole Linux thing, but I've been told that Puppy Linux is very good for lower-end systems.  And the ISO is a mere 72 MB (as a live CD), so I'd imagine that a hard-drive installed version couldn't be much more than that.

---

### Post by Twitch6000 on 2008-03-17
Ok so let me get this right your hard drive is really 5gb or do you have something else on it ;)?
If it is really only 5gb I do not think you will get anything on it.

---

### Post by Istonian on 2008-03-17
DSL might be a good choice.

---

### Post by ugm6hr on 2008-03-17
> **heartburnkid said:**
> I'm kind of new to the whole Linux thing, but I've been told that Puppy Linux is very good for lower-end systems.  And the ISO is a mere 72 MB (as a live CD), so I'd imagine that a hard-drive installed version couldn't be much more than that.

Indeed.  Puppy is a good option.

Or a custom Ubuntu / Debian installation.

If you really like Ubuntu:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by jrusso2 on 2008-03-17
> **Twitch6000 said:**
> Ok so let me get this right your hard drive is really 5gb or do you have something else on it ;)?
If it is really only 5gb I do not think you will get anything on it.

Nonsense I have a computer here with a ten gig drive and it dual boots Windows 98 and Sam Linux.

---

### Post by Lord Illidan on 2008-03-17
Zenwalk might also be good..although I guess Damn Small Linux would be the best contender in this case, it's hard to beat it, especially with your extremely low RAM and CPU stats. Xubuntu - forget it.

---

### Post by AmericasCup222 on 2008-03-17
I would also recomend DSL for a system with those specs, or Fluxbuntu which i found to be a verry nice lightweight system.

---

### Post by LaRoza on 2008-03-17
Zenwalk would run on that pretty well.

---

### Post by Pijits_1 on 2008-03-17
Lots of choices: 
Damn small linux is good
Slax is another
If you want to keep the Debian aspect of an OS you could use
Feather Linux' is not bad

A good site to see some small linux distros would be [HTML]www.pendrivelinux.com[/HTML]

---

### Post by AmericasCup222 on 2008-03-17
Also, if your tech-savy, you could try using free BSD. Or, if your less-tech-savy, you could try something like desktop BSD.  I have found that unix distros generaly require less powerful systems than Linux ones.

---

### Post by alexj.powell on 2008-03-17
Thanks for your replys..

I can run the xfce gui fine on a live cd.

free BSD, how much does an install of that take up and what GUI does that use?

---

### Post by init1 on 2008-03-17
Depends on what you want to do with it. For most purposes, a Debian bootable business card install should be suitable.

---

### Post by AmericasCup222 on 2008-03-17
FreeBSD will almost deffinatly fit on your small HDD, although I do not know the exact size. When it installs, FreeBSD is only a command line interface and any GUI you choose can be installed afterword.  DesktopBSD is basicly FreeBSD with KDE pree-installed.

---

### Post by wolfen69 on 2008-03-17
Tinyflux.

---

### Post by vishzilla on 2008-03-17
Puppy Linux or DSL

---

### Post by ugm6hr on 2008-03-18
I know you are now looking at BSD... but this is a good comparison of lightweight pre-configured distros: [http://www.informationweek.com/news/showArticle.jhtml?articleID=203100989&pgno=1&queryText=](http://www.informationweek.com/news/showArticle.jhtml?articleID=203100989&pgno=1&queryText=)

---

### Post by alexj.powell on 2008-03-18
> **AmericasCup222 said:**
> FreeBSD will almost deffinatly fit on your small HDD, although I do not know the exact size. When it installs, FreeBSD is only a command line interface and any GUI you choose can be installed afterword.  DesktopBSD is basicly FreeBSD with KDE pree-installed.

Cool, do you know the command to install Xfce?

I'm guessing it's:

```
sudo apt-get install xubuntu-desktop?
```

Think i'm wrong though, I only want the DE not the whole of ubuntu.

Or is it something like this?

```

# pkg_add -r xfce4

```

---

### Post by Tomatz on 2008-03-18
Yeah i had this problem with my eeepc which only has a 4gb ssd drive. There is a custom distro called eeexubuntu which i found buggy (drivers etc) so i scraped that.  All i did was installed the base system via a network install then rebooted and installed the rest of the system via apt.  Managing to shave the install size down to 1.6gb.  

Runs a treat :)

---

