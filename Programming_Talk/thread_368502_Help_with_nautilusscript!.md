---
title: "Help with nautilusscript!"
date: 2007-02-23
forum: Programming Talk
---

### Post by olskar on 2007-02-23
Hi!
I would like a nautilusscript that works like this:
I rightclick on a cabfile, click on "Install to device" and after that I want this to be run:

synce-install-cab thefileiclicked.cab

Can someone help me do this?

---

### Post by iraiscoming223 on 2007-02-25
```
#!/bin/bash
synce-install-cab "$*"

```
Assuming you're using GNOME:
Save it in the ~/.gnome2/nautilus-script/ folder and then give the execute privilege.
Then you will find it in the righ-click menu in the "Script" section.

---

### Post by olskar on 2007-03-08
It doesnt work, It just works if i write it in the terminal..Is there a way to solve that?

---

### Post by lnostdal on 2007-03-08
have you done ```
chmod +x thescript
``` ..?

..have you restarted nautilus?  do .. ```
killall -KILL nautilus
``` ..a couple of times until "nautilus: no process killed" is shown

`thescript' will then be visible on the right-click context-menu under scripts

edit:
you can also associate a custom command for .cab-files when left-clicking btw.

---

