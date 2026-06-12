---
title: "Ubuntu 11.10 Freezes after login screen"
date: 2011-07-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by orvillezee on 2011-07-25
After I select my user account, it freezes (but with moveable pointer)
I've tried recovery mode - dpkg, but seems nothing repaired (0 result each problems)
I've reinstalled 3 times, but it still happens

My Laptop specification :
> Intel core i3 M350 2.26GHz
RAM 3072MB DDR3
ATi Mobility Radeon HD 4500 512MB
HDD 320GB
Previous OS : (alongside) Windows 7 Ultimate x64

---

### Post by quique1hn on 2011-07-25
I have de same problem, to enter I select other, then enter mi user name and password

---

### Post by nataraj88 on 2011-07-25
I have the same problem running under vmware workstation 7.1.4 using this CD:
 oneiric-desktop-amd64.iso           25-Jul-2011 08:27  714M  Desktop CD for 64-bit PC (AMD64) computers (standard download)

Live boot works fine.

Nataraj

---

### Post by ubrox on 2011-07-26
good to know its not just me.

---

### Post by mrinsult2000 on 2011-07-26
I just posted this.  About the same thing?

[http://ubuntuforums.org/showthread.php?t=1812503](http://ubuntuforums.org/showthread.php?t=1812503)

Thanks

---

### Post by sgage on 2011-07-26
> **mrinsult2000 said:**
> I just posted this.  About the same thing?

[http://ubuntuforums.org/showthread.php?t=1812503](http://ubuntuforums.org/showthread.php?t=1812503)

Thanks

If you log in by clicking "other", then giving your userid/password, it should work normally afterwards. At least it has for me.

---

### Post by PhantmKllr on 2011-07-26
> **sgage said:**
> If you log in by clicking "other", then giving your userid/password, it should work normally afterwards. At least it has for me.
Yeah, I've been having to do this as well. It all should be fixed before the beta though (hopefully).

---

### Post by David Tomic on 2011-07-28
> **PhantmKllr said:**
> Yeah, I've been having to do this as well. It all should be fixed before the beta though (hopefully).


Hmmm ... this doesn't seem to be working for me.

Even logging in as suggested, I just end up with a blank desktop.  Mouse still works, but absolutely nothing else ...

EDIT: Just finished installing all of the updates released today (there were quite a few), but it's still not working! :(

---

### Post by cariboo on 2011-07-28
This may be a simple thing, but I had the same problem after installing Lubuntu on my netbook last night. Make sure you are selecting a session before logging in.

---

### Post by David Tomic on 2011-07-29
> **cariboo907 said:**
> This may be a simple thing, but I had the same problem after installing Lubuntu on my netbook last night. Make sure you are selecting a session before logging in.

Tried that ... and I still have the same problem (no matter which session I choose).

---

### Post by David Tomic on 2011-07-30
Any more ideas / suggestions, because I still haven't managed to get this system up and running yet ...

---

### Post by PhantmKllr on 2011-07-30
> **David Tomic said:**
> Any more ideas / suggestions, because I still haven't managed to get this system up and running yet ...
You'll probably just have to wait it out.

The problem probably won't be fixed until the beta stage...

---

### Post by pulpo69 on 2011-07-30
i installed xfce. mow i can choose xfce-session (works).
ubuntu session freezes all the time.

---

### Post by David Tomic on 2011-07-30
> **pulpo69 said:**
> i installed xfce. mow i can choose xfce-session (works).
ubuntu session freezes all the time.

Thanks ... I'll give that a go and see what happens ...

---

### Post by David Tomic on 2011-07-31
Well ... no joy with xfce either ....

:(

---

### Post by cariboo on 2011-07-31
Can you get to the desktop, if you start in recovery mode, and select resume from the menu, then log in on the command line and type:

```
startx
```

---

### Post by David Tomic on 2011-07-31
> **cariboo907 said:**
> Can you get to the desktop, if you start in recovery mode, and select resume from the menu, then log in on the command line and type:

```
startx
```

Once I run startx, I just get a black background with a popup error message saying "Failed to load session "gnome""

If I click the logout button (which is the only button there is) the system just hangs again.  Mouse pointer still works fine (same as before), but everything else is dead.

---

### Post by Yahoé on 2011-08-01
Think it has something to do with Lightdm and the greeter / liblightdm version.

From the recovery session, remove lightdm, lightdm-gtk-greeter and liblightdm-gobject-0-0.

Update then reinstall lightdm which will also installs [FONT=Fixedsys]lightdm-gtk-greeter, [/FONT][FONT=Fixedsys]liblightdm-gobject-1-0 all [/FONT][FONT=Fixedsys]version 0.9.2-ubuntu4.
Reboot and you should be back in business.

[/FONT]

---

### Post by trungvkvk on 2011-08-01
good to know its not just me

---

### Post by David Tomic on 2011-08-01
> **Yahoé said:**
> 
Reboot and you should be back in business.

I'm afraid not.  

I've actually already tried that (after reading it in another thread) but unfortunately it hasn't helped my situation at all ...

:(

---

### Post by cariboo on 2011-08-01
Do you have gnome-shell or gnome-session-fallback installed, if not, that's why you're getting the can't start gnome error.

---

### Post by David Tomic on 2011-08-01
So ... I may have just *accidentally* discovered something interesting.

Instead of hitting the "Other" link on the login screen (as I've been doing for the past few days), I just (accidentally) clicked on "Guest Account" ... and lo and behold the darn thing just logged straight in.

Desktop loaded, Unity loaded, all my drives are mounted and everything (that I've tried so far) is running just fine.

Seems a bit odd, doesn't it?

EDIT: I'm curious to know if the same thing happens to anyone else who's also having the same problem!

---

### Post by 3rdalbum on 2011-08-01
I had this problem, or at least a similar problem. I've worked around it.

I hit Control-Alt-F1, log in, and type:

```
sudo apt-get install gdm
```

Afterwards it asks you which display manager to use by default; choose gdm.

Now type:

```
sudo service lightdm stop
sudo service gdm start
```

You should be able to log in with GDM now. If you want to test out lightdm at some point in the future to see if it's working again, type:

```
sudo service gdm stop
sudo service lightdm start
```

When the lightdm problem is fixed, you can remove gdm and it should default back to using lightdm; if not you can manually start it.

---

### Post by grahammechanical on 2011-08-02
I have just followed the instructions given by 3rdalbum and they work. I am now back into Oneiric alpha 2. Thank you.

Regards.

---

### Post by madmcphil on 2011-08-09
No luck with the above fix for me.  says i have latest gdm. No matter if i :confused:choose any dm i cant get passed the login

---

### Post by TDK800 on 2011-08-10
Same problem here... with lightdm Guest account works, user account didn't, and with gdm user account logs in, but only gives blank purple background with Nautilus top menu.

---

### Post by novatillasku on 2011-08-10
I start with recovery mode, as root, and write startx, but there's no launcher.
I think after work in Unity 2D.
Install uploaders, but no work in unity 3D.
And there's no daily yesterday and no today.

---

### Post by tricky76 on 2011-09-05
Is there a fix for this issue? I just upgraded to 11.10 and ran all the updates today and my session is freezing about 2-3 minutes after showing the login in screen.

---

### Post by Harry33 on 2011-09-06
> **tricky76 said:**
> Is there a fix for this issue? I just upgraded to 11.10 and ran all the updates today and my session is freezing about 2-3 minutes after showing the login in screen.

What is the issue you are talking about (how does it freeze, do you see panels, background)?
Which architecture did you install (32-bit, 64-bit)?
What session are you using (if the session is gnome, do you have gnome-shell installed)?
What is your graphics card? What graphics drivers are you using?

---

### Post by tricky76 on 2011-09-06
> **Harry33 said:**
> What is the issue you are talking about (how does it freeze, do you see panels, background)?
Which architecture did you install (32-bit, 64-bit)?
What session are you using (if the session is gnome, do you have gnome-shell installed)?
What is your graphics card? What graphics drivers are you using?


I log in and everything loads up.  After about a minute or so the desktop just freezes. 
32-bit architecture
I am using the default Unity-3d.  Login is lightdm.
Graphics card is nvidia

thanks,
-t

---

### Post by bmbaker on 2011-09-06
ya i am getting the same thing with gdm and gnome-shell !
I am using 32-bit and intel graphics card
can't log out or anything!
sudo service gdm stop
sudo service gdm start
or a full reboot!

one thing i noticed though it takes a long time to log out when its still wking!

---

### Post by bmbaker on 2011-09-06
hmmm i switched back to lightdm and it seems to have solved itself!

ooops spoke too soon !

---

### Post by ScislaC on 2011-09-07
I have been having the same issue and saw an updated lightdm in Synaptic today. So I did a dpkg-reconfigure lightdm, installed the update, restarted, and boom it finally got to the desktop instead of hanging at the black screen.

Hopefully this update really did bring about a permanent fix.

---

### Post by tejaaus on 2011-10-07
I have faced the same issue on VMware workstation. After Google I got below guide & it works for me.. might this will help others..

:)

[http://www.mytricks.in/2011/10/guide-installing-ubuntu-1110-oneiric-in.html](http://www.mytricks.in/2011/10/guide-installing-ubuntu-1110-oneiric-in.html)

---

