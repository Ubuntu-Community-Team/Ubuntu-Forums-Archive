---
title: "2 icon for same app in my dashboard"
date: 2018-12-24
forum: New to Ubuntu
---

### Post by majorpain43 on 2018-12-24
Hi, I'm new to ubuntu and and though it's not a serious issue but I would like to solve this. In my dashboard there are 2 different calculator icons. And both the icons would launch the app correctly and it works.
But I would be very grateful if anyone would recommend something about soving this issue of "2 calculator icons".
Thanks for your time. :)

---

### Post by deadflowr on 2018-12-24
It's quite possible you have both the old apt-based calculator package and the new snap-based calculator package.
What you can do to check is open the Ubuntu Software store and do a quick search for calculator, if two show up as being installed then one of those should be the snap version.
If you want to remove it then click on the listings in the Software store and look at the details section for the packages.
The snap version will list the source as the Snap Store. Feel free to remove it, no harm in doing so.

---

### Post by majorpain43 on 2018-12-25
> **deadflowr said:**
> It's quite possible you have both the old apt-based calculator package and the new snap-based calculator package.
What you can do to check is open the Ubuntu Software store and do a quick search for calculator, if two show up as being installed then one of those should be the snap version.
If you want to remove it then click on the listings in the Software store and look at the details section for the packages.
The snap version will list the source as the Snap Store. Feel free to remove it, no harm in doing so.

Thank you for your response. I searched in the Ubuntu Software Store but only one app is shown there. And I uninsalled the application. Then there was only 1 calcultor icon and it wouldn't launch. So, I  reinstalled the application and now there's 2 icons again. This problem started before I installed "Synaptic pacakage manager", right after I installed "unity-tweak-tools".

---

### Post by deadflowr on 2018-12-25
Odd that only one shows in Software since Software should show both the apt version and the snap version. (whether or not installed doesn't matter, it should still show both)
(synaptic only shows the apt version since it does not have the ability to see snap packages.)
Might double check on it by looking at the install snaps via command line.
In a terminal run
```
snap list
```
(We already know the apt version is installed since it's listed in synaptic.)

Ftr, unity-tweak-tool is useless on the current desktop session you're using since you're using Ubuntu's new gnome desktop.
But you should install gnome-tweak-tool, as that will give you a few extra options and the ability to utilize and control gnome extensions)
Edit: to add, gnome-tweak-tool will show as Tweak Tool or Tweaks in the apps menu, fwiw.

---

### Post by majorpain43 on 2019-05-25
I didn't installed snap back then...

---

