---
title: "[C99] Question about a conjuction"
date: 2013-12-12
forum: Programming Talk
---

### Post by ppplayer80 on 2013-12-12
Hi,

I have a simple question.

If I type something like
```
if (a==1 && b != 3)
```
And lets say that 'a' is equal to 2. Does a program check b's value or stops when it discovers that 'a' doesn't meet a condition?

---

### Post by r-senior on 2013-12-12
It does not check the second condition if the first is false.

See [http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf), section 6.5.13.

---

### Post by ppplayer80 on 2013-12-12
Thank you! :)

---

### Post by ofnuts on 2013-12-12
This is typically used to check pointers and the thing they refer to:

```

if (stringPtr == NULL || *stringPtr == '\0') // Check for string null or empty, the NULL pointer won't be dereferenced 

if (stringPtr != NULL && *stringPtr != '\0') // Check for string not null and not empty, the NULL pointer won't be dereferenced 

```

---

