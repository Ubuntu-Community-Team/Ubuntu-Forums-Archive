---
title: "Keyboard shortcuts not working."
date: 2016-09-19
forum: New to Ubuntu
---

### Post by singleuser on 2016-09-19
Hi , I am new to lubuntu. I used to have ubuntu . But difficulty is I am not getting any shortcut working here as like ubuntu. 

I tried this [https://help.ubuntu.com/community/Lubuntu/Keyboard](https://help.ubuntu.com/community/Lubuntu/Keyboard) , but not working .

none find any setting related to this. How can we do this.?

---

### Post by denter2 on 2016-09-20
since lubuntu uses openbox as a window manager, and openbox manages keybinds, i'd try if ```
obkey
```is installed.
or, you can edit ```
~/.config/openbox/lxde-rc.xml
``` directly.

---

### Post by vasa1 on 2016-09-20
> **denter2 said:**
> ... you can edit ```
~/.config/openbox/lxde-rc.xml
``` directly.
For Lubuntu, it's *~/.config/openbox/lubuntu-rc.xml*.

---

### Post by singleuser on 2016-09-20
yes , I did both by obkey and manually with 
~/.config/openbox/lxde-rc.xml

But when use combination of shortcut for purpose it doesn't work properly.

---

### Post by vasa1 on 2016-09-21
Please provide the output of ```
ls ~/.config/openbox
```

Please use [noparse]```

``` tags when doing so.[/noparse]Thanks!

---

