---
title: "Auto-mounting internal drives"
date: 2008-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Shishire Maiga on 2008-05-21
So I've noticed when running Ubuntu that while my external drives will show up on my desktop when I turn the computer on, my internal drives don't.  They were still accessible from the Places Menu, but they had to mount on the first click, and then I could open them.  Obviously, this is not the desired behavior.  So I did a bit of digging and I found the problem.  HAL apparently tells gnome-volume-manager not to auto-mount internal drives.  I found the file containing this policy, and fixed the problem.

The file is this one:

/etc/hal/fdi/policy/preferences.fdi

To fix it so that internal drives will show up on your desktop when you boot up, change this line:

        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
to this:

        <merge key="storage.automount_enabled_hint" type="bool">true</merge>

Then, reboot, and Voila!

---

### Post by hummos on 2008-05-25
It works.... great

---

### Post by newbreed on 2008-05-25
just tried...no success .. something about not having permission, how do I log in as root admin? in terminal I enter cd / ....thinking I'm in as root admin:confused:..sorry havent had a cup of beans yet. I warm up as the day goes by:)

---

### Post by Shishire Maiga on 2008-05-26
> **newbreed said:**
> just tried...no success .. something about not having permission, how do I log in as root admin? in terminal I enter cd / ....thinking I'm in as root admin:confused:..sorry havent had a cup of beans yet. I warm up as the day goes by:)

It's ok, you shouldn't need root permissions, but if you do, then you can open a terminal and run:
```
gksudo gedit
```
and then once the text editor opens, use it to open specified file

---

### Post by MyNameisTheStig on 2008-05-26
thanks, this is a real help, I was looking to do this

I've done the file edit (needed *gksudo gedit*), now I'll *sudo shutdown -r* to test it

---

### Post by MyNameisTheStig on 2008-05-26
It works :)

big thanks :)

---

