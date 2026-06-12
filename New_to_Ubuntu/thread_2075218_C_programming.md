---
title: "C programming"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by oslokai on 2012-10-23
I am a beginner here, also in C programming. I made a few samples some months back (while my laptop ran on Ubuntu 11.04). Now (with 12.04) they won't run, and new programmes won't run either. The compile OK with the gcc command, and gives appropriate error messages. But when running them nothing happens, no error message.

They have the .out file extension.

Advice appreciated!

Kai

---

### Post by LiamOS on 2012-10-23
If they're giving error messages, they are not actually compiling.

---

### Post by oslokai on 2012-10-23
I meant that errors are pointed out, and after corrected there is no more error message.

---

### Post by MG&amp;TL on 2012-10-23
> **oslokai said:**
> I meant that errors are pointed out, and after corrected there is no more error message.

Respectfully, the fault is not Ubuntu's, it is yours. Otherwise everything written in C would be dying about the place.

I suggest you find out why what you expect to happen is not happening. Use a debugger, or post code. :)

---

### Post by spjackson on 2012-10-23
Post sample code. Post a terminal session showing compilation of the code, and the attempt to execute it.

---

### Post by oslokai on 2012-10-23
Hi MG&TL
The error is not in the code. The fault may not be Ubuntu's either, like you say. It's likely something fundamental I have forgotten or do wrongly, after the compilation is completed without error messages.
Also other similar, beginner programs ran some months ago, but now nothing happens.

("would be dying about the place" .. sorry, I don't understand. English is not my mother tongue.)

---

### Post by oslokai on 2012-10-23
Thanks for taking the time to assist. Does this help?
k@lap:~/Documents$ gcc Hi.c
k@lap:~/Documents$ a.out
a.out: command not found
k@lap:~/Documents$

---

### Post by MG&amp;TL on 2012-10-23
> Hi MG&TL
The error is not in the code. The fault may not be Ubuntu's either, like you say. It's likely something fundamental I have forgotten or do wrongly, after the compilation is completed without error messages.
Also other similar, beginner programs ran some months ago, but now nothing happens.

Looking at your later shell session, you're not running the programs at all. ;)

> ("would be dying about the place" .. sorry, I don't understand. English is not my mother tongue.)

Your English is very good. :) My bad, it's a local thing to my area. Don't worry about it.

> **oslokai said:**
> Thanks for taking the time to assist. Does this help?
k@lap:~/Documents$ gcc Hi.c
k@lap:~/Documents$ a.out
a.out: command not found
k@lap:~/Documents$

You need to tell your shell to look in the current directory, rather than the system directories. Try:

```
./a.out
```

..which should hopefully work. :)

---

### Post by oslokai on 2012-10-24
Looking at your later shell session, you're not running the programs at all. ;)
 - Exactly.

Your English is very good. :) My bad, it's a local thing to my area. Don't worry about it.
 - Thanks! :)

You need to tell your shell to look in the current directory, rather than the system directories. Try:
./a.out
..which should hopefully work. :)

 - Which it does! Thanks! (This is the beginners dept right?) I found something on the "./" and the "a.out" file. Their function wasn't clear either. I thought the system would always look in the current directory unless otherwise specified. Apparently the opposite is the case.

Thanks again!

---

### Post by MG&amp;TL on 2012-10-24
Not a problem! 

Yes, this is the beginners' section. Although if you're programming C, maybe not such a beginner. :)

Yup-the shell looks at the directories specified in the PATH environment variable (try "echo $PATH" in a shell), and doesn't look at the current one at all unless you give it a relative or absolute path. 

Have fun with your C. ;)

---

