---
title: "[SOLVED] Adobe Flash Player Installation problem"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by goldenbough on 2008-05-11
I am trying to install the Adobe Flash player here and am having some problems.  Seemingly the installation was successful.  At the terminal I was prompted to remove Mozilla's xpti.dat file which I did.  I still cannot view videos.  When I look back into the Mozilla files, I see that the xpti.dat file gets regenerated.

---

### Post by Fjatle on 2008-05-11
Just a little question:
Where did you install flashplayer from?

---

### Post by SunnyRabbiera on 2008-05-11
usually its better to install things like this via the repositories, and not from the adobe website like you would do in windows.
If you need a tutorial I can provide one.

---

### Post by goldenbough on 2008-05-11
/home/foo/.mozilla

---

### Post by gandaran on 2008-05-11
you should have installed the flashplugin-nonfree in synaptic, (adobe flash), maybe you'll run into problems now if theres allready something installed, try to find out.

if it's in home mozilla plugins folder, just delete the plugins folder and install the flash in synaptic.

---

### Post by goldenbough on 2008-05-11
Yes, could you post that tutorial?  I did get this file directly from Adobe.

---

### Post by SunnyRabbiera on 2008-05-11
> **goldenbough said:**
> Yes, could you post that tutorial?  I did get this file directly from Adobe.

yeh that method is not very good.
As for how to get the adobe plug in via the repositories its very easy.
First go up to system then to administration and go to synaptic package manager.
after that type in your password and once you are done that ignore the window that will pop up and go up to "settings" and then to "repositories"
another window will pop up and make sure everything is checked off except the source code repository, and in the third party software tab make sure things are check off there too except for the source code repositories there too.
after that hit "refresh" after you are prompted to and then search for "flash"
go down a bit once the search is done and right or left click the box next to "flashplayer nonfree"
and mark it for installation.
if anything comes up hit "apply"
and again hit "apply"
the installation process is very straightforward.

---

### Post by goldenbough on 2008-05-11
Well I went through the process you described and it still does not work.  The file was called flashplugin-nonfree.

---

### Post by SunnyRabbiera on 2008-05-11
> **goldenbough said:**
> Well I went through the process you described and it still does not work.  The file was called flashplugin-nonfree.

alright, it might be due to what you did earlier with the terminal prompting you to remove the xpti.dat file...
you may have to re install firefox, also you may have to manually add the plugin or restart firefox, or log out and log back in.

---

### Post by goldenbough on 2008-05-11
Thanks, that fixed it.

---

