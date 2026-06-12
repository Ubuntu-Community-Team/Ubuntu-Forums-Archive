---
title: "Emacs question"
date: 2008-06-25
forum: Programming Talk
---

### Post by svk on 2008-06-25
I've been peeking at the Linux source code, and I saw a lot of comments preceding functions that  look like this:

```

/**
 * simple_strtoul - convert a string to an unsigned long
 * @cp: The start of the string
 * @endp: A pointer to the end of the parsed string will be placed here
 * @base: The number base to use
 */
unsigned long simple_strtoul(const char *cp,char **endp,unsigned int base)
{
        ...

```

The comments follow a very structured format, and they describe what the function does and what each parameter is meant for.  Emacs seems to recognize this format because it highlights the names of the arguments inside the comment.

I'm wondering what this feature is and how I could use it for my own projects.  Also, are there keybindings to generate comments that look like this?  Or are they all typed out by hand?

Thanks in advance for the help.

---

### Post by LaRoza on 2008-06-25
[http://en.wikipedia.org/wiki/Javadoc](http://en.wikipedia.org/wiki/Javadoc)

[http://en.wikipedia.org/wiki/Comparison_of_documentation_generators](http://en.wikipedia.org/wiki/Comparison_of_documentation_generators)

It is some sort of documentation generator, I don't know what it is called.

---

### Post by CptPicard on 2008-06-25
Probably doxygen.

---

