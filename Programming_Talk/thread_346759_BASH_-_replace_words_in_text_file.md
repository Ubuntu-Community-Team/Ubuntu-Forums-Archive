---
title: "BASH - replace words in text file"
date: 2007-01-26
forum: Programming Talk
---

### Post by ironfistchamp on 2007-01-26
Hey all

Does anyone know a command (or sequence of commands) to run through a file and replace a word with another. Is it also possible to change the case. For example if I had the word "Hello" written 500 time throughout a document, would it be possible to change them all to "hello" instead?

Thanks

Ironfistchamp

---

### Post by ghostdog74 on 2007-01-26
how about sed?
```

sed 's/Hello/hello/g' file 

```

---

### Post by Eric_T on 2007-01-26
Sed is the easiest way. But to make the change permanent, you have to add -i to the command:
```

sed -i 's/Hello/hello/g' file
```

Sed can also use regular expressions, so it's a very powerful tool.

---

### Post by ironfistchamp on 2007-01-26
Thanks that is perfect. It works a treat.

Ironfistchamp

---

### Post by DouglasAWh on 2010-10-12
> **Eric_T said:**
> 
```

sed -i 's/Hello/hello/g' file
```

how would I do that with a variable?

EDIT: The answer is obvious...my problem was that if "Hello" isn't in the file, nothing is going to be changed to "hello".  I guess this is why you test things before putting them into production. :)

---

### Post by s.fox on 2010-10-12
I am happy that you were able to resolve your problem :D

In future please start a new thread if the thread you post in is rather old.

Thread closed - Necromancy.

---

