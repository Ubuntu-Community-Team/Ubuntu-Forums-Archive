---
title: "Problem starting Hunchentoot in Gutsy"
date: 2007-10-30
forum: Programming Talk
---

### Post by filippos on 2007-10-30
Greetings,

first a small disclaimer: I am not quite certain that I am posting at the proper category. Still I hope I got it right.

OK, down to the case: I have an development environment consisting of:

Gutsy
emacs22-nox
slime
SBCL

Note: All of the above are installed through the Ubuntu repositories.

I also installed hunchentoot (using asdf-install - meaning NOT supported by the Ubuntu Community).  So in order for me to start using and developing on the server I first have to start it... (duh)

```

CL-USER> (require 'hunchentoot)
CL-USER> (defvar *server* (hunchentoot:start-server :port 8080))
```

and true enough after these 3 lines of code if I type *server* in the REPL I will get something like that:

```
#<HUNCHENTOOT::SERVER {AAD16C9}>
```

meaning that the server is up and running. No errors, no warnings.

BUT, when I go to [http://localhost:8080](http://localhost:8080) I get nothing... 
Actually not nothing, I get a "The connection was reset" message by Firefox.

So my question boils down to these:

[LIST=1]
[*]As a regular user can I start a service using an unprivileged port (> 1023)? If not what changes should I make and where?
[*]The above is what I believe is the problem, still if you have other suggestions  please share with me.
[/LIST]

Thank you for your time.

---

### Post by filippos on 2007-10-31
OK, I was being just plain stupid :)

Late in the night did it hit me: disable exception handling by the Hunchentoot and pass it along the Lisp image. (It has a settable parameter to do so, don't recall the name now). 

The result was that I found an unbound symbol that prompt me to download the flexi-streams package (again with asdf-install).

Oh the horror, to actually talk nonsense about unprivileged ports and the such (which eventually I wrote a small EchoServer in Java to check what happens, and you are free to start services from 1024 and up as a regular user... duh)

Well then back to Lisp dev/ing.

---

