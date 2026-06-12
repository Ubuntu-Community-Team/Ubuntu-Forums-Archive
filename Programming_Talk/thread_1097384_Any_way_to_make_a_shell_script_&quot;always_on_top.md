---
title: "Any way to make a shell script &quot;always on top&quot;"
date: 2009-03-15
forum: Programming Talk
---

### Post by dsuds on 2009-03-15
Hi all,

I have a shell script that calls a zenity list for the user to make a selection from.  In Ubuntu 7.10 the script would come up on top of other windows, which is what I want it to do.  The problem is that on Ubuntu 8.10 the script does not receive focus and stays on the bottom menu.  If you click on the bottom menu the script then pops up and works fine.

I checked and zenity does not have an "always on top" setting currently.  Is there a setting or programming command that can change this behavior?  I have done quite a bit of programming but I'm a newb at shell scripts.

Thanks

David

---

### Post by lavinog on 2009-03-16
I think this has something to do with "dialog boxes should not steal focus"
This design seems flawed since there is no way for the user to notice error dialogs.

one hack you can try is to use wmctrl
```

zenity --error
wmctrl -a Error

```

Kind of lame, but it should work.
use: wmctrl -a [window title]
You can use: wmctrl -l
to get a list of windows open, so you can get the title if you don't know it.

---

### Post by dsuds on 2009-03-16
Thanks for the suggestion lavinog but unfortunately the zenity command waits for input so wmctrl doesn't work.  Anybody got another suggestion?

Is there a way to disable the "dialog box should not steal focus" behavior in gnome?

Thanks.

David

---

### Post by lavinog on 2009-03-17
This worked:
```

#!/bin/bash

$(sleep 1 && wmctrl -a Select)&

choice=$(zenity --list --text="testing list" --column="test" test1 test2 test3)

echo you picked $choice

```
You can change the sleep 1 to sleep .5 for quicker response
.3 was too low for my system

---

### Post by lavinog on 2009-03-17
> **dsuds said:**
> 
Is there a way to disable the "dialog box should not steal focus" behavior in gnome?
David

If there was a way to do it, it would require your script to be run as super user.

---

