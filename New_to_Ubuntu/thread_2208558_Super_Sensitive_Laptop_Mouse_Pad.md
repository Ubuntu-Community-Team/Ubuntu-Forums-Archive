---
title: "Super Sensitive Laptop Mouse Pad"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by GUZZLR on 2014-02-28
Hello All...
Is there a code to get into, and adjust the mouse pad settings on a laptop?  Windows has this functionality, does Ubuntu 13.10?
Thanks for the help

---

### Post by squakie on 2014-03-01
There is a package called tpconfig that is supposed to provide some sort of configurability for a touchpad, but I have never used it so I couldn't tell you if it would help you or not.  

If you want to install it:

sudo apt-get install tpconfig

---

### Post by GUZZLR on 2014-03-02
So I ran the commands and installed, but  what happens now?  I dont see anything different?
Thanks for the help

---

### Post by artie3 on 2014-03-05
I have the same issue on my Dell laptop. However, I despise the touchpad interface and use a mouse instead. However, if you've installed the utility program as suggested, you can access the help file by using:

```
man tpconfig
```

Enjoy.

Artie

---

### Post by GUZZLR on 2014-03-05
Ran the "man tpconfig" but never really found what I was looking for...Thanks though

---

### Post by SuperFreak on 2014-03-05
My 13.10 PC with cinnamon DE has under preferences/mouse & touchpad settings. There should be something comparable in Unity

---

### Post by wn1ytw on 2014-03-05
This works for mice, and while getting the settings for my mouse I noticed my trackpad settings, so a similar senario should also help your trackpads - though you will have to experiment...

[http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/)

---

### Post by GUZZLR on 2014-03-07
```
[http://patrickmylund.com/blog/loweri...n-ubuntu-9-10/]("http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/")
```

this is interesting,  the problem with my mouse pad, is not the speed of the pointer, this is fine.  The problem is the sensitivity level,  It is so sensitive to the touch, it is basically useless because no matter how "light" of touch, the movement of ones finger makes the pointer miss the target completely.  On the patrickmylund blog, I found the area of adjusting the pointer speed, but not the sensitivity level.  Did I miss it?
The settings in mouse and  pointer allow for pointer speed, but nothing for sensitivity levels.  I have  installed Unity Tweak, but I don’t see a sensitivity level there either.
Thanks for the help

---

### Post by wn1ytw on 2014-03-08
I think that depends on what you get as a result from ```
 xinput --list --short 
``` In any event,  good luck. :)
scott

---

### Post by joeblow9104 on 2014-05-06
I also really need help with this...

---

