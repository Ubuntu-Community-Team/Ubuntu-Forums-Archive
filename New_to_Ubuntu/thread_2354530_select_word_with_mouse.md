---
title: "select word with mouse"
date: 2017-03-03
forum: New to Ubuntu
---

### Post by chri1tian on 2017-03-03
I like to double click a word to select it, or double-click-drag to select several words. The problem seems to be that the mouse has to be held perfectly still during the double click, which is near impossible. So I often have to double click a word several times until the selection works.

Is there any way to configure Ubuntu to be less sensitive about the double click?

It works much better on a Mac where the mouse position during the second click just needs to be on the same word to be detected as a double-click causing a word selection.

Thanks,

Same problem with triple-click to select a full-line.

---

### Post by ajgreeny on 2017-03-03
I am using Xubuntu and there is a settings utility for the mouse that allows me to set the double click time to my own preference; look for something similar in Ubuntu and you may have your answer

---

### Post by chri1tian on 2017-03-03
> **ajgreeny said:**
> I am using Xubuntu and there is a settings utility for the mouse that allows me to set the double click time to my own preference; look for something similar in Ubuntu and you may have your answer

Double Click Time is about how much time can pass between first and second click. This has nothing to do with the sensitivity to mouse movements.

---

### Post by vasa1 on 2017-03-03
Try playing with```
gtk-double-click-distance=0
``` in *~/.config/gtk-3.0/settings.ini*. I think increasing the value from 0 to whatever is comfortable to you might help.

For example,
```
[Settings] 
gtk-double-click-time=1000
gtk-long-press-time=5000
gtk-double-click-distance=0

```
After you modify and save the file, the settings will apply to subsequently opened gtk3 applications.

If you're using a gtk2 app, you can modify *~/.gtkrc-2.0.mine* the same way.

Let us know if that works for you!

---

### Post by chri1tian on 2017-03-14
It did not work. I set the value for gtk-double-click-distance in those two files to as high as 50 without any effect. Even rebooted the machine to make sure, and double checked that the current app was using GTK3.
Any other suggestion? (sorry about the late reply)

---

