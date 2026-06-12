---
title: "&quot;undefined reference to pthread_join&quot;"
date: 2006-08-09
forum: Programming Talk
---

### Post by quvil on 2006-08-09
[SIZE=3]Hello everybody.

Consider the following code snippet - it is not supposed to do anything, it is just an example (let's say that it is written in a file a.c):

 -----------------------------------------
 #include <pthread.h>

 int main() {
     pthread_attr_t attr;

     pthread_attr_init(&attr);
     pthread_join(0, 0);
 }
 -----------------------------------------

 I compile/link it by:

 gcc a.c

 an[/SIZE][SIZE=3]d, unless [/SIZE][FONT=monospace][SIZE=3][FONT=verdana,arial,sans-serif]"-lpthread" switch is used, I [/FONT][/SIZE][/FONT][SIZE=3]get the following error from the linker:

 /tmp/ccKvYgqq.o: In function `main':
 a.c:(.text+0x34): undefined reference to `pthread_join'
 collect2: ld returned 1 exit status

What is the problem here? Obviously, gcc is able to locate and link with libpthread.so, because otherwise the linker wouldn't have been able to resolve reference to pthread_attr_init. So why it couldn't resolve reference to pthread_join? Aren't all the functions from pthread reside in libpthread.so?

 BTW, I still use Breezy.[/SIZE]

---

### Post by LordHunter317 on 2006-08-09
No, that's not true.

GLIBC includes some of the pthread functions because it needs them internally.  However, it doesn't need all of them, so it doesn't include all of them.  Run nm on a non-stripped libc image if you don't believe me.

Pass -pthread to the compiler to compile pthread using code.  There's more to define than just the extra library (On Linux, just -DREENTRANT AFAIK).

---

