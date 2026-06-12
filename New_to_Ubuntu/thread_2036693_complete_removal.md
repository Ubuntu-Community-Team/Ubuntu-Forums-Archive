---
title: "complete removal"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by rosswmcgee on 2012-08-02
I want my-weather-indicator completely removed from 12.04.

I do not wish to see it in synaptic. In synaptic I have un-installed it.

When I run sudo apt-get remove my-weather-indicator it says it has already 

been removed, but it still shows in synaptic as being un-installed and there

are files in the system. I have had trouble launching the app and wish to 

do a complete re-install to fix the problem. How do I get it completely gone?

---

### Post by ajgreeny on 2012-08-02
Try ```
sudo apt-get purge my-weather-indicator
``` which will remove any configuration files in your filesystem except for anything in your home, which you can search for and remove manually.

---

### Post by rosswmcgee on 2012-08-02
sudo apt-get purge my-weather-indicator
[sudo] password for rosswmcgee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package my-weather-indicator is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
rosswmcgee@rosswmcgee-EL1330:~$

still listed in synaptic as un-installed

---

### Post by irv on 2012-08-02
> **rosswmcgee said:**
> sudo apt-get purge my-weather-indicator
[sudo] password for rosswmcgee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package my-weather-indicator is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
rosswmcgee@rosswmcgee-EL1330:~$

still listed in synaptic as un-installed

What happens when you select it and try to completely remove it from there? Does it give you a list of files it is going to remove? Do you get any errors?.

If you continue to have this problem you might want to reboot and go into recovery mode and select fix broken packages from the menu, then try a restart.

---

### Post by audiomick on 2012-08-02
> **rosswmcgee said:**
> I want my-weather-indicator completely removed from 12.04.

I do not wish to see it in synaptic. In synaptic I have un-installed it.

When I run sudo apt-get remove my-weather-indicator it says it has already 

been removed, but it still shows in synaptic as being un-installed and there

are files in the system. I have had trouble launching the app and wish to 

do a complete re-install to fix the problem. How do I get it completely gone?

What do you mean by "completely gone"? Going by what you have written, it is gone.

There may be some relics in your /home/user folder. I can think of two ways to get around that. One is to enable "view hidden files" in your file manager, look for any relevant config files and delete them. 

The other is to "trick" apt-get. You say that the purge command says

```
Package my-weather-indicator is not installed, so not removed
```

So go to synaptic and install it. If there are any config files left on the system, the will be associated with the install. Then run the purge command again. If I am not mistaken, this will then remove everything associated with the program.

As I said, I think it is already completely removed, but if you are not convinced, try the above.

---

### Post by rosswmcgee on 2012-08-02
What I meant was not to have it listed in synaptic period. However after using the 

sudo apt-get purge my-weather-indicator 

I went back to the website and re-installed vis terminal. Then I went to synaptic

and it still said it was un-installed. So I re-installed it via synaptic. This time it launched and I am back in business. I am not sure why.

---

### Post by audiomick on 2012-08-02
> **rosswmcgee said:**
> What I meant was not to have it listed in synaptic period.

This wont happen. If is in the repositories, or if you have added a PPA where the program in question is available, it will always be listed in Synaptic. It will come up as installed, or un-installed which is the same as "available for installation".


As to why it is working now, I dare say something got messed up, and a re-install sorted it out. Happens sometimes. ;)

---

### Post by rosswmcgee on 2012-08-02
Perhaps someone can explain why the weather app in gnome has and does work flawlessly 

and was not used for Ubuntu. I prefer the new Ubuntu over gnome and wish there were

some update down the line to fix bugs like this.

---

### Post by neodirtchief on 2012-08-02
I am fairly new to this but I thought I had read that the new Ubuntu went with unity and not Gnome on this release.

---

### Post by rosswmcgee on 2012-08-02
Correct but why they picked a buggy app is the question, and where is the fix?

 I replaced the ubuntu weather app with my-weather-indicator. The ubuntu weather indicator is on the fritz, and has been for about 2 weeks. the net is full of compalints.

---

### Post by Paqman on 2012-08-03
> **neodirtchief said:**
> I am fairly new to this but I thought I had read that the new Ubuntu went with unity and not Gnome on this release.

Unity is built on top of Gnome, so you actually have both. Ubuntu just decided to put a slightly different top layer on it than what Gnome ship by default (ie: Unity instead of Gnome Shell).

---

