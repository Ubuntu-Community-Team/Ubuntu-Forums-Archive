---
title: "issapce problem in this snippet"
date: 2010-08-26
forum: Programming Talk
---

### Post by navaneethan on 2010-08-26
Here I do the operation for counting the no of words in a given string I know it is pretty simple but I did here as fine i think
but i get some issues here may you fix it plz

```
#include<stdio.h>
#include<conio.h>
#include<ctype.h>
void main()
{
	char *s;
	int count=1;
	clrscr();
	printf("Enter the String:");
	scanf("%s",s);
	while(s!='\0')
	{
		if(isspace(*s))
		{
			count++;
			s++;
		}
		else
		{
		    s++;
		}
	}
	printf("The no of string is%d",count);
	getch();
}
```

---

### Post by schauerlich on 2010-08-26
%s reads until the next whitespace, meaning all you'll get is one word with no spaces. Use fgets instead. You also need to account for punctuation... is "his/hers" one word or two?

---

### Post by Some Penguin on 2010-08-26
"If you move, I will strike.
If you don't move, I will strike."

Conclusion:  I will strike.

---

### Post by navaneethan on 2010-08-27
whether we can't do using scanf to seperate the words till get white space in a given whole string?conceptually is it correct?

---

### Post by navaneethan on 2010-08-27
> **Some Penguin said:**
> "If you move, I will strike.
If you don't move, I will strike."

Conclusion:  I will strike.

you can strike if you can't I am ready to do ;-) :D

---

### Post by schauerlich on 2010-08-27
> **navaneethan said:**
> whether we can't do using scanf to seperate the words till get white space in a given whole string?conceptually is it correct?

The easiest thing is to just fgets the whole line and then analyze the string from there, say by counting up all of your word separator tokens.

---

### Post by worksofcraft on 2010-08-27
> **navaneethan said:**
> whether we can't do using scanf to seperate the words till get white space in a given whole string?conceptually is it correct?

Yes conceptually but you have made some mistakes. The worst is that you didn't allocate any space for your string to read into!!! Here is my rendition... and pay attention to the warning you get from the compiler... gets is dangerous because it can *STILL* overflow the space that I did allocate!

```

#include<stdio.h> // printf, gets
#include<ctype.h> // isspace

int main(void) {
	char s[100]; // you have to allocate some actual space for your string to read into!!!
	char *p = s; // a pointer into that string

	printf("Enter the String:");
	gets(s);
	int count = 1; 
	while (*p) if(isspace(*p++)) ++count;

	return printf("The no of words in your string is %d\n", count);
}

```

I hope that helps :)

p.s. note: it's actually not very good algorithm tho cuz there can be leading spaces and multiple spaces and trailing spaces... and they ALL count as extra words :shock:

---

### Post by Compyx on 2010-08-27
Never, ever use gets(), use fgets():
```

fgets(s, 100, stdin);

```

Also note the only portable values to return from main are 0, EXIT_SUCCESS and EXIT_FAILURE.

---

### Post by worksofcraft on 2010-08-27
> **Compyx said:**
> Never, ever use gets(), use fgets():
```

fgets(s, 100, stdin);

```

Also note the only portable values to return from main are 0, EXIT_SUCCESS and EXIT_FAILURE.

Lol I know

I once wanted to teach computer programming and I learned that in order to teach the right way, you have to show how it fails the wrong way: I deliberately choose gets() so to reinforce the failure of allocating memory for the read result :shock:
as for returning a value... it officilly just has to be an int so the result from printf is just about as useless as a deliberate EXIT_SUCCESS imho. Saves me putting a pointless magical 0 in there ;)

---

### Post by schauerlich on 2010-08-27
> **worksofcraft said:**
> Lol I know

I once wanted to teach computer programming and I learned that in order to teach the right way, you have to show how it fails the wrong way: I deliberately choose gets() so to reinforce the failure of allocating memory for the read result :shock:
as for returning a value... it officilly just has to be an int so the result from printf is just about as useless as a deliberate EXIT_SUCCESS imho. Saves me putting a pointless magical 0 in there ;)

Of course, the printf in your sprogram will always either fail or print something, meaning your program will always exit as a failure...

[http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)

---

### Post by worksofcraft on 2010-08-27
> **schauerlich said:**
> Of course, the printf in your sprogram will always either fail or print something, meaning your program will always exit as a failure...

[http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)

Good point. Admittedly I shouldn't think too many scripts are going to be testing the said result, and it was more just my way of saying that main should officially return something rather than leaving an undefined result... idk doesn't it actually return just whatever happens to be in the eax register if nothing is specified?

Whatever, howz about:

```

return !printf("");

```

Then it will exit as a failure only when printf failed.

---

### Post by dwhitney67 on 2010-08-27
> **worksofcraft said:**
> 

Whatever, howz about:

```

return !printf("");

```

Then it will exit as a failure only when printf failed.

Yeah... that happens often.  :roll:

Why not just return 0.
```

return 0;

```
As you said, nothing will (probably) be checking the return code.  Nevertheless, exit with a status indicating that the program is exiting successfully.

---

### Post by worksofcraft on 2010-08-27
> **dwhitney67 said:**
> Yeah... that happens often.  :roll:

Why not just return 0.
```

return 0;

```
As you said, nothing will (probably) be checking the return code.  Nevertheless, exit with a status indicating that the program is exiting successfully.

... but if printf failed then it wasn't very successful so I would be doing the user a disservice by returning a success status code.

Also it means typing a whole extra line of code :shock: and to do it properly I would have to include the header file that defines symbols EXIT_SUCCESS and EXIT_FAILURE and that would mean I have to go look it up because I forgot which one it is and well basically I'm too lazy for all that, specially when printf gives a nice handy value right where I need one :)

---

### Post by dwhitney67 on 2010-08-28
> **worksofcraft said:**
> ... but if printf failed then it wasn't very successful so I would be doing the user a disservice by returning a success status code.

Doing the user a disservice???  With you ample programming experience, I'm sure you could show me a situation where printf() would fail.

> **worksofcraft said:**
> 
Also it means typing a whole extra line of code :shock: and to do it properly I would have to include the header file that defines symbols EXIT_SUCCESS and EXIT_FAILURE and that would mean I have to go look it up because I forgot which one it is and well basically I'm too lazy for all that, specially when printf gives a nice handy value right where I need one :)
The adjective "lazy" was not what first popped into my mind. The header file you are referencing is <stdlib.h>, which even I had to look up.  Most folks just return a hard-coded 0 when a program exits successfully, and non-zero otherwise.

The use of EXIT_SUCCESS and EXIT_FAILURE, albeit cute, are merely macros that map to 0 and 1, respectively.

---

### Post by worksofcraft on 2010-08-28
> **dwhitney67 said:**
> Doing the user a disservice???  With you ample programming experience, I'm sure you could show me a situation where printf() would fail.


The adjective "lazy" was not what first popped into my mind. The header file you are referencing is <stdlib.h>, which even I had to look up.  Most folks just return a hard-coded 0 when a program exits successfully, and non-zero otherwise.

The use of EXIT_SUCCESS and EXIT_FAILURE, albeit cute, are merely macros that map to 0 and 1, respectively.

Lol - ;) the return result from printf is about as useful as the one from main in this case but how do you persuade **new** programmers to actually return a meaningless result? My question to the OP would be what he/she thinks about returning a status after reading this discussion, but probably more germane would be finding a better algorithm for the application?!

BTW I did hear of a system where EXIT_SUCCESS and EXIT_FAILURE are defined the other way round :shock:

---

### Post by trent.josephsen on 2010-08-28
> **worksofcraft said:**
> Lol - ;) the return result from printf is about as useful as the one from main in this case but how do you persuade **new** programmers to actually return a meaningless result? My question to the OP would be what he/she thinks about returning a status after reading this discussion, but probably more germane would be finding a better algorithm for the application?!

BTW I did hear of a system where EXIT_SUCCESS and EXIT_FAILURE are defined the other way round :shock:
It's possible, but regardless of the values of EXIT_SUCCESS and EXIT_FAILURE, "return 0" is guaranteed to return an appropriate code meaning success.  Other values result in, erm, implementation-defined behavior I think?  The only portable meaningful arguments to exit() or return from main are EXIT_SUCCESS, EXIT_FAILURE, and zero.

---

