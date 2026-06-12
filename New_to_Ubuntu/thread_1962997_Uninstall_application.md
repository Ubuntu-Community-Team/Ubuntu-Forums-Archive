---
title: "Uninstall application"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by GalaxyLinux on 2012-04-21
How do I uninstall an application that's not in a repository?

---

### Post by Curtis6767 on 2012-04-21
Several different ways:

If you installed Synaptic, then the top of the page has the instructions you need. If no Synaptic then scroll down to the bottom of the page.

[http://docs.oseems.com/operatingsystem/ubuntu/completely-remove-program-and-settings](http://docs.oseems.com/operatingsystem/ubuntu/completely-remove-program-and-settings)

To get to the terminal use CTRL+Alt+t

You can also use the software center to search for your app. If you find it there, you can uninstall it from there:

[https://help.ubuntu.com/11.10/ubuntu-help/addremove-remove.html](https://help.ubuntu.com/11.10/ubuntu-help/addremove-remove.html)

---

### Post by critin on 2012-04-21
> **GalaxyLinux said:**
> How do I uninstall an application that's not in a repository?

How did you install it?  Was it a .deb file installed by Software Center?  If so, it can be uninstalled from there.
Everything should be installed through the SC if possible.  For compatibility.

You should be able to remove with commands in the terminal, but you'll need to learn the proper command.

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by na5h on 2012-04-24
For complete removal of a package, open up a terminal (CTRL+ALT+T) and type:
```
sudo apt-get purge packagename
```

---

### Post by Cheesemill on 2012-04-24
> **GalaxyLinux said:**
> How do I uninstall an application that's not in a repository?
That depends on how you installed it in the first place.
More details please.

---

