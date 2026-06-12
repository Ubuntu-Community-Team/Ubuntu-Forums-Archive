---
title: "One Question about Python and one about Perl"
date: 2007-12-18
forum: Programming Talk
---

### Post by Majorix on 2007-12-18
I have two questions, one about Perl and one about Python.

Python Q: Can a Python sourcecode or bytecode be compiled into a Linux exec, like py2exe for Windows?

Perl Q: Can it be expanded with C? I have seen the Perl documentation titles but there was only one about invoking Perl from C.

---

### Post by Wybiral on 2007-12-18
> **Majorix said:**
> Python Q: Can a Python sourcecode or bytecode be compiled into a Linux exec, like py2exe for Windows?

In fact, it can be JIT compiled using [Psyco]("http://psyco.sourceforge.net/"). There is also a project to compile it to C++ named [Shed Skin]("http://mark.dufour.googlepages.com/") (it has some restrictions, but it covers a bulk of the language and will probably continue to cover more and more). There is also [Pyrex]("http://www.cosc.canterbury.ac.nz/greg.ewing/python/Pyrex/"), which makes Python a bit more like C, but if you're willing to alter your code some, it will compile "Python"-esque code too.

---

### Post by skeeterbug on 2007-12-18
> **Majorix said:**
> 
Perl Q: Can it be expanded with C? I have seen the Perl documentation titles but there was only one about invoking Perl from C.

[http://dev.perl.org/perl6/architecture.html](http://dev.perl.org/perl6/architecture.html)

"One of the major reasons to revisit Perl was to fix the mess that is XS (the way you extend Perl with C or C++ subroutines).  Perl5 has no API for extension, separate from the functions used to implement Perl, and extending Perl requires hideous amounts of work.  Dan and Larry are aiming to make C extensions as easy as they possibly can be (Brian Ingerson's excellent perl5 Inline modules give some directions for this).  Anyone who has used XS looks forward to its demise."

---

### Post by Majorix on 2007-12-18
> **Wybiral said:**
> In fact, it can be JIT compiled using [Psyco]("http://psyco.sourceforge.net/"). There is also a project to compile it to C++ named [Shed Skin]("http://mark.dufour.googlepages.com/") (it has some restrictions, but it covers a bulk of the language and will probably continue to cover more and more). There is also [Pyrex]("http://www.cosc.canterbury.ac.nz/greg.ewing/python/Pyrex/"), which makes Python a bit more like C, but if you're willing to alter your code some, it will compile "Python"-esque code too.

I have heard of Psyco and it improving the speed of Python code. But can it do it with all kinds of code? And when I had visited their site I had read that it uses lots of RAM, but how much? Does it use that also while running the code? And finally, how do you run the code you used Psyco in?

I hadn't heard of the Shed Skin project, will look into it.

And about Pyrex, I don't think I can alter the code, as I want it to be cross-platform.

> **skeeterbug said:**
> [http://dev.perl.org/perl6/architecture.html](http://dev.perl.org/perl6/architecture.html)

"One of the major reasons to revisit Perl was to fix the mess that is XS (the way you extend Perl with C or C++ subroutines).  Perl5 has no API for extension, separate from the functions used to implement Perl, and extending Perl requires hideous amounts of work.  Dan and Larry are aiming to make C extensions as easy as they possibly can be (Brian Ingerson's excellent perl5 Inline modules give some directions for this).  Anyone who has used XS looks forward to its demise."

Thanks for the info. Guess I will have to wait a little more :)

---

### Post by slavik on 2007-12-18
keep in mind that in Python, an array might not be the same as an array in C. In Perl, for example, arrays are doubly linked circular lists, which allow you to use them as a stack/queue/list/array and even allow negative indeces. :)

---

### Post by Wybiral on 2007-12-18
> **slavik said:**
> keep in mind that in Python, an array might not be the same as an array in C. In Perl, for example, arrays are doubly linked circular lists, which allow you to use them as a stack/queue/list/array and even allow negative indeces. :)

Something tells me Python and Perls arrays are similar (you can use negative indices in Python too). Well, Python doesn't really have arrays but that's basically how its lists work. There are modules that use real C arrays in Python, but I believe its lists are stored with a linked list of some kind. Tuples might be a form of C array, but I'm not sure.

---

### Post by slavik on 2007-12-18
that could be the reason for larger memory footprint, since you have to have a struct for each item in the list (what it is, where it actually is, etc.)

---

### Post by CptPicard on 2007-12-19
> **Wybiral said:**
> but I believe its lists are stored with a linked list of some kind.

I sure hope not -- indexing the list better be a constant-time operation, which it is not in a list structure, or I'm going to be appalled. :)

---

### Post by Wybiral on 2007-12-19
> **CptPicard said:**
> I sure hope not -- indexing the list better be a constant-time operation, which it is not in a list structure, or I'm going to be appalled. :)

OK, I did some research and I have to correct myself. Pythons lists are not a linked list or hash table of any kind, they are an actual array of references to the real objects (instead of an array of the objects themselves). So don't worry CptPicard, they are constant O(1). And also, Python does have tuples which work much more like a structure than an array (immutable and thus faster).

EDIT:

More stats:
Index: O(1)
Copy: O(n)
Insert: O(n)
Append: O(1)
Sort: O(n log n)

---

### Post by pmasiar on 2007-12-19
> **slavik said:**
> keep in mind that in Python, an array might not be the same as an array in C. In Perl, for example, arrays are doubly linked circular lists, which allow you to use them as a stack/queue/list/array and even allow negative indeces. :)

Python's lists can be used exactly like Perl's lists. The only difference AFAIK is in syntax of slicing a list by another list: perl has "@alist[@blist]", Python has list comprehension: "[alist[x] for x in blist]", which can be even more flexible if needed.

Again, Python instead of heaping special cases on top of special cases in syntax, adds special construct which is more flexible in the long run.

[http://en.wikipedia.org/wiki/Numpy](http://en.wikipedia.org/wiki/Numpy) adds to Python real C-like arrays and matrices.

---

