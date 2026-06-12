---
title: "tualatrix-ppa Duplicate?"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by tg3793 on 2012-08-22
I just installed **Y PPA Manager** and it's telling me that "tualatrix-ppa-natty.list" is a duplicate of "tualatrix-ppa-maverick.list" and it wants to remove the natty one, is that correct?

Two questions:
#1 is this really a duplicate that would be causing problems.
#2 Shouldn't I be removing the Maverick one instead?

thanks.

---

### Post by cortman on 2012-08-22
> **tg3793 said:**
> I just installed **Y PPA Manager** and it's telling me that "tualatrix-ppa-natty.list" is a duplicate of "tualatrix-ppa-maverick.list" and it wants to remove the natty one, is that correct?

Two questions:
#1 is this really a duplicate that would be causing problems.
#2 Shouldn't I be removing the Maverick one instead?

thanks.

1. Yes, it's a duplicate.
2. If (as your info suggests) you are running Natty, then yes you should remove the maverick repository.

If YPPA Manager just won't let you, you can go to /etc/apt/sources.list.d/ and manually delete the Maverick file.

---

