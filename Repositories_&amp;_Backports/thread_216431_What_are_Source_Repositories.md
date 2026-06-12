---
title: "What are Source Repositories?"
date: 2006-07-15
forum: Repositories &amp; Backports
---

### Post by Irony on 2006-07-15
In my repositories list I have source and binary repositories.

I assume that source repositories are only needed for if I compile something from source - where would such a file would actually download to so that it could be compiled?

Do I only need to have binary sources uncommented for synaptic installation, will commenting source repositories stop installation of programs?

---

### Post by reacocard on 2006-07-15
for installing software from synaptic, only the binaries are nessecary.

---

### Post by Irony on 2006-07-15
Thanks.

If I did actually download a source file, where would it go for compiling?

Where are these source files actually listed in Synaptic?

---

### Post by reacocard on 2006-07-15
they are mainly for if you need to compile from source. a program you were compiling might need the development (source) files for, say, sdl. you could simply install the libsdl-dev package, rather than having to get that from the net as well. to find where a package was installed to, open its properties in synaptic and choose "installed files".

---

### Post by zorkerz on 2008-05-27
Usually when adding repos they give you the binaries and the source repo to add. If I am not intending on installing anything from source what is the purpose of the source repo?
Wouldn't it just be extra work to always add the source repo but never use it?

---

### Post by Gina on 2008-05-29
Source repos are for those who wish to compile from source (and many people do).  If you don't wish to do that simply leave the source repo option unchecked in your Software Sources.

---

