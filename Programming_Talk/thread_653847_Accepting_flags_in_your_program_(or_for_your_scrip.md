---
title: "Accepting flags in your program (or for your script)"
date: 2007-12-30
forum: Programming Talk
---

### Post by altonbr on 2007-12-30
I know that when you type in:
```
./my_script.sh name text
```
The variables that are passed are:
> $0 = my_script.sh
$1 = name
$2 = text

But how do you accept flags such as:
```
./my_script.sh -v -p 2222
```
> # -v = verbose
# -p = port

The user can enter them in any order they want, correct, so do you just read $1 and see if it matches a pre-compiled list of flags?

And what about:
```
./my_script --hide-output
```
???

---

### Post by ghostdog74 on 2007-12-30
if you are using bash and doing shell scripting, always refer to the advanced bash guide. [Here is how you do what you want]("http://tldp.org/LDP/abs/html/internal.html"). Read the part on getopts.

---

### Post by slavik on 2007-12-30
you are looking for GETOPT :)

---

### Post by altonbr on 2007-12-30
> **ghostdog74 said:**
> if you are using bash and doing shell scripting, always refer to the advanced bash guide. [Here is how you do what you want]("http://tldp.org/LDP/abs/html/internal.html"). Read the part on getopts.

Thanks ghostdog. I always use that guide, but I didn't know what to search for there.

> **slavik said:**
> you are looking for GETOPT :)

> The getopts construct replaces the deprecated getopt external command. :P

---

### Post by ghostdog74 on 2007-12-30
> **altonbr said:**
> Thanks ghostdog. I always use that guide, but I didn't know what to search for there.
 :P

That's strange. If you have always used that guide, then you should have come across getopts. You should spend your weekends reading it , from start till the end, and practice the examples.

---

### Post by altonbr on 2007-12-30
> **ghostdog74 said:**
> That's strange. If you have always used that guide, then you should have come across getopts. You should spend your weekends reading it , from start till the end, and practice the examples.

Well I am only a hobbiest. How am I supposed to know what the function name was or any sort of hint as to what the function name might? That's why I asked on here. Saying 'you better sharpen your Google skills' isn't exactly a productive statement.

---

### Post by ghostdog74 on 2007-12-30
> **altonbr said:**
> Well I am only a hobbiest. How am I supposed to know what the function name was or any sort of hint as to what the function name might?

It doesn't matter if you are a hobbyist or not. The matter is, whether you spend time reading and understanding it. If you have read, you would know. 

> 
 That's why I asked on here. Saying 'you better sharpen your Google skills' isn't exactly a productive statement.

If you type something like "Bash options" ( you do not know what function, but you do know they are some kinda options ), you will find what you want at the first few links. Forums are the last thing you go to for what you want. Always search first , ( yes, you have to sharpen your searching skills) because most of the time, you can find what you are looking for faster than posting in a forum and waiting for replies.

---

### Post by Peyton on 2007-12-30
Be nice....

---

