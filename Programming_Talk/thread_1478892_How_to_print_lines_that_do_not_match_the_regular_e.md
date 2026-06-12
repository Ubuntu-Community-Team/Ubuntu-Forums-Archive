---
title: "How to print lines that do not match the regular expression"
date: 2010-05-10
forum: Programming Talk
---

### Post by denarced on 2010-05-10
Essentially I'm trying to do the following:
```
find . -type f | grep -vi -e 'xml'
```
by using the find-command only.
Is this possible ?

As always, help is appreciated :)

---

### Post by stevanbt on 2010-05-10
Hi,
Do you get what you want from 

```
find . -type f -exec grep -vi -e 'xml' {} \;
```

Thanks, Steve.

---

### Post by thebigob on 2010-05-10
find . -type f | xargs grep -vi -e 'xml'

---

### Post by denarced on 2010-05-25
> **stevanbt said:**
> Hi,
Do you get what you want from 

```
find . -type f -exec grep -vi -e 'xml' {} \;
```

Thanks, Steve.

This would work, naturally.
I was looking for something that'd do the job with just -iregex or -regex.

---

### Post by trent.josephsen on 2010-05-25
> **denarced said:**
> This would work, naturally.
I was looking for something that'd do the job with just -iregex or -regex.

Use ! to negate a test, per find(1).

```
find . -type f \! -regex '.*xml.*'
```

---

### Post by denarced on 2010-05-25
> **trent.josephsen said:**
> Use ! to negate a test, per find(1).

```
find . -type f \! -regex '.*xml.*'
```

Now this is the answer.
Exactly what I was looking for.

Much thanks, trent.josephsen

---

