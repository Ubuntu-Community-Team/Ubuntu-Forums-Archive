---
title: "I have made a mess. Cannot upgrade. help pls? (involves low latency)"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by cino on 2008-06-03
hello anyone.
I mess about so such is life, but I do not know much about what I am doing?
Can anyone answer a couple of questions?

When I have a choice to load Ubuntu I have 6 options; ranging from 2.6.20-15 generic; 2.6.20-16 low latency and; .22-14 generic/rt/and386.

What are all these? I select low latency (which I want for messing about in music stuff..) but can not upgrade now via update manager (which says I have 703 updates - 1.4MB).

I choose the partial upgrade that it recommends but get this;

"The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a)."

Apologies for not providing any more details, it is absolute beginner, which I am.

Perhaps a fresh start is in order?
What would the best way for me to go about knowing I have the low latency kernel / studio running? Does upgrading dist. to 8.04LTS ever have a chance of working for me? Maybe I try a fresh install. eek!

Anyone? Peace

---

### Post by ibuclaw on 2008-06-03
Reboot you PC and select the 2.6.22-14-generic kernel.

When you log in, open up a terminal and type in:
```
dpkg -l | grep linux-image
```
and post the output in your next post.

Thanks
Regards
Iain

---

### Post by cino on 2008-06-03
start:
ii  linux-image-2.6.20-15-generic              2.6.20-15.27                         Linux kernel image for version 2.6.20 on x86
ii  linux-image-2.6.20-16-generic              2.6.20-16.32                         Linux kernel image for version 2.6.20 on x86
ii  linux-image-2.6.20-16-lowlatency           2.6.20-16.32                         Linux kernel image for version 2.6.20 on x86
ii  linux-image-2.6.22-14-386                  2.6.22-14.52                         Linux kernel image for version 2.6.22 on i38
ii  linux-image-2.6.22-14-generic              2.6.22-14.52                         Linux kernel image for version 2.6.22 on x86
ii  linux-image-2.6.22-14-rt                   2.6.22-14.52                         Linux kernel image for version 2.6.22 on RT 
ii  linux-image-generic                        2.6.22.14.21                         Generic Linux kernel image
ii  linux-image-lowlatency                     2.6.20.16.28.1                       Low latency Linux kernel image
ii  linux-image-rt                             2.6.22.14.21                         Linux kernel image on realtime kernel

:end

---

### Post by ibuclaw on 2008-06-03
lol WOW!
That is quite some list! :D

OK, first, lets just focus on dropping every kernel that you don't need, as no more than two is a very recommendable amount.

Can you print the output of
```
uname -r
```
Just to confirm what kernel your running on (just incase) ;)

Regards
Iain

---

### Post by cino on 2008-06-03
yes! I thought I was doing a pretty good job...

ok:
uname -r = 2.6.20-16-lowlatency

---

### Post by ibuclaw on 2008-06-03
```
sudo apt-get purge linux-image-2.6.20-15-generic linux-image-2.6.20-16-generic linux-image-2.6.22-14-386 linux-image-2.6.22-14-rt
```
Remove everything except the kernel you're on and the 2.6.22-14-generic kernel.

That should cut it down to size :)

---

### Post by cino on 2008-06-03
right. 
(Thanks so far by the way, awfully helpful!)
Now my update manager has 699 updates (but only 1.4MB) as well as a partial upgrade (that did not work) so I am now installing the updates.

Thanks again, install will take a while.

---

### Post by ibuclaw on 2008-06-03
OK, cools.
Run this command, as the Update Manager says:
```
sudo dpkg --configure -a
```

And then retry an upgrade.

Regards
Iain

---

### Post by cino on 2008-06-03
something bad may have happened.
There is a new theme that conflicted with the human theme when installing updates (not upgrading)?. I can load up but I cannot open windows, e.g., from the places menu (well I can but they disappear, immediately). 

Other windows work, such as the browser window I am on now and simple games, so it is something to do with the desktop, that now has no items on it and no mouse menu etc etc.

Fonts are all messed up to.

I have done: 

sudo dpkg --configure -a

but get from update manager:

A upgrade from 'hardy' to 'gutsy' is not supoprted with this tool.

When trying to install the other update (one left and this is the prob I think) I get:

E: /var/cache/apt/archives/human-theme_0.18_all.deb: trying to overwrite `/usr/share/applications/screensavers/ubuntu_theme.desktop', which is also in package gnome-screensaver

---

### Post by ibuclaw on 2008-06-03
Oh, your still on Gutsy?

What does your sources.list file look like?
```
gksu gedit /etc/apt/sources.list
```
Open it up and change all instances of the word "gutsy" to "hardy" and save.

Then run:
```
sudo apt-get update
sudo apt-get dist-upgrade

```

Perhaps the problem may be more deep-rooted than what I first imagined.

Download the [new Hardy iso]("http://www.ubuntu.com/getubuntu/download") and burn it to CD first. Just incase.

Regards
Iain

---

### Post by LowSky on 2008-06-03
ok heres the issue the kernel you are using isn't supported by Hardy, so it tries to "upgrade" to Gutsy. In doing so it fails. You can do a full new install with out wiping your /home folder. Live on the Wild side.

Alternatively you can delete all the old kernels right from synaptic package manager. Just type Kernel and deete all the  packages that have a lower number ie: 2.6.16 is older than 2.6.22.

If the system loads fine on the new kernel you dont need the old ones, and subjectivly newer versions of Ubuntu may/will not run on old kernels

---

