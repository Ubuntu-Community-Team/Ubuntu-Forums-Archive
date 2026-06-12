---
title: "Using SCons with vala?"
date: 2009-03-03
forum: Programming Talk
---

### Post by days_of_ruin on 2009-03-03
Is it possible to use SCons to compile vala programs?

---

### Post by cabalas on 2009-03-03
A quick search on the SCons wiki lead me to this [http://www.scons.org/wiki/ValaBuilder](http://www.scons.org/wiki/ValaBuilder) , which looks like it would be a plugin to allow for compiling with vala could be worth looking into.

---

### Post by days_of_ruin on 2009-03-03
> **cabalas said:**
> A quick search on the SCons wiki lead me to this [http://www.scons.org/wiki/ValaBuilder](http://www.scons.org/wiki/ValaBuilder) , which looks like it would be a plugin to allow for compiling with vala could be worth looking into.

Any idea on how to install it and use it?

---

### Post by cabalas on 2009-03-03
Looking through the user manual it has a whole section on writing/using custom builders [http://www.scons.org/doc/1.2.0/HTML/scons-user/c3427.html](http://www.scons.org/doc/1.2.0/HTML/scons-user/c3427.html) that should help you

---

### Post by days_of_ruin on 2009-03-16
> **cabalas said:**
> Looking through the user manual it has a whole section on writing/using custom builders [http://www.scons.org/doc/1.2.0/HTML/scons-user/c3427.html](http://www.scons.org/doc/1.2.0/HTML/scons-user/c3427.html) that should help you

Still haven't figured it out.Is there any scons users here that have used this or other custom scons builders?

---

### Post by Jan-Nik on 2009-04-19
Create a directory called scons-tools and insert the code into a file called "vala.py".

Then:

```
# Load the custom vala builder
env.Tool('vala', toolpath=['scons-tools'])
env.Decider('content')

vala = env.Vala(Glob('*.vala'))

```

---

