---
title: "reentrant code"
date: 2010-05-09
forum: Programming Talk
---

### Post by cybo on 2010-05-09
what does it mean for code to be reentrant? it is not a homework question, i'm just reading a book and it mentions reentrant code but doesn't define it. i would appreciate a "dummy" explanation, i.e. as if you are talking to a child.

thanks.

---

### Post by MadCow108 on 2010-05-09
> A computer program or routine is described as reentrant if it can be safely called again before its previous invocation has been completed (i.e it can be safely executed concurrently).
[http://en.wikipedia.org/wiki/Reentrant_(subroutine](http://en.wikipedia.org/wiki/Reentrant_(subroutine))

---

### Post by soltanis on 2010-05-09
Code which does not assume that at any one time, it is the only instance of itself that is running is re-entrant. This means that if it uses any variables to track state, it doesn't use them in a global context, or if it does, it uses some kind of locking mechanism to ensure that no two instances of the procedure are modifying the same data at once.

---

### Post by MadCow108 on 2010-05-09
not quite, a reentrant function must not employ locking as this would block other calls to the function.

if you use locking to archive concurrency you only have a threadsafe function which is less than reentrant.
A reentrant function is threadsafe, not necessarily the other way round.

---

### Post by cybo on 2010-05-09
thanks everyone. i think i got it.

---

### Post by slavik on 2010-05-09
EDIT: just read the wikipedia article, it has code samples, too.

---

