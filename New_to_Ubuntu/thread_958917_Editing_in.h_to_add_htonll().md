---
title: "Editing in.h to add htonll()"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by robertm on 2008-10-25
Hi,

I was wondering how I would go about updating and submitting a small change to in.h to the linux community so that everybody could benefit. Is there somewhere I can go or someone I can talk to?

Thankyou for your time.

BTW The edit is just to add a htonll() function (it's a macro actually).

---

### Post by david_lynch on 2008-10-25
> **robertm said:**
> Hi,

I was wondering how I would go about updating and submitting a small change to in.h to the linux community so that everybody could benefit. Is there somewhere I can go or someone I can talk to?

Thankyou for your time.

BTW The edit is just to add a htonll() function (it's a macro actually).

I could have sworn linux has always had htonl() since I wrote some network code in 1993 that used it. But maybe you're meaning something different.

In any case, the linux kernel mailing list is the place to submit kernel patches. I should warn you though, that you'll need thick skin, since there is a lot of "tough love" being shown on lkml.
:lolflag:

---

### Post by robertm on 2008-10-25
No not htonl() -> htonll() two longs, not one.

And thankyou, I'll look for the linux kernel maling list. I just want to suggest it, nothing more.

---

