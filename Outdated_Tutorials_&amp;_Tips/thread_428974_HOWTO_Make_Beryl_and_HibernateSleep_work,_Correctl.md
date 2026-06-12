---
title: "HOWTO: Make Beryl and Hibernate/Sleep work, Correctly"
date: 2007-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Darwin Award Winner on 2007-04-30
How to stop Beryl from putting your sleeping computer in a coma.

REQUIREMENTS: 
ACPI power-management. If you don't know what you have, you probably have ACPI. This fix can probably be made to work with APM instead of ACPI, but I have no way of developing such an adaptation.
Any version of Beryl Manager that responds correctly to the USR2 signal. Any relatively recent version should do this. This fix was developed on Edgy, and I'm now using it on Feisty, so at least the Beryl versions in those two should probably work.

(If you just want the fix, skip down to procedure. If you want to understand it, keep reading.)

BACKGROUND & PROBLEM: It is well known that Beryl and suspend to RAM/Disk have never played well together. Usually, suspending while Beryl is running causes the computer to crash either while suspending or while resuming, in both cases requiring a hard reboot. There are a number of ugly hacks floating around to deal with this. Most of them involve killing Beryl on suspend, and then restarting it upon resume. The methods that these scripts use to get Beryl to restart using the correct user, on the correct screen, and with various other parameters, are inelegant at best. Some involve saving the user and display to a file and then restoring the info, or other odd tricks. Almost invariably, these scripts assume that only one instance of Beryl is running, and won't work for multiple instances.

So, is there a better way? Until recently, there wasn't. But a month or two ago, the Beryl developers added in a feature to Beryl Manager that allows it to handle all of this. All you have to do is send it a special signal once at suspend, and once at resume. My solution uses this feature, and lets Beryl Manager do all the dirty work. ACPI is used to send these signals at the right times.

PROCEDURE: 
Preparation: First of all, you need to have Beryl Manager running, since this fix relies on it. It's that little ruby tray-icon. You should set it to start when you log in, so that it's always running.

First, create the file [FONT="Lucida Console"]/etc/acpi/suspend.d/06-beryl-stop.sh[/FONT] with the following contents:
```
#!/bin/sh

# SIGUSR2 tells it to switch to alternate WM
pkill -USR2 beryl-manager

# and just to make sure beryl dies
pkill '^beryl$'
pkill -KILL '^beryl$'
```
Then, create the file [FONT="Lucida Console"]/etc/acpi/resume.d/97-beryl-start.sh[/FONT] with the following contents:
```
#!/bin/sh

# SIGUSR2 tells it to switch back to beryl
pkill -USR2 beryl-manager
```

Now, make both of them executable, and make sure both are owned by root:
```
sudo chmod +x /etc/acpi/suspend.d/06-beryl-stop.sh /etc/acpi/resume.d/97-beryl-start.sh
sudo chown root:root /etc/acpi/suspend.d/06-beryl-stop.sh /etc/acpi/resume.d/97-beryl-start.sh
```

That should be it.

HOW IT WORKS:
It's pretty simple. As you might expect, the scripts in /etc/acpi/suspend.d and /etc/acpi/resume.d are executed when the computer suspends and resumes, respectively. Each of the scripts above sends the USR2 signal to all beryl-manager processes. So, if you have multiple users logged in, each running their own Beryl and Beryl-Manager (God help your display card!), this solution should still work, because the pkill program sends the signal to all matching programs. (Don't worry about the name; pkill is a program for sending signals. It just so happens that the most commong use of signals is to kill programs, thus the name.) However, I can't guarantee this, because I don't have a multi-user setup.
Additionally, the suspend script ensures that Beryl is killed, forcefully if necessary, just in case sending the USR2 signal fails to kill Beryl (for example, if Beryl Manager isn't running). This *should* ensure that even in the worst case, Beryl gets killed before suspending, so you don't end up with a comatose computer. (However, as usual, no guarantee.)

Possible Pitfalls: 
As described in this thread: [http://forum.beryl-project.org/viewtopic.php?f=39&t=827&hilit=&sid=fc49588857d6375ee11ae167a3f4cb53](http://forum.beryl-project.org/viewtopic.php?f=39&t=827&hilit=&sid=fc49588857d6375ee11ae167a3f4cb53), the earliest versions of Beryl that supported the USR2 signal had a big problem: if you hit suspend when Beryl *wasn't* running, the signal would cause it to *start* right before suspending! Newer versions have fixed this problem: the USR2 signal will only cause Beryl Manager to restart Beryl if it was the USR2 signal that originally told it to stop beryl.
If Beryl isn't what's causing your computer to crash/fail to suspend/whatever, then this fix probably won't help. Please be sure that Beryl is the problem.
The process of killing and restarting Beryl often results in some movement of windows.
On my laptop, Gnome Power Manager always informs me that suspend has failed when I resume. Obviously, it's wrong. I don't know if this involves my Beryl fix or something else.

---

### Post by fmaste on 2007-05-31
I make it work on my DELL inspiron 9400 doing this (no script needed)

- Disable "Sync To VBlank" in beryl.
It is located on general options of the veryl manager. Just unckeck it.

- Update your /etc/X11/xorg.conf and add an "Option "NvAGP" "1" line in the "Section "Device":
(must look like this)
Section "Device"
...
Option "NvAGP" "1"
EndSection

- Disable warm-booting the video hardware on resume by editing your /etc/default/acpi-support as follows :
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

Good luck!!

NOTE: I'm using feisty with beryl installed from the beryl repos, all the other setting are the default ones (I never manually edit xorg.conf or acpi-support and beryl setting were are the default ones) and suspend/hibernate was working out of the box without beryl.

---

### Post by Darwin Award Winner on 2007-06-01
Thank you, that worked perfectly. It's better than my solution because it never even has to touch the beryl process, so there's no funny disappearing and reappearing of window borders and movign of windows during suspend/resume. Would you mind if I updated my first post to use this method?

Also, how did you discover this combination of tweaks, and do you know which of the tweaks or combinations of tweaks is responsible for the fix?

On a side note, for anyone who has implemented my method and is now looking to use this method, you'll have undo my solution.

---

### Post by Onesimus on 2007-06-01
I have a DELL Inspiron 6400 and are running Beryl.  I have been unable to send my laptop to sleep or hibernate on Feisty.  I implemented the method described by modifying as suggested above.

Sleep now works fine !
Hibernate doesn't.  It reboots just as normal (i.e. gives options to select which operating system I would like to reboot from [I have dual boot facility with Vista - I know, I know]) - gets stuck on the orange bar and then my screen flashes rapidly black and white.

So big improvement to what I originally had, but still not quite perfect.

---

### Post by Darwin Award Winner on 2007-06-01
If you're using my solution, then beryl is not the cause of your hibernate problem, at least not directly, since my solution makes sure that beryl isn't running at all during suspend. It is possible that on your computer, 3D graphics don't work in general after a hibernate and resume. Try hibernate/resume without beryl and make sure that works. Other than that, I can't really help you. There are lots of threads about getting hibernation working.

---

### Post by fmaste on 2007-06-02
> **Darwin Award Winner said:**
> Thank you, that worked perfectly. It's better than my solution because it never even has to touch the beryl process, so there's no funny disappearing and reappearing of window borders and movign of windows during suspend/resume. Would you mind if I updated my first post to use this method?

Also, how did you discover this combination of tweaks, and do you know which of the tweaks or combinations of tweaks is responsible for the fix?

On a side note, for anyone who has implemented my method and is now looking to use this method, you'll have undo my solution.

There's no problem if you update you post, please update it! that's it the Ubuntu community for

When I freshly install Feisty I decided that suspend/hibernate was very useful for me, more than beryl, so I did not install beryl. But I missed the desktop effects I used to have on edgy (beryl without suspend/hibernate). Also I dislike the idea of the scripts, suspend/hibernate does not work in a transparent way.
I started searching (googling)
I found some post telling about disabling "Sync To VBlank" and tried it without success. After some reading it doesn't make sense to me that beryl was the real cause of the problem (all the data is saves to disc and back again at resume). I tried the different workaround for suspend/hibernate (not beryl related). hopefully my second test worked and here it is for all of you with the same problem.
I really don't know if some of the options are not needed, it just worked!!

Enjoy!

---

### Post by fmaste on 2007-06-02
> **Onesimus said:**
> I have a DELL Inspiron 6400 and are running Beryl.  I have been unable to send my laptop to sleep or hibernate on Feisty.  I implemented the method described by modifying as suggested above.

Sleep now works fine !
Hibernate doesn't.  It reboots just as normal (i.e. gives options to select which operating system I would like to reboot from [I have dual boot facility with Vista - I know, I know]) - gets stuck on the orange bar and then my screen flashes rapidly black and white.

So big improvement to what I originally had, but still not quite perfect.

Were you able to suspend/hibernate without beryl when you just installed Ubuntu?
I have a DELL Inspiron 9400 and suspend/hibernate worked out of the box. It also worked with Inspiron 6400. I installed Ubuntu at my friends laptop (Inspiron 6400) and is also working fine.
Maybe you change some configuration file that you shouldn't.

Seeing the menu to select you operative system at resume does not mean that hibernate is not working, thats normal. Suppose you hibernate Ubuntu and the next time you turn on your computer you want to use Windows (To play some games), without this menu you won't be able.

Also, if you are hibernating closing you laptop lid, make sure that you set your Ubuntu to do that when closing the notebook. Check it at System->Preferences->Power Management

---

