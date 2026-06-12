---
title: "Problem with clisp"
date: 2008-09-02
forum: Programming Talk
---

### Post by bobbob1016 on 2008-09-02
I have a program due in a class where I can pick whatever language I want to write it in.  It has a lot recursion, so I decided to brush up my lisp skills and use lisp.  I installed clisp via apt, and wrote the code below to make sure everything was working, and to get a bare skeleton:

(defun birthday ()
	(print 'HelloWorld)
)

Simple enough, but after loading and running it in clisp it I get the output:

HelloWorld
HelloWorld
Blank line and 2 HelloWorlds.  Can anyone who knows clisp tell me if this is a clisp error or something?  Or is it my defun by any chance?

---

### Post by CptPicard on 2008-09-02
Can't recall how print of Common Lisp works, but it seems to me like you're seeing both the side-effect of printing *and* the value of the function which is the value of the (print) which I suppose is the value that was printed...

---

### Post by WW on 2008-09-02
> **bobbob1016 said:**
> 
(defun birthday ()
	(print 'HelloWorld)
)

Simple enough, but after loading and running it in clisp it I get the output:

HelloWorld
HelloWorld
Blank line and 2 HelloWorlds.  Can anyone who knows clisp tell me if this is a clisp error or something?  Or is it my defun by any chance?
That is not an error.  Your function prints HelloWorld, and it also returns 'HelloWorld.  The lisp interpreter works in a "read-eval-print" loop, and when you call (birthday), it evaluates to 'HelloWorld, so that is printed.  (I'm not sure why the print function prints the extra blank line; maybe a real clisp expert can explain that.)  You could use the format function instead of print.

E.g.
```

[1]> (defun birthday () (print 'HelloWorld) )
birthday
[2]> (birthday)

HelloWorld 
HelloWorld
[3]> (defun hw () (format t "Hello, world!") )
hw
[4]> (hw)
Hello, world!
nil
[5]> 

```
In input [2], lisp calls birthday, which prints HelloWorld and returns the value 'HelloWorld. The lisp interpreter prints this value, so HelloWorld is printed twice.

In [3], I define a function that uses format instead of print. The format function returns nil, so that is what the lisp interpreter prints after "Hello, world!" is printed when hw is called in [4].

---

### Post by stevescripts on 2008-09-02
You may also find this helpful:

Practical Common Lisp

[http://gigamonkeys.com/book/](http://gigamonkeys.com/book/)

(WW certainly beat me to any sort of explanation... ;) )

Steve

---

### Post by bobbob1016 on 2008-09-02
> **WW said:**
> That is not an error.  Your function prints HelloWorld, and it also returns 'HelloWorld.  The lisp interpreter works in a "read-eval-print" loop, and when you call (birthday), it evaluates to 'HelloWorld, so that is printed.  (I'm not sure why the print function prints the extra blank line; maybe a real clisp expert can explain that.)  You could use the format function instead of print.

E.g.
```

[1]> (defun birthday () (print 'HelloWorld) )
birthday
[2]> (birthday)

HelloWorld 
HelloWorld
[3]> (defun hw () (format t "Hello, world!") )
hw
[4]> (hw)
Hello, world!
nil
[5]> 

```
In input [2], lisp calls birthday, which prints HelloWorld and returns the value 'HelloWorld. The lisp interpreter prints this value, so HelloWorld is printed twice.

In [3], I define a function that uses format instead of print. The format function returns nil, so that is what the lisp interpreter prints after "Hello, world!" is printed when hw is called in [4].

I didn't think about that.  It makes perfect sense though, thanks.  Thanks all.

---

