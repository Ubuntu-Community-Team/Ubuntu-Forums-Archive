---
title: "Evaluation of Logical Expression"
date: 2007-09-21
forum: Programming Talk
---

### Post by TreeFinger on 2007-09-21
I am wondering how this statement will execute:

```
if ( a < c - 2 ) 
```

Will 2 be subtracted from c first? then the logical expression will be evaluated?

---

### Post by LaRoza on 2007-09-21
> **TreeFinger said:**
> 
```
if ( a < c - 2 ) 
```
Will 2 be subtracted from c first? then the logical expression will be evaluated?

Yes, in most languages I know. 

You should make precedence clear, however, using ().

```
if ( a <  (c - 2) ) 
```

---

### Post by TreeFinger on 2007-09-21
Yes, if I was writing the code I would definitely include parentheses. I just have a test today and wanted to double check :) Thanks.

---

### Post by LaRoza on 2007-09-21
> **TreeFinger said:**
> Yes, if I was writing the code I would definitely include parentheses. I just have a test today and wanted to double check :) Thanks.

Rats, I didn't mean to help you cheat.

In case you ever have a quick question like that, try it out and see, Python in interactive mode works wonders.

---

