---
title: "Finding and Tossing Old Junk"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by graypawn on 2008-07-06
So i mucked things up by downloading so much music that i filled my HD.  This resulted in my not being able to boot anymore.  Well, not really.  It gets to the login screen, and when i try to log in it grinds and grinds and then opens a shell terminal.  That's it.

i typed df -h like a friend told me and, yeah...too much space taken up.  I have, if i'm reading this right, 4.1 MB available.  Way to go me.

Which leaves me stuck wandering the forums looking for a dumbed-down way of finding and deleting files in Ubuntu.  And here's the real fun:  This all happened before i moved to my current home.  Six...Months...Ago.  Which is why i can't remember the paths or files ..uh, at all.  I need to check and see what's on my HD before i can remember what it is and delete it.

I'm currently running, uh, Breezy Badger, which is 5.something.  So not only is the Laptop ancient, but even the Linux is old.  I would not be surprised if there is no solution to this.

Final Q:  How do i browse for files in Shell, looking to find one i don't want enough to delete?  (and can't i just type -i and the path to said file once i've found it?)

---

### Post by sdennie on 2008-07-06
A good start would be to run:

```

sudo apt-get clean

```

That will probably delete several hundred megs worth of cached packages that you likely don't need because they are already installed (and you can automatically download again if you do need them).  That should at least get you into a bootable machine again.

---

### Post by Elfy on 2008-07-06
I would guess that you can use the apt clean to get rid of old packages, unless you already do - perhaps that will be enouhg to let you boot and get in and clean 

```
sudo apt-get clean
```

Edit - beaten to the line

---

