---
title: "Best lightness/performance window manager?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-30
What is the best window manager that is extremly light can have a bar in the
bottom (windows like), status indicators in the bar as well, change desktop, time, start button and able to have desktop icons on top of the wallpaper?
A how-to to do this all would be nice.

---

### Post by kpkeerthi on 2008-05-30
[http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)

---

### Post by tactx on 2008-05-30
I'm pretty new to Linux and don't know which is the lightest window manager per se, but I was reading an article which stated that the "smallest" functional gui linux distribution was "Damn Small Linux 4.2" at [http://damnsmallinux.org](http://damnsmallinux.org)

---

### Post by kerry_s on 2008-05-30
jwm + rox-filer

jwm is a 98 style setup window manager

rox-filer is a multi-purpose file manager, does desktop icons, backgrounds, the whole 9 yards.

---

### Post by cristo-father on 2008-05-30
> **kpkeerthi said:**
> [http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)

Wow. I can not believe it so light ... yet "functional". You got a thanks for that.:)

---

### Post by kpkeerthi on 2008-05-30
> **cristo-father said:**
> Wow. I can not believe it so light ... yet "functional". You got a thanks for that.:)

I personally find  [openbox]("http://icculus.org/openbox/index.php/Main_Page") simple, fast, functional and well documented. I suggested LXDE as it uses openbox as its window manager + has other goodies nicely integrated into an out-of-the-box desktop environment.

---

### Post by skymera on 2008-05-30
You could try Enlightenment.
Although it doesn't have a task bar and doesn't match anything you've said.

But it's very nice and maximises window space.

It's in the repos.

---

### Post by cristo-father on 2008-05-30
Lxde should be in synaptic...i mean it deserves to be.

---

### Post by Joeb454 on 2008-05-30
Submit a request to the dev's of both Ubuntu and LXDE then ;)

I've never tried it myself, the only "lightweight" WM/DE's I've tried are XFCE and Fluxbox

---

### Post by cristo-father on 2008-05-30
> **Joeb454 said:**
> Submit a request to the dev's of both Ubuntu and LXDE then ;)

I've never tried it myself, the only "lightweight" WM/DE's I've tried are XFCE and Fluxbox
Sorry for the newbie question, but what are devs?

---

### Post by kpkeerthi on 2008-05-30
devs -> Developers

---

### Post by Joeb454 on 2008-05-30
Sorry I should've explained :) kpkeerthi is right, and beat me to it

---

### Post by cristo-father on 2008-05-30
It actually is possible all i have to do is edit the source list.
Here is the source.
[http://lxde.sourceforge.net/download.html](http://lxde.sourceforge.net/download.html)

---

### Post by Joeb454 on 2008-05-30
Ok so to do that you would run (from a terminal) ```
gksudo gedit /etc/apt/sources.list
```

Then you would add ```
deb [http://people.linux.org.tw/~pcman/ubuntu/](http://people.linux.org.tw/~pcman/ubuntu/) ./
```
To the end of the file, and then save that.

Then back in the terminal, you would run ```
sudo apt-get update && sudo apt-get install lxde
```

---

### Post by eriqjaffe on 2008-05-30
> **Joeb454 said:**
> Ok so to do that you would run (from a terminal) ```
gksudo gedit /etc/apt/sources.list
```

Then you would add ```
deb [http://people.linux.org.tw/~pcman/ubuntu/](http://people.linux.org.tw/~pcman/ubuntu/) ./
```
To the end of the file, and then save that.

Then back in the terminal, you would run ```
sudo apt-get update && sudo apt-get install lxde
```That repo is no longer current:

[http://ubuntuforums.org/showthread.php?t=805334](http://ubuntuforums.org/showthread.php?t=805334)

---

### Post by Joeb454 on 2008-05-30
I didn't know :p I just tend to stick with trusty old Gnome ;)

To the OP - I'm sure that the link posted above would be better for you, as it's more current :)

---

