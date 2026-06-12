---
title: "What do I need to compile a C file?"
date: 2007-07-08
forum: Programming Talk
---

### Post by krugman on 2007-07-08
Hi to all!

I have just started learning the C language and I can't compile the very simple programs I have started to make on Ubuntu.

For instance:

```

// fathm_ft.c -- converts 2 fathoms to feet


#include <stdio.h>


int main(void)


{


    int feet, fathoms;





    fathoms = 2;


    feet = 6 * fathoms;


    printf("There are %d feet in %d fathoms!\n", feet, fathoms);


    printf("Yes, I said %d feet!\n", 6 * fathoms);





    return 0;


}


```

When I run it on my mac it works fine, whereas when I do a gcc fathm_c on ubuntu it yields:

```

fathm_ft.c:3:19: erreur: stdio.h : Aucun fichier ou répertoire de ce type
fathm_ft.c: In function «main":
fathm_ft.c:15: attention : incompatible implicit declaration of built-in function «printf"
fred@uranie-linux:~/C++$ gcc fathm_ft.c 
fathm_ft.c:3:19: erreur: stdio.h : Aucun fichier ou répertoire de ce type
fathm_ft.c: In function «main":
fathm_ft.c:15: attention : incompatible implicit declaration of built-in function «printf"


```

I guess I need some more libraries for gcc  right?
What should I install? For' instance, I have libgcc1, but I guess it's not enough.

Thanks for your help!:)

---

### Post by krugman on 2007-07-08
Well, I have tried adding a few libraries thanks to synaptics, and it seems to be working.
However, I woukd like to understand what I have done, so I would like to know which libraries are mandatory, and which are not.

---

### Post by AnRa on 2007-07-08
You have to install 'build-essential'.

---

### Post by krugman on 2007-07-08
oh, yeah, thanks, I had forgotten about this one!

Btw, I use Emacs for writing the code, and I compile using the terminal.
Is there some easier way to compile? Maybe a compiler with a debugger?

(Even tough I think Emacs has one, but I haven't tried it yet.)

---

### Post by iason86 on 2008-02-26
> **krugman said:**
> oh, yeah, thanks, I had forgotten about this one!

Btw, I use Emacs for writing the code, and I compile using the terminal.
Is there some easier way to compile? Maybe a compiler with a debugger?

(Even tough I think Emacs has one, but I haven't tried it yet.)
yes you can use KDevelop its a vary easy program to write c/c++ code try it you will love it

---

### Post by S15_88 on 2008-02-26
anjuta is a good IDE

---

### Post by Zwack on 2008-02-26
If you're already using Emacs then you should probably just use Emacs...

You can compile, run and debug all from within Emacs.

Admittedly I've only done that with Fortran but it worked nicely.

Z.

---

