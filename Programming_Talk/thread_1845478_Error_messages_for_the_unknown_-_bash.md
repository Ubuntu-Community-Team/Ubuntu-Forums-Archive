---
title: "Error messages for the unknown - bash"
date: 2011-09-17
forum: Programming Talk
---

### Post by whatthefunk on 2011-09-17
My bash scripts contain error messages for errors which I think might occur, but sometimes something happens that I did not expect.  I would like to have a generic error message for these times.  How do I write this into my scripts?

---

### Post by hakermania on 2011-09-17
Hm, an idea is to send all stderr to /dev/null and in every command to check the return code. If it's an error code, run a function which contains your generic error message.
It might be a better way.

---

### Post by karlson on 2011-09-17
> **whatthefunk said:**
> My bash scripts contain error messages for errors which I think might occur, but sometimes something happens that I did not expect.  I would like to have a generic error message for these times.  How do I write this into my scripts?

In general it's a *) in the case statement.  If you are using ifs then it's the last else case.

---

### Post by whatthefunk on 2011-09-17
> **karlson said:**
> In general it's a *) in the case statement.  If you are using ifs then it's the last else case.

Perfect.  I dont know why I didnt think of this before...  Thanks for replying, both of you.

---

