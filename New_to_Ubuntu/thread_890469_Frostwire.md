---
title: "Frostwire"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by loyaleagle on 2008-08-15
Well I got Frostwire working. However it did not install an icon.
What is the default folder for Frostwire?

Thanks,

Loyaleagle

---

### Post by Crafty Kisses on 2008-08-15
> **loyaleagle said:**
> Well I got Frostwire working. However it did not install an icon.
What is the default folder for Frostwire?

Thanks,

Loyaleagle

You can get a icon at "GnomeLook" and just replace the icon.

---

### Post by loyaleagle on 2008-08-15
Thanks, but I need to know where the icon needs to point to invoke Frostwire.

---

### Post by Crafty Kisses on 2008-08-15
> **loyaleagle said:**
> Thanks, but I need to know where the icon needs to point to invoke Frostwire.

Do the following:

```
gconf-editor

apps > usp

applet_icon_name
```

Just add the name of your icon leaving off the extension, it seems to auto-detect the format at least, png and xpm.

---

### Post by Crafty Kisses on 2008-08-15
You wrote in the "PM" 
> I need to know where the icon needs to point to invoke Frostwire. What specific folder and program.... I've already got a png to attach once I got it set up.

Thanks.

I don't really use Frostwire, but I'm assuming wherever Frostwire is located at.

---

### Post by Bradtek on 2008-08-15
According to my launcher properties the command is

/usr/bin/frostwire

---

