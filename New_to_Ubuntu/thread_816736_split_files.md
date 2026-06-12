---
title: "split files"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by person8451 on 2008-06-03
I have a large file that I need to split into DVD-sized chunks.  I don't care about compression or anything, just need to split it up so I can write it to DVDs.  

I have searched here for things about "split", and typed "man split" into the terminal, but I am apparently too stupid to figure it out.  

Is there a GUI-based moron-accessible app that will split up a file like old winrar used to do for me?  I keep trying to learn more about command-line stuff but this one is giving me a headache.

(8.04 Hardy, in case that helps).

Thanks in advance :)

---

### Post by Xiong Chiamiov on 2008-06-03
I don't know about any GUI apps, but [this]("http://www.computerhope.com/unix/usplit.htm") is a little easier to understand than the man page.

---

### Post by Bradtek on 2008-06-03
> **Xiong Chiamiov said:**
> I don't know about any GUI apps, but [this]("http://www.computerhope.com/unix/usplit.htm") is a little easier to understand than the man page.

Was easy to follow if I want to split into pieces of a few bytes each,
but not sure how to get kb or mb or gb size pieces.

Edit:
Have used this in the past in Windows
HJSplit for Linux
[http://www.freebyte.com/hjsplit/#linux](http://www.freebyte.com/hjsplit/#linux)

---

### Post by Xiong Chiamiov on 2008-06-03
Doing a search for "split" in adept gave me a few results that look promising.

---

### Post by aquavitae on 2008-06-03
From the link provided by Xiong:
> -b n m  	Split a file into pieces n*1048576 bytes in size.
This means it will split it into n Mb, e.g.
```
split -b 4400 m original_file new
```
will split original_file into files of size 4400Mb.

---

