---
title: "Installing new Mouse Cursor Themes 11.10"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by slayner117 on 2011-10-22
Hey there, I am trying to install a mouse cursor theme, and I know how to install it once it is shown up on gnome-tweak advanced settings. However the cursor I am trying to install was downloaded online. I imagine I need to extract the tar.gz to the cursor folder. Either way, help me out please.

---

### Post by masgeeks on 2011-10-22
Extract to /usr/share/icons

This worked for me...

---

### Post by slayner117 on 2011-10-22
Okay, It's saying that I don't have the permission to extract into this folder. How do I change the permission? 


In fact I know this is not part of the title question, but how do I give my account "owner access?"

---

### Post by octoamit on 2011-10-23
You could extract the file as root.

[LIST=1]
[*]Press alt-F2
[*]Run the command "gksu nautilus"
[*]Browse to the location of the theme to extract
[*]Extract the file to /usr/share/icons
[/LIST]


I don't know if this would cause any kind of problems, but you could change the permissions of the folder graphically like:
[LIST=1]
[*]Press alt-F2
[*]Run the command "gksu nautilus"
[*]Browse to /usr/share/
[*]Right click the folder "icons"
[*]Click properties
[*]Change the permissions on the permissions tab
[/LIST]

---

