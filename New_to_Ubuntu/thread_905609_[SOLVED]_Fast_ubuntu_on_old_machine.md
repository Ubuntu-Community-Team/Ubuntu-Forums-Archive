---
title: "[SOLVED] Fast ubuntu on old machine"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by natman on 2008-08-30
I have an old gateway laptop, pentium 4,256 ram. I currently have Xubuntu on it and works ok, is there any better options? I dont really want to go outside of ubuntu ( since ubuntu have always been excellent for drivers on wifi cards and stuff )
I have heard of Fluxbuntu would it make much of a difference over Xfce? Any ideas?

Thanks:
Patrick

---

### Post by pytheas22 on 2008-08-30
Yes, Fluxbuntu uses a more lightweight desktop environment than Xubuntu, so you'd probably get better performance.  Fluxbox is not too pretty and requires some configuration (you have to write the menus yourself, for instance), but it's really fast.

You don't need to install Fluxbuntu just to try Fluxbox.  You can install Fluxbox alongside XFCE with:
```

sudo apt-get install fluxbox
```

Then you'll have the option of using either Fluxbox or XFCE the next time you want to log in.

If you can't do anything in Fluxbox at first, it's probably because you need to write menus, etc.  [This]("http://ubuntuforums.org/showthread.php?t=371144") should help.

---

### Post by OutOfReach on 2008-08-30
Of course fluxbuntu would work better than Xubuntu, fluxbox  take a little configuration to get it just right, but it is worth while

---

### Post by nickgaydos on 2008-08-30
I personally like OpenBox better
```
Sudo apt-get install openbox
```

---

### Post by Vivaldi Gloria on 2008-08-30
If I were you I'd install a base system (see CLI in my sig) and install openbox on it. 

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

Also give crunhbang a try:

[http://crunchbang.org/projects/linux/](http://crunchbang.org/projects/linux/)

---

### Post by 4Orbs on 2008-08-30
You already have Xubuntu... try the LXDE desktop or Enlightenment desktop from OzOS (or both) and log onto a different session OS every day. Should drop your memory usage by a few percent below Xfce.

+1 for CrunchBang or the mini Ubuntu cli install.

Maybe give the Mepis antiX live cd a try, even though its not Ubuntu based.

---

