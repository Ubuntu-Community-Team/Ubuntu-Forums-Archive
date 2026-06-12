---
title: "bash question"
date: 2012-01-14
forum: Programming Talk
---

### Post by Diametric on 2012-01-14
Hello,

Regarding positional parameters, is it fair to say that pos params $* and $@ are created "on the fly" and only exist when executing a script with arguments?

Thanks!

---

### Post by Telengard C64 on 2012-01-14
```
test$ echo $*

test$ set one two three
test$ echo $*
one two three
test$
```

Nope.

---

### Post by Diametric on 2012-01-14
Awesome!  Thanks for the quick reply.

---

