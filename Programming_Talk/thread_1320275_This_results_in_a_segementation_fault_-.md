---
title: "This results in a segementation fault -"
date: 2009-11-09
forum: Programming Talk
---

### Post by dE_logics on 2009-11-09
```
#include<stdio.h>
main()
{
	char input[1000];
	short from = 0;
	short jockey = 0;
	input[0] = 'a';
	while(input[from] != '!')
	{
		if(from > 0)
			from++;
		input[from] = getchar();
		if(from == 0)
			from++;
	}
	input[from] = '\0';
	from = 0;
	while(input[jockey] != '\n' || input[jockey] != '\0')
			jockey++;
		jockey--;
}
```

But why?

---

### Post by Arndt on 2009-11-09
> **dE_logics said:**
> ```
#include<stdio.h>
main()
{
	char input[1000];
	short from;
	short jockey = 0;
	while(input[from] != '!')
	{
		if(from > 0)
			from++;
		input[from] = getchar();
		if(from == 0)
			from++;
	}
	input[from] = '\0';
	from = 0;
	while(input[jockey] != '\n' || input[jockey] != '\0')
			jockey++;
		jockey--;
}
```

But why?

You should initialize 'from' to something. 0 perhaps? As it is now, it's undefined. It could be 3425141.

---

### Post by dE_logics on 2009-11-09
That did not work.

---

### Post by MadCow108 on 2009-11-09
also your input[0] is unitialized
make a getchar before the while do loop
or replace it with a do while loop

your loop condition is always true so (a char can't be both newline and null) so it runs infinitly (or until segfault)

and you're missing boundary checks so it may segfault in both loops because of wrong input

---

### Post by Arndt on 2009-11-09
> **dE_logics said:**
> That did not work.

The program seems to count on there being a '!' in 'input'. How does it arrive there?

How is the problem formulated that you're trying to solve? Is it homework?

---

### Post by dE_logics on 2009-11-09
> **MadCow108 said:**
> also your input[0] is unitialized
make a getchar before the while do loop
or replace it with a do while loop

your loop condition is always true so (a char can't be both newline and null) so it runs infinitly (or until segfault)

and you're missing boundary checks so it may segfault in both loops because of wrong input

Initializing input[0] did not work...thanks for telling that.

No, I would not like to use do while (starting off with programing after a long time).

I'm assuming the input to have multiple lines...so there will be a \n but there will always be a '\0' I think - 

```
	input[from] = '\0';
```

---

### Post by dE_logics on 2009-11-09
> **Arndt said:**
> The program seems to count on there being a '!' in 'input'. How does it arrive there?

The use has to input a '!' It's a necessity.

> 
How is the problem formulated that you're trying to solve? Is it homework?

No, I never do homework.

Actually there's an accumulation of source tarballs (I've switched to Gentoo) that's occupying lots of space...so I was wondering about removing the old version of every sources tarball.

This is a cornered part of the program which finds such duplicates.

---

### Post by Arndt on 2009-11-09
> **dE_logics said:**
> The use has to input a '!' It's a necessity.





There's no trace of obtaining any user input in your program.

---

### Post by dE_logics on 2009-11-09
> **Arndt said:**
> There's no trace of obtaining any user input in your program.

What about getchar()?...it's in stdio.

---

### Post by Arndt on 2009-11-09
> **dE_logics said:**
> What about getchar()?...it's in stdio.

Sorry, that's obviously user input. But I was focused on the loop test. The first time it is encountered, nothing has been read yet.

---

### Post by efexD on 2009-11-09
int main would be start

---

### Post by MadCow108 on 2009-11-09
have you fixed your infinity loop?
that is your main problem and the reason for the segfault
(and input needs initializing)

---

### Post by dE_logics on 2009-11-09
> **Arndt said:**
> Sorry, that's obviously user input. But I was focused on the loop test. The first time it is encountered, nothing has been read yet.

hummm...I sorta didn't get that.

[QUOTE=MadCow108]have you fixed your infinity loop?
that is your main problem and the reason for the segfault
(and input needs initializing)[/QUOTE]

But I do not know how it's forming an infinite loop, for e.g this is the input - 

> 
gentoo-sources-2.6.30-r4
gentoo-sources-2.6.30-r5!

Then how can it from an infinite loop?

There's a \n and a \0.

while(input[jockey] != '\n' || input[jockey] != '\0') will end if it encounters a \n or \0.

---

### Post by Arndt on 2009-11-09
> **dE_logics said:**
> hummm...I sorta didn't get that.



But I do not know how it's forming an infinite loop, for e.g this is the input - 



Then how can it from an infinite loop?

There's a \n and a \0.

while(input[jockey] != '\n' || input[jockey] != '\0') will end if it encounters a \n or \0.

No, it will continue if it encounters something that is either not \n or not \0. Think about it, it's not the same thing. Imagine that input[jockey] is \n and do every tiny step of the above in your head.

---

### Post by StunnerAlpha on 2009-11-09
> **dE_logics said:**
> hummm...I sorta didn't get that.



But I do not know how it's forming an infinite loop, for e.g this is the input - 



Then how can it from an infinite loop?

There's a \n and a \0.

while(input[jockey] != '\n' || input[jockey] != '\0') will end if it encounters a \n or \0.

This:
```

while(input[jockey] != '\n' || input[jockey] != '\0')

```
...needs to be:
```

while(input[jockey] != '\n' && input[jockey] != '\0')

```
Because the loop needs to keep looping while the item from the array is not equal to '\n' AND '\0'. It needs to not be equal to either of them, thus you would use &&(and) instead of ||(or).

---

### Post by dwhitney67 on 2009-11-09
Right, the && is needed.

Hopefully the OP will see the need to clean up the code:
```

#include<stdio.h>

int main()
{
   char input[1000];
   short from = 0;
   short jockey = 0;

   input[from++] = 'a';

   while((from < sizeof(input) - 1) && (input[from - 1] != '!'))
   {
      input[from++] = getchar();
   }

   input[from] = '\0';

   while(input[jockey] != '\n' && input[jockey] != '\0')
   {
      ++jockey;
   }
   --jockey;

   /* and then what??? */

   return 0;
}

```

---

### Post by Arndt on 2009-11-09
> **dwhitney67 said:**
> Right, the && is needed.

Hopefully the OP will see the need to clean up the code:
```

#include<stdio.h>

int main()
{
   char input[1000];
   short from = 0;
   short jockey = 0;

   input[from++] = 'a';

   while((from < sizeof(input) - 1) && (input[from - 1] != '!'))
   {
      input[from++] = getchar();
   }

   input[from] = '\0';

   while(input[jockey] != '\n' && input[jockey] != '\0')
   {
      ++jockey;
   }
   --jockey;

   /* and then what??? */

   return 0;
}

```

I think he may be sitting and waiting until we're done repairing his program...

---

### Post by dE_logics on 2009-11-10
Yes, I got it.

Thanks!

---

