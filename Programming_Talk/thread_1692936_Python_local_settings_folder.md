---
title: "Python local settings folder"
date: 2011-02-22
forum: Programming Talk
---

### Post by kumoshk on 2011-02-22
In Python, how do I return the path of the user's local settings?

I know how to get the user's home folder. I could use that and concatenate the settings folder onto it, but I want to do this in a cross-platform fashion&#8212;so that won't really work unless I do some OS-checking (I'd rather not).

In Vala, since it comes with GLib, you can do it like this:
GLib.Environment.get_user_data_dir()

I suppose you could get Gtk in Python and try the same thing, but I'm hoping for something that doesn't require another installation.

---

### Post by DaithiF on 2011-02-22
```
os.path.join(foo, bar)
```
to concatenate two path elements in a cross-OS compatible way.

---

### Post by kumoshk on 2011-02-22
Thanks &#8230; but that's not what I was meaning to ask for, although that is useful in similar contexts. I have the home folder, but the path to the application settings, local settings and all is different between Windows and Linux&#8212;so, I don't really have anything useful to concatenate with the home folder in a cross-platform manner.

All I'm looking for is the variable for the local settings (or documents and settings, application data or some other such).

---

### Post by kumoshk on 2011-02-22
As a side-note, if I don't find an answer, I actually might just use GLib in Python for the variable. Apparently, it's an easy install nowadays (didn't used to be—I mean, I knew how to do it, but I didn't expect everyone who would want to use my program to know)—so, I might use it for my GUI instead of WxPython after all.

---

### Post by Flimm on 2011-02-22
On Linux, you can use the xdg module to find the FreeDesktop data and configuration directories.

[php]
from xdg.BaseDirectory import *
print xdg_cache_home
print xdg_config_dirs
print xdg_config_home
print xdg_data_dirs
print xdg_data_home
[/php]

---

### Post by nvteighen on 2011-02-22
In GNU/Linux there's no standard way to save user-local data... There's the XDG specification, but not too much. So, it boils down to create your own way, usually you should use a folder defined by yourself... usually, you name it '.appname'. Other alternative is to use the .config directory, though that's more a GNOME thing.

---

### Post by kumoshk on 2011-03-01
Thanks everyone.

So, how do I find this information on Windows and Mac respectively? I mean, if I want to save my data in the Application Data folder of Documents and Settings.

Or, what's the equivalent of this for Windows and Macintosh:
```
from xdg.BaseDirectory import *
print xdg_data_home
```

---

### Post by LemursDontExist on 2011-03-01
```
import os
print os.getenv("APPDATA")
```
should do what you're looking for in Windows - I can't help you for Mac though!

---

### Post by kumoshk on 2011-03-01
Awesome! I'm trying it through Wine, but it seems to work. Thanks! Now I just need a method for Macs. It looks like ~/.local/share/myAppDataFolder should work on a Mac. Maybe I could just put that in manually after using os.path.expanduser("~") to get the home directory (that could work for Linux, too, I guess, even though we already have another method). I.e.
```
#Linux and Mac code:
os.path.expanduser("~") + os.sep + ".local" + os.sep + "share" + os.sep + myAppDataFolder

#Windows code:
os.path.join(os.getenv("APPDATA"), myAppDataFolder)
```

Just so I can have it here for reference, I'm going to list some OS determiners in Python that I've found:

os.name (could be any of these, if not more: posix, nt, os2, mac, ce, ricos&#8212;note that posix for Linux; I'm not sure whether os2 or mac is for modern Macs, though)

and

sys.platform (could be any of these, or perhaps more: linux2, win32, darwin)

---

### Post by LemursDontExist on 2011-03-02
You might want to look at ```
platform.system()
```, for windows it outputs "Windows" and for any linux system is should output "Linux" - probably something comparably predictable for a Mac?  I've found it more convenient than sys.platform.

---

### Post by ssam on 2011-03-02
[ http://docs.python.org/library/os.path.html#os.path.expanduser ]("http://docs.python.org/library/os.path.html#os.path.expanduser")
lets you get the home folder reliably.

---

