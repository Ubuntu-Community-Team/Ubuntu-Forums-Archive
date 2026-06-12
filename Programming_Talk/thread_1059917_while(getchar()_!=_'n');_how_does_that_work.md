---
title: "while(getchar() != '\n'); how does that work?"
date: 2009-02-04
forum: Programming Talk
---

### Post by myromance123 on 2009-02-04
Hey there, I'm having trouble understanding how this statement works
 
 ```
while(getchar() != '\n');
```

From what I understand is that it searchs until it reaches the newline character right?
 Well how does it remove that character from standard input?

For example in the code below (which frustrated me until I tried the above statement):
```
#include <stdio.h>

int main()
{
	char words[200];
	char unwanted[2];
	char input;
	int done = 1;
	
	puts("\n\tHey there, what do you want to be reminded?");
	fgets(words, 200, stdin);
	
	puts("\tOk I understand!\n");
	puts("Would you like to exit? (Q) or be reminded? (R)\n");
	
	while(done)
	{
		printf("Choice(type here):");
		
		fgets(unwanted, 2, stdin);
		input = tolower(unwanted[0]);
		while(getchar() != '\n');
	
		switch(input)
		{
			case('r'):
				printf("\t%s\n", words);
				puts("Would you like to exit now? (Q) or be reminded again? (R)");
				break;
			case('q'):
				printf(" Now Exiting...\n");
				done=0;
				break;
			default:
				puts("Invalid key pressed");
				puts("Please press only Q to exit or R to be reminded");
				break;
		}
	}
	
	puts("Thanks for using me!! ");
	return(0);
}

```

Now when I first tried the above I didn't include that statement and the stupid newline character wouldn't stop bugging me ( I also used scanf() instead fgets() at first but it was too troublesome)

So if anyone could help me understand why:
```
		fgets(unwanted, 2, stdin);
		input = tolower(unwanted[0]);
```
 doesn't suffice and that I need the while statement?
Plus how that statement works?

 I had also declared the words variable without stating the amount of elements (the [200]) but found I couldn't use fgets() without a predetermined size...
  Is there a way to use fgets() without determining the size?
Because the point of the program is to record input (which could be very long or short)..
 Im still quite the beginner at C so please keep it simple, thanks!
:)

---

### Post by ncubede on 2009-02-04
I'd recommend to read something like the Harbison and Steele. This is from the manpages:
> 
fgets() reads in at most one less than size characters from stream and stores them into the buffer pointed to by s.  Reading stops after an EOF or a  newline.   If  a  newline  is read, it is stored into the buffer.  A '\0' is stored after the last character in the buffer.


You declared the array as size 2, the char and the following '\0', so fgets did never read the newline itself. If all you care about is to read one char from stdin and then dump all chars to the next newline, you perhaps rather want to just say:
```

int choice;
int ignored;

choice = fgetc(stdin);
do {
  ignored = fgetc(stdin);
} while ((ignored != '\n') && (ignored != EOF));

```

---

### Post by Tony Flury on 2009-02-04
```

while(getchar() != '\n');

```

bear in mind that the expression in the while loop is executed everytime - so even when the character is '\n' is found, it has already been removed from the stream by the getchar() call.

Another way to rewrite the statement would be 
```

char c;
c = getchar();
while(c != '\n')
    c = getchar();

```

Does that make more sense now ? It does exactly the same thing = but you use more lines of code and have to declare a variable.

---

### Post by myromance123 on 2009-02-04
> I'd recommend to read something like the Harbison and Steele.
 Is that a book, ncubede?

  Is it the "C: A Reference Manual" ?
The latest version I've found is 2002, is it not outdated by any chance?

So, you're saying fgets never read the newline? Yet when I dont have the while() statement it takes in the newline meaning it's still taking in the newline but just keeping it in the buffer until the next time input is required again right?

why did you declare the variables choice and ignored as int?
  Remember Im a beginner so going easy on me is much appreciated!

Yes I believe I understand better with that example Tony Flury.
 So basically it just sifts out the characters until it meets the newline and does not include the newline character into the variable once it finds the newline since it completes its task there.

But what are you saying here?
> bear in mind that the expression in the while loop is executed everytime - so even when the character is '\n' is found, it has already been removed from the stream by the getchar() call.
 Are you saying once is enough? Meaning it does not have to be put into the loop but instead above it? I read it several times but I cant tell if I understand correctly or not.

Thanks for your fast replies! :)

---

### Post by Tony Flury on 2009-02-04
> **myromance123 said:**
> 
Yes I believe I understand better with that example Tony Flury.
 So basically it just sifts out the characters until it meets the newline and does not include the newline character into the variable once it finds the newline since it completes its task there.

But what are you saying here?

 Are you saying once is enough? Meaning it does not have to be put into the loop but instead above it? I read it several times but I cant tell if I understand correctly or not.

Thanks for your fast replies! :)
no quite - I don't mean once is enough - certainly in my second example you have to have the getchar() both above and within the loop : You need to fetch the first character that you test (that is the call above the loop), and then each time round the loop you need to get another character (i.e. getchar()) that you then test.

What i meant is in the original statement 
```

while (getchar() != '\n');

```
is that the test - (getchar() != '\n') - gets executed each time you go round the loop, so this fetches a character and tests it against '\n', and goes back round to execute the condition again if the first test fails (i.e. the character is '\n'). One of the key things here is the semi-colon at the end of the statement - which effectively creates an empty loop - so the condition (including the getchar() function).

---

### Post by stroyan on 2009-02-04
The GNU libc which ubuntu uses includes an extension to scanf that can allocate storage for a string as it reads it.

```

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
    FILE *f;
    int i;
    char *line;

    for (i=1; i<argc; i++) {
	f = fopen(argv[i], "r");
	if (f == NULL) return 1;
	while (fscanf(f, "%a[^\n]\n", &line) == 1) {
	    printf("line is '%s'\n", line);
	    free(line);
	}
	fclose(f);
    }
    return 0;
}

```

---

### Post by Nemooo on 2009-02-04
After using fgets i use this little function to avoid the problem you're experiencing. Just as while(getchar() != '\n'); it *eats* what's left in the buffer, so this isn't mistakenly taken as input later.

```
void clear_buffer(char *input)
{
	char *i;

	/* i is the pointer to the occurence of '\n'. */
	i = strchr(input, '\n');

	/* If there is no '\n' get the remaining input left in stdin, so it 
	isn't taken as input later on */
	if(i == NULL)
		while(getchar() != '\n');

	/* If there is a '\n' replace it with a '\0' because we later on don't 
	want the '\n' printed. */
	else
		*i = '\0';
}
```

---

