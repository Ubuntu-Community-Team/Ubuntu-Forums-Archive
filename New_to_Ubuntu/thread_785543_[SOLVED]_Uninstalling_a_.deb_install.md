---
title: "[SOLVED] Uninstalling a .deb install"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-05-07
If I installed a program from a .deb file (which I did), how does one go about removing it?  No problem with the program itself, I just found a better solution.

---

### Post by drs305 on 2008-05-07
It should be listed in synaptic. You can remove it from there.
or
```
sudo dpkg --purge packagename
```

---

### Post by H.Callahan on 2008-05-07
Dang!  I would have SWORN that it wasn't listed there the first time I looked.  But I found it and it is uninstalled.  Thanks!

BTW, I just looked and a package that I installed using the make/make install scenerio is definitely NOT listed (and, yes I checked twice!).  I don't want to uninstall that one, but if I did, how do I do that?

---

### Post by lswest on 2008-05-07
compiled software (e.g. make files) need to be uninstalled by going to the source directory (that you made it from) and running ```
sudo make uninstall
``` or running the available uninstall script that will be there in place of it (that's why it's best if you keep the source folder with the files after the compiling).

---

### Post by H.Callahan on 2008-05-07
[img]http://www2.incredimail.com/english/images/order/smiley.gif[/img]
Well, I am glad I didn't delete the original archive then!

Thanks!

---

### Post by lswest on 2008-05-07
> **H.Callahan said:**
> [img]http://www2.incredimail.com/english/images/order/smiley.gif[/img]
Well, I am glad I didn't delete the original archive then!

Thanks!

no problem, glad i was able to help ^^ Thanks for the thanks, and i hope you enjoy your Ubuntu experience ;)
Lswest

---

### Post by PeterJS on 2008-05-07
Heads up next time you compile something from source if you use checkinstall instead of make install, checkinstall will build a .deb package for you and install that, so you can remove the software like you would any other package.

---

### Post by stchman on 2008-05-07
> **H.Callahan said:**
> If I installed a program from a .deb file (which I did), how does one go about removing it?  No problem with the program itself, I just found a better solution.

To completely remove a .deb package use the autoremove command.

```
sudo apt-get autoremove <.deb package>
```

This will remove all the unused dependencies as well.

---

### Post by H.Callahan on 2008-05-07
> **lswest said:**
> no problem, glad i was able to help ^^ Thanks for the thanks, and i hope you enjoy your Ubuntu experience ;)
Lswest  It's been a blast so far.  Most of my problems have been due to faulty (read: Windowish) thinking on my part.

---

