---
title: "emacs question, sick of googling"
date: 2009-08-22
forum: Programming Talk
---

### Post by mehaga on 2009-08-22
Hi,

A very basic question: how do I make emacs find and open a file?
Let's say I'm looking for a file named Whatever.java, and I know it's 
somewhere in my home folder. I also know that there is only 1 file with 
that name in that folder and all sub-folders.
I found a suggestion to pass this to find-file:
~/-rWhatever.java
but that doesn't work.

Help! :'(

---

### Post by vambo on 2009-08-22
By an open file. Do you mean it was opened from emacs?
If so, then 
C-x C-b will list all open buffers and their associated files names.
To find any old file I just use the shell find command.

---

### Post by mehaga on 2009-08-22
First, I never used emacs before, but I am starting to like it.
I think I meant using C-x C-f. That should start Find-file function, IIRC.
That function can get a parameter with wildcards, I believe. So, I should be able to open a file without knowing the exact path to it, only it's name.
Maybe it can't be done...

---

### Post by vambo on 2009-08-22
> **vekaz said:**
> First, I never used emacs before, but I am starting to like it.
I think I meant using C-x C-f. That should start Find-file function, IIRC.
That function can get a parameter with wildcards, I believe. So, I should be able to open a file without knowing the exact path to it, only it's name.
Maybe it can't be done...

Don't think you can do it that way out the box (could be wrong).
The following should work

```
M-!   # Execute a shell command from mini-buffer
```

At the Shell Command prompt in the mini-buffer

```
find ~/ -iname *.java
```

Will give you a list of all .java files under your home dir

---

### Post by mehaga on 2009-08-22
With find ~/ -iname *.java i get: 
"find: paths must precede expression: kod.java"

Although, the command works as expected in a regular shell, ofc.

---

### Post by unutbu on 2009-08-22
Is the file already opened in emacs? If so, vambo's first suggestion C-x C-b will work.

If the file is not already opened in emacs, and it is buried in some subdirectory, then vambo's second suggestion will work in an emacs shell:

Type M-x shell
Then type
```

find ~/ -iname "*.java"
```

You'll be able to browse through the output more easily than after M-x !

---

### Post by mehaga on 2009-08-22
Your 2nd suggestion will have to do, as the first one works only if I tell emacs the path to the dir containing the file, it won't find the file in sub-dirs. Thanks.

---

### Post by mehaga on 2009-08-22
Even if I start shell (M-x shell), I get the same error:
find: paths must precede expression

---

### Post by unutbu on 2009-08-22
My mistake. You need quotation marks around "*.java":
```

find ~/ -iname "*.java"
```

By the way, once you get the output of the "find" command in the emacs-shell (or any emacs buffer for that matter), you can move the cursor anywhere in the filename, and press C-x C-f to open it.

---

### Post by mehaga on 2009-08-22
> **unutbu said:**
> My mistake. You need quotation marks around "*.java":
```

find ~/ -iname "*.java"
```

By the way, once you get the output of the "find" command in the emacs-shell (or any emacs buffer for that matter), you can move the cursor anywhere in the filename, and press C-x C-f to open it.

Yes! Thanks a lot :)

Btw, [this]("http://www.webweavertech.com/ovidiu/emacs/index.html") is what I was looking for, I just need to find out how to install this extension :)

---

### Post by mehaga on 2009-08-22
Just to report back... The extension I linked to in last post works perfectly. C-x M-f, file name, dir...

---

### Post by unutbu on 2009-08-22
Yeah, that is pretty useful. Thanks! :)

---

### Post by mehaga on 2009-08-22
> **unutbu said:**
> Yeah, that is pretty useful. Thanks! :)

np :)

---

### Post by unutbu on 2009-08-22
Actually, I'm not sure about find-recursive.el. When the file is buried just two sub-directories deep, I seem to run into a 
```

Lisp nesting exceeds `max-lisp-eval-depth'

```
error. Does this happen to you?

---

### Post by mehaga on 2009-08-22
No sir, it just works...

---

### Post by unutbu on 2009-08-22
Ah well, I increased max-lisp-eval-depth to 5000 and the problem went away.... :)

---

