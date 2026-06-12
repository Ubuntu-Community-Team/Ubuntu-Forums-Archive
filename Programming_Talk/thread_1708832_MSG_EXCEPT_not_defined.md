---
title: "MSG_EXCEPT not defined"
date: 2011-03-17
forum: Programming Talk
---

### Post by fla.1257 on 2011-03-17
Hello, I am writing a C program using IPC message queues. When I use msgrcv function with the last flag parameter set to MSG_EXCEPT the compiler says it is not defined. The man page for the function says to include <sys/types.h> <sys/ipc.h> and <sys/msg.h> and I include them. Everything works fine if I don't use that flag. A simple grep in the /usr/include/sys doesn't find the MSG_EXCEPT declaration which is instead found in the /usr/include/linux/msg.h header as:

#define MSG_EXCEPT      020000

If i define that in my source it seems to work as expected, but I think there must be a reason if it is not defined where it should be, any idea of what is going on here?

---

### Post by dwhitney67 on 2011-03-17
The following code compiles fine on my Ubuntu 10.04 system.
```

#include <sys/msg.h>
#include <stddef.h>    // for NULL

int main(void)
{
   int msgid = 1;

   msgrcv(msgid, NULL, 0, 0, MSG_EXCEPT);

   return 0;
}

```

---

### Post by fla.1257 on 2011-03-17
Thank you very much for your reply, I am using ubuntu 10.04 with gcc 4.4.3 and your code is not compiling on my system, it still complains about undeclared MSG_EXCEPT. I have searched inside sys/msg.h header and it includes bits/msq.h where MSG_EXCEPT is defined but it is guarded by 

#ifdef __USE_GNU
# define MSG_EXCEPT	020000	/* recv any msg except of specified type */
#endif

I have printed the pre-defined gcc macros with the command

gcc -dM -E - < /dev/null

and __USE_GNU is not defined. Can you please tell me what version of gcc you are using (gcc --version) and can you please check with the command above if it defines __USE_GNU?

---

### Post by fla.1257 on 2011-03-17
Another problem I have found is that sys/msg.h includes features.h which  explicitly un-define __USE_GNU with:

#undef	__USE_GNU

so even if I define __USE_GNU in my code or with a parameter to gcc it still doesn't compile.
The only solution I have found is to comment the #undef in features.h declare __USE_GNU in my code with:

#ifndef __USE_GNU
#define __USE_GNU
#endif

before including sys/msg.h and then of course everything compiles fine, but I don't think this is a clean solution. Why is it so difficult to use MSG_EXCEPT if it is reported as a normal parameter in the documentation?

---

### Post by dwhitney67 on 2011-03-17
Bingo!  I think you nailed it... I'm using a specialized gcc alias that defines _GNU_SOURCE, and thus the reason I had success compiling the program I posted earlier.

This is my gcc definition:
```

alias gcc='gcc -Wall -pedantic -D_GNU_SOURCE -std=c99'

```

---

### Post by fla.1257 on 2011-03-17
Great the _GNU_SOURCE macro works perfectly it switch on _USE_GNU in features.h with:

#ifdef	_GNU_SOURCE
# define __USE_GNU	1
#endif

I think that the man page anyway should report that to use MSG_EXCEPT one must define _GNU_SOURCE to activate the GNU extensions. 
I add the [link to the libc manual]("http://www.gnu.org/software/libc/manual/html_mono/libc.html#Macro-Definitions") where more is explained on this subject for anyone interested.

Thank you very much for your help I have learnt an important lesson on Linux c development.

---

