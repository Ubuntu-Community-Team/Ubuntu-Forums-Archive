---
title: "How do i update my graphic driver"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by Merimee_Sweet on 2014-02-18
Hi everybody!
im a new user and i new install Ubuntu 13.10 but i can really see that i have a problem with video/display,my graphic is VESA: 6330 and i just wanna know how i can upgrade or update it.
Thanks!!!

---

### Post by Bashing-om on 2014-02-18
Merimee_Sweet; Hi ! My Welcome to the forum .

Let's take a look and see.
A lot depends on the graphics card installed on your system, and if the manufacturer continues to support that card.
Post back the outputs of terminal commands:
```

lspci -nnk | grep -iA3 vga
lspci | grep VGA

```
To see your graphics card and info.

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Maybe able to advise
[INDENT][INDENT]how to see things better
[/INDENT][/INDENT]

---

### Post by coffeecat on 2014-02-18
Not a Forum Feedback & Help question.

*Thread moved to **Absolute Beginners Section**.*

---

