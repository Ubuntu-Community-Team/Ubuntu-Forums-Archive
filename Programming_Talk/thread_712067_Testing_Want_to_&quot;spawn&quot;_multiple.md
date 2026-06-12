---
title: "Testing: Want to &quot;spawn&quot; multiple"
date: 2008-03-01
forum: Programming Talk
---

### Post by mikecrowe on 2008-03-01
Hi folks,

I have an interesting question.  I want to load test a web application (non HTTP).  I've written some php curl-based test scripts.

How can I spawn many copies of this script to hit my server 50 or 100 times simultaneously?  Any framework which might help this?

TIA
Mike

---

### Post by bukwirm on 2008-03-01
[Here's]("http://www.softwareqatest.com/qatweb1.html#LOAD") a list of webserver testing programs - I don't know if any of them will work for you, though.

---

### Post by lloyd_b on 2008-03-01
> **mikecrowe said:**
> Hi folks,

I have an interesting question.  I want to load test a web application (non HTTP).  I've written some php curl-based test scripts.

How can I spawn many copies of this script to hit my server 50 or 100 times simultaneously?  Any framework which might help this?

TIA
Mike

A simple shell script:
```
#!/bin/bash

for NUM in {1..100}; do
     myscript &
done
```
will launch 100 copies of that script, each running in background.  Note that they will *not* be truly simultaneous (there's going to be a very small delay between them), but depending on what your test scripts do it may be close enough.

Lloyd B.

---

### Post by mikecrowe on 2008-03-01
Lloyd,

DOH, I should have thought of that.  I don't know why I didn't think of that.  Thanks.

Mike

---

### Post by slavik on 2008-03-01
does php have fork()?

---

### Post by mikecrowe on 2008-03-01
No, it's really not thread aware (though curl is).  That's why I needed to run separate processes.

---

