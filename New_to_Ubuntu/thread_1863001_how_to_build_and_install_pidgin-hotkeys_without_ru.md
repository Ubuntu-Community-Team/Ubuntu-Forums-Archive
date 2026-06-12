---
title: "how to build and install pidgin-hotkeys without running sudo apt-get?"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by pavel__ on 2011-10-17
hi

i'm trying to install [http://sourceforge.net/projects/pidgin-hotkeys/](http://sourceforge.net/projects/pidgin-hotkeys/), but i have no admin rights on this machine, so I'd like to install the plugin locally, without having to run sudo apt-get install. unfortunately, I don't know how to do so. 

does anyone know how do I get this running?

thanks!

---

### Post by Frogs Hair on 2011-10-17
You will need sudo permission to install software via .deb package or a tar .gz from the terminal . I would see your system administrator if you don't have permission to install software .

---

### Post by pavel__ on 2011-10-17
it's not always the case - e.g. I can install google chrome just by unpacking the .deb package.

is there a way to unpack the pidgin-hotkeys and tell pidgin to look somewhere locally for additional plugins?

---

### Post by Frogs Hair on 2011-10-17
I can't support installing a program without administrator approval . There are many guides for installing tar .gz packages on the web .

---

### Post by mcduck on 2011-10-18
The user directory for pidgin plugins is ~/.purple/plugins. Depending on how the plugin in question works, unpacking it there might do the trick.

---

