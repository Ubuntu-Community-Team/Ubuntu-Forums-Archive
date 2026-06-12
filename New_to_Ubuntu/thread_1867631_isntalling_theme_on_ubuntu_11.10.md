---
title: "isntalling theme on ubuntu 11.10?"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by werty2010 on 2011-10-23
i searched a bit and i found is : extract the theme folder to /usr/share/themes and the select through "gnome-tweak-tools"
i tried and it told me that i don't have the permission to do that.
i dont think this is the right way(changing permissions just to change a theme)
am i doing something wrong(probably)? if yes, which is the proper way to change a theme?

---

### Post by nidzo732 on 2011-10-23
You should extract the theme to /home/username/.themes, it's safer that way. And then use gnome-tweak-tool which can be installed with software center.

---

### Post by nothingspecial on 2011-10-23
Extract the theme to your home folder.

Then open a terminal and type

```
gksudo nautilus
```

move the thene to /usr/share/themes 

Then shut the nautilus window.

**EDIT** or do as above, yes it is probably safer that way.

---

### Post by werty2010 on 2011-10-23
> **nidzo732 said:**
> You should extract the theme to /home/username/.themes, it's safer that way. And then use gnome-tweak-tool which can be installed with software center.

thanks for the quick responses
but there is no folder named .themes in home directory(i checked the hidden too)
could you be a bit more specific?

---

### Post by nothingspecial on 2011-10-23
You can make one

---

### Post by werty2010 on 2011-10-23
thanks it now works

---

