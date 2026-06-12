---
title: "should i reinstall dconf-editor?"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by QXLIANG2013 on 2013-06-02
hi,all
i use Ubuntu 12.04LTS,and want manage some gnome nautilus configurations,then i type
 ```
***dconf-editor***
```
to call the GUI tool,but it seems some trouble took place like below:
[ATTACH=CONFIG]243440[/ATTACH]
may i get some suggestion to fix it

---

### Post by ShadowVegan on 2013-06-02
I'm not sure what is causing that, but if you want to reinstall it, use these commands
```
sudo apt-get remove --purge dconf-tools
```
```
sudo apt-get install dconf-tools
```

---

### Post by QXLIANG2013 on 2013-06-02
thanks very much for your prompt ,i have done like that,but it seems the problem still exists:[ATTACH=CONFIG]243443[/ATTACH]

---

### Post by mc4man on 2013-06-02
They are just some warnings of no particular importance

---

### Post by QXLIANG2013 on 2013-06-02
that's right,when i used ***dconf-editor***  i made a mistake not click on the small "arrow" and thought it didn't work&#65292;but it works well despite those warnings.thanks very much!

---

