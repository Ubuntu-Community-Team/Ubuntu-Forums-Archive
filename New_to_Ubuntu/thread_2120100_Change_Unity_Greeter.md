---
title: "Change Unity Greeter"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by Xenoverse on 2013-02-25
I'm trying to change the login background to a JPG from my Pictures folder. I tried this as lightdm:

```
gsettings set com.canonical.unity-greeter draw-user-backgrounds false
gsettings set com.canonical.unity-greeter draw-grid false
gsettings set com.canonical.unity-greeter background /home/xenoverse/Pictures/image.jpg
```It got rid of the grid but the background itself is still just a solid color. I also tried setting it from Dconf Editor, same thing. How can I make this work?

---

### Post by deadflowr on 2013-02-25
I would think that if you wanted to use a picture from your home directory, that you'd have to set the draw-user-background to true.

---

### Post by Xenoverse on 2013-02-25
> **deadflowr said:**
> I would think that if you wanted to use a picture from your home directory, that you'd have to set the draw-user-background to true.

Nope, either way still solid color. Maybe I should move image somewhere else? If so, where?

**EDIT:** Tried copying image to /usr/share/backgrounds/ (folder where default Unity Greeter background is located) and set this filepath from Dconf. Also tried clearing the background-color field. Still no luck.

---

### Post by Xenoverse on 2013-02-26
Ok I got it to work. Had to change file permissions (chmod 777) and copy file to usr/share/backgrounds/ then (as lightdm) use gsettings or Dconf to set background.

---

