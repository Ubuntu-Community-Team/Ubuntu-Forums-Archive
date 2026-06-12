---
title: "[SOLVED] Bash error message handling"
date: 2008-02-06
forum: Programming Talk
---

### Post by roggo on 2008-02-06
Hello all!

I have a simple question, and my searches have not found an answer so I want your help!

How do I find the string of the error message of a command?

In example...

ls "this file does not exist.txt"
echo THE_ERROR_FROM_LS # (no such file or dir)

Thanks!

---

### Post by ghostdog74 on 2008-02-06
> **roggo said:**
> Hello all!

I have a simple question, and my searches have not found an answer so I want your help!

How do I find the string of the error message of a command?

In example...

ls "this file does not exist.txt"
echo THE_ERROR_FROM_LS # (no such file or dir)

Thanks!

echo $? 
that's the return status. is that what you want. Also, pls try to read the bash manual next time.

---

### Post by roggo on 2008-02-06
> **ghostdog74 said:**
> echo $? 
that's the return status. is that what you want. Also, pls try to read the bash manual next time.

Dude, I've spent the last ~5 hours trying to figure out different stuff on bash to get this figured out. I always read the manual, the forums, the tutorials... And then try to find other places.

Don't always assume the worst with newbie questions.

Back to the point --->

The $? is the return value, not the error string.

I need to get "no such file or directory" if I have ls "this file doesnt exist.txt" into a string, to do stuff to that string further down the script.

EDIT:

Basically something like this but "better" and without the I/O:

ls "this file doesnt exist.txt" 2> error.log
errorstring < error.log
echo $errorstring

---

### Post by stroyan on 2008-02-06
Well behaved programs like ls send their error messages to file descriptor 2.
That is the stderr stream of stdio.h.
You can redirect the file descriptor to a file with 2>filename.
Or you can merge it into stdout with 2>&1.
```
$ ls nonesuch
ls: nonesuch: No such file or directory
$ ls nonesuch 2>errors
$ cat errors
ls: nonesuch: No such file or directory
$ F=$(ls nonesuch 2>&1)
$ echo $F
ls: nonesuch: No such file or directory

```

---

### Post by roggo on 2008-02-06
> **stroyan said:**
> Well behaved programs like ls send their error messages to file descriptor 2.
That is the stderr stream of stdio.h.
You can redirect the file descriptor to a file with 2>filename.
Or you can merge it into stdout with 2>&1.
```
$ ls nonesuch
ls: nonesuch: No such file or directory
$ ls nonesuch 2>errors
$ cat errors
ls: nonesuch: No such file or directory
$ F=$(ls nonesuch 2>&1)
$ echo $F
ls: nonesuch: No such file or directory

```

Thanks!

It's odd... I tried with 2>&1... maybe just a typo or such... :(

---

### Post by ghostdog74 on 2008-02-06
> **roggo said:**
> Dude, I've spent the last ~5 hours trying to figure out different stuff on bash to get this figured out. I always read the manual, the forums, the tutorials... And then try to find other places.

you tried reading [here ]("http://tldp.org/LDP/abs/html/io-redirection.html")? its the bash manual.
> 
Don't always assume the worst with newbie questions.

sorry for that if you feel offended. However, the "solution" you want is in the manual and you said you had read the manual?


> 
The $? is the return value, not the error string.

the $?  is your "error string", represented by a number. If its 0, the file exists. Otherwise not 0. Although, i don't really know what you are going to do further down the script,  the number can still do what you want.
```

ls file
if [ $? -eq 2 ];then
  echo "file is not found"
fi

```

> 
Basically something like this but "better" and without the I/O:

ls "this file doesnt exist.txt" 2> error.log
errorstring < error.log
echo $errorstring

then how about this
```

result=`ls file 2>&1`
echo $result

```

---

