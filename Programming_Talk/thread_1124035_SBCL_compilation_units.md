---
title: "SBCL compilation units"
date: 2009-04-12
forum: Programming Talk
---

### Post by soltanis on 2009-04-12
So I have a question with the SBCL Common Lisp implementation. Why is it that every time I use the REPL and make a mistake, for example,

```

* (apply #'foo (1 2))

```

The error is

```

; in: LAMBDA NIL
;     (1 2)
; 
; caught ERROR:
;   illegal function call
; 
; compilation unit finished
;   caught 1 ERROR condition

debugger invoked on a SB-INT:COMPILED-PROGRAM-ERROR in thread #<THREAD "initial thread" RUNNING {A8345C9}>:
  Execution of a form compiled with errors.
Form:
  (1 2)
Compile-time error:
  illegal function call

```

What is LAMBDA NIL? Does SBCL wrap all its compilation units into a lambda function that takes no arguments, and then execute it?

---

### Post by CptPicard on 2009-04-13
Observe this:

```

* (1 2)
; in: LAMBDA NIL
;     (1 2)
;
; caught ERROR:
;   illegal function call
;
; compilation unit finished
;   caught 1 ERROR condition
...


((LAMBDA ()))

```

Here we're trying to put into function position something that is not a symbol that has a valid function cell. Actually 1 is a literal, not even a symbol that would cause an "unbound variable" or "undefined function" error. So essentially what the reader does is that it produces, seemingly a (lambda ()) for the function, which evaluates to nil. The result of this lambda is probably the LAMBDA NIL you're seeing.

Just a quick analysis, I may be wrong/inaccurate. :)

---

### Post by soltanis on 2009-04-14
Are we the only two on this forum who bother with CL or what?

---

