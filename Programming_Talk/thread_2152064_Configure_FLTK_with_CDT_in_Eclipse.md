---
title: "Configure FLTK with CDT in Eclipse"
date: 2013-06-06
forum: Programming Talk
---

### Post by 1cookie on 2013-06-06
Hi

I'm trying to configure FLTK with CDT in Eclipse. CDT is working fine, I can build and compile .cpp projects
in the workbench.

I'm following this tutorial:
[http://www.eclipse.org/forums/index.php/m/537879/](http://www.eclipse.org/forums/index.php/m/537879/)

From the tutorial, I'm looking for 

```
/usr/lib/freetype2
```

on my system only it doesn't exist. All other components are visible on my system:

```

/usr/include/FL
/usr/lib/fltk
/usr/include/GL

```

I installed FLTK from Synaptic:

```

/usr/lib
drwxr-xr-x  2 root root         4096 Jun  6 19:26 fltk

```

It's a fresh install of Ubuntu 13 and Eclipse.

Can you point me in the right direction? Is there a 
sudo apt-get install XXXX command that will fetch freetype?

Is the tutorial accurate? If I follow it to the letter, will I be able to start programming GUIs in C++?

---

