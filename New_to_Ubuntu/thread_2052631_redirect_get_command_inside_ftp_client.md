---
title: "redirect get command inside ftp client?"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by Kdar on 2012-09-03
Is it possible to redirect get command inside ftp client?

I was only able to do "get filename /dev/null" to redirect it to /dev/null.. However.. what if I want to redirect it to a compression or decompression utility?

---

### Post by Lars Noodén on 2012-09-03
[wget](http://manpages.ubuntu.com/manpages/precise/en/man1/wget.1.html) supports FTP and can be used to pipe to other utilities if the output is to stdout.  See the option -O in the manual, it even gives an example there using a redirect (but not a pipe).

---

### Post by Kdar on 2012-09-03
cool. Thanks. I think I figured it out. I didn't know wget could access ftp, this makes it so much easier.

```
time wget --user=username --password=password -qO - ftp://server/file.gz | gunzip -cf > /dev/null
```

Does it look correct?

---

### Post by timcredible on 2012-09-03
you may want 'expect' if you're looking to do scripts with interactions to apps like ftp

---

### Post by Lars Noodén on 2012-09-04
> **Kdar said:**
> Does it look correct?

Yeah. Does it work?

wget does all kinds of things.  Be sure to look at the other options in the man page, they may come in handy some time.

---

### Post by Kdar on 2012-09-04
> **Lars Noodén said:**
> Yeah. Does it work?

wget does all kinds of things.  Be sure to look at the other options in the man page, they may come in handy some time.

Yes. I got it working. But I am trying to do the same with wput.. to go into other direction.


> **Kdar said:**
> How can I pipe input into wput?

I have tried to use &#8722;&#8722;input&#8722;pipe=command flag, however it didn't work. Maybe I am just doing it wrong.

Initially I tried something like this:

```
gzip -fc fileInput | wput ftp://user:password@serverIP/
```

then I tried this:

```
wput --input-piep="gzip -fc fileInput" ftp://user:password@serverIP/
```

But this doesn't work as well.
--------
--------
I also figured out that I can do
```
get $FILENAME "| gzip -fcd /dev/null"
```
directly from ftp. However, for some reason, using my sh script below still was slower than wget method by like 0.3 seconds. I am not sure what would case it, maybe the way wget does transfer is more cleaner.
```
#!/bin/bash
HOST='hostname'
USER='username'
PASSWD='password'
FILE=$1
ftp -i -n $HOST <<END_SCRIPT
user ${USER} ${PASSWD}
binary
get $FILE "| gzip -fcd /dev/null"
quit
END_SCRIPT
exit 0
```

---

### Post by Lars Noodén on 2012-09-04
What about [ncftpput](http://manpages.ubuntu.com/manpages/precise/en/man1/ncftpput.1.html)? It is part of the package [ncftp](http://linux.die.net/man/1/ncftp)  It's designed for uploading as you seem to be trying to do.

---

### Post by Kdar on 2012-09-05
Well, actually I got wput working somewhere... not all the way I want yet, but.. Here is what command I typed:

```
wput --input-pipe="gzip -cf1 file.tar; echo > /dev/null" ftp://user:password@server-name/run/shm/test/fileout.tar
```

However.. I really would liked to redirect those bits into /dev/null on the remote server location.


Doing something like this, didn't work:
```
wput --input-pipe="gzip -cf1 file.tar; echo > /dev/null" ftp://user:password@server-name/dev/null
```

---

