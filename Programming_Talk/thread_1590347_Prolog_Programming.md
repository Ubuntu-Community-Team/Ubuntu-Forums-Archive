---
title: "Prolog Programming"
date: 2010-10-07
forum: Programming Talk
---

### Post by IUViet on 2010-10-07
I am a new programmer working Prolog. And I try to start with some instructions that have based on building SWI-Prolog.


?- [like].
ERROR: source_sink `like' does not exist
?- [likes].
ERROR: source_sink `likes' does not exist
?- [likes.pl].
ERROR: Syntax error: Operator expected
ERROR: [likes
ERROR: ** here **
ERROR: .pl] . 
?- ['likes.pl'].
ERROR: source_sink `likes.pl' does not exist
?- like/2.
ERROR: toplevel: Undefined procedure: / / 2 (DWIM could not correct goal)
?- ['likes/2'].
ERROR: source_sink `likes/2' does not exist


I have some mistask. could someone help me?

---

### Post by worksofcraft on 2010-10-08
I haven't used Prolog since Borland Prolog running on MS-DOS, and so I don't really understand what you are trying to do there.

However I did install swi-prolog like so:
```

$> sudo apt-get install swi-prolog
Reading package lists... Done
... etcetera

```

Then you can run it...
```

$> swipl
Welcome to SWI-Prolog (Multi-threaded, 64 bits, Version 5.8.0)
Copyright (c) 1990-2009 University of Amsterdam.
SWI-Prolog comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
Please visit **http://www.swi-prolog.org** for details.

For help, use ?- help(Topic). or ?- apropos(Word).

?-

```

You might want to try that url they mention or you can enter a goal like:

```

?- help(help).
help
    Equivalent to help(help/1).

help(+What)
    Show specified part of the manual.  What is one of:

... etcetera

```

---

### Post by IUViet on 2010-10-08
Thanks for your informs, **worksofcraft**.

I attempt to input the data but I alway receives a message error.


[I][HTML][I]gray(elephant).
ERROR: toplevel: [COLOR="Red"]Undefined procedure:[/COLOR] gray/1 (DWIM could not correct goal)[/I]
[/HTML][/I]

 I don't know why?
could you type to guide for me? Thanks

---

### Post by worksofcraft on 2010-10-08
hum... well evidently you are managing to start swi-prolog, so let us make sure you know how to stop it too ;)

Try the following goal:
```

?- halt.

```

OK... then create a new file named 'fac.pl' on your Desktop with following text:
```

fac(0,1).
  
fac(A,B) :-  
           A > 0, 
           C is A-1,
           fac(C,D),
           B is A*D. 

```

Now start swi-prolog again, load the file you created and test it:
```

$ swipl
?- ['fac.pl'].
% fac.pl compiled 0.00 sec, 24 bytes
true.
?- fac(10,What).
What = 3628800 

```
I had a look at the swi-prolog web site and I agree it's no help for someone wanting to get started. However I did a quick google and the first link it came up with seems like [a reasonable tutorial]("http://www.csupomona.edu/~jrfisher/www/prolog_tutorial/1.html")... and if the above worked for youthen you have just done the first example there :lolflag:

---

### Post by IUViet on 2010-10-09
Thank you so much for your answers actively. :guitar:

---

