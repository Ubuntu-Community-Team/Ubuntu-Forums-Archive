---
title: "case insensitive compiling with gcc?"
date: 2009-11-06
forum: Programming Talk
---

### Post by vgokul on 2009-11-06
Hello all,
I have a bunch of files where the headers included do not match the case of the header file names. While compiling gcc cannot find these files because of the case mismatch. I cannot change the original files so what I do is to cp these files to the correct case before and remove them after compiling using a make file.
 
Is there any compiler option that enables case insensitive compiling with gcc?
 
Regards
V.Gokul

---

### Post by samjh on 2009-11-06
No, there is no case-insensitive compilation option for gcc.

---

### Post by Tony Flury on 2009-11-06
Why can't you change the file names permanently ?

---

### Post by nvteighen on 2009-11-06
> **Tony Flury said:**
> Why can't you change the file names permanently ?
Maybe permission issues? If so, ask the owner of those files to allow you modify those names.

---

### Post by vgokul on 2009-11-09
> **nvteighen said:**
> Maybe permission issues? If so, ask the owner of those files to allow you modify those names.
That is correct. I am not the owner of the files. 
 
Just wanted to be sure that I am not missing any obvious solution.
 
Thank you.

---

### Post by Arndt on 2009-11-09
> **vgokul said:**
> That is correct. I am not the owner of the files. 
 
Just wanted to be sure that I am not missing any obvious solution.
 
Thank you.

An alternative to copying may be to make symbolic links.

---

