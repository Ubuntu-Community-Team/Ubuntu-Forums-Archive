---
title: "[SOLVED] Applications Menue is not available"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Tart on 2008-07-15
Hello,

Something happened and Applications menu is no longer available to me. Nothing happens when I click on it. 'Places' and 'System' works fine. 
When I go to System-> Preferences and select "Main Menu" nothing happens.

How to fix it??

Thanks

---

### Post by iaculallad on 2008-07-15
> **Tart said:**
> Hello,

Something happened and Applications menu is no longer available to me. Nothing happens when I click on it. 'Places' and 'System' works fine. 
When I go to System-> Preferences and select "Main Menu" nothing happens.

How to fix it??

Thanks

Press Alt+F2, enter "gnome-terminal" (w/o double quote) and press Enter.

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```

---

### Post by Tart on 2008-07-15
Thank you for reply, but unfortunately it didn't help :-(

---

### Post by dhughes on 2008-07-15
> **iaculallad said:**
> Press Alt+F2, enter "gnome-terminal" (w/o double quote) and press Enter.

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```

 Why not just? ```
 killall gnome-panel 
```

 It should restart, shouldn't it? :/

---

### Post by Tart on 2008-07-15
> **dhughes said:**
> Why not just? ```
 killall gnome-panel 
```

 It should restart, shouldn't it? :/

It does restart panels but doesn't fix "Applications" :-(

---

### Post by iaculallad on 2008-07-15
> **dhughes said:**
> Why not just? ```
 killall gnome-panel 
```

 It should restart, shouldn't it? :/

Doing that would only refresh the panel, and still, using the same configuration that had/either caused it to fail loading the "Applications" menu.

So we used the commands:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```

to restore it to it's default settings. But, as Tart had tried, it did not.

---

### Post by iaculallad on 2008-07-15
Try: Alt+F2 again, "gnome-terminal"

```
sudo debconf gnome-panel
```

Log-Off on your account then log back in.

---

### Post by mc4man on 2008-07-15
if above doesn't work then simply go places -> home folder ->.config-> menus
and delete applications.menu
note .config is a hidden file, enable in view tab in home

---

### Post by Tart on 2008-07-15
No it didn't help :-(. Before log-off it switched to root and Applications did work. But then I log-in it is back to the same problem. When I log in to guest account, Applications work, it is just in my acccount.

---

### Post by iaculallad on 2008-07-15
> **Tart said:**
> No it didn't help :-(. Before log-off it switched to root and Applications did work. But then I log-in it is back to the same problem. When I log in to guest account, Applications work, it is just in my acccount.

Had you tried copying the  ~/.gconf/apps/panel directory of the Guest Account (w/c worked) and transferring it to yours (Overwrite)?

```
gksudo nautilus
```

---

### Post by Tart on 2008-07-15
I found another thread 

[http://ubuntuforums.org/showthread.php?t=277588](http://ubuntuforums.org/showthread.php?t=277588)

and I followed it's advice. Everything works now. 

Thank you for your time and help

---

### Post by iaculallad on 2008-07-16
> **Tart said:**
> I found another thread 

[http://ubuntuforums.org/showthread.php?t=277588](http://ubuntuforums.org/showthread.php?t=277588)

and I followed it's advice. Everything works now. 

Thank you for your time and help

Ok, I'm glad you found it yourself the correct solution for your problem. Good luck w/ Ubuntu.

---

