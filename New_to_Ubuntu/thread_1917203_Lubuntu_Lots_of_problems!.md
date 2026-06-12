---
title: "Lubuntu: Lots of problems!"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by jamedfor on 2012-01-29
Hi all,

I just made the switch last night from Ubuntu 11.04 to Lubuntu 11.10, looking for a faster more reliable system. Instead, I think i got the opposite.  Right now, on startup, my toolbar does not appear, so I can't access anything.  The keyboard shortcuts seem to be partially broken, so ctrl alt T doesn't work.  The shortcut ctrl alt F1 (the text console thing) sort of works, but it just makes the screen black with no prompt. 

Before, when I could see things, anything from a google search to a text editor would crash me to something that looked like a command prompt but would not accept entry.

In other news:  any help on mounting a partition at boot? 

Thanks!
-John

---

### Post by rgreener25 on 2012-01-29
Hmmm. Your CD you installed it on might have errors or lubuntu just doesn't play nicely with your pc. try putting the disc in and loading it up then select check disk for errors if it finds some redownload it and burn it to a disk and try again if it doesnt find any it doesnt play nicely with your computer. try another distro if you are looking for something lightweight try xubuntu

---

### Post by Rodney9 on 2012-01-29
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by jamedfor on 2012-01-29
Thanks for the input guys!

I checked the ISO file before burning, and the disc before installing.  By the way, my system is a HP G62 with 2.29 GHz, 2.93 GB RAM.  

I guess I assumed Lubuntu would be more reliable because it would be simpler than the standard Ubuntu after getting pissed at a variety Unity/11.04 issues, and I didn't see too many complaints about Lubuntu online.  Is it going to stay this crashy consistently, or is it worth giving it another shot?

-John

---

### Post by Rodney9 on 2012-01-29
It is well worth another shot, If you have checked the MD5sum and it's ok,

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

> When one has downloaded an ISO file for installing or trying Ubuntu, it is recommended to test that the file is correct and safe to use. The MD5 calculation gives a checksum (called a hash value), which must equal the MD5 value of a correct ISO.

I would burn the iso again at the slowest speed you can, around 4 speed,  and maybe try another brand of cd.

```
ctrl alt T
``` brings up a terminal.
```
ctrl alt F1
``` logs you out.

You can see the keyboard shortcuts for Lubuntu in - 

```
/home/yourname/.config/openbox  lubuntu-rc.xml
```

Rodney

---

### Post by mörgæs on 2012-01-29
A bad ISO is hardly ever the explanation for this kind of problems. 

Let's be systematic here. How does Lubuntu work in a live boot?

Did you have wired internet access while installing, and did you apply all updates?

---

### Post by jamedfor on 2012-01-29
Update:  I booted back up into lubuntu (currently on XP dual boot), and everything looked fine.  Even the internet seemed to work OK, it crashed again logging into this site.  I got to CLI using ctrl alt F2, which seems to work OK, but I couldn't figure out how to restore the GUI.  I tried killing and starting lxdm (thats the desktop environment, right?), but I couldn't kill it.  I figure maybe by stopping the application I can just restart it without restarting the whole machine.  Would it help to make a log file or something to record the failure?

What do you mean by a "live boot"?  Like from the CD?

Yes, I had a wired internet connection during install and chose to install all updates when asked.

I did the md5sum recommended on the site, and everything matched.  I think I agree with morgaes, the ISO seems to work fine other than these problems.  Almost every time I install or upgrade any ubuntu system I end up with some crap like this.

---

### Post by Kixtosh on 2012-01-29
> **jamedfor said:**
> ...  By the way, my system is a HP G62 with 2.29 GHz, 2.93 GB RAM. ...I've done quite a bit of testing with Lubuntu, Peppermint, Puppy Linux, Xubuntu ... and a few other lightweight distributions besides. With those specifications, I would respectfully suggest that there absolutely no obvious reason to want to use Lubuntu instead of Ubuntu.

In my experience, Lubuntu, and other lightweight distributions, really only help when you have:

[LIST]
[*]A CPU with a clock speed of 1 GHz or less.
[*]Installed RAM of 512MB or less.
[/LIST]
There is one caveat: on older machines (and even on newish ones), I stick to the latest LTS release, so I haven't used any of the newer Unity releases. My statement above holds true when talking about Ubuntu 10.04 LTS "Lucid Lynx". Otherwise, I find ANY LXDE environment good for older hardware, as well as Wary Puppy, but just about useless for even sort of newish hardware.

Just some food for thought!

---

