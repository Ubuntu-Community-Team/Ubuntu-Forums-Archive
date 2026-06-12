---
title: "[SOLVED] vim"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by hovtzi on 2008-10-21
hey

I'm trying to edit a file in VIM and when I try to exit&save it won't let me..[COLOR="Red"]
E45: 'readonly' option is set (add ! to override)[/COLOR]

I think it has something to do that I'm not a superuser
(my prompt line ends with $ instead of #) - how do I enter into a superuser mode?

I was told before that in Ubuntu it's different and that I have to write "sudo *command*" in order to get stuff done. But when I do it I can't edit files in vim..

help?

---

### Post by eentonig on 2008-10-21
[PHP]sudo vi /path/to/filename[/PHP]

Should work. I use it all the time

---

### Post by hovtzi on 2008-10-21
I trying to go from $ mode:
name@machine$
to #:
name@machine#

i understand that i can always type in "sudo" each time i wanna exacute something, but i guess that there's a easier way..

---

### Post by FutanariKitty on 2008-10-21
You mean you want a root shell. Quite easy! Just:
```
sudo -s
```
There ya go!

EDIT: By the way, even once you have superuser access and need to edit a file, chances are it's still going to be marked read-only. When you're done your editing, make sure to quit with :wq! to override the read-only flag.

---

### Post by handydan918 on 2008-10-21
> **hovtzi said:**
> I trying to go from $ mode:
name@machine$
to #:
name@machine#

i understand that i can always type in "sudo" each time i wanna exacute something, but i guess that there's a easier way..

There is, but not with Ubuntu...

---

### Post by ilrudie on 2008-10-21
sudo bash

---

