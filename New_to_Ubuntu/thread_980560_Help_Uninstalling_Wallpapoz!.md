---
title: "Help Uninstalling Wallpapoz!"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Realest07 on 2008-11-12
I recently installed wallpapoz and now I don't want it anymore. How do I uninstall it?  It's not in the add/remove programs list and I can't find it in the synaptic package manager.  How do I remove this program? Please help. Thanks.

---

### Post by jimmy the saint on 2008-11-12
how did you install it in the first place?

---

### Post by Airfoot on 2008-11-12
go into terminal and type:  

$ sudo apt-get remove wallpapoz

this should remove it.

---

### Post by Realest07 on 2008-11-13
I tried "$ sudo apt-get remove wallpapoz" doesn't work. It said Couldn't find package wallpapoz.

---

### Post by Airfoot on 2008-11-13
the wallpapoz package must have a name different then wallpapoz, you can try to find and delete it manually by going into the directory:  
/usr/lib
look for a folder with a name involving wallpapoz and delete it, but be careful, you don't want to accidentally delete a program you still want or need.

---

### Post by Interpreter on 2008-11-13
man -k wallpaper

should give you a list of programs that mention wallpaper(s) in their manual. You could use that to go thru a list of programs and look up the exact name of the package you want to remove.

---

### Post by Nepherte on 2008-11-13
Again, how did you install wallpapoz? It's not in the repositories so that either means you found a .deb file somewhere or you compiled it manually.

---

### Post by Realest07 on 2008-11-13
> **Airfoot said:**
> the wallpapoz package must have a name different then wallpapoz, you can try to find and delete it manually by going into the directory:  
/usr/lib
look for a folder with a name involving wallpapoz and delete it, but be careful, you don't want to accidentally delete a program you still want or need.

I tried searching for it on my computer and hitting delete but it would not delete, it said "Permission Denied" ... 

I followed a short guide to install it but I can't find it to explain exactly. Basically what I did was download a tar file, extract it and run a command in the terminal. I tried running "# python install.py uninstall" because I saw that in a different thread and that's similar to how I installed it but that didn't work either.

---

