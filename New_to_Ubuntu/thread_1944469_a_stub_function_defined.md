---
title: "a stub function defined"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by newport_j on 2012-03-21
I do not know if I am in the correct section, but I need a definition of a stub function as it applies to the c language.
 
I am seeing the term stub function referenced in many papers and tutorials on Ubuntu and c programming.
 
Any help appreciated. Thanks in advance.
 
newport_j

---

### Post by MG&amp;TL on 2012-03-22
A code stub is a piece of code that doesn't do anything useful except exist; It's often used for code porting, or when a third-party piece of code requires function X to be defined, even if it does nothing.

[http://en.wikipedia.org/wiki/Method_stub](http://en.wikipedia.org/wiki/Method_stub)

An example in C:

```

//when this is complete, it will make a dialog box saying "hello"
void hello() {
    printf("Hello\n");
}

```

Next time, you might be better off with the programming talk section. :)

---

