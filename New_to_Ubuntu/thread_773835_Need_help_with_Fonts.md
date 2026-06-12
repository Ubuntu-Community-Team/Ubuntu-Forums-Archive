---
title: "Need help with Fonts"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by iSplicer on 2008-04-29
Hello!

I have been using ubuntu for a while now, mainly for programming and work purposes. However, some websites look really mtessed up when using the default fonts that ubuntu comes with. In windows, this is how [www.gamerenders.com](www.gamerenders.com) looks like:

[IMG]http://img249.imageshack.us/img249/8171/88762309vl3.png[/IMG]


This is how the exact same page looks in ubuntu:

[img]http://img255.imageshack.us/img255/5047/screenshotef3.png[/img]


Could someone please help me solve this problem, and get ubuntu to display text in a font just like windows? 

Thanks!

---

### Post by gn2 on 2008-04-29
Have you added the ubuntu-restricted-extras metapackage yet?

This has a bunch of good stuff, including the msttcorefonts package which is what you need.

Either use Add/Remove or Synaptic Package Manager to install either ubuntu-restricted-extras or just msttcorefonts

Alternatively, open a terminal and run this:
```
sudo apt-get install ubuntu-restricted-extras

**OR**

sudo apt-get install msttcorefonts
```

If this is already installed, in Firefox>Edit>Preferences>Content, Fonts & Colours>Advanced make sure that "Allow pages to choose their own fonts....." is ticked.

---

### Post by iSplicer on 2008-04-29
Thanks mate, its looking a lot better now!

---

