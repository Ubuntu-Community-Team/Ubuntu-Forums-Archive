---
title: "Strange command line argument behaviour"
date: 2007-07-15
forum: Programming Talk
---

### Post by quark_77 on 2007-07-15
Hi All,

Apologies for asking such a simple question but I'm having trouble compiling what should be a simple program. Here's the general idea:
[LIST=1]
[*]The program peforms various sorts based on what you pass as command line options
[*]The syntax is ```
Sorting SORTNAME NUMBERS
```
which does the obvious, namely spits out this is a sorting program followed by each pass of the various sorts, for example shuttle, bubble etc which are passed as the SORTNAME argument.
[/LIST]
OK so far? Right, I have an option license (use instead of sortname) which displays the appropriate section of the GPL. Now, typing ./Sorting license (which works on Windows) doesn't work on Linux. Here's the two relevant pieces of code:
```
	/* Get option string off arg 1 */
			strcpy(options, argv[1]);

```
that is simply options = argv[1]
then:
```
	if ( strcmp("license", options) == 0 )
			{
				license();
				return 0;
			}

```
should, if license passed, print the license.. Now for the program output. Between these lines I put a debug printf (not ideal I know I'm no good with gdb). That spat out this:
```
DEBUG: options = licens&#65533;
```
Now, it does the same thing with the shuttle option but not the shell option, or the bubble, both of which function properly under the strcmp function. So this must be some oddity of the command line?

So my question is- what is causing these problems and how do I fix them? Has anybody else compiled their source files on Linux & Windows using standard stuff?

Thanks in advance for all your help,

---

### Post by rodo-&gt;dave on 2007-07-15
What is the size of "options"?
What happens if you use sprintf(options, "%s", argv[1]);  instead of strcpy(options, argv[1])?

Could you post a bit more of the code?

---

### Post by grado on 2007-07-15
Looks like an encoding problem ... What terminal are you using? echo $TERM ??

---

### Post by grado on 2007-07-15
of course, as dave pointed, how are you allocating "options"?

---

### Post by quark_77 on 2007-07-15
Further weird behaviour...

OK, I wrote this program initially on Windows. I use MinGW on Windows mostly but also use VC 8.0 occasionally (the Mozilla Build System uses VC 6-8 not unreasonably). Here's the story:

Under cmd.exe, VC 8.0 compiles this program fine, I'm able to pass the command line arguments across no problem for bubble sort (as an example). Run it under Powershell and using the following command:
```
./Sorting bubble 4 3 2 1
```
Produces a strange output for one of the numbers. Under BASH, this happens also:
```
DEBUG: options = bubble
Using "Bubble Sort"
Pass 1: 3 2 1 0 
Pass 2: 2 1 0 3 
Pass 3: 1 0 2 3 
Pass 4: 0 1 2 3 

```
(for the above command).

Now, if I were to run this program with one more number:
```
./Sorting bubble 5 4 3 2 1
```
It works perfectly, as it does under powershell.

Just to throw another oddity into the works, IF I use MinGW on Windows to compile the program it runs perfectly every time under PS, it's just the VC one that stuffs up.

I don't think there's anything particularly wrong with my code, as far as I can tell, so I'm not sure why these oddities are produced. I note different compiler versions (gcc 4.1.2 on Linux, 3.4.2 on Windows, VC8 etc) could THESE be causing the difference? 

Someone please rescue me - I thought such a simple program would be a nice way to get started again having taken a while off because of A-levels!

Just to clarify - I don't massively care about the oddities with powershell as I'm likely to use GCC anyway, but the ones with bash do bother me...

Thanks once again for any help...

Quark_77

---

### Post by jixuanliu on 2007-07-15
if you bubble 4,3,2,1, how much is your argc? where is the first element in your array? because i once noticed that with some environment the argument array begins with argv[0] while others with argv[1].

---

### Post by quark_77 on 2007-07-15
OK...

echo $TERM gives: xterm

It wasn't an encoding issue, it's me being a twit. license is seven letters long as is shuttle, I forgot about the mandatory "null" item terminating a char array...

the code in all it's glory:

```
int main(int argc, char* argv[])
{
	char options[8];	/* Options - choose a sort */ <<<< this did say options[7]
	int* list;       /* list array - dynamically resize this */
	int i = 0;			/* loop counter */
	int list_count = (argc - 2);		/* size of array */

	printf("Sorting Demo\n\n");
	if (argc < 2) 
	{ 
		usage(); /* If no arguments print usage */
	} 
	else
	{
		if (strlen(argv[1]) > 8)
		{
			/* if it doesn't fit the array... */
			printf("Your option was too long. Type sorting help\n");
			return 1;
		}
		else
		{
			/* Get option string off arg 1 */
			strcpy(options, argv[1]);
			/* Assign memory for array */
			list = calloc ( list_count , sizeof(int) );
			
			if ( list != NULL )
			{
				for (i=2; i < argc;i++)
				{
					/* Assign items, list arrays start at 0 whereas we 
					 * need to read from the 
					 * second argument onwards. Thus, i-2 = i. */
					list[i-2] = atoi(argv[i]);
					/* Now we are set up */
					printf("%i ", list[i-2]);
				};
			}
			else
			{
				/* Protect against insufficient memory */
				printf("Sorry, I don't have enough memory. On Linux, increase");
				printf("user stack size\nor shorten your list!");
				return 2;
			};
			printf("DEBUG: options = %s\n", options);
			/* Act upon options */
			if ( strcmp("license", options) == 0 )
			{
				
				license();
				return 0;
			}
			else if ( strcmp("errors", options) == 0 )
			{
				errors();
				return 0;
			}
			else if ( strcmp("help", options) == 0 )
			{
				usage();
				return 0;
			}
			else if ( strcmp("bubble", options) == 0 )
			{
				printf("Using \"Bubble Sort\"\n");
				bubble(list, list_count);
			}
			else if ( strcmp("quick", options) == 0 )
			{
				printf("Using \"Quick Sort\"\n");
			}
			else if ( strcmp("shuttle", options) == 0 )
			{
				printf("Using \"Shuttle Sort\"\n");
				shuttle(list, list_count);
			}
			else if ( strcmp("shell", options) == 0 )
			{
				printf("Using \"Shell Sort\"\n");
			}
			else
			{
				printf("Option not recognised. Try just running sorting.exe");
				printf(" for \nhelp - or sorting help.\n");
				return 1;
			};
			
			/* Release memory allocated for list items */
			free(list);
		};
	};
	return 0;
};
```

There you have it. Perhaps all those else if's shouldn't be there but it's neater than case as far as I'm concerned.

Onto the second problem I posted... It's probably my stupidity again so I'll take a look at the code! Thanks for all your help, my apologies!!

---

### Post by Mr. C. on 2007-07-15
There is no "encoding" problem here.

Your test for option length still has a problem.  The string "12345678" is of length 8, which does not pass this:

```
if (strlen(argv[1]) > 8)
```

so you happily copy 8 chars + 1 null into an array which is only 8 chars wide.  You must be sure to check your input sizes before you copy, and check your OBO errors (off by one).

You are also blindly calling calloc without checking the boundary conditions. Consider what happens when you call your program with no arguments !  What will list_count be ?

But why bother copying the option string at all ?  You should separate your argument processing from the actions you will perform based upon the set of options which have been set.  As in:
```

main {
   get arguments and set flags
   
   perform appropriate actions based upon set flags
}
```

MrC

---

