---
title: "How to enable global menu bar?"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by buhala on 2013-05-02
Okay, I am having a really hard time searching for this problem, and I have no idea how to fix it. I did something in the configuration, and now I cannot run windows in full size
Picture:
[IMG]http://img198.imageshack.us/img198/8427/selection002p.png[/IMG]
I want the 2 bars at the top to be merged together. Help, please!

---

### Post by zero2xiii on 2013-05-02
Hay,

In what configuration?

If you have used the terminal to edit anything (or to open a file to edit) please give the output of (ran in a terminal):
```
history
```

If you manually searched for and edited files please list those files here as well. We can then tell you which's content we will need.

Thanks

---

### Post by DenHeldert on 2013-05-02
Try

```
unity --reset
```

it resets the Unity-interface.

---

### Post by slickymaster on 2013-05-02
The global menu bar is a panel applet in the classic gnome desktop. To disable it in the classic desktop, right-click on it and "Remove from Panel". If you want to re-enable it, right-click on the panel > Add to panel > Indicator Applet Appmenu.

---

### Post by Frogs Hair on 2013-05-02
Global menu integration for Firefox in Unity is an add-on in Tools > Add-ons > Extensions. You may have to right click in the tab area and enable the old menu bar to get to it , but it depends what you did in the configuration as to weather that will work.

---

