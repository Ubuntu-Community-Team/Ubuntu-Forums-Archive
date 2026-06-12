---
title: "How can i use wget command to download file?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Victor Chou on 2008-07-15
Hi all,

I am a beginner. Can tell me how can i use wget command to download file?
Thanks a lot.

Best regards,
Victor

---

### Post by hyper_ch on 2008-07-15
how would you do it with wget? Have you ever looked at wget?

---

### Post by techstop on 2008-07-15
You know about the "man" command right? Every shell command has a man or manual page that tells you how to use it. To view the man page for a command, eg wget, type;

```
man wget
```

That will give you the answer you seek:o

---

### Post by kunixos on 2008-07-15
You find the actual link to the file you want to download (ie. something that ends in */filename.fileextension) go into the command line and type in ```
wget http://www.url.com/path/to/filename.fileextension
```and there you have it!

you can also look at the information provided by the creators of wget by typing ```
man wget
``` and having a look! (PS this resource-'man programname'-works for almost all command-line programs, so check it out!)

Hope this helps!

---

### Post by kpkeerthi on 2008-07-15
And.. if you want to resume your half-done download, you would use
```
wget -c http://www.url.com/path/to/filename.fileextension
```

-c ==> Continue partially completed download.

There is also a GUI front-end to it called gwget. Install it using Synaptic.

---

