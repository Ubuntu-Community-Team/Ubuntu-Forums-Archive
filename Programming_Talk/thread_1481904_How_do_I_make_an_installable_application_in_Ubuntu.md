---
title: "How do I make an installable application in Ubuntu?"
date: 2010-05-13
forum: Programming Talk
---

### Post by gemmahenchmen on 2010-05-13
I have made an application in C++ that compiles and runs successfully on Ubuntu, using a Makefile. My question is, how do I make it so that it is installed on my machine, ie. I could find it under Applications>Accessories or the like?

Thanks in advance for the help. :)

---

### Post by Tony Flury on 2010-05-13
If this is just for your machine, you can manually add it to your Main menu by going to System -> Administration -> Main Menu, and add a new item.

If you want to distribute it to others, and enable them to clean install it - then you should be looking at creating a deb package (there is a sticky for that).

The Deb package will allow for automatic resolution of dependencies (so the install will fetch other packages/libraries that might be needed), and can be made to run scripts etc which insert entries into Menus, create config files etc.

---

