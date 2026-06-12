---
title: "[Python] Too repetitive... or maybe I'm too used to Lisp macros..."
date: 2013-04-15
forum: Programming Talk
---

### Post by nvteighen on 2013-04-15
Hey guys.
I've been wondering if there's any way in Python to write a class like this in a better way than this:

```

class MyClass(object):
    def __init__(self):
        self.first_attr = 0
        self.second_attr = 0
        self.third_attr = 0

        # ...

    def add_first_attr(self, n):
        self.first_attr += n
        if self.first_attr >= 100:
            self.first_attr = 100
        elif self.first_attr <= 0:
            self.first_attr = 0

    def add_second_attr(self, n):
        self.second_attr += n
        if self.second_attr >= 100:
            self.second_attr = 100
        elif self.second_attr <= 0:
            self.second_attr = 0

    def add_third_attr(self, n):
        self.third_attr += n
        if self.third_attr >= 100:
            self.third_attr = 100
        elif self.third_attr <= 0:
            self.third_attr = 0

    # ...

```

I know I can't do something like this, which would be trivial and quite common in Lisp:

```

# THIS ISN'T GOING TO WORK
class MyClass(object):

    # ...

    def add_attr(self, attr, n):
        self.attr += n
        if self.attr >= 100:
            self.attr = 100
        elif self.attr <= 0:
            self.attr = 0

```

Neither can I create a static method passing the attribute because these are integers and therefore, they'll be passed by value, not by reference.

I'm sure there's some way out that doesn't involve repeating the whole thing for those attributes whose values are only valid for a 0-100 range. OK, I could create a Stat class so I can pass the attribute by reference, but that seems too convoluted.

Opinions?

---

### Post by MadCow108 on 2013-04-15
how about:
```

class MyClass(object):
  def add_attr(self, attr, n):
      new = getattr(self, attr, 0) + n
      setattr(self, attr, min(max(new, 0), 100)

```

---

### Post by nvteighen on 2013-04-15
Oh, I didn't know there was setattr/getattr :) Really nice! Thanks!

---

