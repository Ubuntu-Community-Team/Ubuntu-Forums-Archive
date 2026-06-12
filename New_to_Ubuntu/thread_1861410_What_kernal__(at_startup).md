---
title: "What kernal ? (at startup)"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Greg Mueller on 2011-10-15
I guess I did something wrong along the way. When my computer boots now, the first thing it does is ask me what kernal I want to run. There's a long list of choices and I just take the top one which appears the newest.

How can I make it just pick that one automatically and continue?

---

### Post by Lisiano on 2011-10-15
If you don't touch your keyboard for 10 seconds then it will automatically pick the top one.
If you wish to decrease the timeout then you need to edit a file, open a Terminal (Ctrl+Alt+T) and type this
```
gksudo gedit /etc/defaults/grub
```
A window will pop-up asking for your password, give it.
Now just find this line
```
GRUB_TIMEOUT=10
```
And change the 10 to anything you want (In seconds)
If you wish to completely remove the menu, find this line
```
#GRUB_HIDDEN_TIMEOUT=0
```
And remove the # (Hash) in front of it

---

### Post by Greg Mueller on 2011-10-15
It says there is no such file

It opens a blank page with gedit and so I thought I would just enter that line and save it and it says it can't find the file?

---

### Post by fleamour on 2011-10-15
Or the GUI way, Grub Customizer:

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

---

### Post by Greg Mueller on 2011-10-15
I rebooted just now and when it gets to the what kernal part it just hangs there until I hit return. I waited the 10 seconds and it did not go on.

The good news is that it will boot to the desktop I want after all the kernal and password sign in BS

---

### Post by Greg Mueller on 2011-10-15
Ok I beat that part

[B]Applications
Other
StartUp-Manager
[/B]
Has a tick mark for "**Use Timeout For Bootloader Menu**"
I set it to "**0**"

It has a selection for "**Default Operating System**" and I chose the most recent

Now it just works around until it comes to the Password Sign in

That will be my next hurdle. I had it set so I did not have to give a password. But I can't remember how I did that.

---

### Post by drs305 on 2011-10-15
StartupManager was written for Grub legacy and while it works, I agree with *fleamour* about Grub Customizer. It was written for Grub 2 and has a lot more capabilities. In addition to the link *fleamour* provided, the "Customizer" link in my signature line will take you to a tutorial on how to install and run it.

As far as the autologin, go to System Settings, User Account. You can enable autologin from that section.

---

### Post by Greg Mueller on 2011-10-15
Thanks and I will do as you suggest.....right after I put out a couple other fires.....:)

---

