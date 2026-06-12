---
title: "fgets function causes strange program flow"
date: 2010-02-22
forum: Programming Talk
---

### Post by Sidneyaks on 2010-02-22
Ok, I'm trying to work on an assignment for class, but I'm having strange issues with fgets. If I have it twice in the same program it causes the second call (and anything in the same function as the second call) to be skipped over completely. I've tried flushing stdin between the two calls, with fflush(stdin), but that appears to have no affect.

Is this a common error, or is there a way I can fix it? I've googled it and found nothing particularly useful. Thanks for your help.

---

### Post by Some Penguin on 2010-02-22
The problem is likely elsewhere.   You'll need to show some code around it and describe the behavior more thoroughly, methinks.

---

### Post by MadCow108 on 2010-02-22
can't help without an example of how you use it

also flushing input streams is undefined in C/C++, so don't do it.

---

### Post by Sidneyaks on 2010-02-22
So far this is the entire program. I'm writing a mall management code for my algorithms and efficiency class.

[PHP]
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>

struct store{
       char store_number[4];
       char store_name[36];
       char phone_number[9];
       char cat1;
       char cat2;
};

store MAX_STORES[52];

void yell();
void find();
void open();
void vacs();
void clos();
void write_new_store(int write_address);
void print_menu();

int main()
{
char menu_input[4];
int i;
while(1)
{
    print_menu();
    fgets(menu_input,4,stdin);		//fgets to aquire an input for the menu
    for (i=0; i <= 5; i++)		    //as well as a toupper loop to allow
    {menu_input[i]=toupper(menu_input[i]);}	//for case insensitivity
////////////////////////////////////////////////////
    if(strcmp(menu_input,"YELL"))	//A series of nested if...else loops is 
        {yell();}		        	//used because a switch statement can't 
    if(!strcmp(menu_input,"FIND"))	//handle strcmp arguements to my 
        {find();}		        	//knowledge
    if(!strcmp(menu_input,"OPEN"))	
        {open();			
	write_new_store(8);		
	}
    if(!strcmp(menu_input,"VACS"))
        {vacs();}
    if(!strcmp(menu_input,"CLOS"))
        {clos();}
    if(!strcmp(menu_input,"PRIN"))
        {printf("%s",MAX_STORES[8].store_name);}
    else if(!strcmp(menu_input,"EXIT"))
        {return 0;}
}
///////////////////////////////////////////////////////
}
void write_new_store(int write_address)
{						//
printf("Please enter store name");		//
fgets(MAX_STORES[8].store_name, 35, stdin);	//
}
//////////////////////////////////////////////////
//filler calls for unfinished functions
//////////////////////////////////////////////////
void yell(){}
void find(){}
void open(){}
void vacs(){}
void clos(){}
//////////////////////////////////////////////////
//Everything below this works as expected
//////////////////////////////////////////////////
void print_menu(){
system("clear");
printf("Please enter a command\n\n");
printf("YELL - Prints an alphabatized list of all stores\n");
printf("FIND - Find an individual store and print it's credentials\n");
printf("OPEN - Open a new store\n");
printf("VACS - Print a list of all vacant stores\n");
printf("CLOS - Close a store\n");
printf("EXIT - Exit the program\n");}[/php]

---

### Post by MadCow108 on 2010-02-22
one thing I see is that your buffers are to small
C strings always have a NULL byte at the end
so to store "abcd" you need a 5 byte buffer for "abcd\0"
also fgets stores this null byte after its read so it only reads num - 1 bytes from the stream (=3 in your  main loop)

use the strn... functions instead of the ones without n. their safer 
because the others can overrun their buffers

And fgets also reads newlines. You'll have to handle these somehow when interpreting the input

---

### Post by Sidneyaks on 2010-02-22
> **MadCow108 said:**
> one thing I see is that your buffers are to small
C strings always have a NULL byte at the end
so to store "abcd" you need a 5 byte buffer for "abcd\0"
also fgets stores this null byte after its read so it only reads num - 1 bytes from the stream (=3 in your  main loop)

use the strn... functions instead of the ones without n. their safer 
because the others can overrun their buffers

And fgets also reads newlines. You'll have to handle these somehow when interpreting the input

So when I type "open" and press enter it inserts a new line? Would just searching for the \n character in the array and write \0 to that address help?

---

### Post by MindSz on 2010-02-22
Hey,

1. You have a typo: You're missing a '!' in the first strcmp statement.
2. You should use strncmp instead, to compare the exact number of characters you're interested in.
3. Try to use 'else if' statements for all the options or else your code will check all the rest of the 'if' statements.

I have it working but it's better if you do it yourself :)

good luck!

Oh yea, as MadCow says, you should make the buffer larger and make your first call to fgets match the number of characters in that buffer.

---

### Post by Sidneyaks on 2010-02-22
Cool, thanks for your help guys. :D I'd tried setting the menu_input variable array size to five, but wasn't accounting for the fifth character being held by "*\n*". Thanks for your help again.

That would also explain why it worked with the gets(); function too, which had me all sorts of confused.

---

### Post by Some Penguin on 2010-02-22
> **Sidneyaks said:**
> So far this is the entire program. I'm writing a mall management code for my algorithms and efficiency class.

```

#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>

struct store{
       char store_number[4];
       char store_name[36];
       char phone_number[9];
       char cat1;
       char cat2;
};
store MAX_STORES[52];

```

Minor observations:
- Based upon the name, I would expect MAX_STORES to be an integer specifying how many stores there can be, not an array of stores.

- Based upon the name, I would expect store_number to be a numerical type, not a string.

  FWIW, some people like to prepend variable names with characters denoting their type, which can reduce such confusion.  See e.g. [http://en.wikipedia.org/wiki/Hungarian_notation](http://en.wikipedia.org/wiki/Hungarian_notation) 

  Variable names create certain expectations.  When their behavior is substantially different, this makes the related code more difficult to understand.

- Phone number is not large enough to include area codes.  It'll work for NNN-NNNN followed by the trailing \0.

- I don't see anything that would support an 'is this vacant' functionality.  Something could be purposed that way (e.g.  0-length name, special value for cat1 et al), but it's not obvious.

> ```

void yell();
void find();
void open();
void vacs();
void clos();
void write_new_store(int write_address);
void print_menu();

int main()
{
char menu_input[4];

```

As noted by a previous respondent, this is too short.  If you insist on 4-letter command names, you must specify 5 to fgets -- it reads at most one less than the number given, and then it will add a '\0' to be the nth character.

> ```

int i;
while(1)
{
    print_menu();
    fgets(menu_input,4,stdin);        //fgets to aquire an input for the menu
    for (i=0; i <= 5; i++)            //as well as a toupper loop to allow
    {menu_input[i]=toupper(menu_input[i]);}    //for case insensitivity
////////////////////////////////////////////////////
    if(strcmp(menu_input,"YELL"))    //A series of nested if...else loops is 
        {yell();}                    //used because a switch statement can't 
    if(!strcmp(menu_input,"FIND"))    //handle strcmp arguements to my 
        {find();}                    //knowledge
    if(!strcmp(menu_input,"OPEN"))    
        {open();            
    write_new_store(8);        
    }
    if(!strcmp(menu_input,"VACS"))
        {vacs();}
    if(!strcmp(menu_input,"CLOS"))
        {clos();}
    if(!strcmp(menu_input,"PRIN"))
        {printf("%s",MAX_STORES[8].store_name);}
    else if(!strcmp(menu_input,"EXIT"))
        {return 0;}
}
///////////////////////////////////////////////////////
}


```

Your if() statements are mutually exclusive, so you could be using 'else if' in each case. 

It would also be a good habit to output something descriptive (including the command that was actually read) if the command given does not match anything you're looking.  This might have warned you if, say, there were a bug in your fgets invocation that was reading one less character than you expected.

> ```

void write_new_store(int write_address)
{                        //
printf("Please enter store name");        //
fgets(MAX_STORES[8].store_name, 35, stdin);    //
}

```

Obvious question:  why 8?  Your array has 52 slots; if one were going to be reserved, the 9th seems fairly arbitrary.

As a cautionary note, the behavior might also be a bit strange if the user types more character than you expect.  You may find it convenient to use 'getline', which isn't part of the C standard library but is a GNU extension thereof.  This goes for reading commands, as well.


> ```

//////////////////////////////////////////////////
//filler calls for unfinished functions
//////////////////////////////////////////////////
void yell(){}
void find(){}
void open(){}
void vacs(){}
void clos(){}
//////////////////////////////////////////////////
//Everything below this works as expected
//////////////////////////////////////////////////
void print_menu(){
system("clear");

```

Starting another process to clear the screen is a touch heavyweight.  You will probably find an better way within the 'curses' library.

> ```

printf("Please enter a command\n\n");
printf("YELL - Prints an alphabatized list of all stores\n");
printf("FIND - Find an individual store and print it's credentials\n");
printf("OPEN - Open a new store\n");
printf("VACS - Print a list of all vacant stores\n");
printf("CLOS - Close a store\n");
printf("EXIT - Exit the program\n");}
```

---

### Post by MadCow108 on 2010-02-22
> **Sidneyaks said:**
> Cool, thanks for your help guys. :D I'd tried setting the menu_input variable array size to five, but wasn't accounting for the fifth character being held by "*\n*". Thanks for your help again.

That would also explain why it worked with the gets(); function too, which had me all sorts of confused.

five is still to low
you need 6 to also hold the null byte and a potential newline

---

### Post by Sidneyaks on 2010-02-22
> **Some Penguin said:**
> Minor observations:
- Based upon the name, I would expect MAX_STORES to be an integer specifying how many stores there can be, not an array of stores.

It's a required name from our instructor, so she can easily review our code.

> 
- Based upon the name, I would expect store_number to be a numerical type, not a string.

In the assignment the mall has two levels, thus two stores have the same numerical value, but are preceeded by u or l for upper or lower.

> - Phone number is not large enough to include area codes.  It'll work for NNN-NNNN followed by the trailing \0.

again, this is from our instructor, we were told that area codes would not be required in the program and not to worry about them.

> - I don't see anything that would support an 'is this vacant' functionality.  Something could be purposed that way (e.g.  0-length name, special value for cat1 et al), but it's not obvious.

The names are simply set to vacant, The cat1 and cat2 are also set to special characters.


> It would also be a good habit to output something descriptive (including the command that was actually read) if the command given does not match anything you're looking.  This might have warned you if, say, there were a bug in your fgets invocation that was reading one less character than you expected.

this will come in time. The first thing I had to do was make the command so I could populate a list with the store names.

> Obvious question:  why 8?  Your array has 52 slots; if one were going to be reserved, the 9th seems fairly arbitrary.

8 was just chosen on a whim. I didn't really want to deal with dynamically selecting an address before I knew that I could successfully write to it.

> As a cautionary note, the behavior might also be a bit strange if the user types more character than you expect.  You may find it convenient to use 'getline', which isn't part of the C standard library but is a GNU extension thereof.  This goes for reading commands, as well.

This was something that I hadn't thought of. Thank you, I will take it into account and find some way to handle the error.



> Starting another process to clear the screen is a touch heavyweight.  You will probably find an better way within the 'curses' library.

I'll look for it. Again, thank you.

---

### Post by Sidneyaks on 2010-02-22
> **MadCow108 said:**
> five is still to low
you need 6 to also hold the null byte and a potential newline

Yeah, I meant I had tried five earlier and it wasn't working, which was confusing me. I did get six eventually. :D

---

