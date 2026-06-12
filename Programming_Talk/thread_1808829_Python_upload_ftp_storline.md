---
title: "Python upload ftp storline"
date: 2011-07-20
forum: Programming Talk
---

### Post by Randy Flagg on 2011-07-20
I have been trying this in the python interpreter and I can't seem to get it to work.

I can connect to the FTP and do a .dir() fine but no matter how I do it the STOR just hangs.

I am trying:

```

f = "out.text"
ftp.storlines("STOR " + f, open(f))

```

Any ideas?

---

### Post by Randy Flagg on 2011-07-20
> **Randy Flagg said:**
> I have been trying this in the python interpreter and I can't seem to get it to work.

I can connect to the FTP and do a .dir() fine but no matter how I do it the STOR just hangs.

I am trying:

```

f = "out.text"
ftp.storlines("STOR " + f, open(f))

```Any ideas?

I figured it out.  I hate to make one var the openfile and the other just the file name.  So this worked:

```

upfile = open("output.text", "r")
upname = "output.text"
ftp.storelines("STOR " + upname, upfile)

```

---

