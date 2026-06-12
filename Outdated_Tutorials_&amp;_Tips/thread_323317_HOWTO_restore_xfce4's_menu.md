---
title: "HOWTO restore xfce4's menu"
date: 2006-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by lmo on 2006-12-21
Broke xfce4 Menu
```
Settings -> Sessions_and_Startup_Settings
Unchecked Display_chooser_on_login
```
After doing that, the Xfce Menu did nothing when clicked on, and clicking the right mouse did not bring up the menu either.

Almost gave up.

HOWTO fix
```
cp /etc/xdg/xfce4/desktop/menu.xml /home/[myusername]/.config/xfce4/desktop/
```

Menu came back

I am not sure why the menu broke or what else I might have done to cause it? I was just about to uninstall/reinstall all of xfce4 when it somehow occurred to me to copy the stock menu.xml from /etc/xdg/xfce4/desktop to my home directory. Happily, that worked for me.

... Just found a new? way to break the xfce4 menu. If I use xfce4 menu editor and either close or save the menu, the result is a completely blank menu. This is with xfce4-menueditor 4.3.90.1.

---

### Post by Cato2 on 2007-10-20
I had this as well, thanks for posting this HOWTO.

I also had a problem where the XFCE panel (top and bottom desktop bars for the new users) crashed, so I couldn't even get to the menu.  I fixed this by running xfce4-panel & from a Terminal window that was already open.

Apparently these problems happen when XFCE crashes - so backing up the contents of ~/.config is well worth it, using a command such as:

[FONT="Courier New"]tar czvf gui-config-backup.tar.gz .config/[/FONT]

Run this command from a Terminal window when you've made some changes to your XFCE setup - then to restore over a broken config you just need to do:

[FONT="Courier New"]cd; tar xzvf gui-config-backup.tar.gz[/FONT]

---

