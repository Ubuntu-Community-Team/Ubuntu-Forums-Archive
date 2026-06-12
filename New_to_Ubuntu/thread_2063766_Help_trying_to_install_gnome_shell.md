---
title: "Help trying to install gnome shell"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by martinjustin on 2012-09-27
I am trying to install Gnome shell. When doing internet searches I found some screenshots that showed that it had a nice UI. For example : [http://www.gnome.org/gnome-3/](http://www.gnome.org/gnome-3/). It looks great.

However when I install it, it looks nothing like the screen shots. Its simple and bland looking. here is a screen shot. [http://i.imgur.com/3tbhB.png](http://i.imgur.com/3tbhB.png)

So, what am I doing wrong here? Thank you.

---

### Post by cbanakis on 2012-09-27
I think the link your looking at is actually a gnome distro.

Looks pretty cool, downloading now.

Gnome Shell is a add on for Ubuntu in place of Unity.

Used to be the default environment, but for whatever reason, the powers that be decided to go with Unity as of Ubuntu 11.04.

I'm sure you can get the same result in Ubuntu by changing tons of settings, but its probably easier to install the distro instead of Ubuntu.

[http://www.gnome.org/getting-gnome/](http://www.gnome.org/getting-gnome/)

Don't let the instructions under the download link confuse you.

Thats just listing a complicated way to make a usb flash drive installer.

All it is, is an iso like anything else.

---

### Post by NikTh on 2012-09-27
Hi , 

first of all , from the screenshot you attached , I can understand that you must reboot , so updates could be installed (red gear like icon up left) :) 

If you installed gnome-shell correctly then you must select "Gnome" from login window. At login box (where you write your username & password) click the little Ubuntu icon and from the dropdown menu select gnome. 

Thanks

---

### Post by jerrrys on 2012-09-27
That pic of your install is gnome-classic (also called gnome-fallback), not gnome-shell.

---

### Post by cbanakis on 2012-09-27
Confirmed.

Just installed the gnome disto.  Looks exactly like the screenshot.

See my screenshot?



> **cbanakis said:**
> I think the link your looking at is actually a gnome distro.

Looks pretty cool, downloading now.

Gnome Shell is a add on for Ubuntu in place of Unity.

Used to be the default environment, but for whatever reason, the powers that be decided to go with Unity as of Ubuntu 11.04.

I'm sure you can get the same result in Ubuntu by changing tons of settings, but its probably easier to install the distro instead of Ubuntu.

[http://www.gnome.org/getting-gnome/](http://www.gnome.org/getting-gnome/)

Don't let the instructions under the download link confuse you.

Thats just listing a complicated way to make a usb flash drive installer.

All it is, is an iso like anything else.

---

### Post by martinjustin on 2012-09-27
What is a distro? A completely new OS? I found gnome shell while googling a UI replacement for Ubuntu. I was under the impression that this UI would run over Ubuntu.

By the way - I restarted and when I got back on, the login screen UI had changed. I made sure "GNOME" was selected (not gnome classic) next to the login button, then logged in. It still looks like my screenshot.

Oh, and I originally downloaded Gnome under the "distributions" section here [http://www.gnome.org/getting-gnome/](http://www.gnome.org/getting-gnome/)

---

### Post by martinjustin on 2012-09-27
> **cbanakis said:**
> Confirmed.

Just installed the gnome disto.  Looks exactly like the screenshot.

See my screenshot?


Ok I downloaded the .iso. How do I install it without a USB?

---

### Post by newb85 on 2012-09-27
Stop the bus!

Yes, what you have downloaded is the install .iso for a distro that has Gnome Shell instead of Unity.  

Installing the Gnome Shell on your current install should give you the different UI you're looking for.  Unless you haven't invested much time in your current system, you're probably better off troubleshooting why it's loading the wrong shell.

First of all, what are your system specs?  If they're not high enough, your system would automatically switch to fallback when you log in.  (This won't be any different if you re-install the entire system from the .iso you've downloaded.)

Second, how did you install the Gnome Shell?  (i.e., what packages did you install, and did they come from the repos or somewhere else?)

---

### Post by martinjustin on 2012-09-27
> **newb85 said:**
> Stop the bus!

Yes, what you have downloaded is the install .iso for a distro that has Gnome Shell instead of Unity.  

Installing the Gnome Shell on your current install should give you the different UI you're looking for.  Unless you haven't invested much time in your current system, you're probably better off troubleshooting why it's loading the wrong shell.

First of all, what are your system specs?  If they're not high enough, your system would automatically switch to fallback when you log in.  (This won't be any different if you re-install the entire system from the .iso you've downloaded.)

Second, how did you install the Gnome Shell?  (i.e., what packages did you install, and did they come from the repos or somewhere else?)

My system specs should be high enough, I have a brand new laptop w/ core i5 and a mid range video card. Although Ubuntu seems to be having trouble installing my video drivers.

I downloaded gnome from the link in my previous post. It redirects to the Ubuntu Software Center where it's listed as simply "gnome"

---

### Post by jerrrys on 2012-09-27
Its like newb85 said, it will automatically go to gnome-fallback if it does not detect the proper setup.  And this also applies to unity-desktop, it will go to 2d instead of 3d.  What video card/driver are you running? Could be whats hanging you up.

---

### Post by HiImTye on 2012-09-28
Gnome Shell switched to 'fallback mode' or 'Gnome (Classic)' without the presence of the required 2D and 3D capabilities. that is the mode that you are in. unless you sort out your video issues, even if you switch to that other distro, you will not have the 'Gnome Shell' that you are trying to get. first off, try going to 'Additional Drivers' and see if there is a proprietary driver for you to use. if there is, activate it and reboot. you should get the 'Gnome Shell' that you are after.

---

### Post by cbanakis on 2012-09-28
> **martinjustin said:**
> Ok I downloaded the .iso. How do I install it without a USB?

If you do not already know, an iso is a cd or dvd image file.

All you need to do is burn it to a cd, then have your computer boot to the cd.

You should have brasero on your Ubuntu computer.

Just open that, and click on "Burn Image" in the lower left.

The select the iso, put a cd in , and burn.

It is a live cd, so it will load directly without installing anything.

I have not had a chance to attempt to install it, but I'm sure there are instructions to make it a permanent install.

---

### Post by martinjustin on 2012-09-28
Hey guys, thanks for the help, I figured it out. It was my video drivers. Everything works fine when I install Ubuntu fresh, but when I go to "Additional Drivers" and install the recommended drivers it messes everything up.

Anyway, does anyone have any suggestions for customizing the Ubuntu UI? I liked Gnome shell but it lacks a task bar which was kind of important, and I like Unitys integration of rhythmbox into the volume control, so I switched back.

I would rather just have a different looking taskbar and custom icons (i.e. I am not really fond of the black/orange color scheme.) I would also like to have a transparent Menu bar at the top of the screen (sorry, not sure what it's called)

---

### Post by Colo993 on 2012-09-28
The screenshot of your current desktop (Gnome classic) is what I get when I've updated Ubuntu and my Nvidia drivers need to be re-installed.  After they are re-installed, I get the "normal" looking Gnome 3 desktop.

Colo993

---

### Post by newb85 on 2012-09-28
> **martinjustin said:**
> Anyway, does anyone have any suggestions for customizing the Ubuntu UI? I liked Gnome shell but it lacks a task bar which was kind of important, and I like Unitys integration of rhythmbox into the volume control, so I switched back.

I would rather just have a different looking taskbar and custom icons (i.e. I am not really fond of the black/orange color scheme.) I would also like to have a transparent Menu bar at the top of the screen (sorry, not sure what it's called)

You could start by trying out different Themes (in the Appearance dialog).  Only a few are installed by default, but more can be added.  (It doesn't take much googling to find them...)

One last thought, have you looked at Cairo-Dock?  When you install it, it sets itself up as an alternative DE to Unity.  (You can also run both at the same time, if you really want...)

---

### Post by jerrrys on 2012-09-28
[gnome-tweak-tool]("https://www.google.com/search?q=gnome+tweak+tool+ubuntu+12.04&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

---

