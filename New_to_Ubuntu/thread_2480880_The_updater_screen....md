---
title: "The updater screen..."
date: 2022-11-13
forum: New to Ubuntu
---

### Post by Innernet on 2022-11-13
Hi.
When the updating is ready, the screen shown I get is attached.

With the choice to install at bottom right.  Where in that screen shows the shown option to remove the Thundersomething that I do not use, never used and do not want to use  ?  If I ignore by closing the window, it reappears daily.

---

### Post by &amp;KyT$0P# on 2022-11-13
There is no way to remove packages via that screen.  To remove Thunderbird, open a Terminal and run
```
sudo apt-get purge 'thunderbird*'
```

---

### Post by Innernet on 2022-11-13
Thanks.  So that screen is wrong showing 'install or remove'

---

### Post by &amp;KyT$0P# on 2022-11-13
It says that because it can offer to remove "unused kernel updates".

* To clarify: if I recall correctly, the exact text it lists such entries under is "Unused kernel updates to be removed".  And there is no way to add additional custom-selected packages to that list.

---

### Post by ActionParsnip on 2022-11-14
Please close the updater GUI app and run
```

sudo apt update
sudo apt -y full-upgrade

```
What is the full output please?

---

