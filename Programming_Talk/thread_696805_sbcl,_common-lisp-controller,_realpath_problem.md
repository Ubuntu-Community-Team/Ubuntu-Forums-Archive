---
title: "sbcl, common-lisp-controller, realpath problem"
date: 2008-02-14
forum: Programming Talk
---

### Post by cujo on 2008-02-14
I am trying to install sbcl on a 6.06.2LTS machine (dapper?), and I've run into a road block.

SBCL requires common-lisp-controller which won't install because it requires realpath.  Realpath doesn't seem to exist.

```
Package realpath is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

How can I get around this?

---

### Post by LaRoza on 2008-02-14
You can try enabling all repositories (Applications->Add/Remove and select "All Available Applications")

Moving to Programming Talk, where you might get a better answer.

(I happen to know there is an SBCL user that is there)

---

### Post by cujo on 2008-02-14
That did it.  Thanks.

---

### Post by LaRoza on 2008-02-14
> **cujo said:**
> That did it.  Thanks.

It worked? I guess SWAGs are the way to go.

---

### Post by cujo on 2008-02-14
One of the main repos wasn't enabled.  Go figure.

---

