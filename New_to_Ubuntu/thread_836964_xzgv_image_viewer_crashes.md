---
title: "xzgv image viewer crashes"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by rockerphil on 2008-06-22
ok, first the system im running. it's an ancient Dell Dimension desktop running a 500 MHz Intel Pentium processor, 128 MB of pc133 SD RAM running a minimalist desktop install buikt on the Gutsy Gibson minimal image CD by installing a CLI first then installing Xorg, Fluxbox as my WM, ROX as my filer and of course Firefox as my browser. now, down to the problem, i installed xzgv image viewer and it worked fine for quite some time, but now when i load it up i get a small flash from the app window right before it crashes. so i tried running it through the terminal and got this error message:


phil@phil:~$ xzgv

Gdk-CRITICAL **: file gdkwindow.c: line 1406 (gdk_window_get_visual): assertion `window != NULL' failed.

Gtk-CRITICAL **: file gtkwidget.c: line 4258 (gtk_widget_push_visual): assertion `visual != NULL' failed.
Segmentation fault
phil@phil:~$ 



i personally can't make heads or tails of it, so i figured i'd kick the problem over to the forums and see if you guys can help me on it. much thanx in advance,



Phil

---

### Post by kerry_s on 2008-06-22
try gpicview, it's lighter and prettier.
sudo apt-get install gpicview

---

### Post by rockerphil on 2008-06-22
ok, i tried installing gpicview, and my terminal says it can't find the package, so i'm gonna ask if anyone knows of a better lightweight image viewer than xzgv, any suggestions?

---

### Post by kerry_s on 2008-06-22
you must not have all the repos turned on.
**cat /etc/apt/sources.list**
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

back in the day i use to use feh, cause i had it to set my background anyways.

---

### Post by rockerphil on 2008-06-22
i've got all my repos enabled, so i searched [http://packages.ubunto.com](http://packages.ubunto.com) for the .deb package and it's not in the Gutsy repos. i'm not using Hardy quite yet, i'm waiting till all the bugs get ironed out, that and i tried Hardy and Wine wouldn't work for me. so i think i'll stick with Gutsy for a while. but i'll try feh, thanx

---

### Post by kerry_s on 2008-06-22
hmm, i thought it was in gutsy, oh well. feh's good for simple image viewing, just as fast as xzgv and gpicview.

you can try adding this gutsy repo->
deb [http://people.linux.org.tw/~pcman/ubuntu](http://people.linux.org.tw/~pcman/ubuntu) ./

it's part of lxde so it might have gpicview.
[http://ubuntuforums.org/showthread.php?t=738958&highlight=openbox](http://ubuntuforums.org/showthread.php?t=738958&highlight=openbox)

sorry, i can't be of more help i'm on debian etch/lenny custom install.

---

### Post by RedSquirrel on 2008-06-22
gqview is pretty nice.

```
sudo apt-get install gqview
```

---

### Post by kerry_s on 2008-06-22
> **RedSquirrel said:**
> gqview is pretty nice.

```
sudo apt-get install gqview
```

and RedSquirrel saves the day!
i forgot all about gqview, haven't used it in ages, it had gotten slow a while back when i last used it.
:lolflag:

---

### Post by RedSquirrel on 2008-06-22
> **kerry_s said:**
> and RedSquirrel saves the day!
i forgot all about gqview, haven't used it in ages, it had gotten slow a while back when i last used it.

I haven't used it in a while either but it used to be one of the standard applications I installed. These days, it seems I don't really *need* an image viewer but I do have feh installed, you know, just in case. ;)

The last time I tried gqview it didn't seem slow. You've got me curious... I might have to install it to see if it's slow now. :grin:

Another possibility is "mirage":

```
sudo apt-get install mirage
```[http://packages.ubuntu.com/gutsy/mirage](http://packages.ubuntu.com/gutsy/mirage)
[http://mirageiv.berlios.de/](http://mirageiv.berlios.de/)

I haven't gotten around to trying that one, but it looks good. I might try it tomorrow. Right now, I can barely keep my eyes open... :lol:

---

### Post by kerry_s on 2008-06-22
man, you are on a roll, mirage had a lot of dependency's the last time i checked it out, but it was okay.

how about "ristretto" use to be the xfce4 image viewer. is that in gutsy?

---

### Post by RedSquirrel on 2008-06-23
> **kerry_s said:**
> how about "ristretto" use to be the xfce4 image viewer. is that in gutsy?

It appears it's only in hardy:
[http://packages.ubuntu.com/hardy/ristretto](http://packages.ubuntu.com/hardy/ristretto)

It has quite a few dependencies.

---

