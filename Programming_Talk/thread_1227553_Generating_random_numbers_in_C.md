---
title: "Generating random numbers in C"
date: 2009-07-30
forum: Programming Talk
---

### Post by themusicalduck on 2009-07-30
Is there a way in C to generate a number of random integers within parameters and then save them into an array?

Basically I need it to generate 8 numbers between say 0-8, save them into an 8 integer array declared in a typedef struct and then stop. It would need to be done using pointers to the array.

---

### Post by snova on 2009-07-30
> **themusicalduck said:**
> Is there a way in C to generate a number of random integers within parameters and then save them into an array?

Basically I need it to generate 8 numbers between say 0-8, save them into an 8 integer array declared in a typedef struct and then stop. It would need to be done using pointers to the array.

You would need the **rand()** function.

[PHP]int num = rand() % max + min;[/PHP]

---

### Post by themusicalduck on 2009-07-30
Perfect! thanks a lot :)

---

### Post by Mirge on 2009-07-30
You should also call srand(...). IE:

srand(time(NULL)); // just need to call this once in the program.

Otherwise you'll end up with the same random numbers.

---

### Post by dwhitney67 on 2009-07-30
Don't forget to seed the random number generator with a large number (eg. the current system time, in seconds) before using the rand() function.
```

#include <time.h>
#include <stdlib.h>

int main()
{
   srand(time(0));

   ...

   unsigned int min = 0;
   unsigned int max = 8;
   unsigned int num = rand() % max + min;

   ...
}

```

---

### Post by themusicalduck on 2009-07-30
How can I tell it to save the generated numbers into an array?

So far I have a switch case structure inside a loop. It compares with count %15 so that it runs through each case and saves the current generated number in an array position. When the count reaches 15, the loop should stop.

This is what I have so far 

```
void uwemax_generator(t_uwemax *x, int note, int count, int min, int max, int time)
{
	count = 0;
	min = 0;
    max = 8;

   while(count < 16)
   {
	
	//srand(time(0));
  

   
   int note = rand() % max + min;


	switch(count %15)
	{
		case 0:
			x->u_pitch[x->sequence[0] = note];
			break;
		case 1:
			x->u_pitch[x->sequence[1] = note];
			break;
		case 2:
			x->u_pitch[x->sequence[2], note];
			break;
		case 3:
			x->u_pitch[x->sequence[3], note];
			break;
		case 4:
			x->u_pitch[x->sequence[4], note];
			break;
		case 5:
			x->u_pitch[x->sequence[5], note];
			break;
		case 6:
			x->u_pitch[x->sequence[6], note];
			break;
		case 7:
			x->u_pitch[x->sequence[7], note];
			break;
		case 8:
			x->u_pitch[x->sequence[8], note];
			break;
		case 9:
			x->u_pitch[x->sequence[9], note];
			break;
		case 10:
			x->u_pitch[x->sequence[10], note];
			break;
		case 11:
			x->u_pitch[x->sequence[11], note];
			break;
		case 12:
			x->u_pitch[x->sequence[12], note];
			break;
		case 13:
			x->u_pitch[x->sequence[13], note];
			break;
		case 14:
			x->u_pitch[x->sequence[14], note];
			break;
		case 15:
			x->u_pitch[x->sequence[15], note];
			break;
	}
		
   count = (count + 1);

   }
}
```

srand(time(0)); caused an error, so is commented out. I'll try to sort out later.

The error says "error C2109: subscript requires array or pointer type" for each case.

I have used a pointer.. and the script looks very similar to someones code who did a similar project. I think I'm missing something obvious but I could just be using the function wrong.

---

### Post by Reiger on 2009-07-30
Look into control structures. Why not try restructuring your code using a for loop with an index variable?

Also, I thought that you only needed to call srand() once, as long as you call it before you call rand(). The idea being that since rand() isn't a true random number generator (in other words it is a fixed sequence of values), to obtain the illusion of randomness you need to seed it once with a unique value (essentially, perform a unique transformation on the rand function) which can be done using system time.

---

### Post by veda87 on 2009-07-31
> x->u_pitch[x->sequence[0] = note];
i don't get how u have made your declaration....
Is both pitch and sequence are array....

it seems u r assigning **note to x->sequence[0]** then wat is the need of **u_pitch** there...
u might do something like this > x->u_pitch[x->sequence[0] = note] = anyvalue;

then there is no need for a **case15** in your program....

---

### Post by lisati on 2009-07-31
> **snova said:**
> You would need the **rand()** function.

[PHP]int num = rand() % max + min;[/PHP]

Wouldn't that result in numbers from min to min+max?

---

### Post by dwhitney67 on 2009-07-31
> **lisati said:**
> Wouldn't that result in numbers from min to min+max?

Yes, without thinking, I made the same mistake when I posted earlier.  Probably something like this would work for numbers in the range of (min, max]:
```

unsigned int num = rand() % (max - min) + min;

```

---

### Post by dwhitney67 on 2009-07-31
@ the OP

Adopt the following to satisfy your programming requirements.  It appears that you are developing under M$.  Perhaps you should consider posting queries on another forum that would offer you specific M$-C support.

```

#include <time.h>
#include <stdlib.h>
#include <stdio.h>

struct Data
{
   unsigned int num;
};

void initializeData(struct Data* data, unsigned int dataSize, unsigned int min, unsigned int max);

int main()
{
   struct Data array[15];

   initializeData(array, sizeof(array) / sizeof(struct Data), 0, 8);

   for (unsigned int i = 0; i < sizeof(array) / sizeof(struct Data); ++i)
   {
      printf("array[%d].num = %d\n", i, array[i].num);
   }

   // ...

   return 0;
}

void initializeData(struct Data* data, unsigned int dataSize, unsigned int min, unsigned int max)
{
   srand(time(0));   // for M$ s/w weenies, you may be required to explicitly specify NULL in lieu of 0

   for (unsigned int i = 0; i < dataSize; ++i)
   {
      (data + i)->num = rand() % (max - min) + min;
   }
}

```

---

### Post by Nemooo on 2009-07-31
Depending on how important the randomness is required to be, you might want to read [Using rand()]("http://eternallyconfuzzled.com/arts/jsw_art_rand.aspx") and eventually [Random Numbers]("http://eternallyconfuzzled.com/tuts/algorithms/jsw_tut_rand.aspx") by the same author.

---

### Post by themusicalduck on 2009-07-31
I've persuaded my current code to work, and the array seems to be setting itself and outputting the ints correctly. However the rand function doesn't seem to be working so well. It doesn't essentially need to be completely random in particular, but in this case the output seems to consist mostly of 0s and duplicated numbers in consecutive order, which doesn't seem very random. This is without the srand(time(0)); line included, because it gives an error:

"error C2063: 'time' : not a function" and "C2143: syntax error : missing ';' before 'type'" Even though there appears to be a ;.

This is the code so far ```
while(count < 16)
   {
	
	srand(time(0));
  

   
   int note = rand() % (max - min) + min;

   //int notes[15];

	switch(count %15)
	{
		case 0:
			x->sequence[0] = note;
			outlet_int(x->u_outlet, x->sequence[note]);
			break;
		case 1:
			x->sequence[1] = note;
			outlet_int(x->u_outlet, x->sequence[note]);
			break;
```

ommitted the other cases so it's shorter.. outlet_int(x->u_outlet, x->sequence[note]); is specific to max/msp api.

Thankyou for the code dwhitney, but because this is getting close to working and I'm finding your code a little more difficult to follow I'm going to try and continue with this. Plus I couldn't only copy and paste your code into the program for risk of plagarism (it's for an assignment)

Thanks for the replies so far, it's nearly there!

---

### Post by Can+~ on 2009-07-31
> **themusicalduck said:**
> ```
while(count < 16)
   {
	
	srand(time(0));
  

   
   int note = rand() % (max - min) + min;

   //int notes[15];

	switch(count %15)
	{
		case 0:
			x->sequence[0] = note;
			outlet_int(x->u_outlet, x->sequence[note]);
			break;
		case 1:
			x->sequence[1] = note;
			outlet_int(x->u_outlet, x->sequence[note]);
			break;
```

That [FONT="Courier New"]switch[/FONT] seems kinda redundant, it's basically doing the same thing but with the index changed, in essence:

[PHP]x->sequence[count%15] = note;
outlet_int(x->u_outlet, x->sequence[note]);[/PHP]

You should include <time.h> also.

*It's kinda funny that I coded something quick as my solution, at it was basically the same thing as Dwhitney's (minus the style of accessing data with [FONT="Courier New"](base+offset)->value[/FONT] (I used [FONT="Courier New"][][/FONT] for readability))

---

### Post by Reiger on 2009-07-31
@OP do look into dwhitney's code a bit further. It contains a fair few "idiomatic" C things which, if you want to learn C that is, should know about. In particular look at the pointer arithmetic and the correspondence between a pointer to something and an array of something.

---

### Post by themusicalduck on 2009-08-01
I've fixed it to use that line instead of the case switch. For some reason srand still gives the same errors though even with #include <time.h> in the source.

---

### Post by Mirge on 2009-08-01
> **themusicalduck said:**
> I've fixed it to use that line instead of the case switch. For some reason srand still gives the same errors though even with #include <time.h> in the source.

post full source please

---

### Post by themusicalduck on 2009-08-01
This is the source in its entirety so far, mess and all..

[http://pastebin.com/m7f5eaa60](http://pastebin.com/m7f5eaa60)

It's compiled with the max/msp framework and is supposed to be used as an object in a max patch if that could cause problems for any reason..

---

### Post by smartbei on 2009-08-01
You are getting as input to the function with the srand in it (uwemax_generator) an int with the name 'time'... I think that is the problem.

---

### Post by themusicalduck on 2009-08-01
That was the problem.. Thanks a lot. :)

---

