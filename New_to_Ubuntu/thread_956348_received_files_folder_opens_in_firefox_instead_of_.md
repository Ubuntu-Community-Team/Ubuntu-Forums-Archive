---
title: "received files folder opens in firefox instead of nautilus"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by AhJah on 2008-10-23
Hello,

when I receive files through skype, if I try to open the folder where the file has been downloaded it is opened in firefox instead of nautilus.

the URL in firefox says file:///blahblah.

this is weird, it happens just since a couple o f days and I don't recall to have done any change. I have only installed the latest java plugin, but I don't think it is related.

Any hint about what to check?
Thanks and regards,
Leo

---

### Post by Hexagoon on 2008-10-23
Try

```
sudo dpkg-reconfigure nautilus
```

in the terminal, that will reconfigure the file manager app. and possibly reset the standard app for file://.

---

### Post by AhJah on 2008-10-23
> **Hexagoon said:**
> Try

```
sudo dpkg-reconfigure nautilus
```

in the terminal, that will reconfigure the file manager app. and possibly reset the standard app for file://.

Unfortunately this didn't work.

where can I find file associations at a system-wide level? there is no such association in firefox, and "preferred applications" tool  in Gnome is limited to internet browser, email client and terminal.

I also looked at nautilus-desktop files, but didn't find any pointer to firefox instead of nautilus itself.

Thanks
Leo

---

