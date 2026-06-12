---
title: "remove appmenu for all apps"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2011-10-05
I am getting really tired of the appmenu. I have spent my entire time since moving to the Alpha trying to like it but it's the most annoying thing I've ever encountered. It's disjointed, and windows always have to be in focus to close or use the applications options correctly. The number of times I've accidentally shut my browser trying to close a background popup are too numerous to mention.

I used the following command to disable it to some degree of success

echo "export UBUNTU_MENUPROXY=0" > /etc/X11/Xsession.d/81ubuntumenuproxy

But for Thunderbird it doesn't work.

---

### Post by bbrg548 on 2011-10-05
> **sonicb00m said:**
> I am getting really tired of the appmenu. I have spent my entire time since moving to the Alpha trying to like it but it's the most annoying thing I've ever encountered. It's disjointed, and windows always have to be in focus to close or use the applications options correctly. The number of times I've accidentally shut my browser trying to close a background popup are too numerous to mention.

I used the following command to disable it to some degree of success

echo "export UBUNTU_MENUPROXY=0" > /etc/X11/Xsession.d/81ubuntumenuproxy

But for Thunderbird it doesn't work.

Check the Thunderbird plugins, I think it's in there [just like the one for Firefox]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html"). They both use different 'architecture' for their interface, so the appmenu had to be integrated via plugins.

It might be listed as the "Global Menu Bar Integration" plugin, or something similar.

---

### Post by madjr on 2011-10-05
agree with you that global menu is half-baked and annoying.

gladly many others feel the same and with a better implementation it could become very good and still serve its goal:

[https://bugs.launchpad.net/unity/+bug/682788](https://bugs.launchpad.net/unity/+bug/682788)

---

### Post by sonicb00m on 2011-10-06
> **bbrg548 said:**
> Check the Thunderbird plugins, I think it's in there [just like the one for Firefox]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html"). They both use different 'architecture' for their interface, so the appmenu had to be integrated via plugins.

It might be listed as the "Global Menu Bar Integration" plugin, or something similar.

That fixed it!

Do you know how to move a fully maximised window to another desktop? There is no right click menu available to move it when it's maximised and I have to drag it down, move it, then remaximise again. Very annoying.

---

### Post by mc4man on 2011-10-06
You can move any window in expo (the workspace switcher

(an alternative to disable the global menu for apps that don't use extensions is to remove the appmenu-gtk & appmenu-qt packages

---

### Post by sonicb00m on 2011-10-06
> **mc4man said:**
> You can move any window in expo (the workspace switcher

(an alternative to disable the global menu for apps that don't use extensions is to remove the appmenu-gtk & appmenu-qt packages

Thanks!

I have previously removed the appmenu packages but they keep coming back with the updates :)

---

### Post by bbrg548 on 2011-10-06
> **sonicb00m said:**
> That fixed it!

Do you know how to move a fully maximised window to another desktop? There is no right click menu available to move it when it's maximised and I have to drag it down, move it, then remaximise again. Very annoying.

With the mouse, you have to use the expo. You can also do it with Ctrl+Alt+Shift+[arrow], if you want to use the keyboard.

---

### Post by fjgaude on 2011-10-06
Also, alt-tab and then the space bar or the arrows keys... lots of way to shift around.

---

