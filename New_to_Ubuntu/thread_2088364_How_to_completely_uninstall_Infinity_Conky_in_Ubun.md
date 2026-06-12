---
title: "How to completely uninstall Infinity Conky in Ubuntu 12.10"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by stelladeli on 2012-11-26
I know this may sound really dumb, but I don't want to create a problem.  Do I simply delete any file that I find associated with Infinity Conky?

---

### Post by SlugSlug on 2012-11-26
```
sudo apt-get remove --purge conky
```

---

### Post by stinkeye on 2012-11-26
Do you mean [**_[COLOR="DarkRed"]THIS[/COLOR]_**]("http://harshit1990.deviantart.com/#/d52qdtq").

If you do, then Infinity is just configs to be loaded by conky.
If you installed according to the included ReadMe.txt,
> Copy these 3 files .conkyrc, .lua and .conky files to your home directory
You would have 2 folders (**.lua** and **.conky**) and one file (**.conkyrc**) in your home folder.
Dot files are hidden. In the file browser press ctrl+h to show hidden.

Just delete the files/folders you moved and/or renamed. 
If you delete the **~/.conkyrc** config file then conky will use the
default config @ **/etc/conky/conky.conf**

If it's the actual conky program you want to uninstall just do
as SlugSlug said.

---

### Post by DuckHook on 2012-11-26
You might also wish to delete any files and directories that you created to run conky. These will sometimes be hidden files that start with a dot (ie .directory). Nautilus will show you hidden files if you type <ctrl>+<h>. Conky files/directories with an infinity install are:

.conky
.conkyrc
.lua

You might also have installed some fonts to run infinity. If you will not use these fonts again, it is your choice whether you wish to keep or delete them. Each font loaded by the OS into font cache at boot time eats up some system resources. I generally don't care on my systems with more memory, but like to keep my font cache absolutely minimal on my 516 MB laptop.

---

### Post by stelladeli on 2012-11-26
Thank you very much everyone!!!
I didn't want to uninstall the program conky but to remove Infinity safely. 
I think everything turned out okay!:)

---

