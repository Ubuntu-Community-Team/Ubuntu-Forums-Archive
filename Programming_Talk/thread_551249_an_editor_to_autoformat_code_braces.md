---
title: "an editor to autoformat code braces"
date: 2007-09-14
forum: Programming Talk
---

### Post by Brokenlynx on 2007-09-14
I'm currently doing some basic C/C++ programming but I've moved to this from programming in Java in netbeans. In this IDE I was used to pressing a single shortcut to move code braces and indents into the correct positioning (namely K&R style braces on the same line as a function header). 

I've been searching all over for plugins to gedit and KATE (KDE Advanced Text Editor) to be able to add some kind of similar functionality (namely because of the fact that code examples im working from put braces on a seperate line below the header). Does anyone know of an editor, or combination of editor indentation file etc that will allow me to press a single shortcut to move braces to the same line as the header and properly indent my code?

---

### Post by slavik on 2007-09-14
give geany a try

---

### Post by psusi on 2007-09-14
emacs will do this, and many, many other things.  IIRC, there was also an indent command that will reindent a source file from the command line.

---

### Post by Compyx on 2007-09-15
```

sudo apt-get install indent
man indent

```

---

### Post by sunshinege on 2009-04-23
> **slavik said:**
> give geany a try

yes, I just tried it and think it is an excellent editor.

---

### Post by cb951303 on 2009-04-23
do you mean a code formatter? if so you can use this with any editor: [http://astyle.sourceforge.net/](http://astyle.sourceforge.net/)

---

### Post by dwhitney67 on 2009-04-23
There's also [uncrustify]("http://linux.softpedia.com/get/Programming/Code-Generators/Uncrustify-10963.shtml") as a code-formatter.  It is useful to use if there are many source files that need to be "cleaned" up to match one's programming style.

---

