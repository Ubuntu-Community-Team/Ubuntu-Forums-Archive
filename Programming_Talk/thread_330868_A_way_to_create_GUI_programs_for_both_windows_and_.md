---
title: "A way to create GUI programs for both windows and linux"
date: 2007-01-03
forum: Programming Talk
---

### Post by Jamesbowden on 2007-01-03
I have been learning C++ for a little while now, and am using to write some calculator and conversion tools for my course-Work at school. However all my school computers run on windows, where all my work stations are Linux.

Is there a way to create GUI programs that i can compile for both linux and windows, or if there is another way to get past this problem.

Thanks

---

### Post by 23meg on 2007-01-03
You can use WxWidgets to make the GUI platform independent.

---

### Post by Wybiral on 2007-01-03
Ignore the cries of the windows users...

Or, GTK. I used to use GIMP back before I found a decent OS and it worked fine.

---

### Post by 23meg on 2007-01-03
GTK is cross-platform, but with WxWidgets you eliminate the need to have the GTK runtime environment installed on the target machine.

---

### Post by Jamesbowden on 2007-01-03
Thanks, so with WxWidgets i dont need to have anything installed on my schools machines?

---

### Post by 23meg on 2007-01-03
No; WxWidgets will use the target platform's native widgets.

---

### Post by Mirrorball on 2007-01-03
Qt too. In short, use any toolkit you like.

---

### Post by Jamesbowden on 2007-01-03
Thanks everyone

---

### Post by pmasiar on 2007-01-03
> **Wybiral said:**
> Ignore the cries of the windows users...

That's eeevil. I like it. :twisted: 

Explain users that by switching to Ubuntu they avoid Vista Genuine Advantage, save money and have safer box which will not spy on them using latest DRM (Device Rigged to Malfunction) technology. Will not be easy tho. :-(

---

### Post by rekahsoft on 2007-01-03
> **pmasiar said:**
> That's eeevil. I like it. :twisted: 

Explain users that by switching to Ubuntu they avoid Vista Genuine Advantage, save money and have safer box which will not spy on them using latest DRM (Device Rigged to Malfunction) technology. Will not be easy tho. :-(

haha i love it :)

---

### Post by Wybiral on 2007-01-03
> That's eeevil. I like it.

lol

BTW, this is COMPLETELY off subject, but if it's just simple stuff like calculator and conversion tools, javascript might be something to look into... You can make it look nice with HTML, and it will run on almost every computer with a web browser. It's also a lot more powerful than people give it credit for... I used it to solve this weeks programming challenge (decimal-fraction conversion, prime number detection).

---

