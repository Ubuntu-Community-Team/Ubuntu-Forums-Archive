---
title: "[NEED HELP] to view sites like youtube.com you need flash player"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by ||Z0di4C|| on 2008-11-26
i downloaded the flash player good right wrong i go back into youtube and go to watch something and it says the same message over again so i was wondering how to fix this problem any and all help is welcome

---

### Post by chrisod on 2008-11-26
I hate to ask the obvious question, but have you actually installed the file that you downloaded? Go to Adobe.com and get the .deb install file for Flash and install it.

---

### Post by Olivier2371 on 2008-11-26
Hi there,

What message does it give you.

Have you tried to browse through firefox addons, there is one that allow you to watch or download youtube movies.

---

### Post by ||Z0di4C|| on 2008-11-26
thanks yeah i just went into the firefox addons and downloaded one that seemed to work

---

### Post by Olivier2371 on 2008-11-26
Thank's,

I am just glad I could help.

If your issue his resolved could mark the thread as solved using the thread tool on the menu above.

---

### Post by zvacet on 2008-11-26
If you go to the **system>admin>software sources<third party** and enable partner repo you will get flash with synaptic.Or you can type in terminal

```
gksudo gedit /etc/apt/sources.list
```

and add this line 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

save and close the file.

```
sudo apt-get update
```

and in synaptic search box type adobe-flashplugin and when synaptic find package install it.

P.S. if you are runing Interpid you will replace **hardy** in the line with **interpid**.

---

