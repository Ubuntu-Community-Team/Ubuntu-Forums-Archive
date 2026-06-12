---
title: "Binary on stdout"
date: 2008-08-31
forum: Programming Talk
---

### Post by clinux on 2008-08-31
Hello,

I was trying to output binary in console and i noticed that many characters as well as line breaks are "executed" thus i can't view them.
However i can write binary to a file and run it.

I found a topic where people say that mode 'b' under linux is being ignored whereas under windows it's not.
So is there any workaround?

Thanks

---

### Post by nvteighen on 2008-08-31
How are you doing this (language, functions, etc.)?

If it's in C (if my guess is right), you should use fwrite(), not fprintf().

---

### Post by Lux Perpetua on 2008-08-31
I think you'd better explain what exactly you're trying to do. I'm having a hard time understanding what someone would accomplish by writing binary data to a text console.

---

### Post by clinux on 2008-08-31
I'm trying it with Python
```
#! /usr/bin/env python
import sys

FILE = open('IMAGE.png', 'rb')
sys.stdout.write(FILE.read())
FILE.close()

sys.exit(0)
```

---

### Post by caljohnsmith on 2008-08-31
How about piping the stdout to hexdump? Not sure exactly how to do that in Python, but trying piping it to "hexdump -C" for example.

---

### Post by Bachstelze on 2008-08-31
> **clinux said:**
> I was trying to output binary in console and i noticed that many characters as well as line breaks are "executed" thus i can't view them.

How do you expect to "view" a line break? A line break is a line break...

---

### Post by caljohnsmith on 2008-08-31
> **HymnToLife said:**
> How do you expect to "view" a line break? A line break is a line break...
Actually you can "view" a line break if you look at the file in a hex editor; the line break is "0A" in hexadecimal. Thus hexdump would also work. :)

---

### Post by Bachstelze on 2008-08-31
> **caljohnsmith said:**
> Actually you can "view" a line break if you look at the file in a hex editor; the line break is "0A" in hexadecimal. Thus hexdump would also work. :)

Yup, but using write() will just output the characters, not their hex values, thus a line break will be a line break. It would be nice if the OP explained a bit what he's trying to achieve.

---

### Post by jinksys on 2008-09-01
Deleted

---

### Post by clinux on 2008-09-01
ok i found [this](http://mail.python.org/pipermail/python-list/2000-July/042460.html) post which is pretty much what i'm trying to do but it's no longer a problem :).
thanks for the replies

---

