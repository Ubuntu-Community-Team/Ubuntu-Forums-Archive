---
title: "Display KDE/Qt Version in Superkaramba Plasmoid"
date: 2015-09-29
forum: Programming Talk
---

### Post by ernieg922 on 2015-09-29
So, for a long time I've used a Superkaramba Plasmoid on my Kubuntu desktop.  ([link here]("https://kde-apps.org/content/show.php?content=86664&forumpage=6"))  It worked flawlessly over the years (I've made several modifications to the original theme/code, specifically for temps, storage and network).  With the arrival of KDE5/Plasma5, I no longer have the KDE and Qt version displayed (it's blank, as seen in screenshot).


The applicable line in the theme is at Line 102:
```

text x=185 y=46 fontsize=11 font="Blue Highway" align=right sensor=program program="echo  `kde4-config --version | grep 'KDE' | sed -e 's/.*E //' | sed -e 's/)//'` /  `kde4-config --version | grep 'Qt' | sed -e 's/.*: //'`" 
```

I have replaced that line with the following code:
```

text x=185 y=46 fontsize=11 font="Blue Highway" align=right sensor=program program="echo `cat /usr/share/xsessions/plasma.desktop | grep "Version" | sed -e 's/.*=//'` /  `/usr/lib/i386-linux-gnu/qt5/bin/qtdiag | grep "Qt " | sed -e 's/.*t //' | sed -e 's/.(i3.*$//'`" 
```

Both of those commands work fine in a bash terminal:
```

[FONT=monospace][COLOR=#000000]ernieg92:~/Temp$ cat /usr/share/xsessions/plasma.desktop | grep "Version" | sed -e 's/.*=//' [/COLOR]
5.2.2 
ernieg92:~/Temp$ /usr/lib/i386-linux-gnu/qt5/bin/qtdiag | grep "Qt " | sed -e 's/.*t //' | sed -e 's/.(i3.*$//' 
5.4.1 
ernieg92:~/Temp$ 
[/FONT]
```[FONT=monospace]

Yet, within the karamba theme it displays nothing.  I've even tried using just one command at a time (removing the "echo" and just running the "cat" or "qtdiag" commands).  Still nothing.

I realize this is not true programming, but I'm just starting out with some simple scripting.  I can't seem to find what I'm doing wrong.

Any insight would be greatly appreciated!
[/FONT]

---

