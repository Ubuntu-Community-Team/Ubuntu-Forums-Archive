---
title: "Forcing version on dependency"
date: 2009-03-05
forum: Packaging and Compiling Programs
---

### Post by jyavenard on 2009-03-05
Hi.

I'm trying to build a package so it depends on a specific version of a library.

I carefully read [http://www.debian.org/doc/maint-guide/index.en.html](http://www.debian.org/doc/maint-guide/index.en.html)

but didn't get the answer I was looking for.

In my debian/control file I have for a given package:
Depends: ${misc:Depends}

Which will install all the dependencies as required ; however it creates a dependency on a newer library I previously installed which doesn't ship with ubuntu. I know that my package will work with the standard library.

Is there a way to force which version of the dependency is going to be installed?
Like right now, my package automatically add a dependency to version 1.0.19 of the library, I want that dependency to be on version 1.0.17

The only way I've found so far is to remove ${misc:Depends} and set manually all the dependencies..
But obviously this isn't an ideal solution, as I could very easily forget about a dependency.

What I tried to do is in the debian/rules add:
dh_makeshlibs -a -V 'libname (>= 1.0.17)'

but this still generate a dependency as:
shlibs:Depends=libartsc0 (>= 1.5.9), libname (>= 1.0.17), libname (>> 1.0.19)

Which I don't know how it will behave...

Any help or recommendations would be greatly appreciated.

Thank you
Jean-Yves

---

### Post by jyavenard on 2009-03-07
No one knows ??

Right now I've created a script that modify the package after it's been created ..

but i'm sure there's an easier way...

---

### Post by jyavenard on 2009-03-14
Still haven't found a solution, could anyone help ?

Thank you
Jean-Yves

---

### Post by cubeist on 2009-03-14
I am not sure this will work, but you could open synaptic, search for the particular libraries on your system, select the library and in the package menu choose *force version*

Then try your ./configure && make again and see if it works.

---

