---
title: "Interfacing libraries from different languages"
date: 2007-08-31
forum: Programming Talk
---

### Post by darsu on 2007-08-31
The vast majority of common Linux libraries are programmed in C (or C++). If one wants to use, say, ALSA or QT or such prominent high-level libraries in a program made in another language, it appears that a special interface is needed. Many languages have binding/wrapper libraries for GTK, for example.

In general terms, what is the nature of a cross-language C(++) library access interface? What does it need to negotiate? What is the M that I should RTF on this topic?

---

### Post by pmasiar on 2007-08-31
[http://en.wikipedia.org/wiki/Cross-platform](http://en.wikipedia.org/wiki/Cross-platform) might be a good start. Whole section about approaches to cross-platform programming, and plenty of links

[Boost C++ libraries](http://en.wikipedia.org/wiki/Boost_C%2B%2B_Libraries) is example of it.

---

### Post by darsu on 2007-08-31
I'm afraid I don't see the connection.

---

### Post by Mirrorball on 2007-08-31
I don't think there is a general approach. It all depends on which languages you want to interface. Here it is how to create a Python interface to a C or C++ library:
[http://docs.python.org/ext/ext.html](http://docs.python.org/ext/ext.html)
PHP's approach is very similar.

---

### Post by pmasiar on 2007-08-31
I see, cross-language not cross-platform.

In that case you need to know detailed api, how calls are organized/checked for type etc, and if differences in API calls between languages exist, implement a wrapper translating one convention to another.

---

### Post by Wybiral on 2007-08-31
> **darsu said:**
> The vast majority of common Linux libraries are programmed in C (or C++). If one wants to use, say, ALSA or QT or such prominent high-level libraries in a program made in another language, it appears that a special interface is needed. Many languages have binding/wrapper libraries for GTK, for example.

In general terms, what is the nature of a cross-language C(++) library access interface? What does it need to negotiate? What is the M that I should RTF on this topic?

For dynamic languages like Python, you just have to use their development files (Python is very easy to write modules for btw).

Basically, if it doesn't have a binding already, you will have to write your own and every language does it a little differently.

---

