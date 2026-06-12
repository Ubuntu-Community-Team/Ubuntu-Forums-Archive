---
title: "Firefox : Install scrollbar fix - how to get rid of it?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by ee19921 on 2008-11-04
I upgraded to 8.10 yesterday. While looking through the System Settings -> Appearaces -> GTK Styles and fonts, for some reason I thought "Install scrollbar fix" is going to fix my firefox settings (when I had no problem whatsoever). Now, the drop down boxes look weird and definitely feel few other things changed which I can't pin point. Scrollbar looks the same(I am using iFox theme). Even tried the suggestion in [this thread]("http://ubuntuforums.org/showthread.php?t=464878&highlight=GTK+install+scrollbar+fix")

I don't know if looks because of yesterday's upgrade or the install scrollbar thing caused it.

is there a way to revert the fix I did?

<edit1>
Avidemux also has got that "windows" looking buttons and drop downs. 
</edit1>

---

### Post by ee19921 on 2008-11-05
soft bump!

---

### Post by ee19921 on 2008-11-05
It seems the "scrollbar fix" modifies the GTK theme. All I had to do is to install one theme switcher and apply the QT4 theme. phew!

```
sudo apt-get install gtk-theme-switch
gtk-theme-switch2

```

[https://answers.launchpad.net/ubuntu/+question/21816](https://answers.launchpad.net/ubuntu/+question/21816)

---

