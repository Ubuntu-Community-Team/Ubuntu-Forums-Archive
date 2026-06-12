---
title: "HOWTO: Change File Manager EASILY"
date: 2009-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by chenxiaolong on 2009-12-11
I've been looking around the web trying to find out how to change the default file manager in (K/X)Ubuntu. Most of them involve renaming/removing binaries or changing init scripts. But, luckily there's an easier way to do it, although you will have to download some KDE runtimes to do it (let's just say, if you do it on dialup, you'll be waiting:)). Anyway, you have to install the "systemsettings" package:

```
sudo aptitude install systemsettings
```

Then, you open up the KDE System Settings program (don't worry, it works on any other window manager):

Press Alt+F2 and type in "systemsettings".

Then, (double)click on the "Default Applications" button under the "Personal" section.

On the left, there will be File Manager tab where you can choose what file manager you want to use.

----------------------------------------

NOTICE that the default Gnome file manager, Nautilus, isn't in the list. So, if you want it back, you will have to add it to the list. Here's how:

Click the "Other: click Add... in the dialog shown here:" radio button.

Click the elipses (...).

Click "+ Add..."

Type in "nautilus" and click Ok.

Then click the new entry in the list and click "Edit..."

Go to the "Application" tab at the top and change the name to whatever you want and make sure that the "Command: " box says "nautilus".

Then click, Ok, and Ok, and however many Ok's it takes to get out of the dialogs. And voila, it works -- without a reboot too!

---

