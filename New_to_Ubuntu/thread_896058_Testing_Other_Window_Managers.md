---
title: "Testing Other Window Managers"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-20
I want to install KDE and XFCE to start playing around with them

So I do:
```

sudo aptitude install kde-desktop
```

AND

```
sudo aptitude install xfce-desktop
```

Now, my question:

When I am finished playing around with them (and this question can also include any and all other window managers) and it comes time to uninstall, will 

```
sudo aptitude uninstall BLANK
```

completely remove everything? (Will any traces of it still be left over like when you uninstall something in windows?)

---

### Post by ApUUbunU on 2008-08-20
I think if you use:

```
# apt-get purge X
```

and then:

```
# apt-get autoremove
```

All the unnecessary packages and dependencies will be uninstalled.
You can also do a:

```
# updatedb
```

followed by:

```
# locate X
```

This will hopefully show some more files or directories related to the application.

---

### Post by tuxxy on 2008-08-20
KDE being KDE will most liekly leave something behind, its not hard to fix though just search for kde in synaptic and remove anything still installed.

---

### Post by Victormd on 2008-08-20
This is a great question! Now... how do you go about loading one or the other manager?

---

### Post by t0p on 2008-08-20
> **Victormd said:**
> This is a great question! Now... how do you go about loading one or the other manager?

To switch between the different managers: when you're logging in, click on the Sessions tab on the login page.  There you'll be able to select Gnome, KDE or Xfce for the session.

---

### Post by tuxxy on 2008-08-20
You choose which desktop you would like at the ubuntu login screen, click session and select either GNOME, KDE etc

---

### Post by Dr Small on 2008-08-20
I hate to break it to ya, but GNOME, KDE and XFCE are not WMs, but DE (Desktop Environments). The WMs are IceWM, Openbox, Wmii, Blackbox, Fluxbox, etc.

---

### Post by ApUUbunU on 2008-08-20
So where does Compiz (which I think is the default in Ubuntu), or Compiz-Fusion get into all this, is it some form of DE?

---

### Post by Dr Small on 2008-08-20
> **ApUUbunU said:**
> So where does Compiz (which I think is the default in Ubuntu), or Compiz-Fusion get into all this, is it some form of DE?
Compiz is a window decorator, so it can be classified as a WM, but it can't stand alone, as far as I am aware, unlike independent WMs.

---

### Post by pparks1 on 2008-08-20
I think the actual packages for the desktop environments are:
kubuntu-desktop
xubuntu-desktop

You can switch to them when you reach the logon window.  There will be an options box in the lower left, and from there you can pick Sessions to pick which desktop environment that you want to run.

---

### Post by bodhi.zazen on 2008-08-20
To remove the various "Desktops" see :

Pure gnome: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

    Pure KDE: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

    Pure XFCE: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by jordanmthomas on 2008-08-20
> **Dr Small said:**
> Compiz is a window decorator, so it can be classified as a WM, but it can't stand alone, as far as I am aware, unlike independent WMs.

It can stand alone.  Compiz is more a window manager than a decorator.  You can run compiz with no window decorations and it'll still work fine.

Also, you don't need any sort of DE to run compiz.

---

### Post by RedSquirrel on 2008-08-21
> **pparks1 said:**
> I think the actual packages for the desktop environments are:
kubuntu-desktop
xubuntu-desktop

The repositories also have these packages:

kde-core
xfce4

which provide the core desktop environment without including a ton of other applications.

@OP: The packages kde-desktop and xfce-desktop do not exist. ;)

---

### Post by diego898 on 2008-08-21
These are the commands I have executed:

sudo aptitude remove kde-desktop

sudo aptitude remove kde-core


Only for the terminal to return like 5 lines of code about building depedency trees etc etc. When I go to my applications menu however, ALL of the programs that were installed with kde are still there. Psychocats doesnt work!

---

### Post by philinux on 2008-08-21
I don't think you read the pure gnome link.

There is another set of command to use which would need to be copied and pasted if you still have programs left. It says if you use synaptic or apt-get then aptitude wont remove them all.

---

### Post by diego898 on 2008-08-21
I did, and I've executed those commands. Now I have to follow the media thread again since I cant see apple trailers again

---

### Post by mikjp on 2008-08-22
> **diego898 said:**
> 
When I am finished playing around with them (and this question can also include any and all other window managers) and it comes time to uninstall, will 

```
sudo aptitude uninstall BLANK
```

completely remove everything? (Will any traces of it still be left over like when you uninstall something in windows?)

No, it won't. You will still usually have all the configuration files in a specific directory (.kde, .icewm, .openbox etc).

mikko

---

