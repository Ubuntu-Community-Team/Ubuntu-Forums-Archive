---
title: "Surf without a GUI?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-06-25
Hi,

I have a copy of Ubuntu Server Ed. installed on an old 600mhz machine and running Gnome on it seems a little too much. 

What I'm wanting to do is surf the web, but am unaware of anyway of doing this without a GUI being installed. 

Is it possible at all? Like perhaps just installing Firefox only, or finding a 'lite' version of a GUI?

I'm just guessing really, so if there is a solution available I'd be grateful if you could tell me.

Thanks for any advice!

---

### Post by Dr Small on 2008-06-25
Try Openbox, Fluxbox, IceWM, Blackbox, etc for something lightweight.

---

### Post by WRDN on 2008-06-25
I don't think you can do it without a GUI (as far as I know), but you could try installing [xfce]("http://www.xfce.org/"), a lightweight desktop environment.

---

### Post by bluepowder7 on 2008-06-25
Xubuntu (Xfce) + Opera = happy

---

### Post by aktiwers on 2008-06-25
you can browser the web without GUI if you install links2 or or lynx. But they are completely without GUI.

```
sudo apt-get install lynx
```

```
lynx
```


```
sudo apt-get install links
```

```
links2
```

I think you type URLS after pressing CTRL+G.

---

### Post by avtolle on 2008-06-25
I've not used any of these, but a quick search in Synaptic reveals some candidates: elinks, lynx, links, links2 as examples. HTH.

---

### Post by Swerve1000 on 2008-06-25
Great!A few options. Will give them a try.

Thanks everyone.

---

### Post by fenian on 2008-06-25
{edit}

---

### Post by JoshuaRL on 2008-06-25
If you want XFCE, you can get that from the repos:
```

sudo aptitude install xubuntu-desktop

```
If you'd like to try out LXDE (I'm testing it out myself right now, it's quick) you can install as per [their instructions here.](http://lxde.org/wiki/Ubuntu)

If you would like to try out Enlightenment (e17), which is a lightweight Window Manager, try [this thread.](http://ubuntuforums.org/showthread.php?t=546746)

---

### Post by dashnak on 2008-06-25
I use elinks to surf without a GUI, it's a text-mode browser....

---

### Post by fenian on 2008-06-25
You can use a text only browser like [Lynx]("http://en.wikipedia.org/wiki/Lynx_(web_browser)") ,install it with...
> 
sudo apt-get install lynx

Or you could install a minimal window manager like [ratpoison.]("http://www.nongnu.org/ratpoison/") with the [conkeror web browser ]("http://weblog.zamazal.org/ratpoison-conkeror.html")

---

### Post by Eisenwinter on 2008-06-25
or.
```
sudo apt-get install links
<after installtion completes>
links <URL>
```

you use d to download stuff, and q to quit.
there are various other features which you will find by using it.

---

### Post by leon.hh on 2008-06-25
Surfing the web without graphical interface, it's not possible: due to the extense use of pictures, CSSs, flash animations and javascript in the modern web sites. If you wish you could try lynx, but it'll only work in text-based web pages.

If you need to surf Internet in the whole meaning of the expression you're gonna have to install some gui, I recommend to you Enlightenment, it's very light, fast and minimal

---

### Post by kregg on 2008-06-25
As someone said before, lynx does the job. And from previous experience of X-Server crashes, it's pretty good too.

Will check out the other browser though...

EDIT: Links is just as good, but it can be confusing to use if you don't know what keys to press... Lynx tells you the available keys you can press, while Links gives you a nice text-based-browser-screen-terminal-thing all to yourself.

---

### Post by Canis familiaris on 2008-06-25
Dillo in fluxbox would be extremely light weight.

---

### Post by Dr Small on 2008-06-25
> **WRDN said:**
> I don't think you can do it without a GUI (as far as I know), but you could try installing [xfce]("http://www.xfce.org/"), a lightweight desktop environment.
Xfce is _not_ lightweight.

---

### Post by JoshuaRL on 2008-06-25
> **Dr Small said:**
> Xfce is _not_ lightweight.

True.  But it is lighterweight then Gnome or KDE.  And it's a standard install from the repos.  So it can be easier for a non-experienced user to use and get help for.

---

### Post by Neo0351 on 2008-06-25
try puppy linux, its very small.
[http://www.puppylinux.org/home](http://www.puppylinux.org/home)

---

