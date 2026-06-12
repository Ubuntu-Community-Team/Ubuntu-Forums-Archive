---
title: "Installing photoshop cs2"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by dtommy79 on 2008-07-19
Hi,

How can I install photoshop cs2 on ubuntu?
I have wine installed, and the photoshop is an iso file.

Thanks

---

### Post by Vorian Grey on 2008-07-19
> **dtommy79 said:**
> Hi,

How can I install photoshop cs2 on ubuntu?
I have wine installed, and the photoshop is an iso file.

Thanks

The iso is sort of like a zip file and it contains all the files. Open the iso with archive manager and extract the files and then click the setup file in that directory and you're good to go.

---

### Post by dtommy79 on 2008-07-19
Hi,

thanks for the answer. i managed to install it, at least almost. I must have screwed up something because on start up photoshop says it's need to be reinstalled. 
Now I don't know how.
So how can I uninstall it first?

Thanks

---

### Post by Vorian Grey on 2008-07-19
You should be able to uninstall it by going to the Wine menu under applications and click Uninstall Wine Software. 

Here is a guide to help you install CS2 on Ubuntu....

```
http://news.softpedia.com/news/Install-Photoshop-CS2-on-Your-Ubuntu-PC-77260.shtml
```

Myself, I use Winetricks and install corefonts, vcrun6, and gecko. Gecko and Iexplore in the article above is the same and corefonts adds all the Window fonts instead of just one. I do use the Wine repo from the above article as well. CS2 works flawlessly for me doing this. 

Winetricks...

```
http://wiki.winehq.org/winetricks
```

---

### Post by dtommy79 on 2008-07-19
Thanks.

I tried to uninstall it, but for some reason it won't uninstall. The install shield runs, and says the stuff is removed, but it's still there.

---

### Post by Vorian Grey on 2008-07-19
Don't worry about the menu items. Just add the stuff you need like fonts and then reinstall it and it should work.

---

### Post by dtommy79 on 2008-07-19
OK, I've installed, but after launching photoshop i get this message:

> An error has been detected with a required application library
and the product cannot continue. Please reinstall the application.

But after reinstall I get the same error.

---

