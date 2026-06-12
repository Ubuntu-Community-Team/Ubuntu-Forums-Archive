---
title: "Possible exit status return codes"
date: 2007-08-08
forum: Programming Talk
---

### Post by jnorthr on 2007-08-08
Is there a document showing all the possible exit status in ubuntu ? Was hoping to find a description for them.

If CUPS dies with exit status 22, how can we determine the reason for exit 22 other than parse the code ?

---

### Post by LaRoza on 2007-08-08
> **jnorthr said:**
> Is there a document showing all the possible exit status in ubuntu ? Was hoping to find a description for them.

It would vary among the applications, you will need to see the documentation of the app in question.

0, usually means success though.

---

### Post by slavik on 2007-08-09
actually, I believe exit codes are defined in stdlib.h ... doesn't mean a program uses them though :)

nvm, it declares only success and failure, read the source, luke :P

---

### Post by jnorthr on 2007-08-12
Ah, yes master. The source be with you.

---

### Post by Mr. C. on 2007-08-14
In traditional Unix, you would find these values in /usr/inlcude/errno.h.  In linux, the actual values are in /usr/include/asm/errno.h.  22 is the standard EINVAL, or invalid argument.  Most well-written programs will use standard error return values when possible, or when it makes sense.  System calls return these standard values also.

MrC

---

