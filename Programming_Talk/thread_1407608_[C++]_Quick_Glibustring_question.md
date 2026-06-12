---
title: "[C++] Quick Glib::ustring question"
date: 2010-02-15
forum: Programming Talk
---

### Post by kahumba on 2010-02-15
Hi,
I'm a bit confused about Glib::ustring. It's an object, not a pointer to an object, right?
So, it's better to pass it as a pointer to avoid copying it's contents, right?

Thus this funcion:
```

void saySomething(Glib::ustring& message) {//pointer
    std::cout << message << std::endl;
}

```is more efficient than this one:

```

void saySomething(Glib::ustring message) {//not a pointer
    std::cout << message << std::endl;
}

```right?

also, does making "Glib::ustring message" constant (const) add anything to the performance (not that it could make a big difference, but still) or is it there only to tell the compiler that the object won't change?

---

