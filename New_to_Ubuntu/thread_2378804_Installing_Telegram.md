---
title: "Installing Telegram"
date: 2017-11-27
forum: New to Ubuntu
---

### Post by forneus2 on 2017-11-27
Downloaded setup.tar.xz. When extracted it just creates a Telegram folder with two files: Telegram and Updater. Is that all? Should I extract it to a specific directory?

I'm using Lubuntu 16.04.

---

### Post by deadflowr on 2017-11-27
Save yourself some pain and install the telegram snap package
```
sudo snap install telegram-sergiusens
```

---

### Post by howefield on 2017-11-27
Double clicking the Telegram icon in the extracted folder is all you need to do to load the application, once open it can be pinned to the launcher if required.

---

### Post by forneus2 on 2017-11-27
> **deadflowr said:**
> Save yourself some pain and install the telegram snap package
```
sudo snap install telegram-sergiusens
```

I read about the downsides of this snap app - there’s no tray icon, it can’t open link via Web browsers and fonts are not  displayed properly.

> **howefield said:**
> Double clicking the Telegram icon in the extracted folder is all you need to do to load the application, once open it can be pinned to the launcher if required.

Where should I put this folder? usr/share? usr/bin?

---

### Post by howefield on 2017-11-27
> **forneus2 said:**
> Where should I put this folder? usr/share? usr/bin?

Extract the tar.xz file to your home folder or any of the folders in it, eg ~/Downloads

---

### Post by deadflowr on 2017-11-27
> I read about the downsides of this snap app - there&#8217;s no tray icon, it can&#8217;t open link via Web browsers and fonts are not displayed properly.

Two of those issues should be fixed; opening links and tray icons.
(Not sure about font rendering.)

No matter, as you can install both versions; the snap package and the telegram binary as they will not conflict with each other.
A (major/selling) point of snaps is they are confined and automatically updated in the background. Bonus that you can also rollback to an older version if the update broke something.

---

### Post by forneus2 on 2017-11-27
> **deadflowr said:**
> Two of those issues should be fixed; opening links and tray icons.
(Not sure about font rendering.)

No matter, as you can install both versions; the snap package and the telegram binary as they will not conflict with each other.
A (major/selling) point of snaps is they are confined and automatically updated in the background. Bonus that you can also rollback to an older version if the update broke something.

Done. Thanks a lot!

---

### Post by DuckHook on 2017-11-27
Please mark thread "solved" using thread tools at the top of this thread, so that others can benefit from your solution.

---

