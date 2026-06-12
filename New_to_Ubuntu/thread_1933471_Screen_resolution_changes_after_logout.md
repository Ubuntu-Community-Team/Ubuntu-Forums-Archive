---
title: "Screen resolution changes after logout"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by Sovereign Entity on 2012-02-29
After I logout and back in to Ubuntu 10.04 my screen resolution changes from the setting of 1600x1200 to 1024x768.I have saved /etc/X11/xorg.conf but the problem still persist. Here is my /etc/X11/xorg.conf

[http://pastebin.com/MuyNe4f4]("http://pastebin.com/MuyNe4f4")

---

### Post by Tyggna on 2012-02-29
Under your monitor section, try adding a line like this:

Option          "PreferredMode" "1600x1200_60.00"

---

### Post by Sovereign Entity on 2012-02-29
> **Tyggna said:**
> Under your monitor section, try adding a line like this:

Option          "PreferredMode" "1600x1200_60.00"

Still same problem. I added the line to /etc/X11/xorg.conf and it sticks. But it changes in the Nvidia X Server Settings manager

---

