---
title: "Panels?"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by Yezinki on 2012-09-28
How can the left side & upper panels be deleted & one created at the bottom in 12.04?

---

### Post by newb85 on 2012-09-28
Don't think that's possible using Unity.

Try using Gnome Fallback instead.

[http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html]("http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html")
(Scroll down to the section "Classic GNOME session - looks almost the same as GNOME 2".)

Also, have a look at Cinnamon and Mate, mentioned in the section just above that.

---

### Post by Yezinki on 2012-09-28
Thanks newb85

this commmand doesn't work     ```
 sudo apt-get install gnome-session-fallback
```

---

### Post by newb85 on 2012-09-28
> **Yezinki said:**
> Thanks newb85

this commmand doesn't work     ```
 sudo apt-get install gnome-session-fallback
```

Be more specific.  Does it give error messages?

---

### Post by Yezinki on 2012-09-28
> **newb85 said:**
> Be more specific.  Does it give error messages?


Gave this command, rebooted, but the upper/side panels wont move despite Alt & rt click?

---

### Post by Frogs Hair on 2012-09-28
Did you choose the Gnome session by selecting it from the icon on the greeter box?

---

### Post by jerrrys on 2012-09-29
could use docks; more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=docks&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=docks&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by uRock on 2012-09-29
```
sudo apt-get install gnome-panel
``` Log out, select classic gnome, then log in again.

---

### Post by Yezinki on 2012-09-29
> **Frogs Hair said:**
> Did you choose the Gnome session by selecting it from the icon on the greeter box?

Never got this opption in the greeter box Frogs Hair?

---

### Post by Yezinki on 2012-09-29
> **uRock said:**
> ```
sudo apt-get install gnome-panel
``` Log out, select classic gnome, then log in again.


Thanks uRock how does one install Cairo dock or is that the same?

---

### Post by newb85 on 2012-09-29
To choose a different session from the LightDM login screen, you have to click the little Ubuntu icon next to your name.

Cairo-Dock is not the same thing.  It is very easy to install.  If no one were here to answer that question, how would you install it?  I think you know enough to figure it out.  ;)

FYI, when you install Cairo-Dock, it will create an alternative session you can choose at the login screen, just like Gnome Fallback.

---

### Post by Yezinki on 2012-09-29
Thanks newb85.

How do I get rid o red cursor & hour glass got installed with Ubuntu tweaks?

---

### Post by Yezinki on 2012-09-29
Can one cutomize the short cuts of cairo dock with open GL effects?

Thanks.

---

### Post by newb85 on 2012-09-29
> **Yezinki said:**
> Can one cutomize the short cuts of cairo dock with open GL effects?

Thanks.

It should be the same with or without OpenGL.

If you're asking about changing which shortcuts (they're actually called launchers) are on the dock, then yes.

To remove one, right click it, click the name of the launcher on the menu that appears (just below Cairo-Dock) and hit "Remove".

To add one, first open the program.  Again, right-click the icon on the dock, click the name of the program, and click "Make it a Launcher".

---

### Post by Yezinki on 2012-09-29
Thanks newb85 for the reply.

A few questions about cairo deck before I reinstall Ubuntu.

1. Which option at the greetings do most experieneced users use like Genome with open GL etc?

2. How does one extract & install a tarz file?

3. Can one add docks at the uppper & lower corners besides top & bottom?

4. Which is the most popular theme & can one import one from where?

5. In configurations which options should mostly be checked?

6. Does it hog  system resources?

---

