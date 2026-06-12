---
title: "Compiz issues"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Face-Ache on 2012-05-15
I quite liked the idea of customizing my desktop workspaces, different wallpaper for each, that cool cube switching effect, etc, and i saw this link posted in a Moderator or Admin's signature.
[https://help.ubuntu.com/community/CompositeManager#Ubuntu_10.04_and_10.10.2C_Edubuntu_10.04.2C_10.10_and_11.04](https://help.ubuntu.com/community/CompositeManager#Ubuntu_10.04_and_10.10.2C_Edubuntu_10.04.2C_10.10_and_11.04)

I followed all the instructions, and got it working fine ..... or so i thought.

I disabled the "Have file manager handle the desktop" in Advanced Settings (or Gnome Tweak?), and now can't right-click on the desktop. Not too bothered about that, but when i try to alt-tab between open windows, the screen goes haywire, and then locks up.

I have to do a soft-reset to get out of it, and completely reload Ubuntu.

Any ideas on what the problem is, and/or how to fix it please?

---

### Post by Face-Ache on 2012-05-16
No-one huh?

Well, sometimes alt-tab works with Compiz running, sometimes it causes the display to go crazy, and then lock-up.

So i'm turning off Compiz, and will let File Manager via Advanced Settings/Gnome Tweak handle the desktop rather than Compiz.

I'm happy to sacrifice custom backgrounds for each workspace if the alternative is having to restart the computer whenever i try and switch open apps via alt-tab.

The cool cube-thingee still works, just no custom backgrounds - i'm okay with that.

Am still accepting solutions to the problem though!! :)

I tell you, i love Ubuntu, but it seems that every time i switch the computer on, there's some kind of issue i have to deal with (Cairo Dock disappearing, screenlets moving themselves, etc).

---

### Post by choppyfireballs on 2012-05-17
Have you completely removed all the applications because it could be an issue of compatability with the beta drivers you're using for grpahics, not that I know what your graphics are it would just be the first thing that I check so do this. 

Remove all installed components you used when you were customising for compiz. Then check to see if your graphics drivers are up to date.

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update

sudo apt-get install nvidia-current

---

### Post by Face-Ache on 2012-05-17
> **choppyfireballs said:**
> Have you completely removed all the applications because it could be an issue of compatability with the beta drivers you're using for grpahics, not that I know what your graphics are it would just be the first thing that I check so do this. 

Remove all installed components you used when you were customising for compiz. Then check to see if your graphics drivers are up to date.

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update

sudo apt-get install nvidia-current

Thanks for the response.

Sorry i'm not quite sure what you mean by 'removed all the applications' - i haven't removed any applications. I've just installed Compiz, followed the steps in the link in my original post to enable the cube-switcher, and then used Gnome Tweak/Advanced Settings to turn off File Manager handling the desktop.

I'm running a Radeon HD 5450 graphics card, and using the Additional Drivers that i understand are the proprietary .

Any other advice or suggestions based on this new information?

Thanks again.

---

### Post by wilee-nilee on 2012-05-17
Here is a custom compiz file I have been using for the last couple of releases, even in the development, if you want to try it just copy and paste it to a gedit name it what you want and load it in the preferences in compiz as an import or import as. It is the cube and some other cool tweaks. I also have all the extra plugins for compiz installed from synaptic as well.

[http://paste.ubuntu.com/993507/](http://paste.ubuntu.com/993507/)

You can load the fusion icon as well and make a launcher on the desktop for restarting compiz, I put the icon in a file and loaded it to the cairo-dock so it is a click in the dock.

Here is a link for making a launcher, works in every release I have used it up to the development as well.

[http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html](http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html)

---

### Post by Face-Ache on 2012-05-17
Thanks wilee-nilee; i'll have a look at that over the weekend when i have a bit more time (and energy) to properly devote to it.

I had 2 exams yesterday and an exam today .....  i'm fried for this week when it comes to technical stuff!!  :)

---

### Post by wilee-nilee on 2012-05-17
> **Face-Ache said:**
> Thanks wilee-nilee; i'll have a look at that over the weekend when i have a bit more time (and energy) to properly devote to it.

I had 2 exams yesterday and an exam today .....  i'm fried for this week when it comes to technical stuff!!  :)

I know the feeling I just graduated from college, keep up the good work. :)

---

