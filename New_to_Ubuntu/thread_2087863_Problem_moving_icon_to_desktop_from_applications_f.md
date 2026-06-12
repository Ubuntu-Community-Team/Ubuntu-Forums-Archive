---
title: "Problem moving icon to desktop from applications folder"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by mmauldin3 on 2012-11-24
First, I've tried to move an icon from the applications folder and received an error message stating that I don't have permission. So I ran Nautilus in a terminal (gksu nautilus) and entered my password. Now It reads in a new error message that, ": The specified location is not supported."

I've used other means to create home and desktop icons on my desktop. I would just like to resolve this easy solution which would be to drag and drop from a folder. Any idea?

---

### Post by monkeybrain2012 on 2012-11-24
The icon is a .desktop file. So what you want to do is to move the .desktop file to the your desktop. I have no idea why you want to clutter your desktop with launcher icons like Windows, but here it goes.

The .desktop files are usually in /usr/share/applications, so find the one you want and copy it onto your desktop.

Say you want vlc on your desktop.

```
sudo cp /usr/share/applications/vlc.desktop Desktop
```
Note the captial D 

After that right click the .desktop file (now on your desktop) and choose properties and check the box "allow execute as a program"

---

### Post by mmauldin3 on 2012-11-24
Okay, thank you. And you're right. I won't use the desktop in that way. Only for files and things I'm working with. Great advice. By the way, even though it works, I will not be using the it.

---

### Post by monkeybrain2012 on 2012-11-24
> **mmauldin3 said:**
> Okay, thank you. And you're right. I won't use the desktop in that way. Only for files and things I'm working with. Great advice. By the way, even though it works, I will not be using the it.

For data files (like pdf, movie files, etc) just drag and drop works.

---

### Post by mmauldin3 on 2012-11-24
Thank you! :KS

---

