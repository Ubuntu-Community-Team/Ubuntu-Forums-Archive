---
title: "how to use Plotutils"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by allynm on 2013-02-26
Hello everyone,

I have been trying to run a PLOTUTILS sample program as listed on pages 97 and 98 of the PLOTUTILS man.  These are sample programs written in C.  I am using Plotutils-2.6.

The first program draws a complex helical shape.  I am able to compile using 
  gcc -c plotter.c

and I use the the following swithces for the link step:
  -lplot -lXaw -lXmu -lXt -lSM -lICE -lXext -lpng -lz -lm

The program links without a hickup, loads, and runs.  But, instead of seeing a visual image on the term window I see instead a very long series of integers plus some English writing.  It looks as if the output is coming from an intermediate file and should instead be headed off to an X11 window--which doesn't in fact appear.

Perhaps someone with Plotutils experience could suggest a solution?

Regards,
Mark Allyn aka allynm

---

### Post by steeldriver on 2013-02-26
I *don't* have plotutils experience, but the example as-is appears to write postscript output to stdout:

```
/* create a Postscript Plotter that writes to standard output */
if ((plotter = pl_newpl_r ("ps", stdin, stdout, stderr,
plotter_params)) == NULL)

```You could try redirecting your program output to a .ps file and then opening with a postscript viewer e.g. gsview

There appear to be instructions on the following couple of pages for modifying the arguments to[FONT=Courier New] pl_newpl_r [/FONT]for other types of output - including popping up an X window:

> If "X" were specified as the first argument of pl_newpl_r, the curve would be drawn
in a popped-up X window, and the output stream argument would be ignored.


---

### Post by allynm on 2013-02-26
Hello Steeldriver,

Very good idea, indeed: redirecting worked.  I was going to try your suggestion about using "X" param next.  I'll let you know.  For the moment I'll keep this thread alive.

Good hearing from you once more.  

Regards,
Mark

---

### Post by allynm on 2013-02-26
Hello again, Steeldriver,

I used the "X" parameter and indeed it opened an X window with a very beautiful and complex pattern--a "C" in fact with many fine filaments forming the overall character.

But, when I clicked on the "close box" the window closed, but an error message (I assume from X windows program) as follows:

> mark@mark-HP-ProBook-4525s:~$ XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 84 requests (84 known processed) with 0 events remaining.
^C
AS you can see from above I had to kill the process with Ctrl-C.  Any idea what might be wrong?

Mark

---

### Post by allynm on 2013-02-26
Steeldriver-

The X term problem seems peculiar to the Xterm app.  When I use "gif" as the parm rather than "X" and redirect output to plotter.gif I can read the resulting gif file with EOG app and all is well and no error messages show up on closing the gif file.

Hmmm.

Mark

---

### Post by steeldriver on 2013-02-26
I wouldn't worry too much about that error Mark - it probably just means the window (or the socket it's attached to) isn't closed gracefully

---

### Post by allynm on 2013-02-26
Hi Steeldriver,

In that case, I will mark this thread as closed.

Thanks,
Mark

---

