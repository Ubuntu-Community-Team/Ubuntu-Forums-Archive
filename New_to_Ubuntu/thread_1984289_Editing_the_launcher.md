---
title: "Editing the launcher"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by CircaSurvives on 2012-05-21
I've been using Ubuntu for a little while now after switching from Fedora and Red Hat about a month ago because I got a new job as an IT Technician and am implementing a new Ubuntu system.
 
Right now I'm trying to figure out which folder the files for the launcher are in because I don't want anyone but the administrator to have a launcher on their desktop. I know that I can do this by editing the permissions to a certain folder but cannot find the folder for the life of me. Can someone please let me know where this folder is?
 
I've already checked /usr/share/unity-2d and /usr/share/unity in which after changing the permission to 750 still did not take the launcher away. I literally just did it on friday and then my system crashed because I was trying to get rid of the guest account so I know it can be done. Does anyone know?
 
Thanks,
 
Dan

---

### Post by CircaSurvives on 2012-05-21
So....

---

### Post by gettinoriginal on 2012-05-21
Try "home folder" "system files" search "launcher", then "properties" "permissions".  Is that what you want ??

---

### Post by CircaSurvives on 2012-05-22
I don't see a folder in "home folder" named "system files"... I see one in root named "sys" and when I searched for launcher in that it didn't come up with anything.

---

### Post by gettinoriginal on 2012-05-22
Sorry, bad communication on my part.  After opening the home folder, look in the left menu pane, select "file system".  Then proceed to search for "launcher".
Double click thumbnail to enlarge.

---

### Post by philinux on 2012-05-22
> **CircaSurvives said:**
> I've been using Ubuntu for a little while now after switching from Fedora and Red Hat about a month ago because I got a new job as an IT Technician and am implementing a new Ubuntu system.
 
Right now I'm trying to figure out which folder the files for the launcher are in because I don't want anyone but the administrator to have a launcher on their desktop. I know that I can do this by editing the permissions to a certain folder but cannot find the folder for the life of me. Can someone please let me know where this folder is?
 
I've already checked /usr/share/unity-2d and /usr/share/unity in which after changing the permission to 750 still did not take the launcher away. I literally just did it on friday and then my system crashed because I was trying to get rid of the guest account so I know it can be done. Does anyone know?
 
Thanks,
 
Dan

I can achieve this with a combination of myunity and compizconfig-settings-manager.

In myunity set the launcher to behaviour Hidden. And in CCSM in Desktop>Unity plugin>experimental set the Reveal pressure to 999 instead of 20.

Launcher is hidden and cant be revealed I think. You would then have to disable access to these two apps.

---

