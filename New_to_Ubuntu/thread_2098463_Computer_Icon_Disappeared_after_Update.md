---
title: "Computer Icon Disappeared after Update"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by riderplus on 2012-12-26
I installed the updates on my Ubuntu 12.10 with Gnome 3 DE and now the Computer icon has disappeared. If I open Nautilus I can see a Computer tab under Devices, along with my other mounted devices. How to bring back the Computer icon on Desktop? Is there a way to do this? I couldn't find it in dconf-editor/gconf-editor/gnome-tweak-tool.

---

### Post by daslinkard on 2012-12-30
> **riderplus said:**
> I installed the updates on my Ubuntu 12.10 with Gnome 3 DE and now the Computer icon has disappeared. If I open Nautilus I can see a Computer tab under Devices, along with my other mounted devices. How to bring back the Computer icon on Desktop? Is there a way to do this? I couldn't find it in dconf-editor/gconf-editor/gnome-tweak-tool.
I'm wondering if resetting Nautilus would solve the issue for you?  Here's a quick [link]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/") that might work.

---

### Post by riderplus on 2013-01-08
Actually that won't solve it. The issue is that now "Computer" stands for "File system" in Nautilus >>3.6. Therefore you have to create a Launcher for "Computer" and in the command tab write "nautilus /". That would bring the computer icon back...of course, without the original icon.

---

