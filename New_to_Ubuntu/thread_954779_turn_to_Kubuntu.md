---
title: "turn to Kubuntu"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Settler on 2008-10-21
Hello,

I would like to know how do I chance my ubuntu to kubuntu by starting my pc from the beggining. What I mean in a list.

1. I have a running setup with Ubuntu installed
2. I want to chance to Kubuntu
3. I don't want to lose my files in the separate /home partition
4. I want all programms/applications used by this distibution not to exist in my "new" / partition. Like firefox, or for example virtualbox which I have installed etc.

Thanks in advance.

Settler

---

### Post by bodhi.zazen on 2008-10-21
you could just:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by Law506 on 2008-10-21
Try this

[https://help.ubuntu.com/community/InstallingKDE]("https://help.ubuntu.com/community/InstallingKDE")

or 

[http://ubuntuforums.org/archive/index.php/t-92723.html]("http://ubuntuforums.org/archive/index.php/t-92723.html")

---

### Post by Settler on 2008-10-21
That will just install KDE or i'm wrong?..

I would like to my / partition too if posible

---

### Post by eks on 2008-10-21
If you have your /home folder on a different partition (make sure you do  with gparted), then you can install Ubuntu or Kubuntu from scratch and you will have all the configuration and desktop files intact.

That's the charm of having /home on a separate partition ;)

And if, for example, you want to keep all your files and configuration, and sill "reset" your gnome configuration, you can delete/rename the folders listed on [this post]("http://ubuntuforums.org/showpost.php?p=4960719&postcount=2") before starting the re-installation. You would have to download again all your theme files though.

---

