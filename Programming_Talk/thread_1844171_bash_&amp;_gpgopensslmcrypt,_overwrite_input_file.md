---
title: "bash &amp; gpg/openssl/mcrypt, overwrite input file"
date: 2011-09-14
forum: Programming Talk
---

### Post by chukchuck on 2011-09-14
I'm writing a bash script that has to encrypt a file with GPG or OpenSSL or mcrypt but i've a problem: i cannot overwrite input file.
I **don't want** to shred or wipe the original file, i want to overwrite it. 
Is it possible?
There's a way to do this?
Thanks :popcorn:

---

### Post by Vaphell on 2011-09-14
overwrite as in **some_command file > file **?
that won't fly
create temporary output file and when the operation ends just move it in the place of original version.

---

### Post by chukchuck on 2011-09-15
> **Vaphell said:**
> overwrite as in **some_command file > file **?
that won't fly

That doesn't work...after this command you're unable to decrypt the file!

> **Vaphell said:**
> 
create temporary output file and when the operation ends just move it in the place of original version.

?? You mean this??

```
gpg -o file.gpg -c file
mv file.gpg file
```

---

### Post by fdrake on 2011-09-15
=D> that's it!.. you cannot read and change at the same time an input file in bash.

---

### Post by chukchuck on 2011-09-15
Oh yes i'm an idiot xD the simplest solution is the best solution :D
But i've a last doubt: is this secure?

---

### Post by fdrake on 2011-09-15
> **chukchuck said:**
> Oh yes i'm an idiot xD the simplest solution is the best solution :D
But i've a last doubt: is this secure?

once you mv a file to another there is no way to get back (it gets wipe out of the memory it does not go in the trash) that first file unless you do some kind of disk recovery, but even then, good luck with it!

---

### Post by chukchuck on 2011-09-15
that's good :D

---

