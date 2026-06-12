---
title: "Pangolin unable to open handbrake"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by czgirb on 2014-01-16
I don't know why? Everytime I click **Handbrake** ... nothing's happen. It never comes up?
Would everybody will do a favor how to repair it? Cos I use **Handbrake** everytime I wish to reduce the video file.
Please ....... thank you.

**PS:**
> 
czgirb@czgirb:~$ ghb
(ghb:2954): GLib-GObject-WARNING **: cannot create instance of abstract (non-instantiatable) type `GtkScale'
Segmentation fault (core dumped)
czgirb@czgirb:~$ ghb &
[1] 2966
czgirb@czgirb:~$ 
(ghb:2966): GLib-GObject-WARNING **: cannot create instance of abstract (non-instantiatable) type `GtkScale'

---

### Post by howefield on 2014-01-16
Try starting the application from the terminal, see if it spits out an error which you can post back here.

```
ghb
```

---

### Post by czgirb on 2014-01-16
czgirb@czgirb:~$ ghb
(ghb:2954): GLib-GObject-WARNING **: cannot create instance of abstract (non-instantiatable) type `GtkScale'
Segmentation fault (core dumped)
czgirb@czgirb:~$ ghb &
[1] 2966
czgirb@czgirb:~$ 
(ghb:2966): GLib-GObject-WARNING **: cannot create instance of abstract (non-instantiatable) type `GtkScale'

---

### Post by kostkon on 2014-01-17
It could be a theme problem if you are using a different than the default. You could try reverting back to the default thus.

Also, how did you install Handbrake?

---

### Post by czgirb on 2014-01-18
I don't know why ... I really really don't know what is going on with my Pangolin.
With the instruction from [**JohnAStebbins**]("https://forum.handbrake.fr/memberlist.php?mode=viewprofile&u=5752") by doing:
> sudo apt-get update
sudo  apt-get upgrade
My Handbrake back normally.
[SIZE=5]Thank you very much to** [JohnAStebbins]("https://forum.handbrake.fr/memberlist.php?mode=viewprofile&u=5752")**[/SIZE]

---

