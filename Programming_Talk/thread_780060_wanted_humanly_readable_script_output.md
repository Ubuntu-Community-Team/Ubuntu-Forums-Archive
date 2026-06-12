---
title: "wanted: humanly readable script output"
date: 2008-05-03
forum: Programming Talk
---

### Post by unutbu on 2008-05-03
Warning: I'm not talking about bash scripts. I'm talking about the unix command 'script'.

Sometimes I want a transcript of my terminal sessions. My terminal buffer fills up too quickly, and copy/pasting from the terminal into an emacs buffer is also a hassle. 

The unix command 'script' almost does what I want

```
script
<ls, man, grep, blah blah>
exit

```

script writes data to a file called typescript by default. But typescript has lots of control characters in it. 

```
less -r typescript
```

almost displays what I want, but I want that in an ascii file. I don't want to have to view the typescript through less.

How can I process the typescript file so I get a humanly readable ascii file?

---

### Post by omrsafetyo on 2008-05-03
cat seems to display without the control characters - but depending on how long it is that may not work.

You can't even redrect cat to another file, because it reproduces the original file exactly.  I tried a combination of things, such as using cat to redirect to awk {print}, which had the same result...

---

### Post by unutbu on 2008-05-04
Thanks very much for reply. I've since found out 
that the lack of a logging feature in gnome-terminal was posted as "bug" (see [http://bugzilla.gnome.org/show_bug.cgi?id=24457](http://bugzilla.gnome.org/show_bug.cgi?id=24457)) in 2000-09, and as of 2007-12 all there is is a patch which doesn't handle backspaces properly.

Somehow gnome-terminal knows how to display the stuff nicely on the screen, but saving it to a file seems oddly difficult.

---

### Post by RIchard James13 on 2008-05-04
The codes you see are terminal control codes. They are converted by script into ASCII by writing them like ^H. If you load the typescript file into an editor you will see the control codes. The only way to get rid of them is to have the typescript file edited afterwards. You can edit by hand or you can make a program that does it for you. Most of the codes can simply be discarded as they mean nothing however some codes like delete ^H and Backspace ^H^[[K need to be handled specially because they alter the contents of the buffer.

---

### Post by unutbu on 2008-05-04
Would you happen to know the right perl module to use to handle all the terminal codes?

---

### Post by stroyan on 2008-05-04
Piping a typescript file through "col -b" will take care of the backspace
and <ctrl>-m characters.  But it will only discard escape characters,
leaving the rest of escape sequences in the file.  You can eliminate
almost all escape sequences from a typescript file by suppressing them
when you are capturing them. ```
TERM=dumb script
```
will tell the shell and other commands that the terminal doesn't know any escape sequences.
(But some commands that you want to run may complain about your dumb terminal.)

---

