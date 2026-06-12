---
title: "[SOLVED] Temporarily disabling compiz"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Flynsarmy on 2008-06-06
Is there a way to temporarily turn off compiz whilst keeping its
settings? If i change the visual effects to none then back to normal all the compiz settings are set to whatever the default ubuntu 'normal' settings are and all the ones i've modified myself are lost.

Is there a tool that can import/export compiz settings?

---

### Post by iaculallad on 2008-06-06
Try the [compiz switch]("http://forlong.blogage.de/article/pages/Compiz-Switch").

---

### Post by wdaniels on 2008-06-06
```
sudo apt-get install compizconfig-settings-manager fusion-icon
```

From CCSM you can go to Preferences and import/export settings there. fusion-icon will allow you to quickly change window manager, or use the commands:

```
compiz --replace &
metacity --replace &
```

---

### Post by Trail on 2008-06-06
You could try hitting Alt-F2 and typing "metacity --replace"

which forces the Ubuntu default window manager (metacity) to replace compiz for this session. To reset this, either log-in again, or do the same and type "compiz --replace"

---

