---
title: "Running shell script with custom launcher"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by amarumayo on 2013-06-15
Hi all,
Noob here :)

I have a shell script named my_script.sh which works fine when I run it from the terminal.
I have also created /usr/share/applications/my_app.desktop which looks like this:

[Desktop Entry]
Name=my app
Exec=bash /path/to/my_script.sh
Terminal=true
Type=Application
Categories=Utility;

My new app is showing up in the menu but when I click it, nothing happens.  Where am I going wrong??

PS please ignore the attached image file

Thanks in advance.

---

### Post by Isamu715 on 2013-06-15
If it's not a problem posting the script would help. You don't need to include bash in the Exec line, /path/to/my_script.sh will do. I suppose when you're running it from a terminal you run it from /path/to/, so adding the following to your launcher may help:
```
Path=/path/to
```

---

### Post by HiImTye on 2013-06-15
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
if you need to see it, then set the launcher command to
```
gnome-terminal -x /path/to/script
```
otherwise it will run in the background, silently

note: unless you set gnome-terminal to stay open when finished, it will close when the script finishes

---

