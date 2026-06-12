---
title: "[SOLVED] Installing Thunderbird"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2008-05-09
I have just upgraded from 7.04 to 7.10.  All the boxes are 'green' in Synaptic, but Thunderbird will not start.  The error message reads - Failed to execute child process "mozilla thunderbird" (No such file or directory)    Why does it not work?

---

### Post by SunnyRabbiera on 2008-05-09
hmm, well did you try to reinstall it?

---

### Post by kestrel1 on 2008-05-09
You could make sure that you have the newest version installed by doing this:
```
sudo apt-get install thunderbird
```
If you have the latest version you will be told this, if not it will install the latest version & hopefully get Thunderbird working for you.

---

### Post by Dumpy Dumpster on 2008-05-09
Thank you SunnyRabbiera, uninstalled and reinstalled - same error message
Thanks also kestrel1  did that and, uess what, same error message 
All seems rather complicated?

---

### Post by kestrel1 on 2008-05-09
Try typing this in a terminal:
```
thunderbird
```
if that gets thunderbird working create a launcher or change your launcher.

---

### Post by Dumpy Dumpster on 2008-05-10
Thank you kestrel1, your suggestion did launch Thunderbird, but on next attempt I got the familiar error message.  So it seems I need to create/change my launcher. How is this done?

---

### Post by Krumar on 2008-05-10
If you want to change the launcher in the applications menu just right click on it and select edit menus, that will give you a program to edit all the launchers in the menu. Just select one and go to properties.

Krumar

---

### Post by kestrel1 on 2008-05-10
As Krumar says right click the applications menu. Once you find Mozilla Thunderbird under Internet, Right click on it & select Properties.
In the box that says command it should read:
```
thunderbird %u
```
Save this & you should be sorted.
Hope that helps.

---

### Post by Dumpy Dumpster on 2008-05-10
Thanks Krumar, eventually found my way there and found Type = Application and Command = thunderbird%u.  This is a similar format to Firefox, which opens normally.  However the Thunderbird icon when clicked gives the same old error message - 'no such directory'.
Thank you also kestrel1, that is what it does say!
GOT IT!  I am not the most computer literate person in the world, but changing the command to thunderbird%u when right clicking the icon's properties has done the trick.
Thanks again to you all.

---

### Post by kestrel1 on 2008-05-10
Glad to have helped.

---

