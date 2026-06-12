---
title: "What are the advantages of lisp-2?"
date: 2010-12-22
forum: Programming Talk
---

### Post by Somelauw on 2010-12-22
One of the differences between scheme and commonlisp is that in scheme functions and variables share the same namespace and in commonlisp they don't.
According to practical lisp, both decisions have their advantages, but I don't see any advantages of lisp-2.

Compare:
(map (lambda (x) (* xx)) '(1 2 3)); lisp1
(map #'(lambda (x) (* xx)) '(1 2 3)); lisp2

(define hand second) (second '(1 2 3)); lisp1
(defvar hand '#second) (funcall hand '(1 2 3)); lisp2

Lisp1 seems to me much cleaner and simpler. What are the advantages of a different namespace for functions?

---

### Post by schauerlich on 2010-12-22
Well, there's the obvious advantage that you can have variable names that overlap with function names and still retain both (such as using "list" as a variable name in a function). It's also easier to differentiate between which variables store functions and which store other types of values by the way they're used. Other than that, it's really just personal preference. I prefer lisp-1s because it seems like if a language is going to be functional, it should treat functions just like anything else, and not require special syntax for storing them in variables. I also agree that it's a lot cleaner looking without all of the #'s and funcalls.

---

### Post by saulgoode on 2010-12-22
Other than being able to use a variable named 'list', I got nothing. :)

---

### Post by CptPicard on 2010-12-22
I also *prefer* Lisp-1's ... but I also suppose that Lisp-2's are easier on the compiler, as a function "value" can always be matched to a function at compile-time instead of doing a runtime check.

---

### Post by saulgoode on 2010-12-22
> **Somelauw said:**
> Compare:
(map (lambda (x) (* xx)) '(1 2 3)); lisp1
(map #'(lambda (x) (* xx)) '(1 2 3)); lisp2
This example is not really indicative of the namespace issue, but does raise the issue of Scheme's lack of distinction between functions and the symbols to which they are bound. At least I think Scheme is ambiguous about this; I just recently started investing creating some Guile bindings to a library and am unclear as to whether redefining callbacks after they've been attached to a GObject will result in the new definition being called or the one at the time it was attached. 

I will hopefully have time to figure this out after the holidays but if anyone has a ready answer, I'd be interested.

---

### Post by CptPicard on 2010-12-22
> **saulgoode said:**
> This example is not really indicative of the namespace issue, but does raise the issue of Scheme's lack of distinction between functions and the symbols to which they are bound. At least I think Scheme is ambiguous about this;

Or, you could say it's consistent... there are just values and bindings to values, and "x" can be bound just as much to a value like "5" or the addition function. When an s-expression gets evaluated, the first symbol is expected to be bound to a function value... but this has to be checked at runtime so that an error can be given, if it is not.

---

