---
title: "Assistance with Emerald please"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by GumboLinux on 2008-10-31
How do I install/activate the theme I want when it is selected in the emerald theme window??? Thanks for help

---

### Post by m_duck on 2008-10-31
By the sounds of it, if you have download and install emerald and chosen a theme, it is just the metacity is still managing the windows instead of emerald. Open up a terminal and type:
```
sudo apt-get install fusion-icon
```
or install fusion-icon via synaptic.

This is then accessible from Applications -> System Tools -> Compiz Fusion Icon. If you click this a blue box icon should appear in your system tray. Right click this -> Select Window Decorator then click Emerald. This should make your emerald themes show on all windows.

In order to make this happen everytime you log in, you need to goto System -> Preferences -> Sessions then click Add. Fill out the form as below:
  Name:   Fusion Icon
  Command:  fusion-icon
  Comment: Fusion icon for emerald

And click ok.  Now thats done you should (hopefully) have emerald managing your window decorations everytime you log in.

---

### Post by xpod on 2008-10-31
Or ALT-F2 then
```
emerald --replace
```

---

### Post by Paqman on 2008-10-31
Actually, i've had trouble with fusion-icon on Intrepid. It crashes Compiz at login. Works fine if you remove the icon from the panel.

---

### Post by m_duck on 2008-10-31
I **knew** there was a simpler way of doing it...

EDIT: Ah, I'm still on hardy so there may be issues then.

---

