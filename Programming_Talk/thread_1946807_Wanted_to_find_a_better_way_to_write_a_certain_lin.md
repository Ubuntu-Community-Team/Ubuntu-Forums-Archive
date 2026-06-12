---
title: "Wanted to find a better way to write a certain line of code"
date: 2012-03-25
forum: Programming Talk
---

### Post by ClientAlive on 2012-03-25
C language...

I suppose the more general issue is gaining a better understanding of and skills with boolean logic. I have a particular line of code I thought would be a good piece to use for talking about it. If anyone is interested, I'd sure appreciate the help.

So...

I have this line of code. What it does (or at least what it seems to do, whether properly or not I don't know) is compare a user's selection with allowable selections. Then the appropriate action is supposed to be taken based on the result of the test. The problem is it seems very cumbersome in it's current form and I was hoping to find a more condensed way to write it. Maybe in the course of that I could gain a better understanding of the logic behind it all.

This is the line in it's current form:

```

[B]if(Selection != 'c' || Selection != 'v' || Selection !='m'
	|| Selection != 'd' || Selection != 'e')[/B]

```

And this is the whole file to show it in the context of the whole:

```


#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>

//struct Record
//{
	//int UID;
	//char Name[32];
	//int Qty;
	//float Price;
//};

void Menu();
int Selection(int *Exit);
int Validation(int Selection);

int main()
{
//struct Record *Temp = (struct Record *)malloc(sizeof(struct Record));
//FILE *fp;
int Exit = 0;

	while(!Exit)
	{
		switch(Selection(&Exit))
		{
			case 'c':
			{
				printf("Selection was valid - Selection was: 'c' or 'C'\n");
				break;
			}

			case 'v':
			{
				printf("Selection was valid - Selection was: 'v' or 'V'\n");
				break;
			}

			case 'm':
			{
				printf("Selection was valid - Selection was: 'm' or 'M'\n");
				break;
			}

			case 'd':
			{
				printf("Selection was valid - Selection was: 'd' or 'D'\n");
				break;
			}

			case 'e':
			{
				printf("Peace out...\n");
				printf("\n");
				printf(" (\\/)\n");
				printf(" (^^)\n");
				printf("\n");
				break;
			}
		}
	}

	return 0;
} //end main

void Menu()
{
	printf("Please choose from the following...\n");
	printf("\n");
	printf("[C]reate Record\n");
	printf("[V]iew Record\n");
	printf("[M]odify Record\n");
	printf("[D]elete Record\n");
	printf("[E]xit\n");
	printf("\n");
}

int Selection(int *Exit)
{
	Menu();
	int Selection = tolower(getchar());

	if(Validation(Selection)) //This block of code does not appear to being executed at all
	{
		printf("Invalid Selection\n");
		printf("Please select again\n");
		printf("\n");
		//Selection = '\0';
	}

	if(Selection == 'e')
	{
		*Exit = 1;
	}

return Selection;
}

int Validation(int Selection)
{
	int Status = 1;

	[B]if(Selection != 'c' || Selection != 'v' || Selection !='m'
	|| Selection != 'd' || Selection != 'e')[/B]
	{
		Status = 0;
	}

return Status;
}


```

It's a work in progress so the parts I haven't approached yet are commented out still.

This is my own attempt at a past assignment I was not able to complete successfully. After submitting the horror show that was what I had for it (last Friday) I decided to take a try at it again on my own.

That being said, back to the original question...

Here are some other variations I tried as alternatives to the line of code up top:

I tried...

```

if(Selection != ('c' || 'v' || 'm' || 'd' || 'e'))

```

Doesn't work that way at all.

And I tried...

```

if(Selection (!= 'c' || != 'v' || != 'm' || != 'd' || != 'e'))

```

Doesn't work that way at all.

Is there not some better way to write this where the variable "Selection" does not have to be repeated over an over?

And I wonder if, in reality, it's actually doing what it's supposed to within the program? I figure that just because something appears to be doing what it's designed to do doesn't mean there's not some case I haven't thought of where it falls apart. The whole, 'what's really happening behind the scenes?' thing. You know?

By the way, my first design involved a...


```

"const int Array[5] = {'c', 'v', 'm', 'd', 'e'};

```

And a...

```

for(int i = 0; i < 5; ++i)
...

```

I was quicly reminded (yes, it's not the first time I tried that, and I was told before too) that approach can never work because it would always be false (even if a valid selection is entered).

Thanks for taking a look with me. I appreciate it.  ):P

---

### Post by schauerlich on 2012-03-25
You're storing Selection in an int, but you seem to be using it as a char - why?
```
int validate(char selection) {
    switch(selection) {
    case 'c':
    case 'v':
    case 'm':
    case 'd':
    case 'e':
        return 1;
        break; // not strictly necessary, but if you change that return statement to something else later you'll need it.

    default:
        return 0;
    }
}
```

---

### Post by r-senior on 2012-03-25
I don't have a problem with the or, but how about this?

```
int valid(int selection)
{
        return strstr("cvmde", selection) != NULL;
}
```

Either way, I think "valid" is a better name, so that it reads more naturally:

```
if (valid(selection)) { ...
```

---

### Post by ClientAlive on 2012-03-25
> **schauerlich said:**
> You're storing Selection in an int, but you seem to be using it as a char - why?
```
int validate(char selection) {
    switch(selection) {
    case 'c':
    case 'v':
    case 'm':
    case 'd':
    case 'e':
        return 1;
        break; // not strictly necessary, but if you change that return statement to something else later you'll need it.

    default:
        return 0;
    }
}
```

getchar() returns an int not a char and I was told in the past that it's the proper way to use it. Or were you refering to the use of single quotes around the characters when the data type is int? I couldn't remember how that part was supposed to go.


> **r-senior said:**
> I don't have a problem with the or, but how about this?

```
int valid(int selection)
{
        return strstr("cvmde", selection) != NULL;
}
```

Either way, I think "valid" is a better name, so that it reads more naturally:

```
if (valid(selection)) { ...
```

I looked up strstr() definition. Very interesting but I'm still pondering how I would use what it returns. Perhaps it will come to me in a moment  :p

---

### Post by schauerlich on 2012-03-25
You probably shouldn't be using getchar anyways - what if the user gives you more than just one character? Getting input in C (or any language) is always a pain. Anyways, for this particular case, I'd use getchar, check for EOF, and if it's successful cast to char and use char everywhere else. It's more correct (error checking) and more clear (types actually are what you're trying to represent).

---

### Post by ClientAlive on 2012-03-25
> **schauerlich said:**
> You probably shouldn't be using getchar anyways - what if the user gives you more than just one character? Getting input in C (or any language) is always a pain. Anyways, for this particular case, I'd use getchar, check for EOF, and if it's successful cast to char and use char everywhere else. It's more correct (error checking) and more clear (types actually are what you're trying to represent).


I understand the gist of what you're getting at; but, unfortunately, I'm still a little green (inexperienced). A term I'm yet unfamilair with is "cast" (I have a notion of what it is but nothing close to a concrete understanding). And "check for EOF" with getchar(). I know what EOF is but not what getchar() does that would give it any concrete meaning to me. This latter things is something I may be able to resolve (at least partially) via an internet search.
--------------------

Edit:

After re-reading several times I recalled something. I think there may be more than one meaning for "cast" (in C at least). One meaning has something to do with pointers and the other to do with type conversion? It's the first sense I'm not familar with - but type conversion, I think, involves syntax something like...

```

char Selection = (**char)**getchar();

```

right?

---

### Post by GeneralZod on 2012-03-25
> **schauerlich said:**
> You probably shouldn't be using getchar anyways - what if the user gives you more than just one character?

Which will, of course, happen when the user presses Enter - getchar won't "swallow" the newline, and it will be retrieved in the next call to getchar! OP: see the discussion here: [http://stackoverflow.com/questions/1384073/problem-with-flushing-input-stream-c/1384089](http://stackoverflow.com/questions/1384073/problem-with-flushing-input-stream-c/1384089)

Generally I'm in favour of splitting out functions as you've done here, but the duplication of the "valid" keypresses (inside your main() loop, and inside Valid(...)) isn't ideal, and you may want to consider folding a lot of it back into your main loop - something like this, for example:

```

#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>

//struct Record
//{
	//int UID;
	//char Name[32];
	//int Qty;
	//float Price;
//};

void Menu();
int Selection();

int main()
{
//struct Record *Temp = (struct Record *)malloc(sizeof(struct Record));
//FILE *fp;
int Exit = 0;

	while(!Exit)
	{
        printf("Loop\n");
		switch(Selection())
		{
			case 'c':
			{
				printf("Selection was valid - Selection was: 'c' or 'C'\n");
				break;
			}

			case 'v':
			{
				printf("Selection was valid - Selection was: 'v' or 'V'\n");
				break;
			}

			case 'm':
			{
				printf("Selection was valid - Selection was: 'm' or 'M'\n");
				break;
			}

			case 'd':
			{
				printf("Selection was valid - Selection was: 'd' or 'D'\n");
				break;
			}

			case 'e':
			{
				printf("Peace out...\n");
				printf("\n");
				printf(" (\\/)\n");
				printf(" (^^)\n");
				printf("\n");
                                Exit = 1;
				break;
			}
            default:
                printf("Invalid Selection\n");
                printf("Please select again\n");
                printf("\n");
                break;
		}
	}

	return 0;
} //end main

void Menu()
{
	printf("Please choose from the following...\n");
	printf("\n");
	printf("[C]reate Record\n");
	printf("[V]iew Record\n");
	printf("[M]odify Record\n");
	printf("[D]elete Record\n");
	printf("[E]xit\n");
	printf("\n");
}

int Selection()
{
	Menu();	
    // TODO - fix this - getchar does not swallow newlines! See e,g, 
    // http://stackoverflow.com/questions/1384073/problem-with-flushing-input-stream-c/1384089
    // This will cause it to always print "Invalid Selection"!
    return tolower(getchar()); 
}

``` 

Not necessarily what I'd do, but another perspective for you to consider :)

---

### Post by Bachstelze on 2012-03-25
> **schauerlich said:**
> You probably shouldn't be using getchar anyways - what if the user gives you more than just one character? Getting input in C (or any language) is always a pain. Anyways, for this particular case, I'd use getchar, check for EOF, and if it's successful cast to char and use char everywhere else. It's more correct (error checking) and more clear (types actually are what you're trying to represent).

Why introduce an additional char variable when using the int one is perfectly fine?

---

### Post by satsujinka on 2012-03-25
Instead of getchar you could try fgets. Something like this perhaps?

```
char selection() {
    char s[2];
    menu();
    fgets(s, 2, stdin);
    return tolower(s[0]);
}

```

---

### Post by Bachstelze on 2012-03-25
> **satsujinka said:**
> Instead of getchar you could try fgets. Something like this perhaps?

```
char selection() {
    char s[2];
    menu();
    fgets(s, 2, stdin);
    return tolower(s[0]);
}

```

You need to allocate three bytes (selection character, newline and terminating null).

---

### Post by ClientAlive on 2012-03-25
What about something along the lines of...

```

[B]char Selection(char *Exit)
{[/B]
 /*Generally not sure about the interaction of return types between fread() and
   strstr() as it relates to variable declarations (pointer vs. not pointer)*/

[B]
	Menu();
	char Selection = fread(%c, sizeof(char), 1, stdin);[/B] //not certain about arg1 of fread()

	/*uncertain about how all what's in the following line really works. "...== NULL" in a
    "return..." ? Among other questions about the logic.*/

[B]
	if((char *Valid = strstr("cvmde", tolower(Selection))) == NULL)
	{
		printf("Invalid selection\nPlease try again\n");
		printf("\n");
		if(Selection == 'e')
		{
			*Exit = 1;
		}
	}
	return *Valid;
}[/B]

```



> **satsujinka said:**
> Instead of getchar you could try fgets. Something like this perhaps?

```
char selection() {
    char s[2];
    menu();
    fgets(s, 2, stdin);
    return tolower(s[0]);
}

```

Been through hell and back with the '\n' fgets() loves to copy. Code to strip it off has worked in the past but it's irritating to have to do so and always leaves me with this uneasy feeling.

---

### Post by satsujinka on 2012-03-25
That's fine. But you don't need to worry about it here. The return makes fgets's weirdness disappear (s[1] will be a '\n' pretty much always, so s isn't actually a proper string.)

---

### Post by Bachstelze on 2012-03-25
> **ClientAlive said:**
> What about something along the lines of...

```

[B]char Selection(char *Exit)
{[/B]
 /*Generally not sure about the interaction of return types between fread() and
   strstr() as it relates to variable declarations (pointer vs. not pointer)*/

[B]
	Menu();
	char Selection = fread(%c, sizeof(char), 1, stdin);[/B] //not certain about arg1 of fread()

	/*uncertain about how all what's in the following line really works. "...== NULL" in a
    "return..." ? Among other questions about the logic.*/

[B]
	if((char *Valid = strstr("cvmde", tolower(Selection))) == NULL)
	{
		printf("Invalid selection\nPlease try again\n");
		printf("\n");
		if(Selection == 'e')
		{
			*Exit = 1;
		}
	}
	return *Valid;
}[/B]

```


No. As you were told several times, % conversion specifiers are only used in the printf and scanf families of functions.

---

### Post by ClientAlive on 2012-03-25
> **Bachstelze said:**
> No. As you were told several times, % conversion specifiers are only used in the printf and scanf families of functions.


Well brother, I got the notion directly from the example of a pretty well respected book. Problem I noticed is he is using it in a totally different way. And, of course, I tried it and saw for myself. Tried a lot of things actually. Got close to an alternative but not sure it's necessarily better. Compiles but doesn't work. Anyhoo...

> 
Source: C The Complete Reference, 4th ed. (pp. 245, 246)
--------------------------------------------------------

/* Write some non-character data to a disk file
and read it back. */
#include <stdio.h>
#include <stdlib.h>
int main(void)
{
FILE *fp;
double d = 12.23;
int i = 101;
long 1 = 123023L;
if((fp=fopen("test", "wb+"))==NULL) {
printf(''Cannot open file.\n");
exit(1);
}

fwrite(&d, sizeof(double), 1, fp);
fwrite(&i, sizeof(int), 1, fp);
fwrite(&l, sizeof(long), 1, fp);
rewind(fp);
fread(&d, sizeof
(double), 1, fp);
fread(&i, sizeof(int), 1, fp);
fread(&l, sizeof(long), 1, fp);
printf("%f %d %ld", d, i, 1);
fclose(fp);
return 0;
}


Anyway I just got slammed with something truly unbelievable for this class' next assignment. I think my teacher is a Nazi and I have no idea how I'll ever pull this off. I typically feel this way about every assgnment but only in passing; and, at least, combined with mostly enthusiasm an confidence. In this case those latter elements seem to have vanished. Bachstelze, you of all people know how cocky I can be about these assignments. With this one all that is smashed. Woe is me, I'm ruined!

I gotta go. Thanks all for everything you've shared. I'll try spend some time here and there on this one if I can; but, for now, I've got to face the beast.

Oh God - have mercy on my soul!!

---

### Post by Vaphell on 2012-03-26
out of curiosity: what your next assignment is? :)

---

### Post by Bachstelze on 2012-03-26
> **ClientAlive said:**
> Well brother, I got the notion directly from the example of a pretty well respected book. Problem I noticed is he is using it in a totally different way. And, of course, I tried it and saw for myself. Tried a lot of things actually. Got close to an alternative but not sure it's necessarily better. Compiles but doesn't work. Anyhoo...

Those are & characters, not %. Totally different thing. ;)

---

### Post by ClientAlive on 2012-03-26
> **Vaphell said:**
> out of curiosity: what your next assignment is? :)

Oh, well, it isn't so much what the assignment is as the fact that my instructor gives us next to nothing to go on for learning the stuff. What little she does give is difficult to understand. Not because the subject at hand is so difficult to learn but because she doesn't communicate clearly and with technical detail and accuracy (as one would expect of someone in her profession). I'm not ragging on my instructor, I like her as a person. I'm just stating facts. I alway end up having to find my own materials and basically teach myself (and you guys are awesome helping me too). It's hard to do when you don't know anything about it. When you don't know anything about it, how do you know what you ought to be looking for?

Anyhow...  We're on to stacks and queues. Mostly what has me worried is that there's at least 2 new concepts being introduced that play into this assignment - and one is pretty hefty I might add. Concepts our instructor has never touched (not now or ever), as well as a couple concepts I found very challenging before and have very limited experience with.

~ Putting stuff in header files/ having more than one file (doesn't seem too bad)
~ Pointers to pointers (God knows what that is)
~ Linked lists (A thing I found very challenging before and have very little experience with, This is what's to be in our header file and what the pointers to pointers thing is connected to. What's worse, it requires a more complex type of linked list)
~ File I/O (which I fell flat on my face with last week and was my motivation for starting this thread - I decided to try again on my own)

I'm one of these people who needs to have some idea to anchor to or I never get off the ground. It's always (and I mean always) the same story with me... I need to know what something "is like" in order to begin using it.

When I had to learn about linked lists, we tossed some metaphors around and that's what enabled me to get started doing anything with it. Then after writing some bad code a few times (and quite a number of hand drawn diagrams) my code got better and better until I was able to produce the completed assignment. Afterward I was able to drop the metaphors almost completely and feel I have a decent grasp of pointers (not pointers to pointers, but pointers), of structs for sure, and slightly of linked lists. I simply have to acquire some picture in my mind of how these concepts work or I'll never get off the ground with it. These aren't the kind of things I can just make up - they have to come from somewhere.

Well, too much carrying on about it I suppose. You did ask though.  :p

> **Bachstelze said:**
> Those are & characters, not %. Totally different thing. ;)

Oh shoot! I guess it is. Thanks for pointing that out. I must have been looking at the wrong line or something.

I have to laugh about it Bachstelze. I'm so dam green with this junk... Possibly disgusting to some but I find it funny 'cause I know I'll get better about it with practice.

---

### Post by Vaphell on 2012-03-26
> ~ Putting stuff in header files/ having more than one file (doesn't seem too bad)
~ Pointers to pointers (God knows what that is)
~ Linked lists (A thing I found very challenging before and have very little experience with, This is what's to be in our header file and what the pointers to pointers thing is connected to. What's worse, it requires a more complex type of linked list)
~ File I/O (which I fell flat on my face with last week and was my motivation for starting this thread - I decided to try again on my own)

doesn't sound too bad :-)
more complex type of linked list is just few pointers per node more ;-)
pointer to pointer is like pointer to any other data structure - difference being that instead finding end value there, you get another jump to perform (and more *'s in code)
pointer to data: p->data
pointer to pointer to data: p1->p2->data

---

### Post by satsujinka on 2012-03-26
Let's see if I can't help you out on pointers to pointers.

So you use a pointer when you want to modify a value somewhere else.
ex:
```
int i = 0;
printf("%d",i);//prints 0
addone(&i);
printf("%d",i);//prints 1
```
here addone is simply a function that increments a dereferenced i (e.g. *i+=1)

so far so good?

similarly, you use a pointer to a pointer when you want to modify where a pointer points.
ex:
```
int i  = 0;
int j = 1;
int *p = i;
printf("%d", *p); //prints 0
change_pointer(&p, &j);
printf("%d", *p); //prints 1

```
here's change_pointer:
```
void change_pointer(int **p, int *i) {
    *p = i;
}

```

does that help, or do you need more?

EDIT: now that I'm at a computer here's a full version:
```
#include <stdio.h>

void addone(int *i) {
	*i += 1;
}

void change_pointer(int **p, int *i) {
	*p = i;
}

int main() {
	int i = 0;
	int j = 0;
	int *p = &i;
	printf("%d\n", *p); //print 0
	addone(p);
	printf("%d\n", *p); //print 1
	change_pointer(&p, &j);
	printf("%d\n", *p); //print 0
	return 0;
}

```

---

### Post by Bachstelze on 2012-03-26
Pointers to pointers. It's simple. A pointer is an object like any other object. And like any other object, you can make a pointer to it. All there is to it. And it has a lot of uses besides "modify something somewhere else". Remember that pointer &#8776; array. In particular, a string is an array of [font=monospace]char[/font]s, often represented by a pointer to [font=monospace]char[/font]. What if you want an array of strings? Pointer to pointer to [font=monospace]char[/font]. That's exactly what [font=monospace]char **argv[/font] is about.

---

### Post by satsujinka on 2012-03-26
> **Bachstelze said:**
> Pointers to pointers. It's simple. A pointer is an object like any other object. And like any other object, you can make a pointer to it. All there is to it. And it has a lot of uses besides "modify something somewhere else". Remember that pointer &#8776; array. In particular, a string is an array of [font=monospace]char[/font]s, often represented by a pointer to [font=monospace]char[/font]. What if you want an array of strings? Pointer to pointer to [font=monospace]char[/font]. That's exactly what [font=monospace]char **argv[/font] is about.

I'd argue you should use s[i][j] if you need an array of strings. If you do need a dynamic array of strings you're correct that **s is necessary. 

However, all uses of a pointer are derived from "modify something somewhere else." Just like all uses of addition are derived from "combine two numbers into one number."

---

### Post by ClientAlive on 2012-03-26
> **satsujinka said:**
> Let's see if I can't help you out on pointers to pointers.

So you use a pointer when you want to modify a value somewhere else.
ex:
```
int i = 0;
printf("%d",i);//prints 0
addone(&i);
printf("%d",i);//prints 1
```
here addone is simply a function that increments a dereferenced i (e.g. *i+=1)

so far so good?

similarly, you use a pointer to a pointer when you want to modify where a pointer points.
ex:
```
int i  = 0;
int j = 1;
int *p = i;
printf("%d", *p); //prints 0
change_pointer(&p, &j);
printf("%d", *p); //prints 1

```
here's change_pointer:
```
void change_pointer(int **p, int *i) {
    *p = i;
}

```

does that help, or do you need more?

EDIT: now that I'm at a computer here's a full version:
```
#include <stdio.h>

void addone(int *i) {
	*i += 1;
}

void change_pointer(int **p, int *i) {
	*p = i;
}

int main() {
	int i = 0;
	int j = 0;
	int *p = &i;
	printf("%d\n", *p); //print 0
	addone(p);
	printf("%d\n", *p); //print 1
	change_pointer(&p, &j);
	printf("%d\n", *p); //print 0
	return 0;
}

```

p, 

Right on. Wow, thank you!

I ran that too and I see what's going on. I started getting curious about some things though so I tried some variations too and they all seem to do the same thing - just in a different way.

I asked myself...

Why can't just a regular pointer do the same thing?

```

int i = 0;
int j = 5;
int k = 3;
...

```

...

```

change_pointer(&p, k);
...

void change_pointer(int **p, int z)
{
	*p = &z;
}

```

Or...

```

change_pointer(p, k);
...

void change_pointer(int *p, int z)
{
	p = &z;
	printf("%d\n", *p);
}

```

Or...

```

change_pointer(p, &k);
...

void change_pointer(int *p, int *z)
{
	p = z;
	printf("%d\n", *p);
}


```

...all seem to produce the same result.

So I got to wondering if there isn't some much more basic concept going on here, possibly even something that's language independed. Possibly something that's simply inherent in logic iteslf!

It seems to me that there is a commonality among all the variations. There's probably some technical word for it but I don't know what it is. The best way I could try to convey it would be to say there's a 'separation of events' and 'number/quantity of -> separations'. Another way to think of it I guess is to think of the saying "...times removed" ("x many times removed"). Does that make sense?

With the code above it seems that the fact a function is being used causes one degree of separation right off the bat (1 x removed). I'm not sure if those variations would be possible (in C anyway) if a function weren't being used. I'm not sure.

I know this is kinda off the beaten path or whatever, but all this gets me wondering about some very very foundational things. Such as: All languages aside, think about the formal rules of logic itself (a philosophical level if you will). These are just concepts, like mathematical rules. You can write them on paper and you have a piece of paper with some ink or lead on it that's tangible, but the rules themselves have no substance. Now, with that in mind, could one conclude that any given programming language is like a framework applied on top of those rules of logic? That the shape of the framework may change from from one language to the next but that the logic itself abides? If that's the case then it means I'm trying to learn one, among many, frameworks and it's as important to know how it weilds logic as it is to know what the framework 'looks like'. (Bachstelze - reminds me of somthing you once told me). 

I wonder if we can't thank the "touring machine" for all the possibilites.

Sometimes it's hard to see the forest from the trees. I hope I'm finding a better vantage point.  :)

So...

Pointers to pointers: I guess I can work with that (we'll see what happens when I try doing it in a more complex situation). In fact, it's starting to seem not so bad after all. Also: if (and only if) some of these more philosophical notions are on target, that might mean there's several ways to accomplish what our teacher was using pointers to pointers for. Hmmm...

> **Bachstelze said:**
> Pointers to pointers. It's simple. A pointer is an object like any other object. And like any other object, you can make a pointer to it. All there is to it. And it has a lot of uses besides "modify something somewhere else". Remember that pointer &#8776; array. In particular, a string is an array of [font=monospace]char[/font]s, often represented by a pointer to [font=monospace]char[/font]. What if you want an array of strings? Pointer to pointer to [font=monospace]char[/font]. That's exactly what [font=monospace]char **argv[/font] is about.

That makes sense in a general way. And I'm pretty sure I could pull it off. I am kind of curious about a couple things though. Just those kinda thing you wonder about and would be real neat to explore - exciting!

I wonder...

Is there a difference between what & and * 'do' (the end result of thier use in code)?

What would that difference be then and what use is it? Things like... why do you need the both? Isn't one good enough? And such...

Then there's...

Can you dereference something with an &? If you use & to pass a variable address will the variable which address was passed remain in that state or is the ampersand's effect just etherial? (Does the & change the variable to a pointer for good?)

And a more foundational curiousity (within the realm of C, as a particular language, yet reaching down, touching the place where programming languages and logic meet)...

Do pointers solve some limitation imposed by scope? I'm thinking, why pointers? Why even have pionters at all? There must have been some good reason for their creation in the first place. Sure we could talk about what they do or even how they do it but that's pretty conrete. What main, all encompassing need are pointers designed to bring to the table?

hmmm...

---

### Post by satsujinka on 2012-03-26
> **ClientAlive said:**
> p, 

Right on. Wow, thank you!

I ran that too and I see what's going on. I started getting curious about some things though so I tried some variations too and they all seem to do the same thing - just in a different way.

I asked myself...

Why can't just a regular pointer do the same thing?

```

int i = 0;
int j = 5;
int k = 3;
...

```

...

```

change_pointer(&p, k);
...

void change_pointer(int **p, int z)
{
	*p = &z;
}

```
 
Actually, this doesn't work. What's happening here is that you're assigning p to the address of the copy of k that's created as z. So if you changed the value of k, it wouldn't actually update p, because p refers to the local variable z and not k.
> **ClientAlive said:**
> 
Or...

```

change_pointer(p, k);
...

void change_pointer(int *p, int z)
{
	p = &z;
	printf("%d\n", *p);
}

```

same problem as above
> **ClientAlive said:**
> 
Or...

```

change_pointer(p, &k);
...

void change_pointer(int *p, int *z)
{
	p = z;
	printf("%d\n", *p);
}


```

here p's value won't propagate back to main. so while it prints the correct value, p won't have the correct address when change_pointer returns.
> **ClientAlive said:**
> 
...all seem to produce the same result.

So I got to wondering if there isn't some much more basic concept going on here, possibly even something that's language independed. Possibly something that's simply inherent in logic iteslf!

It seems to me that there is a commonality among all the variations. There's probably some technical word for it but I don't know what it is. The best way I could try to convey it would be to say there's a 'separation of events' and 'number/quantity of -> separations'. Another way to think of it I guess is to think of the saying "...times removed" ("x many times removed"). Does that make sense?

With the code above it seems that the fact a function is being used causes one degree of separation right off the bat (1 x removed). I'm not sure if those variations would be possible (in C anyway) if a function weren't being used. I'm not sure.

You're on the right track. Basically, if you want a value to propagate upwards (so back to the calling function, and if the value was passed in there, to its calling function.) You need to add a pointer to it (since there's a degree of separation.) This is how pointers to pointers come into play, I want to modify p in a different function and have that modification propagate back to where I am (without doing p = somefunction().) Note, that there's only 1 degree of separation. Either it's a local variable (so I'm doing '=' to change it) or it's a pointer to a local variable (so I'm in some function that it isn't a local variable and I want to change it so I de-reference it to get the local variable and then I can use '='.)
> **ClientAlive said:**
> 
I know this is kinda off the beaten path or whatever, but all this gets me wondering about some very very foundational things. Such as: All languages aside, think about the formal rules of logic itself (a philosophical level if you will). These are just concepts, like mathematical rules. You can write them on paper and you have a piece of paper with some ink or lead on it that's tangible, but the rules themselves have no substance. Now, with that in mind, could one conclude that any given programming language is like a framework applied on top of those rules of logic? That the shape of the framework may change from from one language to the next but that the logic itself abides? If that's the case then it means I'm trying to learn one, among many, frameworks and it's as important to know how it weilds logic as it is to know what the framework 'looks like'. (Bachstelze - reminds me of somthing you once told me). 

I wonder if we can't thank the "touring machine" for all the possibilites.

Sometimes it's hard to see the forest from the trees. I hope I'm finding a better vantage point.  :)

Indeed. All languages are just different "front-ends" to the computer "back-end" so there are some requirements that will make their way in, simply because of how the computer does things. That said, there's a great deal of flexibility here and human ingenuity allows for languages to be extremely high-level.
> **ClientAlive said:**
> 
So...

Pointers to pointers: I guess I can work with that (we'll see what happens when I try doing it in a more complex situation). In fact, it's starting to seem not so bad after all. Also: if (and only if) some of these more philosophical notions are on target, that might mean there's several ways to accomplish what our teacher was using pointers to pointers for. Hmmm...

It is possible to do lists and update them without having pointers to pointers. In fact, most functional languages do so.

> **ClientAlive said:**
> 
That makes sense in a general way. And I'm pretty sure I could pull it off. I am kind of curious about a couple things though. Just those kinda thing you wonder about and would be real neat to explore - exciting!

I wonder...

Is there a difference between what & and * 'do' (the end result of thier use in code)?

What would that difference be then and what use is it? Things like... why do you need the both? Isn't one good enough? And such...

A brief rundown:
& is used to get the memory address of a variable (the reference of the variable.)
* is used to get the value at a memory address (it de-refences a reference.)
They're reverse processes of each other.
> **ClientAlive said:**
> 
Then there's...

Can you dereference something with an &? If you use & to pass a variable address will the variable which address was passed remain in that state or is the ampersand's effect just etherial? (Does the & change the variable to a pointer for good?)

*&i is the same thing as plain i. & doesn't make anything into a pointer it just fetches the memory address (which you then store in a pointer [usually.])
> **ClientAlive said:**
> 
And a more foundational curiousity (within the realm of C, as a particular language, yet reaching down, touching the place where programming languages and logic meet)...

Do pointers solve some limitation imposed by scope? I'm thinking, why pointers? Why even have pionters at all? There must have been some good reason for their creation in the first place. Sure we could talk about what they do or even how they do it but that's pretty conrete. What main, all encompassing need are pointers designed to bring to the table?

hmmm...
Pointers can be used to solve limitations of scope. If x is in function foo() and y is in function bar(), then bar doesn't know where x is (bar(x) still doesn't tell bar where x is, only what x's value is.) However, function baz takes a pointer to a variable, so if we call baz(&x) then baz will know where x is and can modify its value.

Pointers also do one other thing, they allow you to talk about computer memory. For example, in C arrays are more or less pointers. An array is merely a continuous block of memory so we can access elements in an array if we know two things:
[LIST=1]
[*]where the first element of the array is
[*]how large each element is
[/LIST]
In point of fact array[i] is mostly syntactic sugar for *(array+i) (array[i] is safer because it does bounds checking, but they do more or less the same thing.)

Pointers aren't necessary, many languages don't have them. Most of their uses can be worked around with '=' but that can get rather messy when you want to update several variables at once. But if you want to do low level coding pointers are a necessary evil (because you have to control where things in memory are.)

---

### Post by schauerlich on 2012-03-26
> **ClientAlive said:**
> 
Why can't just a regular pointer do the same thing?

```

int i = 0;
int j = 5;
int k = 3;
...

```

...

```

change_pointer(&p, k);
...

void change_pointer(int **p, int z)
{
	*p = &z;
}

```

Or...

```

change_pointer(p, k);
...

void change_pointer(int *p, int z)
{
	p = &z;
	printf("%d\n", *p);
}

```

Or...

```

change_pointer(p, &k);
...

void change_pointer(int *p, int *z)
{
	p = z;
	printf("%d\n", *p);
}


```

...all seem to produce the same result.



This has to do with the way values are passed into functions in C. Everything is "call by value", which means that whatever you pass in is *copied*, meaning it's a different place in memory. So when you use & to get a pointer to 'z' in that function, it's actually a pointer *to the copy*, not the original variable.

So, to get around this, we pass a pointer to a pointer: that way, we have a way to get at the original pointer and change it. The pointer to a pointer is a copy, but what it points at is the original pointer. Got the point? (it helps to draw a picture of what's going on in memory).

> 
So I got to wondering if there isn't some much more basic concept going on here, possibly even something that's language independed. Possibly something that's simply inherent in logic iteslf!


The idea of passing by value vs passing by reference is language independent. C only allows passing by value, so to get around it, it's easy to extract a reference from a value: for something named 'foo', '&foo' is a reference - a pointer - to 'foo'. So, if we can only pass around things by value, the way to pass things by reference is to make references values and pass those in. That's one of the things pointers are good for.

> I know this is kinda off the beaten path or whatever, but all this gets me wondering about some very very foundational things. Such as: All languages aside, think about the formal rules of logic itself (a philosophical level if you will). These are just concepts, like mathematical rules. You can write them on paper and you have a piece of paper with some ink or lead on it that's tangible, but the rules themselves have no substance. Now, with that in mind, could one conclude that any given programming language is like a framework applied on top of those rules of logic? That the shape of the framework may change from from one language to the next but that the logic itself abides? If that's the case then it means I'm trying to learn one, among many, frameworks and it's as important to know how it weilds logic as it is to know what the framework 'looks like'. (Bachstelze - reminds me of somthing you once told me). 

I wonder if we can't thank the "touring machine" for all the possibilites.


(Small point - it's a [Turing machine](http://en.wikipedia.org/wiki/Turing_machine), named after [Alan Turing](http://en.wikipedia.org/wiki/Alan_turing))

Although you haven't said it very precisely here, it seems like you're on the right track: just about every general purpose programming language is called "Turing complete", which just means it's equivalent in power to any other computing machine. A programming language is just a formal way to writing down a computable function, and if a language is Turing complete, it can express *any* computable function. There are a lot of different ways you can be Turing complete, and this is evident by the plethora of different programming languages: assembly languages, C, Python, Scheme, Haskell, Prolog and brainfuck are all precisely equal in the breadth of their ability to express computation. Note that this doesn't necessarily translate to ease of use by a human. :) I'll let CptPicard jump in with a more thorough explanation if he so desires - he's much more knowledgable about these sorts of things than I.

> 
Is there a difference between what & and * 'do' (the end result of thier use in code)?

What would that difference be then and what use is it? Things like... why do you need the both? Isn't one good enough? And such...


Although * and & are related, they are not the same. They are complements. & means "return a pointer to whatever this is", and * means "give me whatever this is pointing to". So, if we want to use the well-worn "pointers are arrows" analogy, & means "give me an arrow pointing to this box", and * means "show me the box this arrow points to". Except the arrows are also boxes. Or something. It's not a great analogy for more complicated things...

> 
Can you dereference something with an &? If you use & to pass a variable address will the variable which address was passed remain in that state or is the ampersand's effect just etherial? (Does the & change the variable to a pointer for good?)


This is very important to understand: the & itself does not change anything about the variable. All it does it return a pointer to the place in memory the variable represents.

> 
And a more foundational curiousity (within the realm of C, as a particular language, yet reaching down, touching the place where programming languages and logic meet)...

Do pointers solve some limitation imposed by scope? I'm thinking, why pointers? Why even have pionters at all? There must have been some good reason for their creation in the first place. Sure we could talk about what they do or even how they do it but that's pretty conrete. What main, all encompassing need are pointers designed to bring to the table?

hmmm...
Pointers have a lot of uses. One of the main reasons to use them is that sometimes you have big chunks of memory, and sometimes you need to pass those big chunks of memory around. Now, what would you rather do: copy a ton of memory all over the place, or just pass in a (relatively small) pointer to it? The pointer lets you "get at" arbitrary places in memory without having to do expensive copy operations.

---

### Post by satsujinka on 2012-03-27
@ClientAlive
A slightly lengthier version of the code before, highlighting some of the problems you'd have with what you were playing with.
```
#include <stdio.h>
//update propagates
void addone(int *i) {
	*i += 1;
}
//update doesn't propagate
void plusone(int i) {
	i += 1;
}
//update propagates
void change_pointer(int **p, int *i) {
	*p = i;
}
//update doesn't propagate
void change_pointer2(int *p, int *i) {
	p = i;
}
//update sets pointer to a new value
void change_pointer3(int **p, int i) {
	*p = &i;
}

void print(int *i, int *j, int *p) {
	printf("&i: 0x%x\n", i);
	printf(" i: %d\n", *i);
	printf("&j: 0x%x\n", j);
	printf(" j: %d\n", *j);
	printf(" p: 0x%x\n", p);
	printf("*p: %d\n\n", *p);
}

int main() {
	int i = 0;
	int j = 0;
	int *p = &i;
	printf("Start:\n");
	print(&i,&j,p);						//i,*p,j are 0
	addone(p);
	printf("After addone:\n");
	print(&i,&j,p); 					//i and *p are 1, j is 0
	plusone(i);
	printf("After plusone:\n");
	print(&i,&j,p); 					//same as before, changes by plusone discarded
	change_pointer(&p, &j);
	printf("After change_pointer:\n");
	print(&i,&j,p); 					//j and *p are 0, i is 1. p changes to the address of j
	change_pointer2(p, &i);
	printf("After change_pointer2:\n");
	print(&i,&j,p); 					//same as before, changes by change_pointer2 diacarded
	change_pointer3(&p, i);
	printf("After change_pointer3:\n");
	print(&i,&j,p); 					//i is 1, j is 0. p's address should be neither &i nor &j, *p's value is arbitrary (and unsafe)
	i++;
	printf("After i++:\n");
	print(&i,&j,p); 					//i is 2, *p doesn't change

	//array/pointer syntax
	puts("Arrays and pointers");
	int array[2] = {1,2};
	printf("array[1]:   %d\n", array[1]);
	printf("*(array+1): %d\n", *(array+1));
	return 0;
}

```

---

### Post by schauerlich on 2012-03-27
> **satsujinka said:**
> 
In point of fact array[i] is mostly syntactic sugar for *(array+i) (array[i] is safer because it does bounds checking, but they do more or less the same thing.)

C does not do bounds checking on array subscripting.

---

### Post by ClientAlive on 2012-03-27
> **satsujinka said:**
> 
You're on the right track. Basically, if you want a value to propagate upwards (so back to the calling function, and if the value was passed in there, to its calling function.) You need to add a pointer to it (since there's a degree of separation.) This is how pointers to pointers come into play, I want to modify p in a different function and have that modification propagate back to where I am (without doing p = somefunction().) Note, that there's only 1 degree of separation. Either it's a local variable (so I'm doing '=' to change it) or it's a pointer to a local variable (so I'm in some function that it isn't a local variable and I want to change it so I de-reference it to get the local variable and then I can use '='.)



I'm still reading your post but something really hit home with me when I read the above portion. I've used pass by reference before so , I suppose I had some notion of this lingering around in the back of my head somewhere. It's like it all just became so clear though. This idea of needeing to use a pointer to modify a variable outside the function you're in...

Well, this has me thinking about things like...

The main thing a C function does for you (code encapsulation, right?). And how, possibly, encapsulation in a function requires that it not have access to outside variables (scope) or it wouldn't be encapsulation...

(I'm making a lot of wild assertions here when I really don't know).

...And how this pointer (a pointer) creates a situation where you can have a kind of interface to connect to that's independent of what you connect with it. (You could swap code around like legos!). Good lord! Add to that the idea of header files and the combinations are limitless!

(These are some wild, wild ideas - I could be way off base here).

Well, anyway, just wanted to say that while it was fresh in my thoughts. Back to reading the rest of your post  :)

About the alternative code stuff in my last post though - I should clarify. If I said it "does" the same thing what I meant was it produces the same output. I tried the alternative shown at the top of your last post again...

```

change_pointer(&p, k);
...

void change_pointer(int **p, int z)
{
	*p = &z;
}

```

It does output the value that's assigned to k. If I change the value where k is initialized it prints that new value. If I pass in j instead of k it prints the value that j is initialized to.

---

### Post by schauerlich on 2012-03-27
> **ClientAlive said:**
> ```

change_pointer(&p, k);
...

void change_pointer(int **p, int z)
{
	*p = &z;
}

```

It does output the value that's assigned to k. If I change the value where k is initialized it prints that new value. If I pass in j instead of k it prints the value that j is initialized to.

This code is badly incorrect. That 'z' variable is local to change_pointer, which means that when the function ends, the memory 'z' once used is recycled for other stuff. So you're passing a reference to "old" memory that could have been overwritten.

Compare:

```
// works.c
#include <stdio.h>

void change_pointer(int **p, int z) {
  *p = &z;
}

int main(int argc, char **argv) {
  int a = 1;
  int *p = &a;

  printf("*p = %d\n", *p);
  change_pointer(&p, a);
  *p = 2;
  printf("*p = %d\n", *p);

  return 0;
}

```

```
$ ./works 
*p = 1
*p = 2

```

```
// what.c
#include <stdio.h>

void change_pointer(int **p, int z) {
  *p = &z;
}

int mess_with_stack(void) {
  int a[10];
  int sum = 0;

  for (int i = 0; i < 10; i++) {
    a[i] = i;
  }

  for (int i = 0; i < 10; i++) {
    sum += a[i];
  }

  return sum;
}

int main(int argc, char **argv) {
  int a = 1;
  int *p = &a;

  printf("*p = %d\n", *p);
  change_pointer(&p, a);
  *p = 2;
  printf("mess_with_stack(): %d\n", mess_with_stack());
  printf("*p = %d\n", *p);

  return 0;
}

```

```
$ ./what
*p = 1
mess_with_stack(): 45
*p = 32767

```

Notice how mess_with_stack has absolutely no reference to p or anything it points to? However, the memory it uses for its local variables ('a' and 'sum') is recycled from the memory used for 'z', and it overwrites the memory that p points to.

---

### Post by satsujinka on 2012-03-27
> **schauerlich said:**
> C does not do bounds checking on array subscripting.
I could have sworn it did... I've been away too long it seems. In that case array[i] notation is really just syntactic sugar.

> **ClientAlive said:**
> I'm still reading your post but something really hit home with me when I read the above portion. I've used pass by reference before so , I suppose I had some notion of this lingering around in the back of my head somewhere. It's like it all just became so clear though. This idea of needeing to use a pointer to modify a variable outside the function you're in...

Well, this has me thinking about things like...

The main thing a C function does for you (code encapsulation, right?). And how, possibly, encapsulation in a function requires that it not have access to outside variables (scope) or it wouldn't be encapsulation...

(I'm making a lot of wild assertions here when I really don't know).

...And how this pointer (a pointer) creates a situation where you can have a kind of interface to connect to that's independent of what you connect with it. (You could swap code around like legos!). Good lord! Add to that the idea of header files and the combinations are limitless!

(These are some wild, wild ideas - I could be way off base here).

Well, anyway, just wanted to say that while it was fresh in my thoughts. Back to reading the rest of your post  :)

And you still haven't bumped into function pointers...

As you pointed out, though, pointers do violate scope. Generally, you use scope to make what you're doing simpler (less to consider in doing the task at hand) so providing pointers makes the image a little more complicated. And if you find you're passing a pointer too frequently, it might be time for a global variable (if only to reduce the number of function arguments and to clean up the usage syntax.) I'm sure you'll find many usages for pointers, but I'd caution that you carefully consider their usage. Like many powerful language features, over use can quickly become abuse.

> **ClientAlive said:**
> 
About the alternative code stuff in my last post though - I should clarify. If I said it "does" the same thing what I meant was it produces the same output. I tried the alternative shown at the top of your last post again...

```

change_pointer(&p, k);
...

void change_pointer(int **p, int z)
{
	*p = &z;
}

```

It does output the value that's assigned to k. If I change the value where k is initialized it prints that new value. If I pass in j instead of k it prints the value that j is initialized to.
As schauerlich pointed out change_pointer (3 in my code) is very very wrong. It's printing the "right" values for you because you aren't doing anything to overwrite that area of memory. Whereas if you ran my code you'd see that the value of *p after change_pointer3 is arbitrary.

---

### Post by ClientAlive on 2012-03-27
> **schauerlich said:**
> This code is badly incorrect. That 'z' variable is local to change_pointer, which means that when the function ends, the memory 'z' once used is recycled for other stuff. So you're passing a reference to "old" memory that could have been overwritten.

Compare:

```
// works.c
#include <stdio.h>

void change_pointer(int **p, int z) {
  *p = &z;
}

int main(int argc, char **argv) {
  int a = 1;
  int *p = &a;

  printf("*p = %d\n", *p);
  change_pointer(&p, a);
  *p = 2;
  printf("*p = %d\n", *p);

  return 0;
}

```

```
$ ./works 
*p = 1
*p = 2

```

```
// what.c
#include <stdio.h>

void change_pointer(int **p, int z) {
  *p = &z;
}

int mess_with_stack(void) {
  int a[10];
  int sum = 0;

  for (int i = 0; i < 10; i++) {
    a[i] = i;
  }

  for (int i = 0; i < 10; i++) {
    sum += a[i];
  }

  return sum;
}

int main(int argc, char **argv) {
  int a = 1;
  int *p = &a;

  printf("*p = %d\n", *p);
  change_pointer(&p, a);
  *p = 2;
  printf("mess_with_stack(): %d\n", mess_with_stack());
  printf("*p = %d\n", *p);

  return 0;
}

```

```
$ ./what
*p = 1
mess_with_stack(): 45
*p = 32767

```

Notice how mess_with_stack has absolutely no reference to p or anything it points to? However, the memory it uses for its local variables ('a' and 'sum') is recycled from the memory used for 'z', and it overwrites the memory that p points to.

Yes, got it. Here is what my output was (using gcc). After several runs it was the same.

```

*p = 1
mess_with_stack(): 45
*p = 45

```

Nevertheless I think the last line, if the code were good, should have printed "*p = 1" right? But it doesn't, so I see what you mean on that level.  :)

I kind of, almost, get why as well. Just that I have an open question to a particular, concrete question:

When you pass a pointer into a function is it still passing a copy of the pointer or is it passing the actualy thing? If it's passing a copy then maybe it's becase of what a pointer is (or contains) that makes that ok - that makes it still work?

Because someone said: "...the way values are passed into functions in C. Everything is "call by value", which means that whatever you pass in is *copied*..."

Even pointers too?
-------------------

Can we revisit something for a minute? I'm pretty sure I get the basics, and we have had some awesome discussion about concept. Now I feel ready to think about the application. Some examples were given me earlier on in this thread but I'm not sure I'm on the same page when it comes to some of the terminology; and then, hopefully, picture the chain of events.

> **schauerlich said:**
> This has to do with the way values are passed into functions in C. Everything is "call by value", which means that whatever you pass in is *copied*, meaning it's a different place in memory. So when you use & to get a pointer to 'z' in that function, it's actually a pointer *to the copy*, not the original variable.

So, to get around this, we pass a pointer to a pointer: that way, we have a way to get at the original pointer and change it. The **pointer to a pointer** is a copy, but what it points at is the original pointer. Got the point? (it helps to draw a picture of what's going on in memory).
> 

When we say "pointer to a pointer" does that mean:

```

**p; //...is the pointer to a pointer because it's "*" (pointer) "*p" (to a pointer)?

```

Or does it mean:

```

**p = *q; //...is the pointer to a pointer because it's "**p" (pionter) "*q" (to a pionter)?

```

I'm trying to get a concrete connection (both syntactically and conceptually). Conceptually beacuse after syntax the next thing I'd think about is 'where what is being stored'. In other words, which pointer contains what peice of data and trace the sequence of events that occurs when using a pointer to a pointer to change a pointer. (If that makes sense).

[QUOTE=schauerlich;11796539]
The idea of passing by value vs passing by reference is language independent. C only allows passing by value, so to get around it, it's easy to extract a reference from a value: for something named 'foo', '&foo' is a reference - a pointer - to 'foo'. So, if we can only pass around things by value, the way to pass things by reference is to make references values and pass those in. That's one of the things pointers are good for.

Although * and & are related, they are not the same. They are complements. & means "return a pointer to whatever this is", and * means "give me whatever this is pointing to". So, if we want to use the well-worn "pointers are arrows" analogy, & means "give me an arrow pointing to this box", and * means "show me the box this arrow points to". Except the arrows are also boxes. Or something. It's not a great analogy for more complicated things...

This is very important to understand: the & itself does not change anything about the variable. All it does it return a pointer to the place in memory the variable represents.


Maybe this is saying the same thing in a different way, I'm not sure. I didn't notice that this was explicitly stated, but...

The asterisk "*" has two purposes doesn't it? -> to declare a variable of the type that stores a pointer - as well as - to dereference and ultimately get at the data stored at the memory location stored in the pointer.

The ampersand "&" has one purpose right? -> to pass the address of a variable

I had never encountered it before but if we call what "&" passes a "pointer" then were applying the term "pointer" to more than one object? (Not object in the technical sense, as far as I know, just me fishing for a good word to use).

One difference between "*" and "&" that I think I see is that if you use "*" you gain an actual other object (a pointer) whereas if you use "&" you don't. Having an actual other object to use makes a difference in what you can do because now you have something you can refer to as often as you like (This address storage container is concrete now, it exists). If you use "&" you may be able to do what you do with the address until that process ends but then it's over. Am I on the right track?

Note that there's a couple things mixed together in the above - one of them involves terminology.

Thanks
------------------

fwiw... I get why I was confused before. I wasn't making the right connection with physical memory and memory address before and I wasn't always considering them together as a pair.

[QUOTE]
//Diagram

          One Pointer has...
--------------------------------------------
| Physical Memory |   Memory address   |
--------------------------------------------

          One Variable has...
--------------------------------------------
| Physical Memory |   Memory address   |
--------------------------------------------

 One of any (object?) has...
--------------------------------------------
| Physical Memory |   Memory address   |
--------------------------------------------


---

### Post by Vaphell on 2012-03-27
```
_type **p;
```
to get the idea what happens when you use p with various numbers of * split the expression anywhere between int and p;
_type | **p => (**p) is of type (_type)
_type * | *p => (*p) is of type (pointer to _type)
_type ** | p => (p) is of type (pointer to pointer to _type)
these sentences are equivalent

```
_type **p = X;
```; means that both **p and X are of type _type;
_type (**p) = (X);


anybody recalls the name of that cli tool translating C to human readable text?

---

### Post by ClientAlive on 2012-03-27
How are you gonna modify what a pointer to a pointer stores when a pointer to a pointer stores a memory address? Did I misunderstand something here? I mean, it's easy to modify what a variable contains becuase that's just a normal piece of data (a number or letter or string, whatever). How could you modify a memory address (what I though I was told a pointer to a pointer is useful for)? It's just some hex number and even if you did modify it what would be the point? It's not like you save memory or something and who cares where the bits are on the stick of ram? Bits are bits right? What difference does it make? I'm not trying to be a smartass. These are sincere questions.
--------------------------

Ok, here...

I'm racking my brain, trying to come up with something. Ok, so if you pass a pointer into a function, and then you dereference it, what you have is a piece of regular data you can do something with. You can set it equal to something else or take user input into or whatever. You pass a pointer to a pointer into a function and you dereference it. What you have is not a regular piece of data you can do anything with. What you have is a memory address. You can't do any of the same things you would do with a regular piece of data on it. All you can really do is exchange the address it has in it with a different one. Now maybe that address which is stored is connected to a regular piece of data at the next step down the line but so what?

So I'm trying to think of an example that makes any sense how this would do anything meaningful for you at all. I'm not talking about a made up example designed to illustrate how a pointer to a pointer works, but a real life, honest to god program that would need something like that. What would such a program do and how would using a pointer to a pionter in it's code help it to do it's job. I real life program that someone would actually use for something.

---

### Post by satsujinka on 2012-03-28
Ok. So a pointer is the physical, memory address of a variable. That address is also a variable, so you have pointers to pointers (the address of an address to a variable.)

If you want to get the memory address of a variable you get its reference (&).
```
int i = 0;
printf("%d", &i); //prints the address of i
```
If you want to get to the value pointed to by a pointer you "dereference" it (*).
```
int i = 0;
int *p = &i; //set p to the address of i
printf("%d", *p); //dereference p to get the value of i
```
This works for pointers to pointers as well.
```
int i = 0;
int *p = &i;
int **pp = &p;
printf("%d", pp); //prints the address of p
printf("%d", *pp); //prints the address of i
printf("%d", **pp); //prints the value of i
```

So far so clear right?

To make it perfectly clear, you can avoid using pointers most of the time. 

```
typedef node struct { int data; node struct *next; } *list;
```

So assuming l is a list and append is a function that adds a new node to the list using some data, we can update l to point to the new node one of two ways:
With a pointer to a pointer
```
append(&l, data);
```
or by returning the new node and setting l equal to it
```
l =append(l, data);
```
Both of these do the same thing. However, let's say that append can have an error. In the second example we need to change append's type signature and pass in an error pointer wherever you call append. Whereas in the first example, you can update append to return an error and any code that uses append doesn't need to be updated.

This of course only comes into play when one of the variables you want to update is already a pointer.

---

### Post by ofnuts on 2012-03-28
> **satsujinka said:**
> Ok. So a pointer is the physical, memory address of a variable.For sufficiently virtual values of  "physical" these days :)

---

### Post by ClientAlive on 2012-03-28
> **satsujinka said:**
> Ok. So a pointer is the physical, memory address of a variable. That address is also a variable, so you have pointers to pointers (the address of an address to a variable.)

If you want to get the memory address of a variable you get its reference (&).
```
int i = 0;
printf("%d", &i); //prints the address of i
```
If you want to get to the value pointed to by a pointer you "dereference" it (*).
```
int i = 0;
int *p = &i; //set p to the address of i
printf("%d", *p); //dereference p to get the value of i
```
This works for pointers to pointers as well.
```
int i = 0;
int *p = &i;
int **pp = &p;
printf("%d", pp); //prints the address of p
printf("%d", *pp); //prints the address of i
printf("%d", **pp); //prints the value of i
```

So far so clear right?

To make it perfectly clear, you can avoid using pointers most of the time. 

```
typedef node struct { int data; node struct *next; } *list;
```

So assuming l is a list and append is a function that adds a new node to the list using some data, we can update l to point to the new node one of two ways:
With a pointer to a pointer
```
append(&l, data);
```
or by returning the new node and setting l equal to it
```
l =append(l, data);
```
Both of these do the same thing. However, let's say that append can have an error. In the second example we need to change append's type signature and pass in an error pointer wherever you call append. Whereas in the first example, you can update append to return an error and any code that uses append doesn't need to be updated.

This of course only comes into play when one of the variables you want to update is already a pointer.


I see. I can see start to see how you might use something like this. First thing that pops into mind for this class project is an array filled with pointers (though I'm not really sure that's the same thing as pointers to pointers). I might play around with it a bit now and see what kinds of things I can come up with. Thanks.

---

### Post by Bachstelze on 2012-03-28
Real life example: the strtol() function.

What it does is read a string, converting it to an integer. For example

```
int n = strtol("123", NULL, 10);
```

would store the integer 123 in the variable n. The third argument is the base in which he conversion is performed, it is not important to this discussion. What's important is the second. The man page gives the prototype of the function:

```
     long
     strtol(const char *restrict str, char **restrict endptr, int base);
```

So the second argument is a pointer to a pointer to a char. If you give a real pointer (not NULL) here, strtol() will set it to the first invalid character in the string. For example:

```
char s[] = "123a123";
char *p;
char **pp = &p; /* pointer to p */
int n = strtol(s, pp, 10);
printf("%d %c %s\n", n, *p, p);
```

will print "123 a a123".

The point of this is that it lets you know at what point strtol() encountered an invalid character (and stopped processing the string). It is useful because maybe you know that you have some other stuff after the number, and you want to do something else with it after you get it. Say I have a line with some sort of ID number and name:

```
char s[] = "12345 John Smith";
```

I do something like:

```
char *p;
char **pp = &p; /* pointer to p */
int id = strtol(s, pp, 10);

/* At this point, p points to the first space in the string,
   advance to the next non-space character */
while (isspace(*p)) {
    p++;
}

/* Allocate space for name and copy it */
char *name = malloc(strlen(p)+1);
strcpy(name, p);
```

---

### Post by ClientAlive on 2012-03-29
> **Bachstelze said:**
> Real life example: the strtol() function.

What it does is read a string, converting it to an integer. For example

```
int n = strtol("123", NULL, 10);
```

would store the integer 123 in the variable n. The third argument is the base in which he conversion is performed, it is not important to this discussion. What's important is the second. The man page gives the prototype of the function:

```
     long
     strtol(const char *restrict str, char **restrict endptr, int base);
```

So the second argument is a pointer to a pointer to a char. If you give a real pointer (not NULL) here, strtol() will set it to the first invalid character in the string. For example:

```
char s[] = "123a123";
char *p;
char **pp = &p; /* pointer to p */
int n = strtol(s, pp, 10);
printf("%d %c %s\n", n, *p, p);
```

will print "123 a a123".

The point of this is that it lets you know at what point strtol() encountered an invalid character (and stopped processing the string). It is useful because maybe you know that you have some other stuff after the number, and you want to do something else with it after you get it. Say I have a line with some sort of ID number and name:

```
char s[] = "12345 John Smith";
```

I do something like:

```
char *p;
char **pp = &p; /* pointer to p */
int id = strtol(s, pp, 10);

/* At this point, p points to the first space in the string,
   advance to the next non-space character */
while (isspace(*p)) {
    p++;
}

/* Allocate space for name and copy it */
char *name = malloc(strlen(p)+1);
strcpy(name, p);
```


This is exactly the kind of solution I was trying to figure out for my file i/o project before. I wanted to read the data in from the file, line by line, and use the first space in the line to delimit the first of 4 different pieces of data per line. I needed to do a manipulation on that first piece of data. That's really cool. It also shows me I could stand to learn more of the library functions there are.  :)

I had kind of revelation about something last night - well, I shouldn't say that until I know it can be done. What I thought was that with pointers to pionters a person could make a sort of generic struct then plug in different stuct members according to need. Then you'd have one generic struct and however many sets/ groups of struct members to load it with. You'd essentially be using a small amount of code for an unlimited variety of different structs. This is something I'd like to experiment with.

I was also pondering what a function that returns a pointer might do for you. Or even a function that returns a pointer to a pointer. Oh my, what possibilities! I think...

---

### Post by Bachstelze on 2012-03-29
Functions that return double-pointers are virtually unheard of. There are a lot of functions that return pointers, though. You already know malloc(), another example is strchr(), which locates a character in a string. For example:

```
char s[] = "abcdefg";
char *p = strchr(s, 'c');
```

p will point to c, so that if I do

```
printf("%c %s\n", *p, p);
```

it will print "c cdefg".

A pointer is an address in memory, it indicates where in memory a certain object is. With malloc(), after you allocate a chunk of memory, you want to know where it is so you can store stuff in it. With strchr(), besides knowing whether or not the given character is in the string, you might want to know *where* it is in the string.

---

### Post by ClientAlive on 2012-03-30
Well, thanks everybody for all your help. Suppose I better get started on this thing (little over 2 wks left to do it).

I was talking to a tutor we have at my local campus. He's an old timer who tutors math but has worked as a developer most of his life (in C no doubt). He was talking to me about something that really has nothing to do with any particular language. He told me that an experienced programmer can watch how someone else programs and tell you exactly how long they've been doing it. He said the new guys always try to pull this hail mary stunt where they try to throw down the whole program all at once before checking to see if it works. The experienced programmers, he says, always start out the same way - "Hello World" (and he was serious)! He said when they write a program they test after every couple or few lines and do it bit by bit like that.

He also said that if you look in the working directory of an experienced programmer you'd see a whole slew of files. Something like "Program-001.c, Program-002.c, Program-003.c ... Program-...n.c". Basically that they'll save and set aside the file after new parts are added. He said the working directory of a less experienced person (but who's starting to pick up on doing that) would be numbered with just one digit, maybe two, but the more experienced would have ...00n, so I know he was talking about saving and setting aside files as you go being very important.

This guy totally hit the nail on the head. I have to admit I do that first thing (write out a whole lot of code before testing it). The things he was talking about (the process of writing code) is something I haven't spent much time thinking about. I guess your approach to writing code is as important, if not more important, than things like learning syntax and memorizing what library functions there are.

I came home and tried the approach he was talking about and got more done in 30 min than I normally would in days. It blew my mind! He talked about starting small and building up too. So trying this out I saw that, for me at least, this is really the best approach. Testing after every few lines, when I ran into trouble I knew exactly where to look for the problem and it wasn't a lot of code to look through so it was easy to find and fix. Then I moved on.

Anyhow, just thought I should share that. I was glad to have that driven home.

Peace out for now fellas. Thanks again.

---

### Post by Bachstelze on 2012-03-30
> **ClientAlive said:**
> 
He also said that if you look in the working directory of an experienced programmer you'd see a whole slew of files. Something like "Program-001.c, Program-002.c, Program-003.c ... Program-...n.c". Basically that they'll save and set aside the file after new parts are added.

Sounds like that was before version control was invented. :p

---

### Post by Vaphell on 2012-03-31
real men do version control by hand :)

---

### Post by dwhitney67 on 2012-03-31
> **ClientAlive said:**
> 
So I'm trying to think of an example that makes any sense how this would do anything meaningful for you at all.

```

int main(int argc, char** argv)   <--- Is this a good enough example?
{
}

```

---

### Post by ClientAlive on 2012-03-31
> **Bachstelze said:**
> Sounds like that was before version control was invented. :p


Lol. Yeah...

I was looking at Mercurial. I have a third computer (old destop I beefed up). Been thinking it would be nice to use it for a server w/ Mercurial being one of the things on it.   :D

---

### Post by honda on 2012-04-03
Not sure if the original question has been answered, I couldn't find it.
```
	if(Selection != 'c' || Selection != 'v' || Selection !='m'
	|| Selection != 'd' || Selection != 'e')
	{
		Status = 0;
	}
```
The validation function has a basic logical error. The Validation function will always return zero and the compiler will probably optimize it away completely since it does nothing. Think about what happens when Selection=='c' for instance. The first is false (Selection!='c'), second true, third true and so on. If Selection is 'v', then the second is false and all other true. If Selection is '7', they all are true. What happens is that at least one is always TRUE, and when combined with logical OR, the whole statement will always be TRUE, and the function always returns zero.

Since the Validation function is supposed to return 1 when the selection is invalid the following will work:

```
int Validation(int Selection)
{
	int Status = 1;

	if(Selection == 'c' || Selection == 'v' || Selection =='m'
	|| Selection == 'd' || Selection == 'e')
	{
		Status = 0;
	}

return Status;
}
```

---

### Post by ClientAlive on 2012-05-08
Thx honda. It's been a while since I asked about that but I'm glad you shared. What you say makes sense. Probably I could stand to get a little better with my boolean logic  :)

Jake

---

