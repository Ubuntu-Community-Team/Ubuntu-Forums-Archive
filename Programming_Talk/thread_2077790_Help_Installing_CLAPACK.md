---
title: "Help Installing CLAPACK"
date: 2012-10-29
forum: Programming Talk
---

### Post by Reek on 2012-10-29
Hey,

Has anyone here had any experience with CLAPACK. I need to use it in a project and have no clue how to install it. I've tried following the readme that came with it but my meagre computer skills are not up that it seems.

I should point out that I have to experience with anything like this.

Thanks for any help.

---

### Post by MadCow108 on 2012-10-29
these lapack things are always a pain to install, if possible use the packages.

this should work

```
cp make.inc.example  make.inc
#edit make.inc to your liking
make f2clib
make all
```

and the copy the libraries where you need them to be (the .a files)

---

### Post by Reek on 2012-10-29
This is probably a pretty dumb question but where do the libraries need to be? Do they go in usr/lib?

Also, do I need to copy the header files to usr/include?

---

### Post by MadCow108 on 2012-10-29
> **Reek said:**
> This is probably a pretty dumb question but where do the libraries need to be? Do they go in usr/lib?

Also, do I need to copy the header files to usr/include?

that depends on how you are using the library
normally there is not much need to copy static libraries to /usr/lib or /usr/include
just specify the paths during compilation directly.
see the -L and -I flags of gcc

or do you need shared libraries?
those would need to be built differently but I'm not sure how

---

