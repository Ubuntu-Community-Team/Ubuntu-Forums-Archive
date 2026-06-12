---
title: "undefined reference to strcmp in C"
date: 2008-08-10
forum: Programming Talk
---

### Post by jon zendatta on 2008-08-10
hell0..i'm a learner learning slowly. my problem is a comparison between string constant & string variable.
#include <stdio.h>
#include <string.h>

main ()
{
   int bins, kgs, packout, dollars_total, dollars_ha ;
   float net_kg, net_cartons, dollars_per_carton;
   float bb = 2.5,
         rg = 1.0,
         f = 1.85,
         pb = 0.5,
         pr = 0.55,
         pq = 0.25,
         gs = 0.5;
   char str1[] = "braeburn";
   char str2[] = "royal gala";
   char str3[] = "fuji";
   char str4[] = "pacific beauty";
   char str5[] = "pacific queen";
   char str6[] = "pacific rose";
   char str7[] = "granny smith";
   char cultivar [15];

   printf("please enter cultivar\n", cultivar);
   scanf("%s", &cultivar);
   printf("number of bins\n", bins);
   scanf("%d", &bins);
   printf("enter packout\n", packout);
   scanf("%d", &packout);

   kgs = (bins * 320);
   net_kg = (int)(kgs * packout);
   net_cartons = (int)(net_kg / 18);

   printf("enter $ per carton\n", dollars_per_carton);
   scanf("%f", &dollars_per_carton);

   dollars_total = (int)(dollars_per_carton * net_cartons); 

   if (!(strcmp(cultivar, "braeburn") == 0))
   {
   dollars_ha = (int)(dollars_total / bb);
   printf("returns $%d per ha\n", dollars_ha);
   }
   if (!(strcmp (cultivar, "royal gala") == 0))
   {
   dollars_ha = (int)(dollars_total / rg);
   printf("returns $%d per ha\n", dollars_ha);
   } 
   if (!(strmcp (cultivar, "fuji") == 0))
   {
   dollars_ha = (int)(dollars_total / f);
   printf("returns $%d per ha\n", dollars_ha);
   }
   if (!(strcmp (cultivar, "pacific beauty") == 0))
   {
   dollars_ha = (int)(dollars_total / pb);
   printf("returns $%d per ha\n", dollars_ha);
   }
   if (!(strcmp (cultivar, "pacific queen") == 0))
   {
   dollars_ha = (int)(dollars_total / pq);
   printf("returns $%d per ha\n", dollars_ha);
   }
   if (!(strcmp (cultivar, "pacific rose") == 0))
   {
   dollars_ha = (int)(dollars_total / pr);
   printf("returns $%d per ha\n", dollars_ha);
   }
   if (!(strcmp (cultivar, "granny smith") == 0))
   {
   dollars_ha = (int)(dollars_total / gs);
   printf("returns $%d per ha\n", dollars_ha);
   }
}

---

### Post by jon zendatta on 2008-08-10
ps: that happy face ain't supposed to be there either.

cheers

---

### Post by lisati on 2008-08-10
> **jon zendatta said:**
> ps: that happy face ain't supposed to be there either.

cheers
The happy face is something to do with the way the forums interpret certain character strings.....something to think about while other forum members are contemplating a reply to your original question.

EDIT: Possible typo: there's a "strmcp" there instead of a "strcmp" where you're checking for fuji.

---

### Post by -grubby on 2008-08-10
Enclosing that in [ code ] tags (no spaces) would greatly increase legibility and we could see any indentation you had, and probably get rid of the smiley too. Too bad I can't help you with any of that C

---

### Post by jon zendatta on 2008-08-10
i don't think indentation makes a scrap of difference nathan. 41 + 1 = 42 thank you - perhaps i should've posted this in 'absolute beginners.

---

### Post by -grubby on 2008-08-10
> **jon zendatta said:**
> i don't think indentation makes a scrap of difference nathan. 41 + 1 = 42 thank you - perhaps i should've posted this in 'absolute beginners.

I wasn't saying that it did, but [ code ] still further segregates it from the page. Although I'm biased towards indentation because I use Python all the time

---

### Post by nrs on 2008-08-10
Because you're not typing strcmp ;-)

---

### Post by nrs on 2008-08-10
[LIST]
[*]Indentation makes a difference for people trying to read it
[*]Not using [code] murders your syntax
[*]int yo main
[/LIST]

---

### Post by LaRoza on 2008-08-10
> **nathangrubb said:**
> Enclosing that in [ code ] tags (no spaces) would greatly increase legibility and we could see any indentation you had, and probably get rid of the smiley too. Too bad I can't help you with any of that C

> **jon zendatta said:**
> i don't think indentation makes a scrap of difference nathan. 41 + 1 = 42 thank you - perhaps i should've posted this in 'absolute beginners.

Yes it does. If you posted it, you expect someone to read it. If you want someone to read it, make it not hard to read. Posting code in code or php tags is not only a good idea, but it is almost required (most people won't even read it without proper formatting)

Also, you declared main improperly (although that might only throw a warning, you shouldn't silently accept it)

---

### Post by lisati on 2008-08-10
Hey, I just noticed that I was born in the town showing in the OP's current location......

---

### Post by cmay on 2008-08-10
to answer the question about undefined reference to strcmp.
you need to include <string.h>

```
#include <stdio.h>
#include <string.h> /* you need to include string to use strcmp*/
int main(int argc, char** argv)
{
	char hi_there[]="hello";
	if( strcmp(hi_there,"hello")==0){
		printf("hello world");
	}
	
	return 0;
}

```
hope it helped.

btw
i am newbie too so please dont kill me if it does not work :)

---

### Post by nrs on 2008-08-10
> **cmay said:**
> to answer the question about undefined reference to strcmp.
you need to include <string.h>

```
#include <stdio.h>
#include <string.h> /* you need to include string to use strcmp*/
int main(int argc, char** argv)
{
	char hi_there[]="hello";
	if( strcmp(hi_there,"hello")==0){
		printf("hello world");
	}
	
	return 0;
}

```
hope it helped.

btw
i am newbie too so please dont kill me if it does not work :)

He did include <string.h>. Check the image I attached earlier.

---

### Post by cmay on 2008-08-10
sorry i did not see that.
i pasted the code from the first post and tried to compile it.
lots of errors. maybe i did not get the whole thing copied.
i was only trying to be helpfull.

nevermind my post then.

---

### Post by nrs on 2008-08-10
> **cmay said:**
> sorry i did not see that.
i pasted the code from the first post and tried to compile it.
lots of errors. maybe i did not get the whole thing copied.
i was only trying to be helpfull.

nevermind my post then.

It took me a minute or two to catch on myself. :(

---

### Post by jamescox84 on 2008-08-10
What command are you using to compile your program. using `ld' to link your objects files often leads to this problem, as the standard c library is not linked by default using `ld' to the resulting executable.

Compile a single source file like this:
```

gcc your_source_file -o executable_name

```

If you still get error maybe the standard C library development files aren't installed, try:
```

sudo apt-get install libc6-dev

```

---

