---
title: "[SOLVED] pipes vs backticks?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by PGScooter on 2008-08-11
Hi,

I cannot seem to accomplish the following code with pipes (by pipe, I refer to using a '|'

this code works:
```

sha256sum `ls *.dta`

```

but why doesn't this code work:
```

ls *.dta | sha256sum

```

thanks

---

### Post by bpowell2005 on 2008-08-11
> **PGScooter said:**
> Hi,

I cannot seem to accomplish the following code with pipes (by pipe, I refer to using a '|'

this code works:
```

sha256sum `ls *.dta`

```

but why doesn't this code work:
```

ls *.dta | sha256sum

```

thanks

I think backticks are the correct way to do this code. The pipe just takes the output of Command a and pipes it into the input of Command B...But not all programs are set up to receive input like that.

With the backticks, you're calling sha256sum with the result of the operation in the backtick. It's strange, but I think that's why this is happening.

---

### Post by sdennie on 2008-08-11
Those are two different things.  The first means, "Check the sha256sum of each .dta file", the second means, "Check the sha256sum of the output of an ls command".  In the latter case, it's not treating the output of the "ls" as an argument but as the actual data to check.

---

### Post by PGScooter on 2008-08-12
ah, I see. Thank you vor and bpowell; that explanation makes sense.

---

### Post by bpowell2005 on 2008-08-12
> **vor said:**
> Those are two different things.  The first means, "Check the sha256sum of each .dta file", the second means, "Check the sha256sum of the output of an ls command".  In the latter case, it's not treating the output of the "ls" as an argument but as the actual data to check.

Much better said! Thanks!

---

