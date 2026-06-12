---
title: "[SOLVED] Ubuntu with GNOME and KDE?"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by AOZ on 2008-07-08
I have ubuntu with gnome right now but i wanted to know if i could download KDE via synaptic and just test it out. also, just curious, if i did use KDE what would eb the differnce between that vs kubuntu?

---

### Post by sydbat on 2008-07-08
I have dl'd KDE from Synaptic and logged into it without a problem (I have Ubuntu).

I think the main difference is Kubuntu is KDE integrated (like Ubuntu has Gnome integrated). Other than that, I dunno.

---

### Post by Patricrawley on 2008-07-08
You can download and install the KDE desktop environment via synaptic or aptitude. I would go with aptitude as it's simpler and easier to uninstall if you don't like it. I can't tell you about just KDE vs Kubuntu though, but I think that they are the same thing because the KDE desktop gives you all the programs you get with kubuntu. If you really just wanted to test it out, you could download and burn a Kubuntu live disk and check it out that way if you don't want the download. When you uninstall, look out for kio-unmountwrapper there are errors with uninstalling it but there are posts around the forum to help you out with it.

---

### Post by blazercist on 2008-07-08
sudo apt-get install kubuntu-desktop

but you will have all the KDE and GNOME applications in the menus on both desktops it will be a bit cluttered....

---

### Post by Bigtime_Scrub on 2008-07-08
Yes you can install KDE with Synaptic. The only difference I've seen (I'm no expert so don't hold me to this) from what I've used is that when you install Kubuntu it comes with different applications. For example your window manager is Konqorer and not nautilus. Konqorer is also a web browser. Things just work a little different too, its kinda hard to explain unless you have used it. 

If you install KDE on a normal ubuntu system, you will get the choice to use it when you log in by using the "Sessions" option. It will keep whatever apps you have already set for Ubuntu/Gnome and transfer them to the K Desktop. Kubuntu just uses whatever it comes with. 

People also say that running KDE apps in Gnome as vice-versa causes problems in computer speed and is also prone to wierd stuff happening but I haven't ever seen that myself first hand.

---

### Post by bumanie on 2008-07-08
You can download KDE and at the login screen go to options (bottom left of screen) and click you should be able to find an option whether to boot into gnome or KDE (select session, I think is the menu to click).

---

### Post by AOZ on 2008-07-08
Thanks alot im just kinda bored and im thinking about putting openSuse on this old box at home to play around with, Just wnate dot see what KDE was all about with dling a live cd

---

### Post by snowpine on 2008-07-08
```
sudo aptitude install kubuntu-desktop
```

And if you try it and don't like it,

```
sudo aptitude remove kubuntu-desktop
```

I've heard that aptitude is better than apt-get at completely removing packages.

---

### Post by AOZ on 2008-07-08
..my...god this is wierd.
Do i get any panels?
Why are my only options for broder size Normal, Large, Very Large, Huge, Very Huge, Oversized?
Everythign seems so....huge

---

### Post by Bucky Ball on 2008-07-08
Download in your prefered fashion, re-boot and at login, change session and you will get a menu. You will find KDE, Gnome and whatever other setups you download there. Fill in details and should ask if you want the change just for that session or for good, verify and you're off. You can make some nice blends because the desktops add their flavours, but you have the same packages loaded as you did with Gnome. Then you can add and subtract packages as required.

Have fun.

---

### Post by AOZ on 2008-07-08
awesome. one mroe question. i know i can load X in more than one virtual terminal, can i have say gnome running in one, KDE running in one, and xfce running in another? i know its kind of ridiculous and completely useless, but it would be kinda cool

---

### Post by Bucky Ball on 2008-07-08
Never tried that one! Good luck and let us all know how it goes ...

---

### Post by stchman on 2008-07-08
> **snowpine said:**
> ```
sudo aptitude install kubuntu-desktop
```

And if you try it and don't like it,

```
sudo aptitude remove kubuntu-desktop
```

I've heard that aptitude is better than apt-get at completely removing packages.

Use the autoremove command:

```
sudo apt-get autoremove kubuntu-desktop
```

---

### Post by AOZ on 2008-07-08
> **Bucky Ball said:**
> Never tried that one! Good luck and let us all know how it goes ...

So if im in say tty1, and i enter startx --:1 or watver, it automatically starts into GNOME because i guess i logged into my original session in gnome. Is there anyway around that / can i access my login screen fomr the terminal?

---

### Post by blazercist on 2008-07-08
the command you are looking for is sudo /etc/init.d/gdm start for gnome and sudo /etc/init.d/kdm start for KDE

---

### Post by Bucky Ball on 2008-07-08
[QUOTE=AOZ]Is there anyway around that / can i access my login screen fomr the terminal?[/QUOTE]

You can also just make like you are shutting down, go to logout instead (switch users may also have this result) and that takes you back to the log in screen and good to go on new session (desktop).

---

### Post by Chris Kupka on 2008-07-12
So after I installed kubuntu, the shutdown interface in gnome (with the picture of the little running guy) took away the options for "shut down" - I have to logout to the sign-in screen and log off from there.  I still have the full array of options in kde, but I can't logoff straight from gnome unless I do it from the terminal.

Has anybody else had the same problem?  Is there a fix?

---

### Post by Chris Kupka on 2008-07-12
errr...can't shut down straight from gnome.   I can log off.   Sorry for the typo(s).

---

