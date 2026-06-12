---
title: "Problem with lstat function in C"
date: 2005-09-11
forum: Programming Talk
---

### Post by kevin1 on 2005-09-11
I am trying to use g_lstat to obtain the attributes of a file.
Partial source code:

```
	#include <glib.h>
	#include <glib/gstdio.h>

	struct stat	*filedata;
	guint		   result;

	result = g_lstat(filename,filedata);
```

I am getting a compiler error:

	"warning: implicit declaration of function `lstat'"

There are no other error messages.

g_lstat is #defined as lstat in gstdio.h.

gstdio.h #includes <sys/stat.h>, (which defines lstat) so I shouldn't have to include it myself.

As expected, adding it to my source file does not solve the problem, nor does adding all the #includes shown by 'man lstat':

	#include <sys/types.h>
	#include <sys/stat.h>
	#include <unistd.h>

I have checked for stat.h on my system - it is under /usr/include/sys/.

What else should I check? 


Thanks for any advice,

Kevin   ](*,)

---

### Post by LordHunter317 on 2005-09-11
Posting your entire source file and the entire error message would be very helpful.

---

### Post by kevin1 on 2005-09-11
LordHunter, 

the entire error message is as shown, and is caused by the line which includes 'g_lstat'.
The entire source file is way too long to post, and is mostly not relevant to the problem.

I have just discovered that I can lose the error message by replacing 'g_lstat' with 'gstat', or I can keep 'g_lstat' and remove the '-ansi' flag from my makefile.

It seems that 'stat' is ansi compliant, but 'lstat' is not.

Kevin

---

### Post by LordHunter317 on 2005-09-11
Well clearly, the issue isn't in what you posted.

My guess is that you have your include files in the wrong order, but that's just me.

---

### Post by Pithikos on 2011-10-05
lstat() is not compliant with strict ANSI. Change your compiler flags.

I had this flag:
```
-std=c99
```changed it to this:
```
-std=gnu99
```and it compiles fine!

---

### Post by GeneralZod on 2011-10-05
Does anyone know what the record for necro-bumping is? ;)

---

### Post by Pithikos on 2011-10-05
> **GeneralZod said:**
> Does anyone know what the record for necro-bumping is? ;)

:lolflag:Oh well at least now if someone runs into this problem and googles it(it's the first result) will at least have a solution.

---

