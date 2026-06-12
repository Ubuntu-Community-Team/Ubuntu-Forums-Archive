---
title: "Icons are not matching between desktop and launcher"
date: 2017-03-05
forum: New to Ubuntu
---

### Post by robertzito on 2017-03-05
I installed Oracle SQL Developer on my Ubuntu 16.04 and created a desktop shortcut giving it its own icon. When I start the application the icon in the launcher match, when it fully loads I get the ugly "?" icon in the launcher bar. How can I get the icon to show launcher, even when I lock to launcher it always reverts back to the "?" icon.

---

### Post by kostkon on 2017-03-05
You could try the following:
start the application in question, open a terminal and type the following command:
```
xprop | grep WM_CLASS
```
then, when a crosshairs cursor is displayed click on the application's window and xprop will output the WM_CLASS of that window; the output could be just one or a list of WM_CLASS names. The first one or two on the list are usually generic names so you'll have to pick the second or third one and so on.

Open the desktop file you've created and add the following line:
```
StartupWMClass=WM_CLASS_I_GOT_FROM_XPROP
```

Also, you'll have to specify your own icon, if you haven't done it already, i.e.:
```
Icon=path/to/icon
```


Hope that helps.

---

