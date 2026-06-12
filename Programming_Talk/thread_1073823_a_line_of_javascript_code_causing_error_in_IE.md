---
title: "a line of javascript code causing error in IE"
date: 2009-02-18
forum: Programming Talk
---

### Post by qmqmqm on 2009-02-18
Hi

This line of javascript code is causing errors in IE.

```
document.write("<TD bgColor=" background_color + ">" + validity_status + "</TD>");
```

I spent a long time but cannot figure out what's wrong with this line of code...

Any ideas anyone?

Thanks,

Tom

---

### Post by simeon87 on 2009-02-18
There's no plus after the first string. And you'd need to escape the quotation marks for the value of bgColor, so:

```

document.write("<TD bgColor=\"" + background_color + "\">" + validity_status + "</TD>");

```

---

