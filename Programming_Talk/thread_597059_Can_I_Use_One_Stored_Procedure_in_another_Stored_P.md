---
title: "Can I Use One Stored Procedure in another Stored Procedure?"
date: 2007-10-30
forum: Programming Talk
---

### Post by David Albert on 2007-10-30
Hi
Can I use one stored procedure in another stored procedure, if yes
please tell my the syntex?

thanks

---

### Post by runningwithscissors on 2007-10-30
Do you mean call one stored procedure from another or define one stored procedure inside another?

The former is definitely possible. The latter isn't.

To call a stored procedure just use
```
exec @return_value = stored_proc arg1, arg2
```

---

