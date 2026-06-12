---
title: "seek and write functions in Python doesn't want to work together."
date: 2009-10-18
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-18
```
song = "mysound.mp3"
fh = open(song, "w")
fsize = os.path.getsize(song)
fh.seek(fsize-125)
fh.write("Test1")
fh.close()

```**Result: **0 byte file

Why it so and how can I write to a specific location ?

---

### Post by Bachstelze on 2009-10-18
Opening a file with mode="w" will overwrite it, so in your script, fsize will be 0. You want mode="a".

---

### Post by unknownPoster on 2009-10-18
> **Bachstelze said:**
> Opening a file with mode="w" will overwrite it, so in your script, fsize will be 0. You want mode="a".

Just for further information I would look at the following link: [http://diveintopython.org/file_handling/file_objects.html](http://diveintopython.org/file_handling/file_objects.html)

Especially, section 6.2.4

---

### Post by OpenGuard on 2009-10-18
> **Bachstelze said:**
> Opening a file with mode="w" will overwrite it, so in your script, fsize will be 0. You want mode="a".

**a** appends text, no matter where I am ( EOF + string, **not** string + edited + string + EOF ). Any other ways of achieving what I want ?

---

### Post by Can+~ on 2009-10-18
Open it on "r+", so you can jump to the desired line and write there (assuming there's a file there in the first place).

And jump to seek(-125, os.SEEK_END)

---

### Post by OpenGuard on 2009-10-18
> **Can+~ said:**
> Open it on "r+", so you can jump to the desired line and write there (assuming there's a file there in the first place).

And jump to seek(-125, os.SEEK_END)

Bingo! Thank you :)

---

