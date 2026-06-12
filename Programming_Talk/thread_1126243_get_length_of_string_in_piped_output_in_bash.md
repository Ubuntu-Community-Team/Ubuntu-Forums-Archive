---
title: "get length of string in piped output in bash"
date: 2009-04-15
forum: Programming Talk
---

### Post by monkeyking on 2009-04-15
Hi

I got a file that looks something like
```

car elephant cat dog rhino
.
.
.

```
Is there some easy of getting the length of the element that is
if I type

```

head -n1 file|cut -f4 
#outputs
dog

```

is there a command to do

```

head -n1 file|cut -f4| length
#outputs
3

```

thanks in advance

---

### Post by ghostdog74 on 2009-04-15
```

awk 'NR==1{print length($4)}' file

```

---

### Post by monkeyking on 2009-04-16
Thanks ghostdog,

its a way to do it,
but its not really bash is it :)

---

### Post by lloyd_b on 2009-04-16
```
TEST=`head -n1 file|cut -f4`;echo ${#TEST}
```

But I don't see why you don't use awk - you're using the external programs "head" and "cut" already...

Lloyd B.

---

### Post by ghostdog74 on 2009-04-16
> **monkeyking said:**
> Thanks ghostdog,

its a way to do it,
but its not really bash is it :)

if you want the bash way,
```
 
exec 3<file #open file handle
read line <&3 #read line 
set -- ${line}
echo "length of field 4 is ${#4}"
exec 3>&- #close file

```

see my sig for bash link.

---

### Post by monkeyking on 2009-04-16
Thanks for your replys.

I find it awkward though,
that there is no beautifull way of doing it.

---

### Post by kaibob on 2009-04-16
My first thought was:

```
head -n1 file | cut -f4 | wc -m
```

I gave this a try, but it returned the number of characters plus 1 (i.e. it returned 4 for dog, 6 for rhino, and so on). It's easy to subtract for this but clumsy.

An alternative that seems to work is

```
head -n1 file | cut -f4 | xargs expr length
```

Still, ghostdog74's awk solution seems best.

RELATED LINK
[http://www.unix.com/shell-programming-scripting/3949-finding-out-length-string-held-within-variable.html](http://www.unix.com/shell-programming-scripting/3949-finding-out-length-string-held-within-variable.html)

---

### Post by stroyan on 2009-04-17
The ${#variable} notation that ghostdog pointed to is quite simple.
You can replace all of the external commands with a bash read.
The "read -a" option will read fields into an array variable.
It is indexed from 0 instead of 1.  So the fourth field is index 3.
```

$ read -a A < file
$ echo length of ${A[3]} is ${#A[3]}

```

---

### Post by monkeyking on 2009-04-18
Thanks for your replies,
I think that the last example of kaibobs is the most straightforward one.

thanks againg

---

### Post by ghostdog74 on 2009-04-19
> **monkeyking said:**
> Thanks for your replies,
I think that the last example of kaibobs is the most straightforward one.

but needs to pipe to 3 processes using 3 tools.

---

