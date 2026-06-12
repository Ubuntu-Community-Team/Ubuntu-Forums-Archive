---
title: "Update messed up system"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by Belgatom on 2012-06-19
I don't know where to start. 

Been running 10.10 for a long time but was getting a bit buggy. Decided to go for LTS so I would be at ease for a while. 

Installed 12.04. I'm not a big Unity fan, so I thought I'd run Gnome 3. Didn't love some aspects but all in all, quite a nice system. 

Untill today. I update. Halfway through updates (before second batch) it says to restart to continue. I do so. Restart gets me to the logon again but then logon keeps popping back to logon after introducing password. I remark that the bar on top of the logon screen is showing some problems. The name of my pc that is normally written in white on a see-through bar, is now grey background with white letters. Same for some other items on the same bar. When I try to chose another environment, the words Gnome, Gnome Classical, Unity and Unity 2d are also messed up. White letters on a white background. I can login with a guest account and logout again. Log in to Gnome Classical and perform rest of updates, hoping this will fix everything. But no go. 

I end up getting into Gnome 3 but my extensions are gone, can't seem to re-install them either from gnome-exentsions website. And when I try to change theme, I remark that all the listboxes do not react. The selected option can not be moved, it flickers but that's it. 

Luckily, I've only been using the system for two days and haven't imported most of my work back in to the system, so formatting and restarting is not a big deal, but I'd prefer to solve this. 

What can I do to give you guys more info so we can find out what went wrong?

---

### Post by wilee-nilee on 2012-06-19
Did you per-chance install a nvidia driver or any from other than the ubuntu repo's?

Or run a partial update/upgrade?

---

### Post by Belgatom on 2012-06-19
Nvidia driver issue? No, everything in the standard repo's

Run a partial update? Well, it said it needed to restart while there were still some updates in the update manager. But that happens a lot with Ubuntu for as far as I know. I ran update manager, it installed the updates, it said in the top part of the window that the system needed to restart but there seemed to be still some updates in the window below. I restarted and after much trial and error, got back into gnome 3. But this is a brand new installation on day two and if I already have some issues (see above) on day two, I need to solve them. This is supposed to be LTS so I'm not planning to change every time a new version comes along. 

If it's too hard to figure out, I will restart/reformat. But, I work in support and all too often we reformat rather than find out the original problem and so learn nothing. 

I want to OWN my system, meaning I know how it behaves and understand what it does. By reformatting, we learn nothing.

---

### Post by QIII on 2012-06-19
For clarification:  did you install a video driver, even if from the repos?

Some users of both NVIDIA and ATI products encounter graphics problems when updating.

Do you remember what was being installed when you were asked to restart?

---

### Post by wilee-nilee on 2012-06-19
> **Belgatom said:**
> Nvidia driver issue? No, everything in the standard repo's

Run a partial update? Well, it said it needed to restart while there were still some updates in the update manager. But that happens a lot with Ubuntu for as far as I know. I ran update manager, it installed the updates, it said in the top part of the window that the system needed to restart but there seemed to be still some updates in the window below. I restarted and after much trial and error, got back into gnome 3. But this is a brand new installation on day two and if I already have some issues (see above) on day two, I need to solve them. This is supposed to be LTS so I'm not planning to change every time a new version comes along. 

If it's too hard to figure out, I will restart/reformat. But, I work in support and all too often we reformat rather than find out the original problem and so learn nothing. 

I want to OWN my system, meaning I know how it behaves and understand what it does. By reformatting, we learn nothing.

If it is a partial it will tell you, don't run a partial.

You want to know the differences.

---

### Post by QIII on 2012-06-19
Partial upgrade = bad juju

---

### Post by Belgatom on 2012-06-19
> **QIII said:**
> For clarification:  did you install a video driver, even if from the repos?

Some users of both NVIDIA and ATI products encounter graphics problems when updating.

Do you remember what was being installed when you were asked to restart?


I didn't install a driver. It installed during basis 12.04 installation. I did not install anything from anywhere else. I might be totally at home with drivers on windows, linux drivers are still a mystery to me. 

Unfortunately, I didn't check what was being installed. I remember that the second part of install contained samba. I have to be honest. I've been running Ubuntu for some years now and have never had any problem with updates, so I don't pay much attention to them.

---

### Post by Belgatom on 2012-06-19
> **wilee-nilee said:**
> If it is a partial it will tell you, don't run a partial.

You want to know the differences.

I've learned a lesson. 

It will cost me an hour maximum to reformat. Do you suggest going that way as the time it will take me to resolve this will not be worth it?

---

### Post by Belgatom on 2012-06-19
By the way, thanx for the advice and your time. 

I would love to pour you guys a nice glass of my special bottle of Ichiro Nine of spades but the internet does not allow that kind of courtesy.

---

### Post by wilee-nilee on 2012-06-19
> **Belgatom said:**
> I've learned a lesson. 

It will cost me an hour maximum to reformat. Do you suggest going that way as the time it will take me to resolve this will not be worth it?

Your choice personally since I back up everything I'm for the quickest route.

You might note that any update run in synaptic leaves a history which can be copied for just these sort of situations.

I use this method to always know exactly what is installed and it can be reloaded on a install, if all the repo sources are set the same. This just needs dselect installed on the reload setup.

I found out how to do this recently and thought it might be helpful to some people. To output this information to a file in your home directory you would use,

Code:
dpkg --get-selections > installed-software

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

Code:
dpkg --set-selections < installed-software

followed by
Code:
dselect

---

### Post by Kopkins on 2012-06-19
You could try updating without the gui. 

For me (running 12.04 on a MBP), when I press Ctrl+Alt+f5 (note that any of the function keys 1-6 work.) it takes me to a virtual console where I can login. I often have trouble after the system resumes and even though the GUI isn't working I can still work with the system in a virtual console. 

You could update from the command line.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Then reboot and see if your system is working. 

Kopkins

---

### Post by QIII on 2012-06-19
That will do the same thing as doing it using the gui and will result in a partial upgrade.

Best not to do it at all.

dist-upgrade will try to resolve the dependency issues that a partial upgrade brings, but it is *still *something that should only be done if you are sure what you are doing.

Partial upgrades are just something that ought not be done.

---

### Post by Kopkins on 2012-06-20
True, I didn't think of that. If he wants to check if it will partial upgrade or full upgrade or not, he could still do it. When the command, *sudo apt-get upgrade*, is issued it gives you information before you actually upgrade.

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
[COLOR="Red"]4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]
Need to get 19.2 MB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? 

```

The important part is when it tells you what is going to happen. As long as there will be no packages *not updated* there is no partial upgrade.

Right now my Quantal Quetzal VM wants to partial upgrade.

```
71 upgraded, 0 newly installed, 0 to remove and [COLOR="Red"]27 not upgraded.[/COLOR]
Need to get 5,438 kB/42.9 MB of archives.
After this operation, 347 kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

Kopkins

---

### Post by Belgatom on 2012-06-20
Back on the flipside with a clean install.

Thanx for the effort.

---

