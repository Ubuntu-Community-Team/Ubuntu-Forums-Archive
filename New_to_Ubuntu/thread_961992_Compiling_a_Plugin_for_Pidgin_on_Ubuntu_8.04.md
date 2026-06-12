---
title: "Compiling a Plugin for Pidgin on Ubuntu 8.04"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by LilaLand on 2008-10-28
I'm trying to compile the attached plugin for pidgin on ubuntu 8.04.

When i cd to the extracted folder and type sudo make... it gives me a lot of errors. I contacted the maker of the plugin, and he told me that i need to build pidgin so that i have all the libraries and stuff... now i tried building pidgin, but i got a bunch of errors doing that too.

I know pidgin comes with ubuntu 8.04. Yet, i guess you just can't build new plugins for it?!

If anyone has ubuntu 8.04, could I ask a favor... and please help me... please compile the attached plugin, and give me the final .so file... 

thanks....

---

### Post by marshalium on 2008-10-28
> **LilaLand said:**
> I'm trying to compile the attached plugin for pidgin on ubuntu 8.04.

When i cd to the extracted folder and type sudo make... it gives me a lot of errors. I contacted the maker of the plugin, and he told me that i need to build pidgin so that i have all the libraries and stuff... now i tried building pidgin, but i got a bunch of errors doing that too.

The developer was right that you need the development libraries for pidgin. But you don't need to build pidgin yourself. 

The pidgin development files are available in the repository, just install them with:
```
sudo apt-get install pidgin-dev libpurple-dev
```

Then you should be able to build your new plugin.

---

### Post by LilaLand on 2008-10-30
IT WORKED! THANKS SO MUCH!

But there are a few things that need to also be done prior to doing the above code... I'll list them here for future reference!

sudo apt-get update
sudo apt-get libgtk2.0-dev

THEN you can do the above code. 

So the full sure-fire way to install plugins for pidgin on ubuntu 8.04 hardy heron is:

1. download Build-essentials for 8.04
2. do the following code in terminal:

sudo apt-get update
sudo apt-get install libgtk2.0-dev
sudo apt-get install pidgin-dev libpurple-dev


:D:D:D:D:D THANKS!

---

### Post by marshalium on 2008-10-30
You are welcome.

---

