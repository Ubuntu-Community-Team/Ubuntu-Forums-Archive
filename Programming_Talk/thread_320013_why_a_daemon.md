---
title: "why a daemon?"
date: 2006-12-16
forum: Programming Talk
---

### Post by jmc1024 on 2006-12-16
Why are server type applications written as daemons?  Security?  They seem harder
to debug to me.  There are lots of example of how to do it, just nothing on why.  I 
know I read why years and years ago, but I've forgotten.  Why do I ask?  Okay, I'm
writing yet-another-jukebox program.  It starts under init.d and the user interacts 
with it via web browser.
Thanks,
Mark

---

### Post by lnostdal on 2006-12-17
> **jmc1024 said:**
> Why are server type applications written as daemons?  Security?  They seem harder
to debug to me.  There are lots of example of how to do it, just nothing on why.  I 
know I read why years and years ago, but I've forgotten.  Why do I ask?  Okay, I'm
writing yet-another-jukebox program.  It starts under init.d and the user interacts 
with it via web browser.
Thanks,
Mark

Not sure what you mean:
  [http://en.wikipedia.org/wiki/Daemon_%28computer_software%29](http://en.wikipedia.org/wiki/Daemon_%28computer_software%29)

One (I) usually write server type application as a (blocking) foreground process. Then later _execute_ it as a daemon (background process).

Under Linux this is done with `start-stop-deamon' or by simply appending a & when you execute the program from your shell.

---

