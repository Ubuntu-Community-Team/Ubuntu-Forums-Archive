---
title: "Slime/Emacs Compiling Failure"
date: 2009-03-09
forum: Programming Talk
---

### Post by tdashroy on 2009-03-09
Okay so I am pretty new to both emacs and lisp, so if I am doing something wrong or stupid please point it out. Here it goes...

Recently I have been learning lisp for a class and I heard/read that emacs/slime was the best place to program and compile in lisp. Whenever I load slime (through M-x slime) and then load the file with my .lisp functions in it (through C-x C-f 'filename'), and then compile and load my .lisp file (by C-c C-k), everything works fine. Then I'll do a couple of test commands in the slime window (I think called the REPL) and everything will still be fine. But, then when I go back and write a couple more lines of code or edit something and compile and load again it will do one of two things:
1. it will work just as it did before and everything will be fine.
2. it will tell me that it is compiling and loading, but will then bring up the command prompt thing that says <CL-USER>, as if it were done. But, at the bottom it still says compiling and loading and never finishes. Then I will try to type a command, and it will just go to a newline when I hit return. After this I try to open up another slime, in which case it asks me if I would like to open another slime, since one is still running. I then kill the buffers related to slime and try again. Eventually, the same thing happens. All I can say is...please help me. 

Also, as a side note, whenever I do this opening of a separate slime after killing the first one, the cmucl process is not killed and another one is opened. Thanks.

-Troy

---

### Post by Cracauer on 2009-03-09
Switch to the *inferior-lisp* buffer and tell us whether that has anything that looks related.

Is your Lisp alive at all?

---

### Post by tdashroy on 2009-03-09
I do not have an *inferior-lisp* buffer, is this a problem? And could you clarify what you mean by is your Lisp alive? At the REPL I am able to type stuff, but when I hit enter, it  doesn't execute the commands, but rather just goes to a new line.

The buffers I have are:

*slime-repl cmucl* * (where I type commands)
hw6.lisp (file with source code)
*GNU Emacs* % (Emacs startup page)
*scratch* 
*Messages* *

I'm not really quite sure what the last two are for, but the last one, *Messages* *, has the following in it:

```
(tojava tree) [2 times]
 [2 times]
(concatenate output-type-spec &rest sequences) [9 times]
(and &rest forms) [13 times]

byte-code: End of buffer
(if &rest stuff) [4 times]
 [12 times]
Compiling /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp...
Compilation finished: 0 errors  0 warnings  0 notes [0.14 secs]
Highlighting notes...
Compilation finished: 0 errors  0 warnings  0 notes [0.14 secs]
(concatenate output-type-spec &rest sequences) [5 times]

(defun name lambda-list &parse-body (body decls doc)) [2 times]
 [2 times]
Save file /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp? (y or n) 
Wrote /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp
Compiling /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp...
Compilation finished: 0 errors  0 warnings  0 notes [0.13 secs]
Highlighting notes...
Compilation finished: 0 errors  0 warnings  0 notes [0.13 secs]

History item: 0
(tojava tree) [15 times]
(sin number) [6 times]
(- number &rest more-numbers) [7 times]
(sin number) [2 times]
(+ &rest args) [2 times]

History item: 0
(tojava tree) [15 times]
(sin number) [2 times]
(- number &rest more-numbers) [6 times]

byte-code: End of buffer
(concatenate output-type-spec &rest sequences) [8 times]
(defun name lambda-list &parse-body (body decls doc)) [7 times]
byte-code: Beginning of buffer
(defun name lambda-list &parse-body (body decls doc))
byte-code: Beginning of buffer
(defun name lambda-list &parse-body (body decls doc))
byte-code: Beginning of buffer
(defun name lambda-list &parse-body (body decls doc))
byte-code: Beginning of buffer
(defun name lambda-list &parse-body (body decls doc))
byte-code: Beginning of buffer
(defun name lambda-list &parse-body (body decls doc))
byte-code: Beginning of buffer
(defun name lambda-list &parse-body (body decls doc))
(if &rest stuff) [22 times]
byte-code: Beginning of buffer
(if &rest stuff)
byte-code: Beginning of buffer
(if &rest stuff) [18 times]
 [2 times]
(if &rest stuff) [9 times]
byte-code: Beginning of buffer
(if &rest stuff)
byte-code: Beginning of buffer
(if &rest stuff)
byte-code: Beginning of buffer
(if &rest stuff) [2 times]
 [3 times]
(vars tree) [9 times]
(+ &rest args) [8 times]
(- number &rest more-numbers) [12 times]
(+ &rest args)
(vars tree) [2 times]
 [2 times]
History item: 0
(vars tree) [2 times]
(+ &rest args) [3 times]
(vars tree) [9 times]
(+ &rest args) [7 times]

History item: 0
call-interactively: End of buffer
(vars tree) [22 times]
backward-delete-char-untabify: Text is read-only
(vars tree) [2 times]
(remove-duplicates sequence &key (test #'eql) test-not (start 0) from-end end key) [3 times]
(let &rest stuff) [29 times]
Save file /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp? (y or n) 
Wrote /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp
Compiling /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp...
[Commencing GC with 14.1 MB in use.]
History item: 0
backward-delete-char-untabify: Text is read-only [2 times]
Undo! [23 times]
Save file /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp? (y or n) 
Wrote /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp
Compiling /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp...
byte-code: Beginning of buffer [9 times]
byte-code: End of buffer [6 times]
byte-code: Beginning of buffer [9 times]
Mark set
byte-code: Beginning of buffer [10 times]
byte-code: End of buffer [2 times]
byte-code: Beginning of buffer [21 times]
byte-code: Beginning of buffer
```

and here is what I see at the REPL:

```
; SLIME 2008-02-23
;;;; Compile file /media/school_drive/College/Spring09/cs315/proj ...

; Python version 1.1, VM version Intel x86 on 09 MAR 09 12:07:30 pm.
; Compiling: /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp 09 MAR 09 12:07:30 pm


; /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.x86f written.
; Compilation finished in 0:00:01.
; Loading #p"/media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.x86f".
CL-USER> (ptojava '((sin x)))
; Evaluation aborted.
CL-USER> (ptojava '(sin x))
; Evaluation aborted.
CL-USER> (tojava '(sin x))
"Math.SIN(X);"
CL-USER> (tojava '(+ (sin x) (- 7 (- 6))))
"Math.SIN(X)+(7-(-6));"
;;;; Compile file /media/school_drive/College/Spring09/cs315/proj ...

; Python version 1.1, VM version Intel x86 on 09 MAR 09 12:10:09 pm.
; Compiling: /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp 09 MAR 09 12:07:30 pm


; /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.x86f written.
; Compilation finished in 0:00:00.
; Loading #p"/media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.x86f".
;;;; Compile file /media/school_drive/College/Spring09/cs315/proj ...

; Python version 1.1, VM version Intel x86 on 09 MAR 09 12:10:27 pm.
; Compiling: /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.lisp 09 MAR 09 12:10:27 pm


; /media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.x86f written.
; Compilation finished in 0:00:01.
; Loading #p"/media/school_drive/College/Spring09/cs315/proj6/lisp_files/hw6.x86f".
CL-USER> (tojava '(+ (sin (- 7)) (- 7 (- 6))))
"Math.SIN((-7))+(7-(-6));"
CL-USER> (tojava '(+ (sin (- 7 6)) (- 7 (- 6))))
"Math.SIN(7-6)+(7-(-6));"
CL-USER> (vars '(+ (- x y)))
(NIL X Y)
CL-USER> (vars '(+ (- x y) y))
(X Y)
;;;; Compile file /media/school_drive/College/Spring09/cs315/proj ...

; Python version 1.1, VM version Intel x86 on 09 MAR 09 12:14:40 pm.
CL-USER> 
;;;; Compile file /media/school_drive/College/Spring09/cs315/proj ...

```

As you can see, the last two times I tried to compile, it never finished, which is when it freezes up. If you need more information please let me know.

---

### Post by Cracauer on 2009-03-09
I haven't used CMUCL under SLIME.

I was under the impression that all Lisps use an *inferior-lisp* buffer for the real Lisp. Maybe CMUCL doesn't due to not using threads the same way? Dunno.

---

### Post by tdashroy on 2009-03-09
That's alright, I'll try it with another lisp and see if the same thing happens, thanks.

---

