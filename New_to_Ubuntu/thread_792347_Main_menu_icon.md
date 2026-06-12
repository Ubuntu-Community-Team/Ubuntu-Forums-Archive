---
title: "Main menu icon"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by garrettstarnes on 2008-05-12
Ok guys, I want to change my main menu icon to the penguin guy (tux)  I have an icon that is the right size, I just don't know how to make it work.  I have read and tried to make it happen.  I was reading off of this page  
[http://ubuntuforums.org/showthread.php?t=498890&highlight=change+main+menu+icon](http://ubuntuforums.org/showthread.php?t=498890&highlight=change+main+menu+icon)
I just don't know how he did it.  I don't really understand the filesystem or the terminal, but if you could tell me what to do, I will do it.  Thanks guys!!

---

### Post by mevets on 2008-05-12
According to this tutorial its real simple. If you want to do it through the gui follow these steps:

1. Open nautilus and navigate to your home folder. An easy way to do this is Places > Home Folder
2. Press ctrl+h in order show hidden files
3. Find the .icons folder, go into it
4. Find the Human folder, go into it
5. Find the scalable folder, go into it
6. Find the places folder, go into it
7. Find the distributor-logo.png file and replace it with your image. Make sure it has the same name.
8. Logout then log back in

---

### Post by garrettstarnes on 2008-05-12
I made the directories and everything, but when i do the 'killall blah blahng' it just restarts the panel and everything is the same as at first.

---

### Post by mevets on 2008-05-13
I think the configuration for gnome's main menu is stored in a different place. I am running a version of mint thats based on gutsy and I had a .icons folders. On my hardy install it does not exist. I figure this was changed when hardy came out cause it ships with a later version of gnome. I think this accounts for the problem you are having.

Anyway I am looking for the directory this is stored in under hardy. If anyone knows where this is please mention it.

---

### Post by Bodsda on 2008-05-13
The .icons folder /home/user/.icons  still exists, but only after you install an icon theme (or at least, my icon theme is the only one in this folder) so an annoying workaround would be to copy the icons in use on your machine into this folder and edit. (not sure if this will work, but the theory is good)

;~)

---

### Post by Bodsda on 2008-05-13
i just tried the howto on the other page, but it didnt work for me, i still have the same icon

---

