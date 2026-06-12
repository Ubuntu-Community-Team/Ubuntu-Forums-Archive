---
title: "bash: ./rot13: /usr/bin/perl: bad interpreter: Permission denied"
date: 2006-01-10
forum: Programming Talk
---

### Post by Rovenhot on 2006-01-10
Just testing out a simple perl script, but it won't let me.  I'm not sure if what won't let me is bash, perl, Ubuntu, or something else.  The script works fine when run explicity with perl, but not when executed directly.

```
$ cat rot13
#!/usr/bin/perl
...
$ ls -l rot13
-rwxr-xr-x  1 rovenhot rovenhot 91 2006-01-10 19:03 rot13
$ ls -l /usr/bin/perl
-rwxr-xr-x  2 root root 16104 2005-09-21 08:10 /usr/bin/perl
$ ./rot13
bash: ./rot13: /usr/bin/perl: bad interpreter: Permission denied
$ perl rot13 << EOF
> This is a test.
> EOF
Guvf vf n grfg.
$
```

---

### Post by purpleturtle on 2006-02-02
Is the file in DOS format? (CR/LF) rather than Unix format (LF)?

You can check this with:

file ./rot13

---

### Post by Rovenhot on 2006-02-02
Problem found: it was on a noexec flash drive.  I just had to move it off.

---

