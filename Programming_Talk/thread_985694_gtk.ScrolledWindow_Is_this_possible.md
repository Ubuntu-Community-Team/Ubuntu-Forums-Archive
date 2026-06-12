---
title: "gtk.ScrolledWindow: Is this possible?"
date: 2008-11-17
forum: Programming Talk
---

### Post by days_of_ruin on 2008-11-17
Is there a function that will scroll it to the bottom?

---

### Post by nvteighen on 2008-11-18
Maybe gtk_scrolled_window_set_placement()? (translate it from C to Python) But I'm not sure.

---

### Post by Tony Flury on 2008-11-18
i think set_window_placement just changes where the scroll bars appear - ie to the left or the right of the scrolling area

This code is in python - you might need to translate to your favourite language.

The only way i can see is (if _sw is your scrolling window object)
```

_vadj = _sw.get_vadjustment()
_vadj.value = _vadj.upper()

```

(if that scrolls in the wrong direction try : 

```

_vadj.value = _vadj.lower()

```

Edit - left out this bit - sorry ;
I think you then have to use the emit method to make sure that the change is used (it artificially generates an event as if the user had clicked on the scroll bar.

```

_vadj.emit('changed')

```

---

### Post by G|N| on 2008-12-10
Thanks for the solution, i have been looking for this for some time now :)

But you made a mistake:
```
 
_vadj.value = _vadj.upper()
_vadj.value = _vadj.lower()

```

has to be:
```
 
_vadj.set_value(_vadj.upper)
_vadj.set_value(_vadj.lower)

```


```
_vadj.emit('changed')
``` is not needed anymore since set_value emits the 'changed' method

Sometimes it works, but most of the time the scrollbar is located in the middle and not at the end....
Any ideas?

---

### Post by days_of_ruin on 2008-12-10
> **G|N| said:**
> Thanks for the solution, i have been looking for this for some time now :)

But you made a mistake:
```
 
_vadj.value = _vadj.upper()
_vadj.value = _vadj.lower()

```

has to be:
```
 
_vadj.set_value(_vadj.upper)
_vadj.set_value(_vadj.lower)

```


```
_vadj.emit('changed')
``` is not needed anymore since set_value emits the 'changed' method

Sometimes it works, but most of the time the scrollbar is located in the middle and not at the end....
Any ideas?

Really? So far it always seems to work for me.

---

