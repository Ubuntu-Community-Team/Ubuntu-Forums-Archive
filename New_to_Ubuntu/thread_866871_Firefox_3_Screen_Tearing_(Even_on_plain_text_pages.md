---
title: "Firefox 3 Screen Tearing (Even on plain text pages)"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Xolamee on 2008-07-22
When I scroll down in Firefox 3 (on any page) the graphics do some extreme tearing (like multiple riffs in the page where the display is jumbled), and I have to either refresh the page or hit ctrl+a to select all to make the screen refresh. I am running ubuntu and Advanced Desktop Effects Settings and I have an Nvidia graphics card that I used EnvyNg to setup. I've tried searching for the problem a lot but all I can find are pages on tearing in flash videos on ubuntu and that is not the problem. Flash videos play just fine. I have attached a screenie. Does anyone know what causes this? Thanks in advance.

---

### Post by paul101 on 2008-07-22
have you enabled accelerated graphics drivers




it happened with me on windows untill i installed the drivers for my graphics card :)

---

### Post by Xolamee on 2008-07-22
I installed the driver I currently have with EnvyNG (didn't really get what that is, but figured that was the best one). I can enable the accelerated graphics drivers in System>Administration>Hardware Drivers but when I do that my screen goes in to low graphics mode when I restart and I cant get resolution over 640x480.

---

### Post by Xolamee on 2008-07-23
Do I need to supply more information?

---

### Post by northern lights on 2008-07-23
Does it also happen when all extension are disabled, i.e. with a clean firefox?
--> Create a new profile and browse the same pages from there...

---

### Post by eragon100 on 2008-07-23
> **Xolamee said:**
> I installed the driver I currently have with EnvyNG (didn't really get what that is, but figured that was the best one). 

If you have envy, you have downloaded and installed the hardware-accelerated 3d drivers automatically, that's what envy is made for :wink:

Do you have an ATI card?

Screen tearing is a well-known problem with ATI in linux, but it has been solved by the latest open-source driver:

[http://www.phoronix.com/scan.php?page=news_item&px=NjU5NQ](http://www.phoronix.com/scan.php?page=news_item&px=NjU5NQ)

---

### Post by Xolamee on 2008-07-23
Its an Nvidia card...
I tried a clean profile and it seemed to be okay, but then again the problem is intermittent ... sometimes ill go for half an hour before it starts doing that again and I have to restart firefox a couple times.
The add-ons I have installed are
FireGestures
Google Bookmarks Button
StumbleUpon
Tab Wheel Scroll
Ubuntu Firefox Modifications
Its hard to test which one it is because I don't always have the problem. If anyone know which one causes this that would be great, in the meantime ill start testing them.

---

### Post by northern lights on 2008-07-23
> **Xolamee said:**
> in the meantime ill start testing them.
Good plan. I think it's fairly safe to assume it's the extensions, for reference check [this]("http://ubuntuforums.org/showthread.php?t=865052") thread.

---

### Post by Xolamee on 2008-07-24
Well apparently the issue also occurs in non-firefox programs too. In the Synaptic Package Manager it did the same thing in the description area. I don't think its the firefox plugins. Also of note, when I click anywhere on the panel the tearing immediately goes away.

---

### Post by northern lights on 2008-07-24
okay. That info is quite important to isolate the core of the problem. Have you reconfigured X?

If not, do this:

First, let's backup your current xorg.conf```
cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

Now, let's reconfigure the xserver:

Run ```
sudo /etc/init.d/gdm stop
``` from a terminal. You will be leaving the graphical environment, so remember the next two steps!

Press Alt+F1 to log in and execute ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart the interface with ```
sudo /etc/init.d/gdm start
```

Try to change resolution again.

In case something gets (even more) screwed, revert back with```
cp /etc/X11/xorg.backup /etc/X11/xorg.conf
```

---

### Post by GreenN00b on 2008-07-24
I once had a similar issue on an older hardware. It was fixed after I disabled the visual effects from System\Preferences\Display\Visual Effects.

Maybe this will temporary fix your display issues until you find a better solution ...

---

### Post by Xolamee on 2008-07-25
northern lights,
just to clarify... 
while using the "nvidia accelerated graphics card" that is installed from the System>Administration>Hardware Drivers i get the low graphics mode issues...
i should preform the fix you wrote out while in low graphics mode? and that will fix the problem with the resolution? and when i am using that hardware driver i should not have a problem with tearing?

also, is there a way to keep all my advanced desktop effect settings? everytime i play with the xorg file i lose all my customizations

---

### Post by northern lights on 2008-07-25
> **Xolamee said:**
> while using the "nvidia accelerated graphics card" that is installed from the System>Administration>Hardware Drivers i get the low graphics mode issues...
i should preform the fix you wrote out while in low graphics mode?Yes.

> **Xolamee said:**
> and that will fix the problem with the resolution? and when i am using that hardware driver i should not have a problem with tearing?Gee, I am going to refrain from promising anything, but it's likely it'll fix it.

> **Xolamee said:**
> also, is there a way to keep all my advanced desktop effect settings? everytime i play with the xorg file i lose all my customizations
Executing the above will not screw with your compiz preferences.

---

### Post by Xolamee on 2008-07-25
So I went into System>Administration>Hardware Drivers and enabled the driver. Then I log off and it goes to the login screen that looks all low res and warns me about running in low graphics mode. After I log in I followed your steps and had no errors. When I start /etc/init.d/gdm again it loads up a full res login screen and i logon and everything looks great, but if I go back into System>Administration>Hardware Drivers the driver is no longer enabled.

---

### Post by Xolamee on 2008-07-25
P.S.
I'm not sure why, but doing those steps resets my compiz preferences... it switches it back to 2 desktops and disables the rotating cube and all that. When I restore the xorg.backup all the settings come back.

P.S.S.
Just tried restoring xorg.backup and the settings didnt come back. And that backup was the original from before I started messing around with it.

---

### Post by northern lights on 2008-07-25
> **Xolamee said:**
> P.S.
I'm not sure why, but doing those steps resets my compiz preferences... it switches it back to 2 desktops and disables the rotating cube and all that. When I restore the xorg.backup all the settings come back.

P.S.S.
Just tried restoring xorg.backup and the settings didnt come back. And that backup was the original from before I started messing around with it.

Very sorry. Thought it did for me.

I suppose you'll have to go through configuring it once more. Again, apologies.

You can export/save a profile in compiz though (for future avoidance of this dismay). Check under "Preferences", button on the left hand side.

I don't quite get one thing though: If the resolution is fine, how is it a problem that proprietary drivers are disabled? Exactly what driver is running the device?
And foremost: Does the screen tearing persist?

---

### Post by Xolamee on 2008-07-28
No apology necessary northern lights. Thanks again for your help. Oddly enough, when I restore the xconf file it restored my compiz settings.

I'm assuming it didn't actually restore my settings though, I'm assuming what happened was when it was in low graphics mode the settings get cracked up, but when you revert back to normal your settings are still there. 

Either way I don't even know if the driver is the issue, although after tinkering so much with the display it seems to have at least started to happen less often. (And I am currently using the driver installed by EnvyNG again, but it still happens from time to time). 

I will probably end up reinstalling ubuntu after I've spent a pretty good amount of time "learning" (and by learning I mean breaking stuff and trying to fix it).

---

### Post by northern lights on 2008-07-28
> **Xolamee said:**
> after I've spent a pretty good amount of time "learning" (and by learning I mean breaking stuff and trying to fix it).
That's the spirit!

---

### Post by miggols99 on 2008-07-28
Heh. This reminds me of when it happened to me :-P

[http://ubuntuforums.org/showthread.php?t=396210](http://ubuntuforums.org/showthread.php?t=396210)

Compositing should fix it..but my old computer didn't support it.

---

