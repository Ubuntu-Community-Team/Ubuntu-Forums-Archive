---
title: "Lisp execute generated code"
date: 2008-12-14
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-12-14
I made a function that returns common lisp code, how do I execute it

[PHP]
(defun code () (list <quote>+ <quote>X 1))
[/PHP]

---

### Post by CptPicard on 2008-12-15
Check out the "eval" function.

---

### Post by Mr.Macdonald on 2008-12-15
but eval didn't seem to work with executing code that I generated with a function

functions
[PHP](defun mkvar (x) x)
(defun mkconst (c) c)

(defun mksum (poly0 poly1) (list '+ poly0 poly1))
(defun mksub (poly0 poly1) (list '- poly0 poly1))
(defun mkmult (poly0 poly1) (list '* poly0 poly1))
(defun mkdiv (poly0 poly1) (list '/ poly0 poly1))
(defun mkpow (poly0 poly1) (list '** poly0 poly1))[/PHP]

command
[PHP](mkpow (mksum (mkvar 'x) (mkconst 1)) (mkconst 2))[/PHP]

how would I evaluate the result of that command, by passing in x

---

### Post by CptPicard on 2008-12-15
It sort of looks like you may be interested in macros instead...

---

### Post by nvteighen on 2008-12-15
> **CptPicard said:**
> It sort of looks like you may be interested in macros instead...
Yes, that was what I thought...

---

### Post by Mr.Macdonald on 2008-12-15
macros are preoprocessor right? I want to do this during runtime, so the user can pass information in

---

### Post by Wybiral on 2008-12-15
> **Mr.Macdonald said:**
> macros are preoprocessor right? I want to do this during runtime, so the user can pass information in

You have much to learn about Lisp...

Don't be so quick to draw the line between compile-time and run-time.

---

### Post by Mr.Macdonald on 2008-12-15
> You have much to learn about Lisp...

Don't be so quick to draw the line between compile-time and run-time. 

Well this is learning, and I guess that the user can pass info into macros?

---

### Post by wtwood on 2008-12-15
First, if you are using Common Lisp then the function for exponentiating is **expt**, not ******.  You need to change the definition of **mkpow** to
```
(defun mkpow (poly0 poly1) (list 'expt poly0 poly1))
```

Your biggest problem is handling variables.  The function **mkvar** won't work because lisp wants to evalute all the args to a function call while you want the symbols passed to **mkvar** to not be evaluated until you call **eval** on a constructed expression.  Here's where a *macro* can do the trick.  If the definition of **mkvar** is changed to
```
(defmacro mkvar (x) (list 'quote x))
``` then you can just use the variable names without quoting them when you build and evaluate an expression.

Finally, the Common Lisp function **subst** can be used to substitute a value for a symbol in an expression.  Here's the modified code:
```
(defmacro mkvar (x) (list 'quote x))
(defun mkconst (c) c)

(defun mksum (poly0 poly1) (list '+ poly0 poly1))
(defun mksub (poly0 poly1) (list '- poly0 poly1))
(defun mkmult (poly0 poly1) (list '* poly0 poly1))
(defun mkdiv (poly0 poly1) (list '/ poly0 poly1))
(defun mkpow (poly0 poly1) (list 'expt poly0 poly1))

(defun evaluate-expression (expr var val)
  (eval (subst val var expr)))
```
Here's a test run (Steel Bank Common Lisp):
```
* (evaluate-expression (mkpow (mksum (mkvar x) (mkconst 1)) (mkconst 2)) 'x 2)

9
* 
```
Note that in this implementation you still must quote **x** when you supply it to **evaluate-expression**.

There is also the function **sublis** which can be used to substitute values for several variables at once.

If you intend to pursue this kind of programming in lisp you should study macros, the "back-quote" facility and lisp evaluation rules.

---

### Post by Mr.Macdonald on 2008-12-15
thanks I had nothing against macros, I just didn't (and still don't) know when they are executed (compile-time, run-time, inbetween, etc.)

I will learn them soon, after I have functions and that sort down

---

### Post by nvteighen on 2008-12-16
> **Mr.Macdonald said:**
> thanks I had nothing against macros, I just didn't (and still don't) know when they are executed (compile-time, run-time, inbetween, etc.)

I will learn them soon, after I have functions and that sort down
Macros are functions... but that instead of returning data, they return code. There's nothing fundamentally different to the C preprocessor, apart from the very subtle detail (which does all the trick): macros are expanded on demand (i.e. when the eval-apply loop encounters one), not just expanded simultaneously at "compile-time" (à la C).

Anyway, Paul Graham's "On Lisp" says you better use macros when a regular procedure won't do it.

---

### Post by CptPicard on 2008-12-16
> **nvteighen said:**
> macros are expanded on demand (i.e. when the eval-apply loop encounters one), not just expanded simultaneously at "compile-time" (à la C).

Really? :shock:

I thought they're expanded by the reader, prior to compilation...?

---

### Post by Cracauer on 2008-12-16
I re-read the thread for the third time and can't figure out what the OP is trying to do here.

In SBCL Macros are expanded with separate mechanisms by either the compiler or the evaluator (interpreter, which is normally turned off). The reader only gets s-expressions and special chars.

Any kind of evaluation will hit either of these no matter what you do.

---

### Post by wtwood on 2008-12-16
*CptPicard* may be thinking of *reader macros*, implemented via the readtable and the function **set-macro-character**

---

### Post by nvteighen on 2008-12-16
> **Cracauer said:**
> I re-read the thread for the third time and can't figure out what the OP is trying to do here.


I feel better... I though I was the only one... :p

---

### Post by Cracauer on 2008-12-16
Reader macros just invoke the evaluator (which in SBCL is the compiler unless you explicitly turn the interpreter on).

Somehow reader macros rub me the wrong way. I have enough fun (or difficulty) having normal compile-time computing around. I think most cases of use I have seen in the wild is when people tried to help stupid compilers that didn't have real constant (or constant expression) folding.

But alas this works, you can even call reader macros from code that comes in as strings at run time:
```

#.(defun mooh () '(+ 1 41))

(defun foo1 ()
  (eval (read-from-string "#.(mooh)")))

[compile and load above code]
:cl-user 120 K Yes, Master? (foo1)
42

```

---

