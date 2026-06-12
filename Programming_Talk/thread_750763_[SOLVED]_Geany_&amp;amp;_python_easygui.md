---
title: "[SOLVED] Geany &amp;amp; python easygui"
date: 2008-04-09
forum: Programming Talk
---

### Post by rabbitman on 2008-04-09
I've made a short test routine in python using easygui, which does nothing more than display a messagebox on the screen.

I've also set PYTHONPATH in my .bashrc file so easygui can be found.

If I run the following from a terminal the program I've written works correctly.

```
python test.py
```

If I try and run the program in geany however, I get an ImportError message telling me that the easygui module cannot be found.

Can anyone offer any help? :(

---

### Post by dwblas on 2008-04-10
You'll have to use a sys.path.append("/path/to/easygui").  Geanly can't find it.  First, did you reboot after adding the path to PYTHONPATH? Second, print sys.path, which will tell you if the path has been added (and check for typos).  Third, being a general text editor, it's possible that Geany doesn't use PYTHONPATH for python specific things.

---

### Post by rabbitman on 2008-04-10
Thank's for trying to help. :KS

I'd already tried the sys.path.append thing & it didn't work. :(

The problem appears to be a Linux one, as I own an Ubuntu / Vista Dualboot. I've got Geany & [DrPython](http://drpython.sourceforge.net/index.php) installed on both operating systems. EasyGui is on the PYTHONPATH in Vista & everytime I run my test program it works.But when I try running my program in Ubuntu neither Geany or DrPython can locate easygui on the PYTHONPATH.

---

### Post by LaRoza on 2008-04-10
> **rabbitman said:**
> Thank's for trying to help. :KS

I'd already tried the sys.path.append thing & it didn't work. :(

The problem appears to be a Linux one, as I own an Ubuntu / Vista Dualboot. I've got Geany & [DrPython](http://drpython.sourceforge.net/index.php) installed on both operating systems. EasyGui is on the PYTHONPATH in Vista & everytime I run my test program it works.But when I try running my program in Ubuntu neither Geany or DrPython can locate easygui on the PYTHONPATH.

Put the easygui.py in the same directory as your script then.

---

### Post by WW on 2008-04-10
> **dwblas said:**
>  First, did you reboot after adding the path to PYTHONPATH? 
*Reboot?* Nah, this is not windows.  At worst he could log out and log in.  If that doesn't work, rebooting won't help.

---

### Post by WW on 2008-04-10
If you are using gnome (i.e. the standard Ubuntu, not, say Kubuntu, Xubuntu, etc), and you are starting Geany from a gnome menu (and not from the command line), try setting the environment variable in the file .gnomerc.   (That used to work, but I'm not sure it still does.)  If that doesn't work, try .xsession. (Be sure to save a backup before you go mucking around with these files.)  You might have to log out and log in again for the change to take effect.

EDIT:  ... or maybe .xprofile, or .xinitrc, or ...?  Sorry, I only have access to an Ubuntu server with no X at the moment, so I can't test it, and trying to find a definitive answer by googling has been fruitless.

---

### Post by rabbitman on 2008-04-10
Thank's for everyone who tried to help, the problem is now solved. :)

I found [this](http://ubuntuforums.org/showthread.php?t=724070) thread on the forum regarding someone who was having Java classpath trouble in Geany. 

Based on what I read there, I added the PYTHONPATH variable to the file located at /etc/profile. I rebooted my computer & the easygui program I wrote worked first time.

---

### Post by dwblas on 2008-04-12
Thanks for posting the solution.  It's interesting that Geany is reading a system-wide profile file and seemingly ignoring the user's .bashrc.  This will likely come up again, and may be pertinent to other programs as well.

---

### Post by rabbitman on 2008-04-13
Thank's for the comment, so far only [Geany](http://geany.uvena.de/) & [DrPython](http://drpython.sourceforge.net/) appear to have this problem.

Thread marked as solved. :)

---

