---
title: "python 3 input() not do spacing"
date: 2016-09-08
forum: Programming Talk
---

### Post by lance bermudez on 2016-09-08
```

-----BEGIN PGP MESSAGE-----
Version: GnuPG v1

hQIMA3qClorwwKU+AQ//ZIPVedWt+dKzmWgqv8TQVEmLjxOoju8MKdwUVL6pwvI1
toeJ/p9DEgBq59K0kJjV0pD7RCbDUnYqjqgc3RQSyYQpctYVxJ22svd5RB5ORb76
jvXs7RXqxwCJA9egwSmjATWaVPju1jaAFwfkicmZrxGDFY3bxOc0pm2t9fepycY0
DOKo3qYdA6yaoucldB7iFCCjGeGmwo2ZfBcQcAC0qG9jqQYGD8XguEWsg/UoD5Eu
tojQm3m0esQvCYBW3CcGKNe/t9oQrHbsHAOyWAwnjLF/HDyMnWUJIKW+xJPJQxiE
kPDB4xvxiZ1lfiZ7um+eZ/25Fb+CjJhYeMqclZEzRyhFjiX8o/6XuYaSy/9YiBrm
apmKuXFhq1/yBU3AKYTCUykP7q32keKdOYfkfNURMpN78knGZTdpKccq/ho2QpZX
f2RzgvmiZH9jxi1Op9lr48qL7ORnBa/nu2dSI9Sby4k+nhJyI+oFtG0zjQWnQB1Q
VQAGi0gIIGnx2JCUTzs4P4KdsmcizrTPT9HVk0CVkfu4Zkrb2Ue4Kf7rZIIfs/2U
S9MoiKvPmJy/HVrlS6HFRsJ3n8IqDWdxK/OkpvrrPduMM1XXAKdZt/O7z2iV0jYa
Nir592Go58pF8RcmX14Tvn6OhVdm/JK7ZKwcQEQ/veMRLuWw78bSC1h7ybtZBEXS
RgEfnvoLFH4G2deCgk3fvgMlezGrfgE/I9JAmDuaWW9fGrGvEO1Pc3FjbD7ioqpG
BwrVvb275zZpMNCn2opdKEQLZO1P9dw=
=bZHO
-----END PGP MESSAGE-----

```
I put the above code in code=input('past code here\n: ')
but when i print it i get
-----BEGIN PGP MESSAGE-----
how do i get the rest?

---

### Post by &amp;KyT$0P# on 2016-09-11
I'd probably do it something like [this]("http://stackoverflow.com/questions/13128951/how-to-get-user-input-for-multiline-lines-in-python-3/13128996#13128996")...

---

### Post by Wadim_Korneev on 2016-09-12
[COLOR=#242729][FONT=Arial]A common way of doing this in programs is to have an "I'm done" string (e.g. a single period), and to keep reading in lines until the line read matches that string.[/FONT][/COLOR]

---

