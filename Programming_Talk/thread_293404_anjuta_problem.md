---
title: "anjuta problem"
date: 2006-11-05
forum: Programming Talk
---

### Post by tommy1987 on 2006-11-05
I have installed anjuta and gcc.

However, when trying to build my application it says:

WARNING **: Cannot execute command: "make"

If I go to execute it says the target executable does not exist (im guessing because it didnt make it as part of the build?)

Anybody got any ideas?

---

### Post by amo-ej1 on 2006-11-05
have you installed make ? (apt-get install make or even better apt-get install build-essentials)


And if anjuta can't compile your source it's highly unlikely it will be able to execute it ;)

---

### Post by tommy1987 on 2006-11-05
Okay having done that, the error I am now getting is:

make: *** No targets specified and no makefile found. Stop.

---

### Post by tommy1987 on 2006-11-06
Does anybody know what the above error is all about, really can't figure it out?

---

### Post by mvaniersel on 2006-11-06
Have you checked that there is actually a Makefile in the project? If so, what does it look like? What happens if you invoke make from the command line directly?

---

