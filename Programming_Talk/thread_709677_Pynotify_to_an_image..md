---
title: "Pynotify to an image."
date: 2008-02-27
forum: Programming Talk
---

### Post by solarwind on 2008-02-27
Hey all,

How can I add a pynotify to a gtk.Image or gtk.Eventbox?

---

### Post by G|N| on 2008-02-28
First you need to know the position of the image or eventbox:
```
x = widget.get_allocation()[1][0]
y = widget.get_allocation()[1][1] 
``` 

After create the notification:
```

toast = pynotify.Notification("title","body")
toast.set_hint("x", x)
toast.set_hint("y", y)
toast.show()

```

That should work :)

---

### Post by solarwind on 2008-02-28
> **G|N| said:**
> First you need to know the position of the image or eventbox:
```
x = widget.get_allocation()[1][0]
y = widget.get_allocation()[1][1] 
``` 

After create the notification:
```

toast = pynotify.Notification("title","body")
toast.set_hint("x", x)
toast.set_hint("y", y)
toast.show()

```

That should work :)

Thanks! I used a different method but this should work too!

---

