---
title: "[Lisp] My first function, not working as expected"
date: 2009-07-16
forum: Programming Talk
---

### Post by JordyD on 2009-07-16
I've been fiddling with this thing for an hour now. It looks perfect to me, so I'm looking for help from higher powers.

Here it is:
```
(defun check-prime (num)
  (if (> 2 num)
    (do ((dividend 2 (1+ dividend))
	 (chk-to (/ num 2)))
	((equal (mod num dividend) 0) nil)
      (when (>= chk-to dividend)
	(return t)))
    t))
```

When run, it's supposed to check whether a number is prime or not, returning t if prime and nil if not.
...
It doesn't do that. Instead, it returns t if prime and if not... well, also t.

Anybody know why this happens? I'm hoping that I've made a very simple mistake that I'm just totally missing.

Thanks,
Jordy

---

### Post by cyberslayer on 2009-07-17
The inequalities are backwards.

Try this:
```
(defun check-prime (num)
  (if (< 2 num)
    (do ((dividend 2 (1+ dividend))
	 (chk-to (/ num 2)))
	((equal (mod num dividend) 0) nil)
      (when (<= chk-to dividend)
	(return t)))
    t))
```

---

### Post by JordyD on 2009-07-17
> **cyberslayer said:**
> The inequalities are backwards.

Try this:
```
(defun check-prime (num)
  (if (< 2 num)
    (do ((dividend 2 (1+ dividend))
	 (chk-to (/ num 2)))
	((equal (mod num dividend) 0) nil)
      (when (<= chk-to dividend)
	(return t)))
    t))
```

Thank you! I knew it was something simple.

**EDIT:** I was thinking "num greater than 2" instead of "2 greater than num".

---

