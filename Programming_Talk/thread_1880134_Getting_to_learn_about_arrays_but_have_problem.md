---
title: "Getting to learn about arrays but have problem"
date: 2011-11-13
forum: Programming Talk
---

### Post by ClientAlive on 2011-11-13
Hi,

Ok, so, I guess I get to learn about arrays in class too. Problem is, I use the same syntax our instructor shows us and get a compile error. I'd look for it on the internet but I'm not sure what you even call what gcc is telling me.

So our instructors tells us:

> 
int a[10];

int i;
for (i=0; i<10; ++i)
{
printf(&#8220;%i\n&#8221;, a[i]);
}


I try to get slick with it and see if I can make it do something cool and learn something at the same time, so I write:

```

#include <stdio.h>

int main (void)

{

int x, i, j, ttl;

printf("How many numbers will you be entering today? \n");
scanf("%i", &ttl);

int num[ttl];

	for(i=0; i<ttl; ++i)
		{
		printf("Enter a number: \n");
		scanf("i", &num[i]);
		}

        printf("The numbers you entered are: \n");
		
	for(j=0; j<=i; ++j)
		{
                printf("%i\n", &num[j]);
		}

}


```

I run it throught the compliler (or try to), and I get:

```

 ~/ProgrammingPlayground/Array-Practice > gcc Array-Practice[01].c -o Array-Practice.bin
Array-Practice[01].c: In function &#8216;main&#8217;:
Array-Practice[01].c:24: warning: format &#8216;%i&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;int *&#8217;

```

What the heck is a "int *" and how come when I write the same thing our instructor shows it gives me this kind of grief?

:confused:

---

### Post by 1clue on 2011-11-13
My c experience is fairly old, but I can help a little.

int* is a pointer to an int.  It's an alternate array notation, so that's your array.

---

### Post by squenson on 2011-11-13
I may be wrong but instead of:```
		scanf("i", &num[i]);

```try:```
		scanf("%i", &num[i]);

```

---

### Post by ClientAlive on 2011-11-13
> **squenson said:**
> I may be wrong but instead of:```
		scanf("i", &num[i]);

```try:```
		scanf("%i", &num[i]);

```


Yup. That was right. That's odd. I guess even instructors can make a mistake. I copy/ pasted that right from our notes. Unless she's just intentionally trying to be tricky but that would suck.

So the program doesn't do what I was shooting for but that's ok. It compiles and now I have something to work from and get it sorted out.

Thanks man.
--------------------

Edit:

I just noticed this. Actually when I applied your advice I must have read what you wrote upside down to begin with. I had the % sign in there to begin with and had the problem when it was like that. It's when you remove the % sign that it compiles.

---

### Post by ClientAlive on 2011-11-13
> **1clue said:**
> My c experience is fairly old, but I can help a little.

int* is a pointer to an int.  It's an alternate array notation, so that's your array.

> **Alice748 said:**
> My c experience is fairly old, but I can help a little.
 
int* is a pointer to an int. It's an alternate array notation, so that's your array.
 
[img]http://www.mboxmusic.info/jh2.jpg[/img]
[img]http://www.mboxmusic.info/2.jpg[/img]


Well, while removing the % sign may get it to compile I don't think it's proper. The output of that program with the % sign removed from that last statement prints "i" whatever number of times you enter for how many numbers. So I think anything w/o the % sign is not going to be connected to a variable at all. Hmmm . . .

I wonder if it's just something with the gcc compiler. I've heard that sometimes comilers are different from one another in what they will do.

I'll try looking for some information on printing array values.
--------------

Edit:

I see my mistake. It's actually that there is no & sign in front. So it goes

```

printf("%i\n" num[j]);

```

Not

```

printf("%i\n" &num[j]);

```

Now I have another challenge though. How to design the thing so my loop doesn't just execute all at once but waits for the user to enter something before incrementing again. Maybe an nested loop or something. Idk. Hafta play around with it a little I guess.

Thanks guys.

---

### Post by squenson on 2011-11-13
I stand to what I said, you need the '%' as '%i' means that the scanf function expects an integer.

However the problem is not there. When a compiler gives you an error, it tries to spot the proper line. If you read carefully, you seee that the culprit statement is on line 24 which from your code is:```
               printf("%i\n", &num[j]);
```There is an error on this line, I let you find it, this is the best way to learn! :D

---

### Post by Vaphell on 2011-11-13
there are few problems with your program, i slightly modified the printf line to contain both num[] and &num[]

```
for(j=0; j[COLOR="Blue"]<=[/COLOR]i; ++j)
  printf("%i %i\n", [COLOR="DarkGreen"]&num[j][/COLOR], num[j] );
```

output:
```

How many numbers will you be entering today? 
2
Enter a number: 
1
Enter a number: 
2
The numbers you entered are: 
[COLOR="DarkGreen"]517633760[/COLOR] 1
[COLOR="DarkGreen"]517633764[/COLOR] 2
[COLOR="DarkGreen"]517633768[/COLOR] [COLOR="Blue"]391983400[/COLOR]

```

as it stands, there will be one iteration too many. For i=2 j={0,1,2}
that additional iteration will produce garbage, you reach to a memory that is not a part of the array.
Also note the difference between &num[j] and num[j] - num[j] is an integer, no problems here, but look what happens with & (it means 'location in memory of the stuff that is right after', in other words 'pointer to'). You print out memory address in an integer form.

---

### Post by ClientAlive on 2011-11-13
> **Vaphell said:**
> there are few problems with your program, i slightly modified the printf line to contain both num[] and &num[]

```
for(j=0; j[COLOR="Blue"]<=[/COLOR]i; ++j)
  printf("%i %i\n", [COLOR="DarkGreen"]&num[j][/COLOR], num[j] );
```

output:
```

How many numbers will you be entering today? 
2
Enter a number: 
1
Enter a number: 
2
The numbers you entered are: 
[COLOR="DarkGreen"]517633760[/COLOR] 1
[COLOR="DarkGreen"]517633764[/COLOR] 2
[COLOR="DarkGreen"]517633768[/COLOR] [COLOR="Blue"]391983400[/COLOR]

```

as it stands, there will be one iteration too many. For i=2 j={0,1,2}
that additional iteration will produce garbage, you reach to a memory that is not a part of the array.
Also note the difference between &num[j] and num[j] - num[j] is an integer, no problems here, but look what happens with & (it means 'location in memory of the stuff that is right after', in other words 'pointer to'.

I had just made a couple stupid mistakes. It works the same by only removing the & sign and having just the one instance. I had forgotten to put a % in in my earlier scanf statement, which was pionted out to me before but I didn't get it. Thanks squenson.

Here's the program I have and it works fine exept for printing some junk from memory at the end.

```

#include <stdio.h>

int main (void)

{

int x, i, j, ttl;

printf("How many numbers will you be entering today? \n");
scanf("%i", &ttl);

int num[ttl];

	for(i=0; i<ttl; ++i)
		{
			printf("Enter a number: \n");
			scanf("%i", &num[i]);
		}
		
		printf("The numbers you entered are: \n");
		
	for(j=0; j<=i; ++j)
		{
		printf("%d\n", num[j]);
		}

}


```

Output:

```

 ~/ProgrammingPlayground/Array-Practice > ./Array-Practice.binHow many numbers will you be entering today? 
5
Enter a number: 
1
Enter a number: 
2
Enter a number: 
3
Enter a number: 
4
Enter a number: 
5
The numbers you entered are: 
1
2
3
4
5
-1074216528


```
--------------

Edit:

This is kinda fun! Actually. Programming is cool.

:D

---

### Post by Vaphell on 2011-11-13
junk in the end is the consequence of not being careful with bounds.

when you count from 0 (like arrays do) you need to go from 0 to ARRAY_SIZE-1 (4: 0,1,2,3) which can be written as j<ARRAY_SIZE or j<=(ARRAY_SIZE-1)
you have <= there which will also be fulfilled for j=ARRAY_SIZE

you did the right thing with the reading loop, but made a mistake in the printing loop.

---

### Post by squenson on 2011-11-13
Any idea to print one less entry? Look at your loop!

---

### Post by ClientAlive on 2011-11-13
How do you get rid of the junk from in memory? That's something I've been wondering about for a while now.

---

### Post by ClientAlive on 2011-11-13
> **squenson said:**
> Any idea to print one less entry? Look at your loop!

Well that's odd. Yes, removing the equals sign from the loop with the printf statement in it does make it loop one less time - except when I followed the ttl and i varibles through in my mind I came up with the right numbers. If a user had entered 5 ttl would be 5, i would stop at 4 so it would go 0, 1, 2, 3, 4 and the loop with the prinf at the end would stop at <= i so it would stop at 4 also and would go 0, 1, 2, 3, 4 just. Seemed like all the right numbers the way it was. But I removed the equals sign, recompiled and ran it and it works like it should now. Hmmm. Gave it a sentinel number though  :D

```

#include <stdio.h>

int main (void)

{
int x, i, j, ttl;

do
	{
	printf("How many numbers will you be entering today (enter -99
        to exit)? \n");
	scanf("%i", &ttl);

	int num[ttl];

		if(ttl > 0 && ttl != -99)
			{
			for(i=0; i<ttl; ++i)
				{
					printf("Enter a number: \n");
					scanf("%i", &num[i]);
				}

			printf("The numbers you entered are: \n");
			
			for(j=0; j<i; ++j)
				{
				printf("%d\n", num[j]);
				}
			}
	}
while(ttl != -99);
return 0;
}


```
-------------------

Edit:

Oh wow! I think I was getting confused because i was ending on 4 (assuming you pick the number 5 to trace it out). 0, 1, 2, 3, 4 is still 5 times around so when i would get to my j loop it would be 5 even though it ended on 4 in the previous loop. right? If that's what's going on behind the scenes here that just seems odd.
-------------------

Edit:

If that's what's going on then it must mean there are really two diff sets of numbers going on here. There's the number the varible starts on and ends on and everything in between, there's that set of numbers, then there's the quantity of times (two different things). If that's right, and a guy didn't figure that out, it could give you all kind of grief trying to get it right. What a trip!

---

### Post by Bachstelze on 2011-11-13
It does not "stop on 4". It stops when the condition i<5 stops being true, i.e. when i becomes 5. This happens between the 5th and 6th iterations of the loop. You do not seem to understand how for loops work, so how about reading up on that instead of writing code you do not understnad yourself?

---

### Post by ClientAlive on 2011-11-13
> **Bachstelze said:**
> It does not "stop on 4". It stops when the condition i<5 stops being true, i.e. when i becomes 5. This happens between the 5th and 6th iterations of the loop. You do not seem to understand how for loops work, so how about reading up on that instead of writing code you do not understnad yourself?


So you advise that I stop writing code?

Or is the problem just that I don't know everything in advamce of learning it?

---

### Post by Bachstelze on 2011-11-13
> **ClientAlive said:**
> So you advise that I stop writing code?

Or is the problem just that I don't know everything in advamce of learning it?

Writing code at random is not a good way to learn, as you should have guessed by now. You don't start working on car engines before you have at least a basic understanding about their internal structure and are able to tell which part does what and when. Same thing for C loops, especially for loops. They have four different parts, and before you start working with them, you should have a basic understanding of which part does what and when. And you can only get to know this by reading up on it, not by throwing various things at it and try to guess how it works.

---

### Post by ClientAlive on 2011-11-13
```

#include <stdio.h>

int main (void)

{
	
int i, j, k;

	for(i=0; i<5; ++i)
		{
		printf("for(i=0; i<5; ++i)\n");
		printf("The value of i is %i\n", i);
		}
		
/*The output shows the last value of i to be 4. This is deceptive because it really
is only the last time the printf statement executed. The counter increments after
the body of the loop is executed so the value of i will be increased one last time
but will not be printed to the screen. I assume that, after the counter increases
the value of i that last time, the program does yet one more thing - it reads the
for conditions again. (This is called the scientific method: hypothesis, conduct
experiment, evaluate results and compare, repeat). It is at that time that it finds
the statemtent to be untrue (this is called the hypothesis). It is at that time that
it does not execute again because the conditions are found to be no longer true -
et, because it does not execute that last time it does not print the final value of
to the screen. To discover what that final value is FROM WRITING AND EXECUTING CODE
we must add the additional for loops below that are tied to the value of the
variable in the first for loop.*/
	 
	for(j=0; j<=i; ++j)
		{
		printf("for(j=0; j<=i; ++j)\n");
		printf("The value of j is %i\n", j);
		}
		
/*The output shows the last number printed is 5. But the last number printed is
based on the 'actual' last value of i (a final value which was not reflected in the
output from the for loop in i) from our first for foop this shows that the variable
in a for loop is increased one last time after the for loop stops executing. (it is
throught the addition of this loop that the hypothesis is tested and proved).*/
		
	for(k=0; k<=j; ++k)
		{
		printf("for(k=0; k<=j; ++k)\n");
		printf("The value of k is %i\n", k);
		}
		
/*The output shows the last number printed is 6. But the last number printed is
based on the 'actual' value of j from our second for loop, which is in turn based on
the 'actual' value of i before it. This proves definitively that the variable in a
for loop is increased one last time after the for loop stops executing  --(not
because someone else gave you their way of understanding how a for loop works but
because the program itself told you what it is doing, how it is doing it, what order
it's doing it in). (It is through the addition of these two loops that deductive
proof is formed). But don't rely on my SUBJECTIVE WAY OF UNDERSTANDING AND
DESCRIBING HOW IT WORKS - look at the output and compare it with the code yourself.*/
		
return 0;
}


```

---

### Post by muteXe on 2011-11-13
OP, have a little read of this: [http://en.wikipedia.org/wiki/Off-by-one_error](http://en.wikipedia.org/wiki/Off-by-one_error) .

And I agree with Bachstelze. If you ever write code that don't understand, stop and make an effort to understand. And just because it compiles doesn't make it correct.

---

### Post by ofnuts on 2011-11-13
.

---

### Post by ClientAlive on 2011-11-13
> **Vaphell said:**
> there are few problems with your program, i slightly modified the printf line to contain both num[] and &num[]

```
for(j=0; j[COLOR="Blue"]<=[/COLOR]i; ++j)
  printf("%i %i\n", [COLOR="DarkGreen"]&num[j][/COLOR], num[j] );
```

output:
```

How many numbers will you be entering today? 
2
Enter a number: 
1
Enter a number: 
2
The numbers you entered are: 
[COLOR="DarkGreen"]517633760[/COLOR] 1
[COLOR="DarkGreen"]517633764[/COLOR] 2
[COLOR="DarkGreen"]517633768[/COLOR] [COLOR="Blue"]391983400[/COLOR]

```

as it stands, there will be one iteration too many. For i=2 j={0,1,2}
that additional iteration will produce garbage, you reach to a memory that is not a part of the array.
Also note the difference between &num[j] and num[j] - num[j] is an integer, no problems here, but look what happens with & (it means 'location in memory of the stuff that is right after', in other words 'pointer to'). You print out memory address in an integer form.


Vaphell, you tried to show me what was going on but I didn't see it at first. It wasn't until I ran some tests and then saw this again that I realized you'd shown me the difference between what you get with the & sign in a statment like that and without it. My bad, man. Sorry I missed it the first time.

---

### Post by Bachstelze on 2011-11-13
"I assume", "I assume", "I assume".

NO. You should never "assume" anything. You should read a good source on C and find out exactly how things work. Your pseudo-scientific method of trying random things until you get something that looks like it could possibly be how things work might work on something as simple as this but will fail miserably on more subtle aspects of the language.

---

