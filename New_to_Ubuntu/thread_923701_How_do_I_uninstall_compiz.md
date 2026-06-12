---
title: "How do I uninstall compiz?"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by tc101 on 2008-09-18
How do I uninstall compiz?

---

### Post by Sef on 2008-09-18
1) What version of Ubuntu do you have?

2) How did you install it?

---

### Post by tc101 on 2008-09-18
I have hardy.  

I installed compiz by creating a launcher on the desktop and giving it the command "compiz".

If I go to system/Administration/System monitor/Processes,  I see:

compiz  sleeping
compiz-decorato sleeping
compiz.real  sleeping

---

### Post by KIAaze on 2008-09-18
Doesn't ```
sudo apt-get remove compiz compiz-gnome
``` work?

Or more radically, remove all packages related to compiz:
```
dpkg -l | grep compiz | awk '{print $2}' | xargs sudo apt-get remove
```

I made a simulation and it doesn't seem to remove any vital packages.
Of course you should check first.
You can simulate it this way:
```
dpkg -l | grep compiz | awk '{print $2}' | xargs sudo apt-get **-s** remove
```

> I installed compiz by creating a launcher on the desktop and giving it the command "compiz".
Does that mean you installed it from source?

---

### Post by Therion on 2008-09-18
If you're using gnome...```
sudo apt-get remove compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```should do it.  

Then, to delete your configuration, delete the ~/.compizconfig and ~/.compiz folders.

Might wanna wait until someone can confirm it all, but that should give you a pretty clean, thorough, un-install of Compiz Fusion.

---

### Post by tc101 on 2008-09-18
> Quote:
I installed compiz by creating a launcher on the desktop and giving it the command "compiz".

Does that mean you installed it from source?

I don't know what installing it from source means.  Is it possible that it was automatically installed when Hardy was installed, or along with something else?  

Would creating a launcher on the desktop and giving it the command "compiz" even install it?  

Does seeing the following prove that it is installed:

> If I go to system/Administration/System monitor/Processes, I see:

compiz sleeping
compiz-decorato sleeping
compiz.real sleeping 

---

### Post by tc101 on 2008-09-18
> If you're using gnome...

How do I know if I am using gnome?  Is it installed when you install Hardy?

---

### Post by KIAaze on 2008-09-18
> **tc101 said:**
> How do I know if I am using gnome?  Is it installed when you install Hardy?
Yes, it's the default "Desktop environment" of Ubuntu.
So if you don't know, you're probably using Gnome. :)

> **tc101 said:**
> I don't know what installing it from source means.  Is it possible that it was automatically installed when Hardy was installed, or along with something else?  

Yes, compiz is installed by default on Hardy (and later versions).
If you don't know what installing from source means, it means it was installed through packages and therefore the commands given above with "apt-get" should work to remove it.

> **tc101 said:**
> Would creating a launcher on the desktop and giving it the command "compiz" even install it?
No, a launcher is just like the desktop shortcuts in Windows.
It's just a shortcut and doesn't necessarily mean that the program is installed.

> **tc101 said:**
> Does seeing the following prove that it is installed:
Yes, but a better way is the following:
```
dpkg -l | grep compiz
```
You can also check this by starting Synaptic:
```
System->Administration->Synaptic Package Manager
```
and then doing a search for "compiz"

Since you seem to be quite new to Ubuntu, I recommend looking at this site:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And more generally this sticky:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by mc4100 on 2008-09-18
Do you really need to un-install it?
Compiz can simply be turned off in System -> Administration -> Appearance, in the Visual Effects tab.

---

### Post by tc101 on 2008-09-19
> Do you really need to un-install it?
Compiz can simply be turned off in System -> Administration -> Appearance, in the Visual Effects tab.

I don't have System -> Administration -> Appearance on my system, but I do have System -> Preferences -> Appearance.  However, under System -> Preferences -> Appearance, the Visual Effects tab only has 3 settings.  There are 3 radio buttons, "None", "Normal" and "Extra".  I am currently set to "Normal"

---

### Post by Elfy on 2008-09-19
Should be off then - and you have the correct menu there. As long as it's off then none should be running.

---

### Post by tc101 on 2008-09-19
I may not even need to uninstall compiz.  My problem is a sporadic flicker on the screen that I am trying to fix..  About 1/3 of the time when I boot up, I get a flicker that comes about once every 15-30 seconds, making a flash on the screen.  I can usually get rid of it by rebooting.  I am just trying to isolate the error and the first thing I wanted to try was removing compiz.

---

### Post by Elfy on 2008-09-19
I would check that the graphics card if you have one is fitted correctly, I assume that you have the driver installed for the card, check the cables and maybe try another monitor if you have one as well.

If you are getting the problem with 'None' effects then it isn't having compiz I would say.

It might also have been better to have said that in your first post ;)

---

### Post by Dyqik on 2008-09-19
compiz is only off if "None" is selected in the Visual Effects tab.

There's no need to uninstall compiz though, just switch it off.

Switching it off may help if the flicker is being caused by an overheating graphics card.  The other probable causes of the flicker that I can think of right now are a loose or damaged monitor cable or socket on either the monitor or computer, or maybe a dodgy screen resolution/timing setting.  

How old is the monitor (and what type), and does it get auto-detected if you go to System->Preferences->Screen Resolution?

---

### Post by tc101 on 2008-09-19
> It might also have been better to have said that in your first post

You are right.  I was trying to figure this out on my own, but made it more complicated by not mentioning everything from the start.

---

### Post by tc101 on 2008-09-19
> How old is the monitor (and what type), and does it get auto-detected if you go to System->Preferences->Screen Resolution?

It is a Dell flat panel, about a year old.  

It does not get auto detected at System->Preferences->Screen Resolution.  That says it is "Unknown".

---

