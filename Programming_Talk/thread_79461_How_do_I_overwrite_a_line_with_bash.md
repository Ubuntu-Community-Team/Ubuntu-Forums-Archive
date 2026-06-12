---
title: "How do I overwrite a line with bash?"
date: 2005-10-20
forum: Programming Talk
---

### Post by David Marrs on 2005-10-20
Is it possible to output text to the begining of the same line each time, rather than continue from the end of the last character or on a new line? I've got a lot of info to output to the terminal but it would be more useful to me if it just rewrote to the same line rather than overtook the entire terminal window.

---

### Post by JmSchanck on 2005-10-20
Yes you can do this with the escape character "\r"

example:
```

echo -e "ABCDEF\r123"

```

output:

123DEF


Same thing in c:
```

printf("OooOo I wrote some text \r and now I overwrote it\n");

```

---

### Post by David Marrs on 2005-10-21
thanks :)

---

