---
title: "compiling gdesklets"
date: 2005-01-04
forum: Packaging and Compiling Programs
---

### Post by cacofonix on 2005-01-04
Help!!!

I'm at my wits end I keep running into errors and I can't find the files I need to fix them.
when I do the configure command I get this error:
```

configure: error: Library requirements (glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >=
 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your
 libraries are in a nonstandard prefix so pkg-config can find them.

```
I tried searching in synaptic and I can't find the files where do I get them?

thanks in advance

cacofonix

---

### Post by hashimoto on 2005-01-04
[QUOTE=cacofonix]Help!!!

I'm at my wits end I keep running into errors and I can't find the files I need to fix them.
when I do the configure command I get this error:
```

configure: error: Library requirements (glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >=
 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your
 libraries are in a nonstandard prefix so pkg-config can find them.

```
I tried searching in synaptic and I can't find the files where do I get them?

thanks in advance

cacofonix[/QUOTE]
 AFAIR, Gdesklets is in the "universe" or "multiverse". Add them to your repositories and at the same time add Marillat to your repositories. Go to: [http://ubuntuguide.org/index.html#extrarepositories](http://ubuntuguide.org/index.html#extrarepositories) 
for instructions. After that you can install gdesklets & gdesklets-data using synaptic

BR
Hashimoto

---

### Post by cacofonix on 2005-01-04
I grabbed the gdesklet from the universe repository and one of the displays didnt work any more and the fix was to get the newest version, thats why I'm compiling it. any Ideas where I can get the needed packages from.

Thanks for your help hashimoto :D

cacofonix

---

### Post by rbran100 on 2005-01-04
I ran into the same problem and my research led me to believe that compiling from source on a newer version was a real pain, and that a lot of people didn't get it working.  I am just going to try to hold out till April but if you get it working please let me know!

Richard

---

### Post by Perfect Storm on 2005-01-04
[QUOTE=cacofonix]Help!!!

I'm at my wits end I keep running into errors and I can't find the files I need to fix them.
when I do the configure command I get this error:
```

configure: error: Library requirements (glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >=
 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your
 libraries are in a nonstandard prefix so pkg-config can find them.

```
I tried searching in synaptic and I can't find the files where do I get them?

thanks in advance

cacofonix[/QUOTE]

You have to compile these files it asking for, the reason is that you can't find those files with the right version in the ubuntu, universe or multiverse (I tried).

---

### Post by duff on 2005-01-11
[QUOTE=cacofonix]Help!!!

I'm at my wits end I keep running into errors and I can't find the files I need to fix them.
when I do the configure command I get this error:
```

configure: error: Library requirements (glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >=
 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your
 libraries are in a nonstandard prefix so pkg-config can find them.

```
I tried searching in synaptic and I can't find the files where do I get them?

thanks in advance

cacofonix[/QUOTE]
You need to install a bunch of *-dev packages.  Start by installing `libgtk2.0-dev` to fix the above errors, run configure again, and see what else needs to be installed....it may take 4 or 5 tries. IIRC< `python-gtk2-dev` and `libgtop2-dev` are among the other packages you'll need.

---

