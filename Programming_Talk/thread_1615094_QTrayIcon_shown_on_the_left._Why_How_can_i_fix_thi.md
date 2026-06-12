---
title: "QTrayIcon shown on the left. Why? How can i fix this?"
date: 2010-11-06
forum: Programming Talk
---

### Post by leon.vitanos on 2010-11-06
Hi i am trying to make a System Tray Icon to be shown everytime i minimize my application......
this is the void function while it is minimized:

```
if (isMinimized()) {
trayIcon->show();
enum MessageIcon { NoIcon, Information, Warning, Critical };
QSystemTrayIcon::MessageIcon icon = QSystemTrayIcon::MessageIcon(Information);
trayIcon->showMessage("titlos", "mplampla", icon, 10000);
emit minimized();}
```

I don't know why but the message is shown on the left and not below the application's trayicon. Why is this happening and how can I fix it?

---

