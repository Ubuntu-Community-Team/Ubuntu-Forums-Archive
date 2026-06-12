---
title: "libgnomeui installation error"
date: 2005-03-16
forum: Repositories &amp; Backports
---

### Post by Stefan Koopmanschap on 2005-03-16
hey everyone,

I'm trying to install gnomad2 on my wife's Ubuntu PC. Since it's not in the Ubuntu repositories, I need to compile it myself. Since it has some dependencies, I try to get those libraries installed from the Ubuntu repositories using the Synaptic that was installed when installing Ubuntu.

Some libraries are fine, however, when trying to install libgnomeui-dev, I'm running into trouble.
I run into the error: 

[img]http://www.stefankoopmanschap.com/gnomeuiinstallerror.jpg[/img]

I tried to trace it down, and it seems there is some trouble, especially with libart. There is a very slight version mismatch between the actual libraries and the dev package that is preventing me from installing the dev package, which is needed for gnomeui.

[img]http://www.stefankoopmanschap.com/libartinstallerror.jpg[/img]

Has anyone run into these problems before? Or, does anyone know if it's possible to simply mount a Creative Zen xtra device without all this extra software? It seems the Zen doesn't get an entry as /dev/sd* ...

Any help is much appreciated

---

