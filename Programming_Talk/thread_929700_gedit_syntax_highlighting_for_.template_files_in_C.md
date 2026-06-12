---
title: "gedit syntax highlighting for .template files in C++"
date: 2008-09-25
forum: Programming Talk
---

### Post by NovaAesa on 2008-09-25
Has anyone noticed that syntax highlighting doesn't work automagically for .template files (implementation of a template class) in gedit? You have to go and set it under view every time you load a file.

So this led me to wonder, is .template the standard name for template implementation files for C++? Maybe it's not highlighting automatically because it's not the standard file extension. Anyone know?

---

### Post by dribeas on 2008-09-26
> **NovaAesa said:**
> So this led me to wonder, is .template the standard name for template implementation files for C++? Maybe it's not highlighting automatically because it's not the standard file extension. Anyone know?

I would not say that is a standard... I don't even think there is one. Some of the things that I have found are:

.cpp, included from .h -> don't quite like it though
.tmpl
.impl
.tpl

You can also leave the code inside your .h file in most use cases (unless you want to precompile template instantiations, that is, not include-ing your template code in caller code)

---

### Post by andyba on 2008-12-14
> **dribeas said:**
> I would not say that is a standard... I don't even think there is one. Some of the things that I have found are:

.cpp, included from .h -> don't quite like it though
.tmpl
.impl
.tpl

You can also leave the code inside your .h file in most use cases (unless you want to precompile template instantiations, that is, not include-ing your template code in caller code)

But gedit doesn't automatically highlight .tpl files as well.

---

### Post by dwhitney67 on 2008-12-14
There are no standards, however most developers use a .h or a .hpp.

---

