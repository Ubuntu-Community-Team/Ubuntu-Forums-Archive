---
title: "Background image, different at login"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by jmriverofernandez-4 on 2014-04-27
I just installed today (/04/27/2014) Ubuntu 14.04, and chose an image of my own pictures folder as background image. The problem is that the background in the login screen shows a different image (the default purple image of 14.04). 
If I move the image in my background desktop to usr/share/backgrounds, then everything works fine. 
Also, I created a new user and changed the background with an image downloaded from the internet, and everything works fine too (the login screen shows the image from the internet).
So, does anyone have an idea of why is this happening?

---

### Post by pfeiffep on 2014-04-27
Try changing the image type to .png

---

### Post by jmriverofernandez-4 on 2014-04-28
I'm afraid that's not the issue. All the default wallpaper images are .jpg (the ones in the /usr/share/backgrounds folder); and if a choose the other user I created, and choose a .jpg image, it works (the image in the desktop is the same as the image in the login screen).

---

### Post by pfeiffep on 2014-04-28
Maybe I'm not quite understanding your situation, here's a thread to [read]("http://ubuntuforums.org/showthread.php?t=2216311")

---

### Post by Toz on 2014-04-28
Question: is your home directory encrypted? 
If so, there is no access to it when not logged in (from the login screen).

---

### Post by jmriverofernandez-4 on 2014-04-28
No, my home directory is not encrypted. I'm using a Lenovo ideapad u310, wich has a 32 GB SSD (in where the / folder is mounted) and a 500 GB disk drive (in where /home is mounted).
But still, why doesn't it work in my user, but does it in the other user I created?

---

### Post by mcduck on 2014-04-28
Check the permissions of the image, and the folder where it's located. You need to have the "read" permission for "others" for the Lightdm to be able to access the image.

---

### Post by jmriverofernandez-4 on 2014-04-28
It has the "read" permission for "others". Still, the desktop background and the login background mismatch; while when I use the other user I created, they do match.

---

### Post by mcduck on 2014-04-28
how about the folder where the image is? The full path needs to be accessible, so you'll need to make sure all the directories have execute permission for others.

(So, if you have a picture in */home/yourusername/Pictures/Wallpapers*, the picture itself needs read permission, while */home/yourusername*, the *~/Pictures* and the *~/Pictures/Wallpapers* directories all need execute permission for "others".)

---

### Post by jmriverofernandez-4 on 2014-04-28
mcduck that was it. One of the folders in the path had "none" as the permission for "others". Once I changed that to "Accsess files", everything worked fine. Thank you very much.

---

