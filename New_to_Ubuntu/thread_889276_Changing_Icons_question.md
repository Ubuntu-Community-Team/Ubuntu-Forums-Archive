---
title: "Changing Icons question"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-08-13
I'm trying to change my firefox icon but when I edit the shortcut on my desktop and select the icon I want it gives me error messages about permissions. I dont know how to launch the shortcut config as a su. Is there some menu in the settings to change individual program's icons? If there is I cant find it.

---

### Post by original_jamingrit on 2008-08-13
that's unusual, the things on your Desktop should be owned by you.

Open a terminal, and type in the following:

```
sudo chmod +rw Desktop/*
```

Then you should be able to modify the link all you want.  Either that, or it will give us an error and a reason why.

To rebrand it though, there's supposed to be a better way of doing that that replaces all uses of mozilla's firefox icon with a different one.  There was an old script for this, but I don't know if it will work in Hardy.

---

### Post by HittingSmoke on 2008-08-14
Thanks, but still the same error message.

> Could not save properties. You do not have sufficient access to write to **/home/johnson/Desktop/firefox.desktop**

It pops up twice then the properties window closes.

I'm surprised there isnt some central place for changing icons related to file types or programs.

---

### Post by HittingSmoke on 2008-08-15
Well I managed to get around it by just deleting the original Firefox link and making my own and setting the icon at the same time. I'm not sure why the original one that the installer created wouldnt let me edit it.

---

### Post by LeetSpeak on 2008-08-15
same thing happened with my icon theme, said that exact thing, so what i did was delete the original *.icons* folder and created a new folder named the same thing. To my suprise that worked, very strange.

---

### Post by Gannon8 on 2008-08-15
You should be able to install icons by dragging it to the themes selector in System > Preferences > Appearance and then applying them.

---

### Post by HittingSmoke on 2008-08-15
No no, I already had the theme I wanted installed but I was trying to change the Firefox desktop shortcut icon because I use Crystal Diamond which has like 6 different Firefox icons. When I went in to the shortcut properties and selected a new icon it gave me access restrictions. So I tried deleting the original Firefox shortcut and creating my own new one which worked.

Just want to be clear on that if anyone else has this same problem.

---

