---
title: "Python opengl and Python GTKGLExt support not enabled?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by essethug on 2008-07-19
How do I enable this support? 

Help total linux noob!!

---

### Post by sea_monkey987 on 2008-07-19
Install the packages "python-opengl" and "python-gtkglext1".  One way to do by typing this in the terminal:
```
sudo apt-get install python-opengl python-gtkglext1
```

---

### Post by Andras B. on 2009-07-15
Sorry for bringing up this old thread, found it through search.

I suppose you got that message, while trying to enable 3D view in Chess game? At least that was the case for me. I have installed the two packages, like suggested, set up 3D view in Chess, and wasn't able to start Chess ever since. A window pops up and immediately disappears.

I have the Restricted NVidia driver enabled (ver. 180), desktop effects work fine. I'm using 9.04 Jaunty. Any suggestions?

---

### Post by niteshifter on 2009-07-15
> **Andras B. said:**
> Sorry for bringing up this old thread, found it through search.

I suppose you got that message, while trying to enable 3D view in Chess game? At least that was the case for me. I have installed the two packages, like suggested, set up 3D view in Chess, and wasn't able to start Chess ever since. A window pops up and immediately disappears.

I have the Restricted NVidia driver enabled (ver. 180), desktop effects work fine. I'm using 9.04 Jaunty. Any suggestions?

python-opengl may need python-numpy:
```
sudo apt-get intall python-numpy
```

If that doesn't work and you want to get Chess (glChess) back to 2D:
Open the Configuration Editor: Click Applications -> System Tools -> Configuration Editor. Not present in the menus? Then in Terminal type:
```
gconf-editor
```

In the Configuration Editor, left side pane, click the triangle beside "apps" - see Screenshot 1 below.

Scroll the left side down, looking for glchess. Click on it. 

Scroll the right side pane down, look for the "show_3d" entry. Click the box to clear it - see Screenshot 2 below.

Close the Configuration Editor.

---

### Post by Martin Marshalek on 2009-07-15
Wait, the real issue is that Jaunty has the beta 6 package of python-opengl. The way to fix this is to uninstall python-opengl and install the deb that I attached to my post.

I didn't find this myself though, its on another post somewhere on the forum, I forget which one though.

---

### Post by Andras B. on 2009-07-15
Thanks for the replies! :)

That's odd, I opened up gconf-editor, and the 'show_3d' checkbox was CLEAR, while Chess still would not start. I installed the "python-numpy" package, as suggested, and now 3D view works! :)

It is very sluggish, though, animations are going with 2 FPS tops.

---

### Post by DarthZimmeris on 2009-07-16
Worked for me! Thx!!!

NVIDIA 9600GT w/ NVIDIA Restricted Drivers v180
):P

---

### Post by solemortal on 2010-01-20
3d Chess worked for me after installing these two packages. Honestly expected a better 3d view though. 
Cheez

---

### Post by mrdmanohar on 2010-02-27
Thanks a lot

---

