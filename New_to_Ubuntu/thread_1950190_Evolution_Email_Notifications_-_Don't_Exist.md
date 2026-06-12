---
title: "Evolution Email Notifications - Don't Exist"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2012-03-31
Hopefully the title didn't give away to much of this exciting topic :)

Basically in the top right hand corner, were the time is we have that little email icon (Ubuntu 11.10 x64). That email icon seems to be configured with Thunderbird on my system, and since I don't use Thunderbird (I use Evolution) how do I change it so it is set up to use Evolution?

Also is it normal for Evolution not to notify of new emails, it just sits in the Unity bar and doesn't tell me when I receive new emails. I have to check it by clicking on the icon :(

Cheers

---

### Post by Zill on 2012-03-31
terrykiwi83:  I use Lucid (10.04 LTS) which uses Evolution by default so cannot confirm this will work with 11.10 but I would suggest installing evolution-indicator:
> indicator-applet is an applet to display information from
various applications consistently in the GNOME panel.

This package provides a plugin for Evolution that uses libindicate and
libnotify to provide additional information about Evolution's state.```
sudo apt-get install evolution-indicator
```

---

### Post by terrykiwi83 on 2012-03-31
Cheers Zill, will give it a try and report back.

Edit: Installed the evolution-indicator and uninstalled thunderbird. Worked a treat when logging off and in again.

Thanks...Solved

---

