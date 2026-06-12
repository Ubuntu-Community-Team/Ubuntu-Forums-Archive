---
title: "How to uninstall a program which was not installed thru the default add/remove thing?"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by kramer65 on 2008-09-17
Hello,

Yesterday I installed dropbox. Although I think the idea is just brilliant, it doeesn't really work for me (yet). I now want to uninstall dropbox which I installed with a downloaded deb. However, I don't know how?

I looked in the add/remove apps section but I can't find it there. I clicked the deb again, but I can only reinstall it with that. Is there any way that I can uninstall it? 

Why doesn't ubuntu have some kind of "installed programs" list?

---

### Post by Elfy on 2008-09-17
It does - use synaptic - iof you installed with a deb it should be there to remove.

You can also do it from the terminal, replace package with name of installed program

```
sudo apt-get remove *package*
``` removes the program

```
sudo apt-get purge *package*
``` will also remove the config files

---

### Post by Mornedhel on 2008-09-17
> **forestpixie said:**
> It does - use synaptic - iof you installed with a deb it should be there to remove.

Yup. Under Origin/Local Installation tab. Or something like that.

> **forestpixie said:**
>  ```
sudo apt-get purge *package*
``` will also remove the config files

That's sudo apt-get --purge remove package.

---

### Post by SunnyRabbiera on 2008-09-17
> **kramer65 said:**
> Hello,

Yesterday I installed dropbox. Although I think the idea is just brilliant, it doeesn't really work for me (yet). I now want to uninstall dropbox which I installed with a downloaded deb. However, I don't know how?

I looked in the add/remove apps section but I can't find it there. I clicked the deb again, but I can only reinstall it with that. Is there any way that I can uninstall it? 

Why doesn't ubuntu have some kind of "installed programs" list?

well it does, via a application called Synaptic.
Go to system> administration> synaptic

Synaptic is like a more advanced version of add/remove, it lists what is installed and what is not installed.
Synaptic lists more applications by default then add/remove does alone, as add/remove only gives a base amount of applications to get one started.
In synaptic you can remove applications you dont want by simply clicking the box (right or left click) next to the name of the application you dont want.
Or it can be used to install applications that might not be listed via add/remove.
Synaptic is easy enough to figure out but if you need help just ask.

---

### Post by kramer65 on 2008-09-17
Great thank you! I did use synaptic before indeed, but always associate it with the words "difficult and confusing" since it lists all these things that don't mean anything to me. This is why I didn't think of it for simply uninstalling something.. It went perfect though, everything is now uninstalled.

Thanks!

---

### Post by SunnyRabbiera on 2008-09-17
> **kramer65 said:**
> Great thank you! I did use synaptic before indeed, but always associate it with the words "difficult and confusing" since it lists all these things that don't mean anything to me. This is why I didn't think of it for simply uninstalling something.. It went perfect though, everything is now uninstalled.

Thanks!

Truth be told Synaptic is actually very easy in itself, it just lists a lot of packages thats all (it lits all the applications and junk from the repositories)
Synaptic is like a shopping list and picking out what you need/ dont need.
Its search function is very useful, and installing things in it is as easy as pie.
I know bit helped me out when I first started, back then they didnt even have add/remove!
I started 4 years ago, never looked back thanks to the ease of Debian based distributions.

---

