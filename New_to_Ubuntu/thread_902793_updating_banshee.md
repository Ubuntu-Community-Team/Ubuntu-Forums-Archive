---
title: "updating banshee"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Truant_84 on 2008-08-27
Hi all. I followed the instructions to install Banshee off of their website. Everything went fine, except that under "about" page in the program, it says I'm running version 0.13.2 instead of the new version 1.2. That, and the Banshee running on my desktop looks nothing like the one pictured on the project-banshee website. I would greatly appreciate some advice on how to get Banshee upgraded to the new version. Thanks!

---

### Post by Cheesehead on 2008-08-27
Did you uninstall your previous version? Completely?

---

### Post by Truant_84 on 2008-08-27
No i never uninstalled anything. The first version I ever tried to install was version 1.2 and I got 0.13.2 instead.

---

### Post by Daeluin on 2008-08-27
Yes, this was rather annoying. Fortunately I finally checked out the file listing lower down on this page

[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

and saw that "banshee" was the 0.13 version, while "banshee-1" is the 1.2.1 version. Then I noticed that the instructions DO say to install banshee-1. Hurrah for easily overlooked details.

So just 
sudo aptitude remove banshee
sudo aptitude install banshee-1

and that should get you straight. (with the PPA repo lines added to /etc/apt/sources.list, or however it says to do it)

---

### Post by Truant_84 on 2008-08-27
okay, so I downloaded the banshee-1 package through synaptic. Now what do I do? I realized that the earlier verision I was running I had actually gotten through the "add/remove programs" section listed under "applications" (sorry for giving incorrect info). But yeah...I downloaded the package, now I'm not quite sure how to actually install/run the program.

---

### Post by mc4man on 2008-08-27
If you used synaptic then it's installed, look in applications menu under sound & video or open a terminal and type in banshee-1, press enter.

Note - you can have both banshee and banshee-1 installed at same time, no need to uninstall either.

---

### Post by Truant_84 on 2008-08-27
Cool, that got the program running. It doesn't show up under my applicatiions menu though. Is there a command I can enter to make that happen?

---

### Post by jmate24 on 2008-08-27
yes you do because i have had problems with having both versions installed so i had to uninstall banshee 1.2.1: ```
$ sudo apt-get purge banshee
``` and reinstall banshee 0.13: ```
$ sudo apt-get install banshee
``` and then open a terminal and type:```
$ sudo apt-get purge banshee
```

then i installed 1.2.1 from the website. there was a problem with having both versions config files.](*,)

---

### Post by mc4man on 2008-08-28
> yes you do because i have had problems with having both versions installed so i had to uninstall banshee 1.2.1:  there should be no problem if banshee is installed first, then banshee-1 on top of.
see screen (running both at same time

---

### Post by Truant_84 on 2008-08-28
Okay....so Banshee is running fine throught the terminal. However, as previously requested, I would love it if somebody could tell me how to get it to open through applications, how to get a desktop icon, etc. Thanks!

---

