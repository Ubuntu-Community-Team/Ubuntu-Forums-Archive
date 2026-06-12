---
title: "keyboard symbols all mixed up"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by scientist1971 on 2008-04-29
I had a problem with my graphics driver which meant ubuntu would not load
thanks to the forum that was sorted out quickly
however now when I try to use an symbols on my keyboard they are all mixed up and in the wrong places!
any ideas how to change them back?

---

### Post by tompickles on 2008-04-29
probablly telling you to suck eggs - but check your language in the Keyboard config window in System -> Preferences

---

### Post by scientist1971 on 2008-04-29
cheers tom
the keyboard layout was US en but my laptop is japanese so I changed it ands its fine now
thanks

---

### Post by spacesamurai on 2008-04-29
How are you doing. I had the same problem when installing on my Japanese system. Can you see what your keyboard is set to by  looking inside the x-server configuration file /etc/X11/xorg.conf ?

Under input device, I have the following output:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "jp106"
        Option          "XkbLayout"     "jp,jp"

---

### Post by billgoldberg on 2008-04-29
Why did you make a new thread?

The answer was in your original thread and was posted before you even opened this post.

---

### Post by scientist1971 on 2008-04-29
will know in future

---

### Post by scientist1971 on 2008-04-29
spacesamurai
not sure about that generally stick to the gui
new to this stuff....

---

