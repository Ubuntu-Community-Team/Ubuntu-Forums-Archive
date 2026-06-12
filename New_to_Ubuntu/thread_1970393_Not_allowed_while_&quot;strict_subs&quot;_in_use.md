---
title: "Not allowed while &quot;strict subs&quot; in use"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-01
Hello All,

I was trying to name a file when I got the following error message:

```

glenn@acer:~/Evolution Backup$ rename -v evolution-backup20120430.tar.gz evolution-may1-backup.tar.gz
Bareword "evolution" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "backup20120430" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "tar" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "gz" not allowed while "strict subs" in use at (eval 1) line 1.
glenn@acer:~/Evolution Backup$ 

```Can someone please tell me what "strict subs" mean?

Glenn.

---

### Post by jtarin on 2012-05-01
> : Not allowed while "strict subs" in useis Perl nomenclature.Not sure what that has to do with what your doing. Have you tried just opening up your file manager and right-click "rename"?

---

### Post by Senior_Buckethead on 2012-05-01
No I was in terminal. I was renaming Evolutions backup mail file. Perhaps Evolution still had its claws on the file..?

---

