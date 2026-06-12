---
title: "Cancel jobs."
date: 2008-05-29
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-29
Hi everyone how can i cancel printing jobs?
Hope you can help.:)

---

### Post by unutbu on 2008-05-29
```
17:14:48 snack@tack:~% lpq
Gutenberg is ready and printing
Rank    Owner   Job     File(s)                         Total Size
active  snack   **113**     Viewsonic-Rebate-2008-04-14.ps  78848 bytes
17:14:50 snack@tack:~% lprm **113**
17:14:57 snack@tack:~% lpq
Gutenberg is ready
no entries

```

lpq shows you the printer's job queue.
Find the job number (e.g. 113) and then you can cancel the job by typing

```
lprm <job number>
```

---

### Post by cristo-father on 2008-05-29
> **unutbu said:**
> ```
17:14:48 snack@tack:~% lpq
Gutenberg is ready and printing
Rank    Owner   Job     File(s)                         Total Size
active  snack   **113**     Viewsonic-Rebate-2008-04-14.ps  78848 bytes
17:14:50 snack@tack:~% lprm **113**
17:14:57 snack@tack:~% lpq
Gutenberg is ready
no entries

```

lpq shows you the printer's job queue.
Find the job number (e.g. 113) and then you can cancel the job by typing

```
lprm <job number>
```

It says there are no entries, but in gnome-cups-manager it says there are 2. And i cannot print

---

### Post by kwacka on 2008-05-29
In a browser enter the address 127.0.0.1:631 to access the cups 'web interface' manager.

---

### Post by cristo-father on 2008-05-29
> **kwacka said:**
> In a browser enter the address 127.0.0.1:631 to access the cups 'web interface' manager.

The site sometimes requests a username and password is it supposed to be my 
ubuntu's username and pass?

---

### Post by kwacka on 2008-05-29
yes

---

### Post by cristo-father on 2008-05-29
What should i do from here?

---

