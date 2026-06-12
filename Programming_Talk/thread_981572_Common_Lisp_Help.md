---
title: "Common Lisp Help"
date: 2008-11-13
forum: Programming Talk
---

### Post by CommonUser on 2008-11-13
I have a few questions about lisp. First, is there any way I can save a file as "sometext.lisp" and go to terminal type in a command to interpret whatever is written in that text file? As of now I am typing out everything each time. 

Second, I'm trying to work with loops, if statements and variables but I can't seem to get it working.

```

(defvar *x* 0)
(defun foo(element list)
	(loop for i from 0 to (length list)
		do (if (= element (nth i list) (incf *x*) nil)
	)
)

```

Thanks for your help.

---

### Post by CptPicard on 2008-11-13
Well, from the REPL, function "load" does the trick. However, I have a feeling you're going about this completely the wrong way -- you do not code in lisp the way you code in other languages where you run the source file through the compiler/interpreter. Instead, you work "inside" the Lisp environment and build your code in there piece by piece.

Get something like Emacs and [SLIME]("http://common-lisp.net/project/slime/") working, or alternatively the Eclipse cusp plugin... those are the "right way" to go about setting up a Lisp development environment.

---

### Post by CommonUser on 2008-11-13
Thanks, I'll give it a try. 

Any suggestions as to how I can get my piece of lisp code working?

---

