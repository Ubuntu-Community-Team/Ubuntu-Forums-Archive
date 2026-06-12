---
title: "Help with LISP"
date: 2010-11-08
forum: Programming Talk
---

### Post by zaheen on 2010-11-08
I recently started learning LISP and I am having trouble loading files. Every time I try loading any file in SLIME, I get this error message:

The variable CL-USER> is unbound
   [Condition of type UNBOUND-VARIABLE]

I have set my default directories and all but what can I do about this problem? Any advice anyone?

---

### Post by amauk on 2010-11-08
never used lisp (well apart from scripting the gimp)
but it's probably helpful to post a snippet of code so people can see what you're doing

---

### Post by zaheen on 2010-11-08
For example, say I'm trying to load a file on SLIME using this syntax:

CL-USER> (load "foo.cl")

For any file, whatever the code is it just won't load. I keep getting that error message.

---

### Post by Lux Perpetua on 2010-11-09
Don't type the "CL-USER>" part!

---

### Post by zaheen on 2010-11-09
I can't get rid of the CL-USER part. It's always there at each statement in SLIME. And also in the tutorial, they have that written in the statement as well. Here is the link to the page (it's in the part titled Saving Your Work): 

[http://www.gigamonkeys.com/book/lather-rinse-repeat-a-tour-of-the-repl.html](http://www.gigamonkeys.com/book/lather-rinse-repeat-a-tour-of-the-repl.html)

---

### Post by worseisworser on 2010-11-09
Does foo.lisp contain "CL-USER>"? It shouldn't.

---

### Post by zaheen on 2010-11-09
Thanks! That solves the problem. Unfortunately it actually brings up another. When we use the save feature from SLIME, it copies everything, including the CL-USER> portions. Is there any other way to save rather than pressing C-x C-s in the SLIME editor? I am a LISP noob.

---

### Post by worseisworser on 2010-11-09
You shouldn't save the contents of the REPL buffer to a file.

Instead, create a new buffer and file by pressing C-x-f and typing in hello.lisp and pressing enter.

Now the REPL buffer is hidden underneath the hello.lisp buffer just opened (the file was created at the same time) and it would be nice if you could see both the REPL buffer and the hello.lisp buffer at the same time so hit C-x 2 to split your current frame in two, then use the menu at the top (or hit C-x b) to make the top window contain hello.lisp and the bottom window contain your REPL.

Now add code and functions to your hello.lisp buffer and use C-c k to evaluate that entire buffer; use C-x o to navigate between the hello.lisp window at the top and the REPL buffer at the bottom.

You can now use the REPL buffer at the bottom to test the code you are working on in the hello.lisp buffer at the top, and it is the hello.lisp buffer that's interesting and is to be saved (C-x s).

edit: There's a ton of stuff you can do to make your programming easier; I do not like how Emacs/Slime asks whether I want to save the file/buffer in question before evaluating (C-c k) so I've added this amongst several other things to my ~/.emacs file:

```

  (define-key slime-mode-map [f7] (lambda ()
                                    (interactive)
                                    (save-buffer)
                                    (slime-compile-and-load-file)))


```

..and so I just hit F7 to save and eval/compile in one go.

---

### Post by zaheen on 2010-11-09
Thanks, man. Good stuff.

---

### Post by rnerwein on 2010-11-09
> **amauk said:**
> never used lisp (well apart from scripting the gimp)
but it's probably helpful to post a snippet of code so people can see what you're doing
hi
sorry but lisp:  for some problems it is  a very powerful tool. just has a look in the web for "the towers of hanoi". try to solve the problem with 4 lines of code :-)
c++ is a realy good solution - but lisp is a bummer ( i'am a c programmer )
but don't forget a stack overflow can come very fast.
ciao

---

### Post by worseisworser on 2010-11-09
> **rnerwein said:**
> hi
sorry but lisp:  for some problems it is  a very powerful tool. just has a look in the web for "the towers of hanoi". try to solve the problem with 4 lines of code :-)
c++ is a realy good solution - but lisp is a bummer ( i'am a c programmer )
but don't forget a stack overflow can come very fast.
ciao

I'm not sure I understood what was said here.

If you're talking about stack overflow in context of doing recursion you'll want to ensure that your code is tail call optimizable and that the implementation you're using will or can do tail call elimination; you might need to add declarations for speed.

 [http://en.wikipedia.org/wiki/Tail_call](http://en.wikipedia.org/wiki/Tail_call)


In any case this might be interesting to some, but not very related to the topic and question at hand at all.

edit: ..for the record GCC can do similar things for C; it too need to be told to optimize code generation.

---

