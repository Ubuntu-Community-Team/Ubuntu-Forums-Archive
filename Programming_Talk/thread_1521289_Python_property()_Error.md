---
title: "Python property() Error"
date: 2010-06-30
forum: Programming Talk
---

### Post by Penguin Guy on 2010-06-30
I'm writing a curses 'Snakes' game in Python but I'm having problem with the [FONT="Courier New"]property()[/FONT] function. I've used [FONT="Courier New"]property()[/FONT] successfully before, but this time it seems to be having no effect. The code is still in the early stages of development, so all I want at this point it something that moves in some form or another.

Screenshot: Notice how [FONT="Courier New"]position[/FONT] is not the same as [FONT="Courier New"](y, x)[/FONT].

EDIT: I've given up on doing this, I've switched to using lists and indexes (`[1]`) instead.

---

### Post by Penguin Guy on 2010-07-02
Bump.

---

### Post by Bachstelze on 2010-07-02
Python 2.6 has two "styles" of classes. "Old-style" classes is what you have, they are defined with

```
class Class:
```

and "new-style" classes inherit from the object base class, and are therefore defined with

```
class Class(object):
```

Te Python doc says property() is for new-style classes, maybe you should try fixing that.

---

### Post by Penguin Guy on 2010-07-05
I've tried changing the class style and messed around with some other stuff too. But whatever I do I am still getting this error.

---

