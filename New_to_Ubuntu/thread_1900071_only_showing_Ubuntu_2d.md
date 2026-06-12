---
title: "only showing Ubuntu 2d"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by miguel71 on 2011-12-25
One friend of mine show me a app called compiz we installed and playd a bit with it but now on the login screen i only get the option of "Ubuntu 2d" and i dont get the "ubnutu" normal option.:(

---

### Post by BC59 on 2011-12-25
Compiz is the Windows manager for Ubuntu/Unity.

To be sure your computer is 3D Unity compatible run this from a terminal CTRL+ALT+T

/usr/lib/nux/unity_support_test -p

If you see "Unity" is good to go.

Then try to reset Compiz. Open the Compiz Config Settings Manager (if you don't have it install it through Ubuntu Software Center) and in the left pane you can see the button "Preferences". From there push the button "Reset to defaults".

---

### Post by grahammechanical on 2011-12-25
You may find this link useful:[https://help.ubuntu.com/community/CompositeManager]("https://help.ubuntu.com/community/CompositeManager")

I only saw it yesterday, myself. Go down the page to the heading: Window Managers & The Commands To Start Them Manually.

You may need to run the command

```
compiz --replace
```

Others on this forum may confirm this.

Regards.

---

### Post by BC59 on 2011-12-25
Well the most updated command for reseting Compiz is this:

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

The problem is that sometimes the medicine has side effects...

---

### Post by hatalar205 on 2011-12-25
> **miguel71 said:**
> One friend of mine show me a app called compiz we installed and playd a bit with it but now on the login screen i only get the option of "Ubuntu 2d" and i dont get the "ubnutu" normal option.:(

I think you are looking for something like Gnome 2. If so, install "Gnome-shell" from the software center and choose "gnome classic" on the login screen.

---

