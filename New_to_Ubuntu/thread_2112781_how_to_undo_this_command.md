---
title: "how to undo this command"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by rilesac on 2013-02-05
I'm using ubuntu in my laptop and the right click doesn't work so I was trying to solve it. I execute the command showed below and now my mouse is really slow and some things doesn't work as it used to.

```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```how can I undo this?

Thanks! :D

---

### Post by omeomi on 2013-02-05
I believe the default is auto so does this work?
```
echo options psmouse proto=auto > /etc/modprobe.d/psmouse.modprobe
```

What is the content of psmouse.modprobe? If it is just that one option you could also just remove the file.

---

### Post by Cheesemill on 2013-02-05
Just delete the file that the command created...
```
sudo rm /etc/modprobe.d/psmouse.modprobe
```

---

### Post by rilesac on 2013-02-05
Thanks Cheesemill & omeomi!

There was only that option so I deleted it and is fixed.
Thanks & Greetings!

---

