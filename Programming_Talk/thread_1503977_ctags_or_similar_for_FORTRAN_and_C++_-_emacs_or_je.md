---
title: "ctags or similar for FORTRAN and C++ - emacs or jedit"
date: 2010-06-07
forum: Programming Talk
---

### Post by Zorgoth on 2010-06-07
How would I get tags for Fortran or C++ on either or both of emacs and jedit?  (I have a bunch of Fortran code to read and possibly C++ code to write)

---

### Post by gmargo on 2010-06-07
The **ctags(1)** command from the **exuberant-ctags** package will do the job.

---

### Post by Zorgoth on 2010-06-07
I have ctags and exuberant ctags installed (on Fedora, I am using the Ubuntu forums because they usually work better for programming in my experience), but don't really understand how to use the commands.  My situation is that I have a load of source files in a folder with a couple folders of source files inside that one and I am trying to read them, which is annoying since I don't know where the subroutines are declared.  So how do I use ctags to actually be able to find the declaration of a function efficiently? (I have never used anything like this before, it is something I heard about from a friend)

---

### Post by gmargo on 2010-06-07
You use ctags to generate a tags file.  The editor is responsible for accessing and interpreting the generated 'tags' file.

As I don't know emacs or jedit, I can give only you a vim example:

To generate the tags for a whole project and then start at the main() routine:
```

ctags -R .
vim -t main

```Then inside vim place the cursor on a name and use ^] to follow the tag, and ^T to pop up the stack.  For emacs usage you probably want "etags -R ." or "ctags -e -R .".

---

### Post by Zorgoth on 2010-06-08
Thank you I got it working with emacs (but not jedit, it gives errors - but emacs is pretty cool)

---

