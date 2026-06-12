---
title: "[SOLVED] Having trouble with external monitor/ xorg file"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by ShadowPuppet on 2008-06-15
Okay- I'm trying to get my Dell D620 w/docking station to work. It's the model with the nVidia card, so I've got the nvidia x server settings program installed. I was able to briefly have my external monitor working properly, but after I restarted my X session, everything went back to broken normality. I figured out I didn't save the updated xorg.conf file. When I try to save the xorg.conf file with the nvidia x server settings program, it states "Unable to create new X config backup file '/ect/X11/xorg.conf.backup'." I went in file explorer and tried to cut and paste the output of the nvidia program, but I don't have permission. As you can see, I'm really new at this, and could use some help. Thanks!

---

### Post by overdrank on 2008-06-15
> **ShadowPuppet said:**
> Okay- I'm trying to get my Dell D620 w/docking station to work. It's the model with the nVidia card, so I've got the nvidia x server settings program installed. I was able to briefly have my external monitor working properly, but after I restarted my X session, everything went back to broken normality. I figured out I didn't save the updated xorg.conf file. When I try to save the xorg.conf file with the nvidia x server settings program, it states "Unable to create new X config backup file '/ect/X11/xorg.conf.backup'." I went in file explorer and tried to cut and paste the output of the nvidia program, but I don't have permission. As you can see, I'm really new at this, and could use some help. Thanks!

Hi and are you using root to use the nvidia settings
```
gksu nvidia-settings
```

---

### Post by ShadowPuppet on 2008-06-15
> **overdrank said:**
> Hi and are you using root to use the nvidia settings
```
gksu nvidia-settings
```

That's what I expected. Still learning all of this unix/ command line stuff- I thought it'd be a root user issue. Whatever you typed- that did the trick. Mind explaining what that command does? All I found when I looked it up was full of complex stuff that a newbie like me can't comprehend. Thanks!

EDIT: From what I understand, it basically lets you launch a GUI under sudo operation (something like that?)

---

### Post by overdrank on 2008-06-15
> **ShadowPuppet said:**
> That's what I expected. Still learning all of this unix/ command line stuff- I thought it'd be a root user issue. Whatever you typed- that did the trick. Mind explaining what that command does? All I found when I looked it up was full of complex stuff that a newbie like me can't comprehend. Thanks!

EDIT: From what I understand, it basically lets you launch a GUI under sudo operation (something like that?)

Hi and correct. You can launch a graphical app as root. 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ShadowPuppet on 2008-06-15
Neat! Thanks again!

---

