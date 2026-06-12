---
title: "[SOLVED] Fresh Ubuntu install is near useless - HELP!!!!!"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2008-11-29
I just installed 8.10 from the CD (Yes I check for disc errors, there were none). I had to boot it with the acpi=off parameter  to get it to work. Now I am logged into the machine using an xterm session because gnome loaded a light tan background then went black. It played the ubuntu theme (?) and just sat there with a white cursor. This is a total pain. 

Can someone help me out?  

P.S. For those who don't know -  Don't ask me to paste things from the terminal. I can't do it in this mode.

---

### Post by Mayhem77 on 2008-11-29
What are your machine specs?

---

### Post by linuxguymarshall on 2008-11-29
I have a HP a705w - 

2.9 GHz Intel Celeron - 512 MB RAM - Intel Integrated graphics and NVIDIA 6200. Currently using the intel integrated.

---

### Post by jakupl on 2008-11-29
Is it not possible for you to boot up in recovery mode?

[here is how to do that]("http://psychocats.net/ubuntu/fixsudo#recoverymode")

---

### Post by linuxguymarshall on 2008-11-29
It gives me the same issue. The boot goes fine until after login.

I have restarted X tried GNOME and Failsafe GNOME but nothing.

---

### Post by Mayhem77 on 2008-11-29
I found this thread on another forum that MIGHT help.

[http://vb.serverknecht.de/showthread.php?t=142186](http://vb.serverknecht.de/showthread.php?t=142186)

sudo nano /etc/modprobe.d/blacklist

blacklist agpgart
blacklist intel_agp

Have you flashed your BIOS with the latest?

---

### Post by linuxguymarshall on 2008-11-29
I have not flashed my BIOS however I doubt that will make a difference because I installed 8.10 correctly the other day but when I installed my NVIDIA drivers is stopped working. I would go back down to 8.04 however I am out of blank cds so I must make this work.

---

### Post by linuxguymarshall on 2008-11-29
I some setting I had to change in my BIOS before the Live Cd would load were 
Plug and Play OS = No
Video Adaptor - Onboard     instead of PCI



This version of Ubuntu is really a lot of trouble.

---

### Post by Mayhem77 on 2008-11-29
Try turning off power management in your BIOS, if its not already off.

Are you using the restricted drivers or the ones off NVIDIA's site?

---

### Post by linuxguymarshall on 2008-11-29
I have tried both power management settings. Right now I have nothing on this system except a fresh Ubuntu install but they were from restricted drivers. It wasnt a problem with the drivers themselves it was with Ubuntu.

---

### Post by Xiong Chiamiov on 2008-11-29
> **linuxguymarshall said:**
> Right now I have nothing on this system except a fresh Ubuntu install but they were from restricted drivers. It wasnt a problem with the drivers themselves it was with Ubuntu.

> **linuxguymarshall said:**
> I installed 8.10 correctly the other day but when I installed my NVIDIA drivers is stopped working.

> **linuxguymarshall said:**
> Currently using the intel integrated.

This is a bit confusing to me.  Did it all work fresh from the install?  If so, what did you do when it stopped working?  Have you always been using the integrated, rather than the NVIDIA card, or did you switch because you couldn't get something to work?

Also, have you tried installing, say kde, and having it set kdm to be on startup, rather than gdm?  It sounds to me like a gnome problem.

To install just the basic kde (which is all you want, since it's for testing purposes):
```

sudo aptitude install kde-core

```

---

### Post by linuxguymarshall on 2008-11-29
I was always using integrated because my hardware and 8.10 don't seem to like each other and Ubuntu hangs at the infamous 20% on the loading bar when I am using my NVIDIA card. So know that I have an NVIDIA card but im only using the intel card. I will deal with drivers when this is fixed.

---

### Post by linuxguymarshall on 2008-11-29
I don't want to install KDE but does anyone know the package name for Enlightment? I would like to install that as it would take less time.

---

### Post by Coreigh on 2008-11-29
I don't think this a GDM (or KDM or XDM) issue It is most likely a driver issue.

Did you try booting the LiveCD before installing? Does the LiveCD work?
Did you enable the restricted and multiverse sources in your /et/apt/sources.list? This can be done from the command line. simply remove the # from the front of the lines that start with deb and end in universe and multiverse. then do
```
sudo apt-get update
```
And
```
sudo apt-get upgrade
```
Finally
```
sudo dpkg-reconfigure xserver-xorg
```


You will need to enable the Proprietary Driver support too, sorry I don't know how from the command line. 

here is a link with more info:
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

EDIT:
Link for Enlightenment How-To:
[http://www.ubuntugeek.com/howto-install-e17-enlightenment-desktop-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-e17-enlightenment-desktop-in-ubuntu.html)

---

### Post by linuxguymarshall on 2008-11-29
It isnt a gnome problem, I know that.

---

### Post by Xiong Chiamiov on 2008-11-29
Single posts, man!

The package name is "enlightenment", and [is not in]("http://packages.ubuntu.com/search?keywords=enlightenment&searchon=names&suite=all&section=all") the intrepid repos.  You can search your package listing easily by using either
```

aptitude search ~n[text]

```
to search package names, or
```

aptitude search ~d[text]

```
to search descriptions.

If I knew how Ubuntu set up it's launching of things, then you could install any window manager, and just launch that.  Check if there is a ~/.xinitrc.  If so, you can try commenting out the line that's currently active, and add something like
```

exec fluxbox

```
if you install fluxbox.  Then when you run startx, fluxbox will launch.

I would also recommend renaming your ~/.gnome2 folder, so that gnome will create a new one from defaults on next boot.  If that works, then you know it's something in your gnome configuration.

EDIT:
Ah, my typing speed has decreased recently!
> **linuxguymarshall said:**
> It isnt a gnome problem, I know that.
How can you know for sure unless you try something else?  The most essential part of problem-solving is narrowing down which variable is causing the issue by swapping out every individual part that has anything to do with the problem.

Although driver issues are far more common, from your description, X is working just fine, since you're not getting a black or white screen, but the gnome tan one.

---

### Post by linuxguymarshall on 2008-11-29
Live CD did the same thing. I will try those commands

---

### Post by Xiong Chiamiov on 2008-11-29
> **linuxguymarshall said:**
> gnome loaded a light tan background then went black. It played the ubuntu theme (?) and just sat there with a white cursor.

Excuse me, I missed the went-to-black part.  It could perhaps be an X issue, then, although you still have a cursor...

You might want to attach your /var/log/Xorg.0.log.

---

### Post by linuxguymarshall on 2008-11-29
None of the previous solutions worked however I did try ```
gksudo nautilus
``` and lo and behold nautilus came up and the Ubuntu background loaded. Maybe that is a good start.

---

### Post by linuxguymarshall on 2008-11-29
ok. nothing seems to work. should I just wait to get a blank disc and use 8.04?

---

### Post by Xiong Chiamiov on 2008-11-29
> **linuxguymarshall said:**
> None of the previous solutions worked however I did try ```
gksudo nautilus
``` and lo and behold nautilus came up and the Ubuntu background loaded. Maybe that is a good start.

What about if you run nautilus without root permissions?  Have you tried running gnome-panel (I think that's the proper name)?

If nautilus will run, then it sounds less and less like a graphics driver issue and more like a gnome one.  I'd still suggest trying my previous suggestions, both of installing another DE/WM and of renaming your ~/.gnome2.  If you tried either (or both) of those, could you elaborate on what the results were?

> **Xiong Chiamiov said:**
> 
You might want to attach your /var/log/Xorg.0.log.

---

### Post by linuxguymarshall on 2008-11-29
> **Xiong Chiamiov said:**
> upload you xorg log

I can't. 

Renaming my gnome folder made it do the same thing

---

### Post by Xiong Chiamiov on 2008-11-29
You can access the Ubuntu forums using elinks, I know, so you should be able to log in and post with an attachment.  Otherwise, if you have a USB drive, you can transfer the file to the computer you're posting from.

---

### Post by linuxguymarshall on 2008-11-29
no im on the Ubuntu forums using Firefox

---

### Post by linuxguymarshall on 2008-11-29
But I cant do uploads because I can't select a window. I can only use the last opened window and another window covers the upload when I bring it up.

---

### Post by Xiong Chiamiov on 2008-11-29
(There's an edit button in the bottom-left of all your posts.)

Then install another window manager and launch that, whether it be fluxbox, openbox, xfwm, kdm, awesome, jwm, etc.  Of course, since ncurses doesn't really have popup windows, you can still use a text-based browser to avoid having that problem.

---

### Post by linuxguymarshall on 2008-11-29
ok. ill give fluxbox a shot. Ive heard it is great

---

### Post by Xiong Chiamiov on 2008-11-29
> **linuxguymarshall said:**
> ok. ill give fluxbox a shot. Ive heard it is great
It doesn't really matter whether you like it or not, as the point is to simply have a working window manager from which you can operate while trying to solve this problem.

Now, of course, if you end up finding that you enjoy its customizability better than Gnome, then you've found yourself a new window manager...

I'm an awesome fan myself, but I'd never recommend a tiling window manager to someone without a bit of time to learn how to use the darn thing.

---

