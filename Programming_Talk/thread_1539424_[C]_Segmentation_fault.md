---
title: "[C] Segmentation fault"
date: 2010-07-26
forum: Programming Talk
---

### Post by SpinningAround on 2010-07-26
Keep getting segfault with this code, it compiles fine (gcc -std=c99) but it don't run, don't understand why.

verktyg.h
[PHP]
extern char *reportTraffic(long trafficBytes, int level);
extern void debug(void);
[/PHP]

verktyg.c
[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "verktyg.h"
void debug(void){
	static char msg[]="debug";
	static int x=1;
	printf("%s %d",msg,x);
	x++;
}

char *reportTraffic(long trafficBytes,int level){
	debug();
	int x=0;
	long temp;
	static char msg[30]="";
	char *s;
	debug();
	if((x<=level) && (temp=trafficBytes/(long)1e9)>0){
		sprintf(s," %ld GB",temp);
		strcat(msg,s);
		trafficBytes-=(temp*(long)1e9);
		x++;
	}
	if((x<=level) && (temp=trafficBytes/(long)1e6)>0){
		sprintf(s," %ld MB",temp);
		strcat(msg,s);
		trafficBytes-=(temp*(long)1e6);
		x++;
	}
	if((x<=level) && (temp=trafficBytes/(long)1e3)>0){
		sprintf(s," %ld kB",temp);
		strcat(msg,s);
		trafficBytes-=(temp*(long)1e3);
		x++;
	}
	if((x<=level) && (temp=trafficBytes)>0){
		sprintf(s," %ld byte",temp);
		strcat(msg,s);
		x++;
	}
	return msg;
}

int main(void){
	traffic("eth0");
	debug();
	reportTraffic((long)123456,(int)3);
}
[/PHP]

---

### Post by Simian Man on 2010-07-26
People aren't likely to want to debug your code for you.  Have you used the debugger?  If so what line of code causes the segfault?

<edit>
Nevermind I can tell one of your problems just by looking at your code.  You try to use sprintf to sotre a string in the well-named variable "s", but it doesn't have any space allocated to it.  You should allocate some as you did for "msg".

---

### Post by SpinningAround on 2010-07-26
> **Simian Man said:**
> People aren't likely to want to debug your code for you.  Have you used the debugger?  If so what line of code causes the segfault?

<edit>
Nevermind I can tell one of your problems just by looking at your code.  You try to use sprintf to sotre a string in the well-named variable "s", but it doesn't have any space allocated to it.  You should allocate some as you did for "msg".

Thanks :) Don't have a debugger, is there any you would recommend?

---

### Post by nmaster on 2010-07-26
gdb is the one people usually use.
[http://en.wikipedia.org/wiki/GNU_Debugger](http://en.wikipedia.org/wiki/GNU_Debugger)

---

### Post by splicerr on 2010-07-26
Crash course debugging segfaults :).

[LIST=1]
[*]Compile your app with debug info (-g)
[*]Open a terminal
[*]ulimit -c unlimited
[*]start your app, and watch it dump core
[*]gdb ./myapp core
[*]bt
[/LIST]

---

### Post by MadCow108 on 2010-07-27
you don't need to dump the core during development.
just run the application in gdb from the beginning.
gdb ./app or gdb --args ./app --argument
run
backtrace

---

### Post by Linteg on 2010-07-27
.

---

### Post by WitchCraft on 2010-07-27
You don't even need a debugger for this, just use your brain:

```

 [COLOR="Red"]char *s;[/COLOR] 
    debug(); 
    if((x<=level) && (temp=trafficBytes/(long)1e9)>0){ 
        [COLOR="Red"]sprintf(s," %ld GB",temp);[/COLOR] 

```


This should be char s[20];
You're declaring a pointer, NOT an array. 

Then you write to memory where you don't have write access permission to --> memory access violation --> segmentation fault.


Note:
char* s; is the same as const char* s;
which is not the same as char s[];

and both are not the same as char s[n>=0]

---

### Post by trent.josephsen on 2010-07-27
Note that if you use char s[N] like WitchCraft suggests, you would be well advised to use snprintf rather than sprintf, as it will prevent accidentally writing past the end of the string.  There are other ways to avoid  this; careful construction of the format string is one possibility.

I'm not sure what WitchCraft means by saying "char *s" and "const char *s" are the same thing; they obviously aren't, but perhaps I misunderstood.

---

### Post by WitchCraft on 2010-07-28
> **trent.josephsen said:**
> Note that if you use char s[N] like WitchCraft suggests, you would be well advised to use snprintf rather than sprintf, as it will prevent accidentally writing past the end of the string.  There are other ways to avoid  this; careful construction of the format string is one possibility.

I'm not sure what WitchCraft means by saying "char *s" and "const char *s" are the same thing; they obviously aren't, but perhaps I misunderstood.

Well ok, with const char* you cannot even change the pointer, and that's indeed a difference.

I meant the data it points to, but thanks for the correction, you're of course right.

---

### Post by trent.josephsen on 2010-07-28
No, "const char *s" means that *s (the char s points to) is read-only.  You're thinking of "char * const s" which would imply that the pointer itself is read-only.  You could pass the latter to the first argument of sprintf (which expects char*), but not the former (well, not without violating its const-ness).

Declaration follows use.
```
int const *i; // *i is readonly; *i is int (i: pointer to const int)
int * const j; // j is readonly; *j is int (j: const pointer to int)
int const * const k; // k is readonly; *k is readonly; *k is int (k: const pointer to const int)
i = &number; // okay
j = &number; // constraint violation
```
That's why I personally prefer "<type> const" instead of "const <type>"; it makes the parsing easier (the way I do it).

---

