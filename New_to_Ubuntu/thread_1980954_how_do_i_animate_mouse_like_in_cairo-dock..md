---
title: "how do i animate mouse like in cairo-dock."
date: 2012-05-16
forum: New to Ubuntu
---

### Post by bariamtak on 2012-05-16
I am using ubuntu 12.04 and i installed cairo-dock and i really like it, especially the animations.
In other previous ubuntu releases it seems that we can animate mouse from compiz setting but i cannot find it in my system. 
I saw in youtube where they use compiz but their compiz version seems to be diffrent. How do i achieve it ?
I could animate the mouse only in the dock bar. I want it to be animated all the time. Any suggestion will be greatly appreciated.
Thank you.

---

### Post by jtarin on 2012-05-16
[http://glx-dock.org/index.php](http://glx-dock.org/index.php)

---

### Post by bariamtak on 2012-05-16
I follwed jtarin's link and it does have any information regarding animating mouse. Am i missing something ?

---

### Post by stinkeye on 2012-05-16
Think you need to install
```
compiz-plugins-extra
```
for the **Show mouse** plugin.

---

### Post by bariamtak on 2012-05-21
> **stinkeye said:**
> Think you need to install
```
compiz-plugins-extra
```for the **Show mouse** plugin.
Thank you Stinkeye. I installed the plugins in two of my sytems but i dont know why its not working even after ticking the show mouse button. i am using ubuntu 12.04.
Do i need to change any other settings ?

---

### Post by stinkeye on 2012-05-21
I just tested by setting unity back to default with
```
unity --reset
```

...enabled the show mouse plugin, pressed Super+k and it worked.
Perhaps try changing the shortcut key to initiate.
Also check compiz is actually running and your not in the **Ubuntu 2d** session.

Check session...
```
echo $DESKTOP_SESSION
```

---

### Post by bariamtak on 2012-05-21
> **stinkeye said:**
> I just tested by setting unity back to default with
```
unity --reset
```...enabled the show mouse plugin, pressed Super+k and it worked.
Perhaps try changing the shortcut key to initiate.
Also check compiz is actually running and your not in the **Ubuntu 2d** session.

Check session...
```
echo $DESKTOP_SESSION
```

Thank you very much. I was in ubuntu 2D. Now its working. Thanks to you.

---

