---
title: "My terminal is GONE!"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by necronzero on 2008-06-04
So yeah, basically, my terminal is nowhere to be found O_O... i tried finding it, but no luck... is there a way to reinstall it?

---

### Post by wolfen69 on 2008-06-04
```
sudo apt-get remove --purge gnome-terminal
```
```
sudo apt-get install gnome-terminal
```

---

### Post by necronzero on 2008-06-04
> **wolfen69 said:**
> ```
sudo Apt-get Remove --purge Gnome-terminal
```
```
sudo Apt-get Install Gnome-terminal
```

I Love U

---

### Post by Kevbert on 2008-06-04
If you've just lost the icon right click on Applications - Select Edit menus and look for the terminal under Applications - Accessories.  Check that Terminal is ticked.
If you've lost the Terminal program, go to Applications - Add/Remove, Select Accessories and enter terminal in the Search Box.  Tick either terminal and then click on Apply Changes.

---

### Post by jamewill on 2008-06-04
> **necronzero said:**
> So yeah, basically, my terminal is nowhere to be found O_O... i tried finding it, but no luck... is there a way to reinstall it?

i don't think it is gone i think you just deleleted the shortcut/link to it in the start menus by mistake

here is a quick way to see if terminal is still available to you

right click on panel (bar at top of screen) and select ADD TO PANEL
choose ADD CUSTOM APP LAUNCHER and put xterm in the name and the command fields

close and now you have an icon which should give you a terminal window

does it work?
if so you can search for info on how to add things to the applications menu and restore "Terminal" to Applications | Accesories if you wish

jw

---

### Post by necronzero on 2008-06-04
> **Kevbert said:**
> If you've just lost the icon right click on Applications - Select Edit menus and look for the terminal under Applications - Accessories.  Check that Terminal is ticked.
If you've lost the Terminal program, go to Applications - Add/Remove, Select Accessories and enter terminal in the Search Box.  Tick either terminal and then click on Apply Changes.

managed to run a Sudo terminal and applied changes with the codes above, thanks to both :D

---

### Post by necronzero on 2008-06-04
> **jamewill said:**
> i don't think it is gone i think you just deleleted the shortcut/link to it in the start menus by mistake

here is a quick way to see if terminal is still available to you

right click on panel (bar at top of screen) and select ADD TO PANEL
choose ADD CUSTOM APP LAUNCHER and put xterm in the name and the command fields

close and now you have an icon which should give you a terminal window

does it work?
if so you can search for info on how to add things to the applications menu and restore "Terminal" to Applications | Accesories if you wish

jw
It was deleted for some reason, i do know how to add stuff on the panel :P but still it was weird >_>
thanks to all, my problem is SOLVED

---

### Post by .Michael on 2008-06-04
I think terminal is a pretty cool guy. eh is gone and doesnt afraid of anything.

1. hit Alt + f2
2. type xterm
3. ???
4. profit

---

