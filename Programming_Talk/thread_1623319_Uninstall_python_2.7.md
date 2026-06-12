---
title: "Uninstall python 2.7?"
date: 2010-11-16
forum: Programming Talk
---

### Post by trippn740 on 2010-11-16
I just installed Python 2.7 from the source and started to work on one of my Tk apps. I tried to run it and it gives the error that _tkinter can't be imported. So I tried wx/ gtk/ pygame and none of these could be imported... 

I just need to know how to uninstall Python 2.7, as it's not in my installed programs on the software center, and make uninstall didn't work.

---

### Post by ibod on 2010-11-16
> **trippn740 said:**
> I just installed Python 2.7 from the source and started to work on one of my Tk apps. I tried to run it and it gives the error that _tkinter can't be imported. So I tried wx/ gtk/ pygame and none of these could be imported... 

I just need to know how to uninstall Python 2.7, as it's not in my installed programs on the software center, and make uninstall didn't work.

Hi 

Try synaptic package manager

---

### Post by Vox754 on 2010-11-16
> **ibod said:**
> Hi 

Try synaptic package manager

Please read carefully the post before answering. He explicitly said he had installed Python 2.7 from source, and is thus not available to remove it through the package manager.


As for the OP. Are you having problems with your entire Ubuntu system or only with your program?

It is quite natural that you cannot import third party modules, because the new Python installation may be searching other paths with non-existent modules. It is a bad idea to install a newer Python version just because it's newer. You need to know what you are doing before doing it, specifically to avoid over-writing your older Python installation.

In general, there is no straight-forward way to remove Python 2.7 installed from source. You could simply remove the directories that were created and their contents.

And make sure you don't have Python binaries such as "/usr/local/bin/python" which override the default "/usr/bin/python". This last one should be a symbolic link to the previous Python binary, "/usr/bin/python2.6".

Also see this thread ["How do I install python 2.7 in lucid?"](http://ubuntuforums.org/showthread.php?t=1529315), for a similar issue regarding installing/removing Python from source.

---

### Post by trippn740 on 2010-11-17
I worked it out with changing the link to python;

```
sudo ln -f /usr/bin/python2.6 /usr/local/bin/python
```

I'm back to 2.6 for the default, and didn't have to delete 2.7

---

