---
title: "Removing the -Werror option from gcc"
date: 2009-06-14
forum: Programming Talk
---

### Post by rymonroe on 2009-06-14
When I compile programs it keeps saying "warnings being treated as errors". I dont know how to turn this -Werror option off. Ive looked everywhere online. Thanks for the help.

---

### Post by unknownPoster on 2009-06-14
If you are using a makefile it could be an option enabled in there.

---

### Post by mali2297 on 2009-06-14
Assuming that you are using 'make', I think you can override the default C flags by issuing the command as
```

make CFLAGS='-O2 -Wall'

```
(Change the C flags to whatever you prefer.)

---

### Post by rymonroe on 2009-06-14
> **mali2297 said:**
> Assuming that you are using 'make', I think you can override the default C flags by issuing the command as
```

make CFLAGS='-O2 -Wall'

```(Change the C flags to whatever you prefer.)

thanks alot! this worked perfectly.

---

