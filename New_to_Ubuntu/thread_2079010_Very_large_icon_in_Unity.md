---
title: "Very large icon in Unity"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Frozen Forest on 2012-11-01
I have added an program to unity using .desktop file. but for some reason does the icon become very big.

desktop file
```

[Desktop Entry]
Type=Application
Name=Eclipse
Comment=Eclipse Integrated Development Environment
Icon=/opt/eclipse/icon.xpm
Exec=/opt/eclipse/eclipse
Terminal=false
Categories=Development;IDE;Java;

```

---

### Post by pdoes on 2012-11-09
It seems to be a bug in 12.10

[https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/1061037](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/1061037)

---

### Post by Mr_JMM on 2012-11-09
This happens using the Aptana icon too. To correct, simply copy the image, scale it to 48x48 and link to that one instead.

[edit] As Kostkon below mentions, and I'd forgotten to mention here, change it to a PNG file.

---

### Post by kostkon on 2012-11-09
> **Mr_JMM said:**
> This happens using the Aptana icon too. To correct, simply copy the image, scale it to 48x48 and link to that one instead.
Also convert it to png, just to be on the safe side. Or just google for one.

---

### Post by Mr_JMM on 2012-11-09
> **kostkon said:**
> Also convert it to png, just to be on the safe side. Or just google for one.

Sorry, yes, what Kostkon said, I forgot to mention that. I'll edit my post if I can.

---

### Post by Popenuj on 2012-11-09
Haha! Are you sure they didn't do that on purpose? It's pretty apropos that a program called "Eclipse" has an icon so large that it gets in the way of surrounding icons and its own name.

---

### Post by praimmugen on 2013-01-19
Check out this comment to the bug report

[https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/1061037/comments/13](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/1061037/comments/13)

You don't have to convert/resize your icon, you can just copy the original /opt/eclipse/icon.xpm into ~/.local/share/icons and edit the Icon entry in .desktop file to

Icon=icon.xpm

(well, maybe changing the file name would be a good thing)

---

