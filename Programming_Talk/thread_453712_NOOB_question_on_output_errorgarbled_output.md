---
title: "NOOB question on output error/garbled output"
date: 2007-05-24
forum: Programming Talk
---

### Post by timdoc1 on 2007-05-24
I have a simple program (for a class) that I have been able to run at school properly:

/* PUBLIC DOMAIN. BY TOM VAJZOVIC */
#include <pthread.h>
#include <stdlib.h>
#include <stdio.h>
void *thread_func( void *vptr_args );
int main( void ){
int i, j;
pthread_t thread;
pthread_create( &thread, NULL, &thread_func, NULL );
for( j= 0; j < 20; ++j ){
fprintf( stdout, "a\n" );
for( i= 99999999; i; --i ); /* use some CPU time */
}
pthread_join( thread, NULL );
exit( EXIT_SUCCESS );
}

void *thread_func( void *vptr_args ){
int i, j;
for( j= 0; j < 20; ++j ){
fprintf( stderr, " b\n" );
for( i= 99999999; i; --i ); /* use some CPU time */
}
pthread_exit( NULL );
}



It just prints out "A"'s and "B"'s to stdio -worked using Cygwin,

Now I tried it on my NOOB Fiesty install and I get garbage. Your help is appreciated.
Is it a compilation library problem?
I have installed:

libc6
libc6-amd64
libc6-dev
libc6-dev-amd64

Below is the output:
^?ELF^A^A^A^@^@^@^@^@^@^@^@^@^B^@^C^@^A^@^@^@<80>< 84>^D^H4^@^@^@T^O^@^@^@^@^@^@4^@ ^@^G^@(^@$^@!^@^F^@^@^@4^@^@^@4<80>^D^H4<80>^D^Hà^ @^@^@à^@^@^@^E^@^@^@^D^@^@^@^C^@^@^@^T^A^@^@^T<81> ^D^H^T<81>^

---

### Post by WW on 2007-05-24
The "output" that you are showing appears to be the compiled program, not the output of the program.  Please show the commands that you used to compile and run your program.

Also, it would be helpful if you enclosed your program listings inside the tags [color=blue][ code ][/color] and [color=blue][ /code ][/color] (but without the spaces inside the brackets.  That way, instead of this:
for (i = 0; i < 10; ++i) {
printf("%d\n",i);
}
we will see this:
```

for (i = 0; i < 10; ++i) {
    printf("%d\n",i);
}

```

---

### Post by timdoc1 on 2007-05-24
No ****.  I am such an idiot!!! You are right.
So I changed the executable  "chmod +x a.out" and then issue the command "a.out"
And it still does not execute.

bash: a.out :command not found

---

### Post by WW on 2007-05-24
a.out will be executable automatically.  Run it by putting **./** in front of it:
```

./a.out

```

---

### Post by tht00 on 2007-05-25
> **WW said:**
> a.out will be executable automatically.  Run it by putting **./** in front of it:
```

./a.out

```

And just to clarify why this happens, when a command is executed in the terminal/BASH, it looks for that command in various locations on the computer (/usr/local/bin, /bin, etc.).  To execute a local command, you have to explicitly tell it where it is.  In this case, ./ is essentially saying 'this directory'.

Again, just for clarification.  There is a how/why behind the madness. ;)

---

