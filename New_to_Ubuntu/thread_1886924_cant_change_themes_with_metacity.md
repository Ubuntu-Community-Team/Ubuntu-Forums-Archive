---
title: "cant change themes with metacity"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by boregard on 2011-11-25
Hello, when I was using Natty I could change to different themes and icons with meta-city. But with 11.10  I cant find this option. I know I am prolly overlooking something simple. Any help or advice would be appreciated, Thanks.

---

### Post by lolpenguin on 2011-11-25
Oops. Ubuntu 11.10 uses GNOME 3 so the dialog you are looking for doesn't exist anymore. To change themes, you must use a harder method.
1. Install the GNOME Tweak Tool
```
sudo apt-get install gnome-tweak-tool
```
2. Download theme, extract to /usr/share/themes/ (~/.themes may work in the future, not sure about now)
3. Launch GNOME Tweak Tool (called Advanced Settings)
4. Theme tab. You can customize the cursor, icon, gtk (GTK+3.x), window themes (metacity).

---

### Post by boregard on 2011-11-26
ahh, that explains why i was having trouble finding it  lol. much thanks for your help lolpenguin, have a good one!

---

