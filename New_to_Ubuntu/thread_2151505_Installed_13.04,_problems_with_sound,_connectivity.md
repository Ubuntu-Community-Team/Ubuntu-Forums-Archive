---
title: "Installed 13.04, problems with sound, connectivity"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by paravasta on 2013-06-04
Hello all! Salutations from a hopeful newbie! 

Yesterday, I made my very first foray outside the world of Windows, installing Ubuntu 13.04. Not as a replacement OS (yet) but running alongside Windows 7 Home Premium. I REALLY like the look and feel of the new OS, but a couple of problems have cropped up immediately after the install - one of them is affecting my Windows use, the other is a problem while I'm using Ubuntu. 

Your assistance will be truly appreciated by this absolute, but hopeful beginner.

First problem - When I'm booted into Ubuntu, I cannot connect to the internet. I know that our WiFi signal is very strong. I also know that the computer is detecting the correct WiFi network, and that I am definitely using the correct password. In fact, I can't even connect to a local un-password-protected network. 

And though I can't connect while I'm using Ubuntu, there is no problem at all connecting while I'm using Windows. I've looked at posts made by others on similar problems, but nothing seems to match my situation exactly, and I haven't found any solutions that seem to work.

Second problem - When I'm using Windows - and I plug in my headphones - there is no sound at all. When headphones are unplugged, there is sound. The headphones were working perfectly right up until installing Ubuntu. There seems to be no problem with my laptop's built-in speakers.  I've heard this is not an uncommon problem for people installing Ubuntu, but again, none of the fixes I've seen posted seem to have any effect.

I'm not giving up on the new OS: like I said, I really like what I see. And my techie friends have been singing Ubuntu's praises to me for a long time. Provided I'm able to resolve these two issues (with a little help from you, my new friends), I'm sure that I'll soon be singing those praises to others as well. Who knows, down the line, I may decide that Ubuntu adequately fills all my needs, and that I may as well uninstall Windows. :KS

Thank you in advance, and looking forward to your insights!

Paravasta

---

### Post by 0N3 on 2013-06-04
Can you connect to your wifi router via ethernet cable? You may need to install a closed source driver that aren't provided by ubuntu by default.

---

### Post by varunendra on 2013-06-04
Welcome to the forums paravasta ! :)
> **paravasta said:**
> Who knows, down the line, I may decide that Ubuntu adequately fills all my needs, and that I may as well uninstall Windows.

Don't do that until you are comfortable enough with Ubuntu (or any other distro of Linux), and are absolutely sure you won't need windows again. Even in that case I'd suggest to keep backup DVD's of your paid OS, simply because you have paid for it and will have to pay again if you lost the current one and need it back for whatever reason.

To let us know of your Network adapter and Ubuntu/kernel version and driver in use, please open a terminal (ctrl+alt+T), enter the following commands one-by-one (you may copy-paste to avoid errors) and post back their outputs here :
```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
```

Also, like 0N3 asked already, do you have a wired connection available? Not necessary, but it makes things a lot easier.

---

