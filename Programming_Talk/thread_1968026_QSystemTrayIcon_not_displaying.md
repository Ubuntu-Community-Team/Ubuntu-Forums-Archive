---
title: "QSystemTrayIcon not displaying"
date: 2012-04-28
forum: Programming Talk
---

### Post by Woody1987 on 2012-04-28
My qt app has a QSystemTrayIcon but it is not showing in the appindicator area. It displays in kde but not in unity. I have sni-qt ([https://launchpad.net/sni-qt]("https://launchpad.net/sni-qt")) installed but it doesnt seem to be working. I have also whitelisted everything using: ```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```


My code
```

QMenu *menu = new QMenu(this);
menu->addAction("Test");

QSystemTrayIcon *icon = new QSystemTrayIcon(this);
icon->setContextMenu(menu);
icon->setIcon(QIcon(":/Images/Resources/icon.png"));
icon->setVisible(true);
icon->show();

```

---

### Post by Woody1987 on 2012-05-05
bump

---

### Post by RockBull on 2012-06-12
@Woody1987

Did you manage to solve your issue?

I've the same issue with my App and would like to know what you did to solve it.

---

### Post by RockBull on 2012-06-20
To help others with more clues to look for:

I've managed to fix my issues by changing the resolution of the image to 744x744.

This is the resolution being used in the example app provided by Qt.

I also changed the image format from png to svg. I did a couple of tests and found some resolutions not working.

Regards,

---

