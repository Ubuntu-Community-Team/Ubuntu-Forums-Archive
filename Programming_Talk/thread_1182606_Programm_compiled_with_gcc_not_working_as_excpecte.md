---
title: "Programm compiled with gcc not working as excpected"
date: 2009-06-09
forum: Programming Talk
---

### Post by Bartuk on 2009-06-09
Hi there,
So i have a problem with a program i've written in C and compiled it using the standart gcc(gcc-Version 4.3.3 (Ubuntu 4.3.3-5ubuntu4))
actually i dont know if its a gcc bug or only my crappy coding skills.
so heres the complete code:
```
#include <stdio.h>
struct kombi
{
	char bezeichnung[20];
	double zet;
	char atyp;
};
void show(struct kombi *kombi_ptr){
printf("Bezeichnung: %s\n",(kombi_ptr)->bezeichnung);
printf("Zet: %f\n",(kombi_ptr)->zet);
printf("Atyp: %c\n",(kombi_ptr)->atyp);
}
int main (void)
{
	struct kombi kombi_obj, *ptr;
	ptr = &kombi_obj;
	printf("bitte Bezeichnung eingeben:");
	fgets(kombi_obj.bezeichnung,sizeof(kombi_obj.bezeichnung),stdin);
	printf("bitte zet eingeben:");
	scanf("%lf",&kombi_obj.zet);
	fflush(stdin);
	printf("bitte atyp eingeben:");
	kombi_obj.atyp=getchar();
	show(ptr);
	return 0;
}
```
it compiles just fine without any warnings or errors.
as you can see it should ask the user to enter 3 values.
the problem is that it will ask the first 2 values and just skip the third one.
the output looks like this:
```
bitte Bezeichnung eingeben:bla
bitte zet eingeben:123
bitte atyp eingeben:Bezeichnung: bla

Zet: 123.000000
Atyp: 

```

i send the code to a friend using M$ visual studio and it just ran fine.
on the other hand i did send it to a friend using debian and it made the same as on my ubuntu.

could someone please point to me where the error is?
greetings and thanks for your advice
Bartuk

---

### Post by dwhitney67 on 2009-06-09
The fflush() is not doing what you would expect.  It is useful for flushing stdout, but AFAIK, it does not work for stdin.

The newline character that you entered after double value is still awaiting to be read.  When the getchar() is invoked, it reads the newline.

See if this modified scanf() works for you:
```

scanf("%lf%c",&kombi_obj.zet);

```
and of course, remove the fflush().

---

### Post by Bartuk on 2009-06-09
allright i tried the modified scanf you posted.
at first it wasnt working, i had to add a space between %lf and %c,
it read the character correctly, but it didnt solve my problem couse i wanted to have a printf before entering the next value.
maybe i missunderstood something.
i enterd the following code:
```
scanf("%lf %c",&kombi_obj.zet,&kombi_obj.atyp);
```
thanks for the reply.

---

### Post by Linteg on 2009-06-09
It should be working without the space, just copy & paste. It will however cause a warning (when using -Wall). If you want to avoid it you could always write:
```
scanf("%lf",&kombi_obj.zet);
getchar();
```
Which pretty much does the same thing.

And you don't need a \n when you print the Bezeichnung, fgets stores the trailing newline.

---

### Post by Bartuk on 2009-06-09
Ah now i see :)
i missunderstood the warning and thought it hadnt compiled...
so now its working. :)
is there some "cleaner" way to get this working?
or are these warnings or getchar()s after reading a float variable normal use in C?
thanks for the help

PS: oh and what do i do, if i want it to compile and work with linux and windows?
i mean it was working in windows as i had it before without the extra %c or getchar().

---

### Post by Linteg on 2009-06-09
You could use ifdef (if defined) and ifndef (if not defined), like:
[php]
int main()
{
	code...

#ifdef WINDOWS
	windows specific code
#endif

	more code...

#ifndef WINDOWS
	linux specific code
#endif
}[/php]
And then compile with -DWINDOWS if you want it to be defined.

---

### Post by Bartuk on 2009-06-09
ah ok thought about that.
thanks for your help

---

### Post by Lux Perpetua on 2009-06-09
> **Bartuk said:**
> Ah now i see :)
i missunderstood the warning and thought it hadnt compiled...
so now its working. :)
is there some "cleaner" way to get this working?
or are these warnings or getchar()s after reading a float variable normal use in C?
thanks for the helpOf course: use fgets to get an entire line of the user's input, and use sscanf to parse it. Then you don't have to worry about this "flushing" business at all: if the user gives you extra spaces or junk after the input proper, then you just ignore it. This approach is much more flexible than trying to use scanf to parse the input directly, so I'd recommend learning it now. 
[quote=Bartuk]PS: oh and what do i do, if i want it to compile and work with linux and windows?
i mean it was working in windows as i had it before without the extra %c or getchar().[/QUOTE]Write portable code. Sometimes you have to make use of functionality for which the interface depends on the operating system (like inter-process communication or dealing with the filesystem, for example), but this is not one of those times. The C standard does not allow you to fflush an input stream, so if you want your code to compile on Linux and Windows, the correct approach is simply to avoid such practices.

---

