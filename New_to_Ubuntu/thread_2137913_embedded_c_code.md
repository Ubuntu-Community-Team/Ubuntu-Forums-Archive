---
title: "embedded c code"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by akansha05 on 2013-04-22
i

---

### Post by r.stiltskin on 2013-04-22
isn't this a ridiculous place to be asking a question like this?

Think about the error message.  Not only does it tell you what  kind of error to look for, it probably also tells you a line number (which you didn't post), doesn't it?  Even if it doesn't, you can examine each place where you have a { character and look for a syntax error in that vicinity.

Hmm, perhaps a good place to start would be here:
```

#define begin {
#define end }

```

---

