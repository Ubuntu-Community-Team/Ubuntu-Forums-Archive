---
title: "Unity Tweak Tool install error"
date: 2018-08-10
forum: New to Ubuntu
---

### Post by ubantunovice2 on 2018-08-10
Running Ubuntu 18.04.1 in a wirtualbox in Windows 10.  Looking for a tool to configure the launcher bar, etc I found "Unity  Tweak Tool" which installed fine. But when I tried to launch it I got an  error about missing packages (see attached). How do I correct this? Is  there a better utility to use?  I think I figured it out. The book I am learning Ubuntu from Said my desktop is Unity. But I nw realize it is not. What I have is gnome. So I will look for a gnome config tool.  [ATTACH=CONFIG]280707[/ATTACH]

---

### Post by Frogs Hair on 2018-08-11
```
sudo apt install gnome-tweaks
```

---

### Post by deadflowr on 2018-08-11
There is nothing in Tweaks to control dock functions, for that you need to install an extension such as dock-to-dash.
(Look in Ubuntu Software and search dash-to-dock, it should bring up an extension. Install that.)
Then in Tweaks >> Extensions, disable dash to dock as Ubuntu already has it enabled under the name Ubuntu Dock.
Then use the dash to dock settings panel to control the dock settings ( access the dash to dock setting panel by click on the cog in the dash to dock entry in Tweaks >> Extensions.)
The settings used in the dash to dock settings will affect the setting for the Ubuntu dock.

Hope that helps.

---

### Post by ubantunovice2 on 2018-08-11
Thank you both.  Did I do anything bad to the system when I tried to install that Unity tweak. I seemed to install  properly and I only got the error when I tried to launch it. I now see I have "unity Control Center" and "Unity  Tweak Tool" installed. I will remove them but did I mess up the system?

---

### Post by deadflowr on 2018-08-11
> **ubantunovice2 said:**
> Thank you both.  Did I do anything bad to the system when I tried to install that Unity tweak. I seemed to install  properly and I only got the error when I tried to launch it. I now see I have "unity Control Center" and "Unity  Tweak Tool" installed. I will remove them but did I mess up the system?

I doubt you did anything that cannot be remedied.

Though before you uninstall those packages I think you might have inadvertently installed the unity desktop.
It's rather simple to find out if you did by logging out and in the login screen, after you select your username when the password field appears a cog will show next to (under) the sign in box.
Click on the cog and see if unity is listed. No need to do anything after that, you can close the cog window and login as normal. (or you can toggle it to run unity and see what it's all about.)

If you don't care for unity, then go ahead and remove the unity tweak tool package, removing that should also clean up all the unity stuff.
(If it doesn't it, you might need to run a terminal command to clear it out
```
sudo apt autoremove --purge
```
should suffice.)

---

### Post by ubantunovice2 on 2018-08-12
I would like to thank you for all your advice but there seems to be no "thank you" icon to click on. Is there a different way to thank someone on this forum?

I shut off the Ubuntu vm (I'm running Ubuntu in a virtualbox in Windows 10) and started it up from scratch. It booted straight into what looks like the Gnome desktop. So I think I escaped installing Unity or it uninstalled when I 'removed' Unity-tweak.

Being in a vm I want to learn one thing at a time. Is there any problem with running "sudo apt autoremove --purge" anyway? To keep the vm small for now.

And, thank you for sharing your time and expertise.

**EDIT**
It looks like I inadvertently did install Unity - based on what I see in Double commander.[ATTACH=CONFIG]280713[/ATTACH]
So, I will run the command you suggested.

---

