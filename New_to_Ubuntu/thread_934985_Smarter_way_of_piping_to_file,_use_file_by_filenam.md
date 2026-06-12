---
title: "Smarter way of piping to file, use file by filename, delete file by filename?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by tnek on 2008-10-01
Hi,

In my quest to learn more I'm wondering if there is a smarter way to do what I do. What I do is: **neato test.dot -Tpng > test.png && feh test.png && rm test.png**

Neato creates a standard output stream of type PNG image which I redirect into a temporary file called test.png. Then I want to view this file using the feh image viewer, it expects a *file name* as its argument, which I give it. When I'm done viewing the image I close feh and the image is deleted.

I can't **neato test.dot -Tpng | feh test.png **as feh expects a file name. It would have been nice, as I wouldn't have to create an explicitly named temporary file which *might* overwrite an existing file.

Is there anything similar to the pipe statement I could write which works?

---

### Post by aeiah on 2008-10-01
i cant test right now, but what does ```
neato test.dot -Tpng | feh -
``` do?

---

### Post by Bachstelze on 2008-10-01
If feh supports reading from standard input, you can do

```
test.dot -Tpng | feh
```

If it doesn't then you have no choice but to use temporary files. If you want to avoid the risk of overwriting existing files, you can use uuidgen (from the package uuid-runtime) to generate UUIDs (Universally Unique IDentifiers).

---

### Post by tnek on 2008-10-01
Hi,

Sorry about the || when I meant a single | pipe. And it came out a valid statement too. :oops: I have corrected my original post now.

And yes. It seems feh doesn't like it's input from a pipe, it wants a file name. And this means I'm stuck with temporary files. Which I can create using uuidgen which was nice to know, I didn't know it existed! :)

---

