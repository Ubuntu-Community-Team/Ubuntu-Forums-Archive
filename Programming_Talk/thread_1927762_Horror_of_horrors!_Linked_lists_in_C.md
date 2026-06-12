---
title: "Horror of horrors! Linked lists in C"
date: 2012-02-18
forum: Programming Talk
---

### Post by ClientAlive on 2012-02-18
My instructor just isn't breaking things down in enough detail and I don't know what to do about it. Trying to ask more questions is like beating a dead horse. There comes a point where there's no point anymore at all.

What I'd like help doing is tracking through, line by line and assignment by assignment, what is happening with assignments when we change head to temp and then assign head's pointer to NULL. One distinction I need to pull out of this (or have recognized if you will) is the distinction between the whole struct and a member in the struct when talking about the assigment being made. In the end, another thing is seeing where there is an equivalent way to describe one or more of the assignments that occured.

I attached the file containing the entire example code we were given. I'll use two lines of code from within the function called "void insert(int num)" below.

So, now to try and give a more specific question(s) using two lines of code from our example code (location referenced in the paragraph above).

> 
[B]If we say something like:

Head  = temp;
Head -> nextPtr = NULL;

When we use "Head" in the first line we are referring to the entire structure right? (That would mean everything in it as well right? The int and the pointer it contains).[/B]

[Comment: By that, I meant to say: "hey, lets look at this "whole" in the context of being something that has stuff in it - not just make some generalization about it."]

**Then, in the second line, we are referring to just one of the two members in that struct - namely the pointer in it.**

[Comment: By this point (the point of considering that second line of code, in addition to the first - yes I'm looking at it as what the two lines are doing, together in my mind now) when I get to that second line, I'm seeing 3 things involved in my picture here, not just two. (1) The whole struct "Head" (2) The whole struct "temp" (3) The member "nextPtr"]

**I understand that Head is a *pointer* to memory but there [still] has to be some way to think of the difference between setting values to the entire thing and referring to just a member in it (pointer to memory or not).**

[Comment: The paragraph below ties in what I'm more concerned about. I can visualize the differenct between a whole something an a member inside it - I'm not a retard. It's sequentially tracking the assignments being made in the context of what it's being made to (whole or member) and especially what that means/ what it results in. Then it's to see if there is an equivalent way to view it (for instance if the whole "Head" equals the whole "temp" then when we later say "Head -> nextPtr = NULL" isn't that the same as saying "temp -> nextPtr = NULL" because Head was made equal to temp before that? See below...]

**It's not just to make that distinction but to grasp it in the context of what is actually happening with the assignments we make. (In the first line Head is being assigned the value of temp (which is itself an instance of this struct), and in the second line, just an element in Head is being assigned the value NULL - but we already assigned Head the value of temp so does that mean it's really the nextPtr in temp that is set to NULL?).**



Additionally but much lower priority: I know they always say it's not accurate to do this, but if I just had some image of something I already know that I could use to visualize linked lists and structs (linked list AND structs - one involves the other)... Something familiar to attach this new concept to...  Some analogy... One that is simple in real life - boxes inside boxes not complicated thinkgs like skyscrapers, etc. You know? A good analogy.

---

### Post by Tony Flury on 2012-02-18
in your code sample :
```
Head = temp;
Head -> nextPtr = NULL;

```
> 
When we use "Head" in the first line we are referring to the entire structure right? (That would mean everything in it as well right? The int and the pointer it contains).

You are not assigning the whole of temp into the Head variable.

judging my the code snippet - both Head and temp are pointers, so what you are doing is setting Head to point to whatever temp is pointing to.

Assuming that before that line Head pointed to another item in memory, that memory would still be intact, it just would not have Head pointing to it any more, and so long as something else was pointing to it - you will not loose that data.

If you want to change the entire structure, you can change it element by element (like the 2nd line changes the nextPtr element), or you can change it all in one go : 

```

*Head = *temp

```
Will replace the content of the structure pointed at by Head, with the contents of the structure pointed at by temp (but the pointers stay pointing at the same areas of memory.

I hope this helps.

---

### Post by JKyleOKC on 2012-02-18
I'll probably regret this, Jake, but here's the analogy you asked for: A treasure hunt.

That is, the game kind where you're given a note that says "Look in the hollow tree." You find the hollow tree, and there's another note in it that says "Try the refrigerator." In the refrigerator, you get still another saying "Go to the pantry." Finally in the pantry, you find the treasure you're looking for.

Now you want to make the hunt a bit more complicated, so you go to the hollow tree, take out its note, replace it with a new one that says "Go to the woodshed" and finally hide the original tree note in the woodshed.

That's how the multiple pointers and struct definitions work, using memory addresses rather than notes. To put your two lines into context you have to go back to the "malloc" call at the start of the function. This gets a block of memory just the right size to hold the "node" struct, and stores its memory address in the pointer "temp" for future reference. The "Head = temp" line copies that address into a second pointer "Head" and the next line then uses the struct definition's "nextPtr" value to determine which area of the struct to use, and stores NULL at that location.

Yes, it's still the same memory area to which "temp" points. The reason for using two pointers instead of just one is to protect against possible failures. The "Head" pointer is more or less global and defines the entire list, which is a linked chain of "node" structs. If you're out of memory so that the malloc call cannot insert yet another node into the chain, it returns "NULL" rather than a valid memory address. Since you don't want to destroy the chain when this happens, you use the "temp" pointer to get the result, and copy it over to "Head" only if it contains a valid address.

A better analogy for the linked list might be a physical chain, where each link corresponds to an entire "node" struct. In fact, that analogy is where the name "linked" originated back in the late 50s.

---

### Post by ofnuts on 2012-02-18
> **ClientAlive said:**
> My instructor just isn't breaking things down in enough detail and I don't know what to do about it. Trying to ask more questions is like beating a dead horse. There comes a point where there's no point anymore at all.
[http://en.wikipedia.org/wiki/Linked_list](http://en.wikipedia.org/wiki/Linked_list)

No?

---

### Post by ClientAlive on 2012-02-18
> **Tony Flury said:**
> in your code sample :
```
Head = temp;
Head -> nextPtr = NULL;

```

You are not assigning the whole of temp into the Head variable.

judging my the code snippet - both Head and temp are pointers, so what you are doing is setting Head to point to whatever temp is pointing to.

Assuming that before that line Head pointed to another item in memory, that memory would still be intact, it just would not have Head pointing to it any more, and so long as something else was pointing to it - you will not loose that data.

If you want to change the entire structure, you can change it element by element (like the 2nd line changes the nextPtr element), or you can change it all in one go : 

```

*Head = *temp

```
Will replace the content of the structure pointed at by Head, with the contents of the structure pointed at by temp (but the pointers stay pointing at the same areas of memory.

I hope this helps.


That makes sense. You know, I think I was confusing myself about something. Conceptually, one would think theres something like that mirror within a mirror thing going on because of the fact that there's a struct within a struct (the next pointer). After I drew this diagram (attached to this post), and got to dwelling on it a little, I realized that you can't have memory within memory. When it comes to allocating memory it is just one level. Still, how does the compiler know when to stop? How is it that your compiler wouldn't enter something like an infinite loop and start allocating memory for memory for memory, add infinitum?

So, in the end, I think I'm starting to grasp this. Also, I think maybe there is an important differece to be recognized between a pointer and a regular variable that isn't a pointer. A distinction that ties into the difference in behavior.

Something I just pondered, I wonder if you were to assign a value to the next pointer in the struct's definition (an address) you would get that sort of thing => (Now the compiler probably wouldn't do it; but, conceptually, it would be like telling it to assingn memory within memory within memory, add infinitum). But we don't do that. We only decalare the next pointer in the struct's definition. Maybe that's why it stops at just one/ one level.


> **JKyleOKC said:**
> I'll probably regret this, Jake, but here's the analogy you asked for: A treasure hunt.

That is, the game kind where you're given a note that says "Look in the hollow tree." You find the hollow tree, and there's another note in it that says "Try the refrigerator." In the refrigerator, you get still another saying "Go to the pantry." Finally in the pantry, you find the treasure you're looking for.

Now you want to make the hunt a bit more complicated, so you go to the hollow tree, take out its note, replace it with a new one that says "Go to the woodshed" and finally hide the original tree note in the woodshed.

That's how the multiple pointers and struct definitions work, using memory addresses rather than notes. To put your two lines into context you have to go back to the "malloc" call at the start of the function. This gets a block of memory just the right size to hold the "node" struct, and stores its memory address in the pointer "temp" for future reference. The "Head = temp" line copies that address into a second pointer "Head" and the next line then uses the struct definition's "nextPtr" value to determine which area of the struct to use, and stores NULL at that location.

Yes, it's still the same memory area to which "temp" points. The reason for using two pointers instead of just one is to protect against possible failures. The "Head" pointer is more or less global and defines the entire list, which is a linked chain of "node" structs. If you're out of memory so that the malloc call cannot insert yet another node into the chain, it returns "NULL" rather than a valid memory address. Since you don't want to destroy the chain when this happens, you use the "temp" pointer to get the result, and copy it over to "Head" only if it contains a valid address.

A better analogy for the linked list might be a physical chain, where each link corresponds to an entire "node" struct. In fact, that analogy is where the name "linked" originated back in the late 50s.


That's a pretty good analogy. I think I can work with that, thanks. Nice to see you around Jim.
-------------------------

On the attachment here - probably just illustrates my confusion, I'm getting past it though. It's starting to make sense. Thanks guys.

---

### Post by Bachstelze on 2012-02-18
I think your main problem is you haven't yet grasped the concept of pointers.

> The entire instance of struct Node called &#8220;Head&#8221; is set to null.

No, Head is a *pointer*. It is not an instance of struct Node, it's just the memory address of one.

>  It contains two members: an int
Called &#8220;x&#8221; **and another instance of struct Node called nextPtr**. NextPtr, in turn must have two
Members in it since it's based off the same template &#8220;Node&#8221;.

No, it contains *a pointer to another instance of struct Node*. It's just an integer storing the address of the next node. *It is not the node itself.*

---

### Post by JKyleOKC on 2012-02-18
That link posted by ofnuts is an excellent description of exactly how a linked list works, although I would pick a bone with the history it contains. I believe that the idea was invented independently at about the same time by a leading British computer scientist whose name escapes me at the moment, and by Newell, Simon, and Shaw. I even did so a decade later, not knowing it already existed, to make it easier to edit text files!

To get along with C and any of its variations, you have to get the concept of pointers very clear in your mind. It's almost the central nervous system of the language. Many current systems make use of pointers to pointers to pointers (and so on, ad nauseum), and it's very easy to get lost. 

Drawing diagrams is the best way I know to deal with this. In your sample code, represent the "node" struct by a box that has two parts; one is the value itself and the other is a pointer to another instance of the node struct. What your two lines are doing is simply creating an instance of the struct, saving its address in "Head" and setting the pointer part to NULL to indicate that this is the last instance in the chain. The specific two lines you chose are executed only once, when creating the linked list originally. Other lines of the program are executed when adding or deleting links.

Study the diagrams in that wikipedia article until you grok it well, and things will be a lot simpler!

---

### Post by muteXe on 2012-02-19
> 
Something I just pondered, I wonder if you were to assign a value to the next pointer in the struct's definition (an address) you would get that sort of thing => (Now the compiler probably wouldn't do it; but, conceptually, it would be like telling it to assingn memory within memory within memory, add infinitum). But we don't do that. We only decalare the next pointer in the struct's definition. Maybe that's why it stops at just one/ one level.


The compiler doesn't magically know when to stop iterating over the list.  Look at your printList() method to see how it doesn't print forever.

> 
Also, I think maybe there is an important differece to be recognized between a pointer and a regular variable that isn't a pointer.

You bet there's a difference.

---

### Post by ClientAlive on 2012-02-20
Well, after thinking about what's been said so far, and thinking about that diagram I'd drawn up, I had a couple realizations about what's really going on (at least I thought I did). I dug in and was off to a great start (at least I thought I was).

So I have this awful habit of pulling these hail mary stunts with my code and not testing until I've written way too much in. Then, I figure I have all this time and effort into what I've done so far; and, when 3 pages of compiler errors burst onto the screen (ok it's not really 3 pages, but a lot), when that happens, I don't want to pare anything down. So I did it again.

I got about half the code written, tried to compile and got a lot of errors. Was able to sort out almost all of them but two. Started out, I tried what I thought the fix to the problem was; then, when that didn't work I just started trying variation of syntax I could think of. Now I see either one, certain, compile error or annother - depending on how I change the syntax. I'm pretty sure I'm mostly on target (though there's likely a much simpler/ better allaround design). Well, I'll post my code just in case someone feels like giving me a little love...   (I'm teasing)  :p


```

/*
Objective: Create a doubly linked list. Use a design in which it is the
current node that is used to create a new node or to delete. Prev and Next
are there for navigation and searching.

Tip: 

Status: 

Next steps: 
*/

#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>

typedef struct
{
	char Name[32];
	char Phone[18];
	struct Node *Prev;
	struct Node *Next;
}Node;

Node *Curr = NULL;

void Menu(); //Done
char ValidSelection(char S); //Done
void Insert(char InsName[], char InsPhone[]); //Done
//Delete();
//Search();
void Print(int Selection); //Done

int main(void)
{
	Menu();
	char Selection = ' ';

	Selection = getchar();
	ValidSelection(Selection);

	switch(Selection)
	{
		case 'A':
		case 'a':
		{
[B]			//insert

			char Name[32];
			char Phone[18];

			printf("Enter a name...");
			fgets(Name, 31, stdin);
			printf("Enter a phone number...");
			fgets(Phone, 17, stdin);

			Insert(Name, Phone);[/B]

			break;
		}

		case 'D':
		case 'd':
		{
			//delete
			break;
		}

		case 'S':
		case 's':
		{
			//search
			break;
		}

		case 'P':
		case 'p':
		{
			//print

			int Selection = 0; //initialize to zero?

			printf("Would you like to: Print [A]ll or Print [E]ntry ?\n");
			Selection = getchar();
			ValidSelection(Selection);
			Print(Selection);

			break;
		}
	} //end switch

return 0;
} //end main

void Menu()
{
	//display menu to user

	printf("Please select one of the following...");
	printf("[A]dd an entry\n");
	printf("[D]elete an entry\n");
	printf("[S]earch for an entry\n");
	printf("[P]rint entries\n");
	printf("[Q]uit\n");
	printf("\n");
} //end function

char ValidSelection(char S)
{	//accept user's selection - include validation

	const char ValidSelection[13] = {'E', 'e', 'A', 'a', 'D', 'd', 'S', 's', 'P', 'p', 'Q', 'q', '\0'};
	int i;

	if(isalpha(S) != 0)
	{
		while(ValidSelection[i] != '\0')
		{
			if(S == ValidSelection[i])
			{
			return S;
			}

			else
			{
				printf("Invalid selection. Please enter your selection again...\n");
				printf("\n");
			}

			++i;
		}
	}

	else
	{
		printf("Invalid Selection. Please enter your selection again...\n");
		printf("\n");
	}
} //end function

void Insert(char InsName[], char InsPhone[])
{
	//create a new node with data entered by user

	Node *Temp;
	Temp = (Node *)malloc(sizeof(Node));

	if(Temp != NULL)
	{
[B]		Temp->Name = *InsName;
		Temp->Phone = *InsPhone;[/B]

		if(Curr == NULL)
		{
			Curr = Temp; //insert to curr - first entry
			Curr->Prev = NULL; //make this the beginning of the list
			Curr->Next = NULL; //make this the end of the list
		}

		else
		{
			Curr->Next = Temp; //insert to end of list
			Temp->Next = NULL; //make temp the new end of the list
		}
	}
} //end function

//Delete()
//{
	//removwe an existing struct instance
//} //end function

//Search()
//{
	//search for a specific, existing instance and print the entire instance
//} //end function

void Print(int Selection)
{
	Node *Pointer = Curr;

	if(Selection == 'A' || Selection == 'a') //user entered [A[ll)
	{
		//Print entire list

		while(Pointer != NULL)
		{
			printf("%s", Pointer->Name);
			printf("%s", Pointer->Phone);
		}
	}

	else if(Selection == 'E' || Selection == 'e')//user entered [E]ntry
	{
		//code to print a single entry - use search function call
	}

	else
	{
		printf("Invalid entry\n");
		printf("Please enter your selection again...\n");
	}
} //end function

```


The two bolded lines in the "Insert()" function are the lines referred to in the compiler output. I also bolded the part in main that's tied to it.

> 
//Compiler output

shine@BashBox ~/Programming/ProgrammingPlayground/LabPads > gcc LabPad[05].c -Wall -Werror -o LabPad[05].bin
LabPad[05].c: In function &#8216;Insert&#8217;:
LabPad[05].c:149: error: incompatible types when assigning to type &#8216;char[32]&#8217; from type &#8216;char&#8217;
LabPad[05].c:150: error: incompatible types when assigning to type &#8216;char[18]&#8217; from type &#8216;char&#8217;
cc1: warnings being treated as errors
LabPad[05].c:161: error: assignment from incompatible pointer type

---------------------------

Edit:

Well, not sure this is the right solution, but it did get rid of my first two compile errors. Still doesn't run though.

I changed those two lines to:

```

*Temp->Name = *InsName;
*Temp->Phone = *InsPhone;

```

Now I get some kind of syntax error when I try to run it. Good grief...

> 
./LabPad[05).bin
bash: syntax error near unexpected token `)

-----------------------

Edit:

This thing the compiler is saying about an "assignement from incompatible pointer type" - I have no idea what it's talking about.

I found another post here on the forums: [http://ubuntuforums.org/showthread.php?t=673631](http://ubuntuforums.org/showthread.php?t=673631)

In a response there he is told it's because he's not using malloc correctly. As for me, I'm pretty sure I'm using it exactly as the example code we were given:

> 
//Example code we were given:

temp = (struct Node *) malloc (sizeof(struct Node));


```

//My line of code for that - note that I used typdef in my struct definition

Temp = (Node *)malloc(sizeof(Node));

```

What gives?

---

### Post by Barrucadu on 2012-02-20
The incompatible pointer type is because Prev and Next are of type "struct Node*", but the compiler has no idea what a "struct Node" is. You haven't defined it. What you *have* done, is defined an anonymous struct, and typedef'd it.

The incompatible types are because you're trying to assign to a char[] from a char. These are clearly not the same type.

---

### Post by ClientAlive on 2012-02-20
> **Barrucadu said:**
> The incompatible pointer type is because Prev and Next are of type "struct Node*", but the compiler has no idea what a "struct Node" is. You haven't defined it. What you *have* done, is defined an anonymous struct, and typedef'd it.

The incompatible types are because you're trying to assign to a char[] from a char. These are clearly not the same type.


So then when I define my struct I have to do something like:

typedef struct Node { };

Rather than:

typedef struct { } Node;

??

And, when I declared those variables in the first case of my switch I wrote:

char Name[32];
char Phone[18];

So I thought that was declaring an array because of the "[]" in it.

This doesn't make sense.

---

### Post by JKyleOKC on 2012-02-20
Your initial problem of "incompatible types" is because you're passing a single character to a routine that you've defined as receiving an array of characters. However it looks to me as if this assignment is requiring a deeper knowledge of the way C handles character strings than you've gotten so far. Here's the quick review (bear with me if you already know these things):

In C, a "char" is a single 7-bit (aka signed byte) value with a possible value ranging from -128 to +127, that's usually used to represent a single character from the ASCII character set. An array of chars, referenced as char[], is a contiguous group of char variables, each of which is accessed by means of its index. Char[0] is the one at the lowest memory address. 

Text strings are always stored in char arrays, but are usually referenced by means of a char pointer (char*) that contains the address of char[0] in the array. The end of the string is denoted by an all-zeroes byte. Thus to store a 31-character string, you need an array of 32 chars (to provide room for the terminating NULL byte). And there's no built-in check -- if you try to put 45 characters into that array, the language will let you. That's what the security folk mean by "buffer overflow" and it's one of the major causes of system invasions.

Thus at first glance you would need a char* in addition to the array itself -- but the language provides a few shortcuts since the handling of strings is such an important part of the language. Any place that a char* is required, you can simply use the array's identifier (WITHOUT an index specifier) instead. That is, the identifier without an index specifier IS a pointer to byte 0 of the array. 

The tricky part of all this is that since we're usually dealing with pointers, rather than the strings themselves, we can't just assign the value of one array to another one. Instead, we must use a function from the "standard library" to copy each byte over. The one most used is strcpy(a, b) where a and b are both char pointers (or array identifiers) and it copies the values from string a to string b. If you use this in your "insert" function you may see better results. Also take a look at "strncpy" which adds a length check to prevent buffer overflows.

Another error is present also, though it didn't trigger any compiler warning since it was an error in your design: you need to set BOTH links in your insert function, not just the "next" one. Take another look at the discussion of doubly linked lists in that wikipedia article I recommended before -- it includes sample pseudo-code that can guide you to a perfect solution!

Your verification routine can be made much simpler by using another library function, "instr()." This searches a string for presence of a substring. If it fails to find it, the return value is (if I remember correctly) -1; if it does find it, the return value is the index where the match begins. You can use this to replace the entire "switch" construct with a single call, returning success if the return is >= 0 and failure otherwise. This, however, is just a tweak and might be getting ahead of your course's lesson plans...

---

### Post by trent.josephsen on 2012-02-20
Mkay, first things first.

**typedef** is, in my not so humble opinion, the most abused construct in C.  The best use of typedef is to simplify declarations when you don't need to know what a data structure looks like internally.  FILE in stdio.h is a great example of this; it's described in C99 simply as "an object type capable of recording all the information needed to control a stream" (7.19.1p2).  Another example is to create aliases for types when you know *something* about the type at write time but not *everything*, like size_t.

However, what you're doing with typedef is hiding *important* information behind a *less descriptive* name.  I know it's common to typedef structs, and the question I always ask is, "Why?"  To make it look more like C++, where you can omit the word "struct"?  Is space at such a premium that you can't spare 7 characters to make it obvious that you're using a struct?

When you do something like
```
Node *p = { 0 }; /* whatever initialization stuff */
printf("%s\n", p->Name);
```
the fact that p is a pointer-to-struct is something that you *need to know* in order to make sense of this code, and while it's possible to infer that from the code given, there's no reason to hide that important information behind a typedef because *you're using it anyway*.  And that means that when you're reading your own code 6 months later and you see this in isolation:
```
Node *p;
```
you're not going to remember off the top of your head whether *p is a union, a struct, a pointer or whatever.  Which is fine if you're just passing p around to other functions like you would do with a FILE *, but not so great if you have to access its component parts or dereference it or do whatever you forgot you were supposed to do with it and now because you have no visual clues can't remember.

TL;DR This works just fine.
```
struct Node {
	char Name[32];
	char Phone[18];
	struct Node *Prev;
	struct Node *Next;
};
```

If you later feel a burning need to obfuscate your code, you can always add a simple "typedef struct Node node_t;" immediately after the struct definition.

I was going to explain the incompatible types thing but it looks like I've been beat to the punch, plus I'm pushing my limit on cranky C explications already.  Good night :)

---

### Post by ClientAlive on 2012-02-20
Ok, so I abandoned using typedef. This is probably an especially good idea for someone just learning this stuff. I also eliminated (by commenting out) my ValidSelection() and everywhere I was trying to use it. It's just too  premature to be trying to add something like that. And I've attempted to just move the code that takes the user's string input into the function itself, and apply it directly to my "Temp" struct. Now my code compiles with no complaints at all (and I'm using -Wall and -Werror too) but when I go to run it I'm getting the same thing I have been getting before this.

> 
bash: syntax error near unexpected token `)'


The only thing I can think of is there is a stray ")" somewhere in the code. I've been over the code top to bottom left to right over and over and I'm not seeing anything like that. What am I doing wrong here? I'm trying to back the code off and make adjustments to it, to get to a point where I have something functional. Them perhaps I can advance from there.

Here's what I did:

```

/*
Objective: Create a doubly linked list. Use a design in which it is the
current node that is used to create a new node or to delete. Prev and Next
are there for navigation and searching.

Tip: 

Status: 

Next steps: 
*/

#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h> //for strcopy

struct Node
{
	char Name[32];
	char Phone[18];
	struct Node *Prev;
	struct Node *Next;
};

struct Node *Curr = NULL;

void Menu(); //Done
//char ValidSelection(char S); //Done
void Insert(); //Done
//Delete();
//Search();
void Print(int Selection); //Done

int main(void)
{
	Menu();
	char Selection = ' ';

	Selection = getchar();
	//ValidSelection(Selection);

	switch(Selection)
	{
		case 'A':
		case 'a':
		{
			//insert

//copied to function definition in an attempt to move the code into there

			//char Name[32];
			//char Phone[18];

			//printf("Enter name...");
			//fgets(Name, 31, stdin);
			//printf("Enter phone number...");
			//fgets(Phone, 17, stdin);

			Insert();

			break;
		}

		case 'D':
		case 'd':
		{
			//delete
			break;
		}

		case 'S':
		case 's':
		{
			//search
			break;
		}

		case 'P':
		case 'p':
		{
			//print

			int Selection = 0; //initialize to zero?

			printf("Would you like to: Print [A]ll or Print [E]ntry ?\n");
			Selection = getchar();
			//ValidSelection(Selection);
			Print(Selection);

			break;
		}
	} //end switch

return 0;
} //end main

void Menu()
{
	//display menu to user

	printf("Please select one of the following...");
	printf("[A]dd an entry\n");
	printf("[D]elete an entry\n");
	printf("[S]earch for an entry\n");
	printf("[P]rint entries\n");
	printf("[Q]uit\n");
	printf("\n");
} //end function

//char ValidSelection(char S)
//{	//accept user's selection - include validation

//	const char ValidSelection[13] = {'E', 'e', 'A', 'a', 'D', 'd', 'S', 's', 'P', 'p', 'Q', 'q', '\0'};
//	int i;

//	if(isalpha(S))
//	{
//		while(ValidSelection[i] != '\0')
//		

//			if(S == ValidSelection[i])
//			{
//			S = S;
//			}

//			else
//			{
//				printf("Invalid selection. Please enter your selection again...\n");
//				printf("\n");
//			}

//			++i;
//		}
//	}

//	else
//	{
//		printf("Invalid Selection. Please enter your selection again...\n");
//		printf("\n");
//	}

//	return S;
//} //end function

void Insert()
{
	//create a new node with data entered by user

	struct Node *Temp;
	Temp = (struct Node *)malloc(sizeof(struct Node));

	//char Name[32];
	//char Phone[18];

	if(Temp != NULL)
	{
		printf("Enter name...");
		fgets(Temp->Name, 31, stdin);
		printf("Enter phone number...");
		fgets(Temp->Phone, 17, stdin);
	}

	if(Temp != NULL)
	{
		//strcopy(Temp->Name, Name);
		//strcopy(Temp->Phone, Phone);

		if(Curr == NULL)
		{
			Curr = Temp; //insert to curr - first entry
			Curr->Prev = NULL; //make this the beginning of the list
			Curr->Next = NULL; //make this the end of the list
		}

		else
		{
			Curr->Next = Temp; //insert to end of list
			Curr->Prev = NULL; //reset to NULL
			Temp->Next = NULL; //make temp the new end of the list
		}
	}
} //end function

//Delete()
//{
	//removwe an existing struct instance
//} //end function

//Search()
//{
	//search for a specific, existing instance and print the entire instance
//} //end function

void Print(int Selection)
{
	struct Node *Pointer = Curr;

	if(Selection == 'A' || Selection == 'a') //user entered [A[ll)
	{
		//Print entire list

		while(Pointer != NULL)
		{
			printf("%s", Pointer->Name);
			printf("%s", Pointer->Phone);
		}
	}

	else if(Selection == 'E' || Selection == 'e')//user entered [E]ntry
	{
		//code to print a single entry - use search function call
	}

	else
	{
		printf("Invalid entry\n");
		printf("Please enter your selection again...\n");
	}
} //end function

```
-----------------------------

Edit:

Well that was the stupidest thing in the world. It didn't have anything to do with the code. It was an error in the way I typed the command. Good grief...

---

### Post by JKyleOKC on 2012-02-20
You're getting there, but I believe you need a total of four pointer assignments when adding a new node to an existing one. You're assigning NULL to the new node's Prev pointer, but it needs to be set to point to Curr. Finally, you should set Curr equal to temp so that the new node becomes current. This should be the very last pointer assignment made in the operation, because it will change which node is current.

Also, your code is geared to put the new node at the end of the list, but as I read the goal it should be able to put the new node immediately after ANY existing one that happens to be current. This may change things slightly...

It's helpful to have a text editor that can search for the matching end of parentheses, brackets, and so on; this is one of the commonest fat-finger errors I've encountered, and when a program gets longer than just a couple of screens becomes almost impossible to locate by visual inspection...

---

### Post by ClientAlive on 2012-02-21
> **JKyleOKC said:**
> You're getting there, but I believe you need a total of four pointer assignments when adding a new node to an existing one. You're assigning NULL to the new node's Prev pointer, but it needs to be set to point to Curr. Finally, you should set Curr equal to temp so that the new node becomes current. This should be the very last pointer assignment made in the operation, because it will change which node is current.

Also, your code is geared to put the new node at the end of the list, but as I read the goal it should be able to put the new node immediately after ANY existing one that happens to be current. This may change things slightly...

It's helpful to have a text editor that can search for the matching end of parentheses, brackets, and so on; this is one of the commonest fat-finger errors I've encountered, and when a program gets longer than just a couple of screens becomes almost impossible to locate by visual inspection...


Thanks Kyle. I'll take a look at that, but it does make sense. Maybe I'll draw something out on paper so I can see what needs to be going on with that. Aside from that, and it seems like it's always like this with me, some of the things that are happening don't even make sense. Just Twilight Zone bizarro!

The first line in my Menu(). It shouldn't have been much of a priority for me, all thing's considered, but I noticed the way it prints to the screen wasn't exactly formatted 'pretty'. I figure it's a simple and quick fix that I can actually see some results. And I'm tired of dealing with these problems I can't seem to diagnose (beleive me, while I'm making progress, there are things I haven't even mentioned here)... so I go in and add two "\n" to the end of the first line in that function (to make the "[A]dd an entry" line below it actually print below it. Turns out, it doesn't matter where I put the "\n" I save the changes, run it through the compiler again, and no change to what is actually printed to the screen. This is just bizare! I put the "\n" in the first line at the end, I put it in the second line at the beginning, I put two of them at the end of the first line, nothing. I save changes, I compile again, nothing, no change to what's printed to the screen. I only mention it because maybe it's a clue to some of the other problems I'm having. I can't invent the things I don't know.

Btw, I went back to passing the string into the function from inside main. Got it to compile but I don't know what the difference is/ what I did differently. Well, I take that back - what I did different is use strcopy instead of initialization. So now I'm using strcopy inside the function to copy what's passed in to the member(s) in Temp. -Werror makes the compiler bitch about an implicit declaration of strcopy. If I go back to "Temp->Name = ..." or "Temp->Phone = ..." (the initialization route) I get the other problem about incompatible pionter type or whatever. What's the use? I can't seem to win!
----------------------

Edit:

I think this is what you were talking about?

```

Temp->Prev = Curr;
Curr->Prev = NULL;
Temp->Next = NULL;
Curr = Temp;

```

---

### Post by dwhitney67 on 2012-02-21
> **ClientAlive said:**
> 
```

void Menu()
{
	//display menu to user

	printf("Please select one of the following...");  <--- INSERT NEW LINE HERE
	printf("[A]dd an entry\n");
...
} //end function


void Insert()
{
	//create a new node with data entered by user

	struct Node *Temp;
	Temp = (struct Node *)malloc(sizeof(struct Node));   <-- $0.02 - combine this and previous line; no need for cast.

	if(Temp != NULL)
	{
		printf("Enter name...");
		fgets(Temp->Name, 31, stdin);    <-- USE sizeof(), not hard-coded number.
		printf("Enter phone number...");
		fgets(Temp->Phone, 17, stdin);   <-- USE sizeof()

                <-- REMOVE newline CHARACTER FROM STRINGS! -->
	}

	if(Temp != NULL)   <-- WHY CHECK AGAIN?
	{
                <-- WHERE DO YOU WANT TO INSERT - AT THE BEGINNING or THE END OF THE LIST?? -->
		if(Curr == NULL)
		{
			Curr = Temp; //insert to curr - first entry
			Curr->Prev = NULL; //make this the beginning of the list
			Curr->Next = NULL; //make this the end of the list
		}

		else
		{
			Curr->Next = Temp; //insert to end of list
			Curr->Prev = NULL; //reset to NULL
			Temp->Next = NULL; //make temp the new end of the list
		}
	}
} //end function


void Print(int Selection)
{
	struct Node *Pointer = Curr;

	if(Selection == 'A' || Selection == 'a') //user entered [A[ll)
	{
		//Print entire list

		while(Pointer != NULL)
		{
			printf("%s", Pointer->Name);
			printf("%s", Pointer->Phone);

                        <-- MISSING CODE TO ITERATE OVER LIST -->
		}
	}
...
} //end function

```
-----------------------------



See my comments above.

P.S.  I used all-caps in my comments, not to shout, but merely to grab your attention.

P.S. #2   Look into using toupper() or tolower() when comparing a single character.  This helps having to look for both uppercase and lowercase letters.  Something like:
```

#include <ctype.h>
...
switch (tolower(selection))
{
    case 'a':
        ...
        break;

    case 'b':
        ...
        break;

    etc.
}

```

---

### Post by JKyleOKC on 2012-02-21
> **ClientAlive said:**
> Edit:

I think this is what you were talking about?

```

Temp->Prev = Curr;
Curr->Prev = NULL;
Temp->Next = NULL;
Curr = Temp;

```Not really. Setting the pointers to NULL breaks the chain at that point and destroys the list. You need to copy the Next pointer from Curr to Temp, then make Curr's Next point to Temp, make Temp's Prev point to Curr, then make the Prev pointer of the node that Temp->Next now points to point back to Temp, and finally set the Curr pointer itself to be Temp. The only time you set either pointer in a node to NULL is when you're creating the very first link.

One thing I've overlooked before is that you need some way to remember where the list begins, so that you have a starting point. I would create another global Node* variable called Home, and when creating that very first link copy its address into Home as well as into Curr. After that, nothing would change Home and it could be copied into Curr at the start of a search or print operation. However until you grok the steps involved in adding and deleting links, this is just another tweak...

When modifying the link pointers, the main thing to keep in mind is that you want the full chain to remain usable even if the power goes down in the middle of an operation. While at this stage the program is merely an exercise in RAM and would all go away if the power failed, really usable linked lists get written to permanent storage at each step along the way and it's essential that they not get broken by a power failure. This is what dictates the sequence of the various pointer changes. They must be changed in a sequence that maintains the linkages in a recoverable condition, so the new link should get connected to the one that will follow it, before attempting to put it after the one in front. Thus if power goes away, both the new link and the old Curr will still point to the old Next and the list survives. Keep this requirement in mind when drawing your pictures -- it will help you determine what has to happen.

---

### Post by JKyleOKC on 2012-02-21
> **ClientAlive said:**
> I go in and add two "\n" to the end of the first line in that function (to make the "[A]dd an entry" line below it actually print below it. Turns out, it doesn't matter where I put the "\n" I save the changes, run it through the compiler again, and no change to what is actually printed to the screen. This is just bizare! I put the "\n" in the first line at the end, I put it in the second line at the beginning, I put two of them at the end of the first line, nothing. I save changes, I compile again, nothing, no change to what's printed to the screen. I only mention it because maybe it's a clue to some of the other problems I'm having.Did you add these [COLOR="Red"][COLOR="Red"][COLOR="Black"][/COLOR][/COLOR][/COLOR]newlines INSIDE the quotes, like so:```
	printf("Please select one of the following...[COLOR="Red"]\n\n"[/COLOR]);
	printf("[A]dd an entry\n");

```or were they actually at the end of the line?```
	printf("Please select one of the following...");[COLOR="Red"]\n\n[/COLOR]
	printf("[A]dd an entry\n");

```

If they were inside the quotes, they should have done exactly what you wanted. If not, they would have been ignored since the newline is just whitespace to the compiler...

---

### Post by dwhitney67 on 2012-02-21
> **JKyleOKC said:**
> 
When modifying the link pointers, the main thing to keep in mind is that you want the full chain to remain usable even if the power goes down in the middle of an operation.

This is beyond the scope of the OP's exercise.  Even so, merely storing addresses in a file won't help once power is restored, since the application may operate using a different range of virtual memory.

Of course it is possible to commit to file the sequence of entries in a list, but don't confuse this with storing previous and next pointers.

Anyhow, I have not had the time to read this entire thread, so I'm still unsure if the OP wants to insert at the front of the list or at the end, or perhaps somewhere in the "middle" so as to maintain a sorted list.

If at the beginning, then only one pointer to the head node is required.  If inserting at the end, then a tail pointer is needed.

At the head:
```

struct Node* newNode = malloc(...);

// get/fill in Node data (ie name and phone number)...

if (headNode == null)
{
    // empty list
    newNode->next = NULL;
    newNode->prev = NULL;

    headNode = newNode;
}
else
{
    newNode->next = headNode;
    newNode->prev = NULL;

    headNode = newNode;
}

```

If inserting at the end:
```

struct Node* newNode = malloc(...);

// get/fill in Node data (ie name and phone number)...

if (headNode == null)
{
    // empty list
    newNode->next = NULL;
    newNode->prev = NULL;

    headNode = newNode;
    tailNode = newNode;
}
else
{
    tailNode->next = newNode;
    newNode->prev  = tailNode;

    tailNode = newNode;
}

```

---

### Post by JKyleOKC on 2012-02-21
> **dwhitney67 said:**
> This is beyond the scope of the OP's exercise.  Even so, merely storing addresses in a file won't help once power is restored, since the application may operate using a different range of virtual memory.When I mention writing to permanent storage, the addresses involved were not RAM addresses but actually disk addresses. That was the implementation in which I learned how to manipulate doubly linked lists; it was a text editor written in assembly language and later ported into C. The data portion of each node was a text buffer. Using a linked list allowed for insertion of new text in the middle of a buffer, by splitting it and inserting a new node, and the Prev and Next pointers were actual disk addresses, not RAM.

This was on a mainframe system some 10 years before PCs came into existence; things were rather primitive in those days!

For tutorial purposes, the OP's assignment is to be done entirely in RAM and requires use of "the current" node as the reference point, so the code has to be able to handle insertion at either end of the list, or in the middle.

I wouldn't give such an assignment with double linkage until after a full introduction to string handling and single linkage, but I didn't set up the lesson plan...

---

### Post by Arndt on 2012-02-21
All this text about linked lists makes me ponder that there surely must be one or two good tutorials on youtube where someone shows these things graphically.

---

### Post by Tony Flury on 2012-02-21
Single linked list animation :

[http://www.slideshare.net/sshinchan/single-linked-list](http://www.slideshare.net/sshinchan/single-linked-list)

---

### Post by dwhitney67 on 2012-02-21
> **Arndt said:**
> All this text about linked lists makes me ponder that there surely must be one or two good tutorials on youtube where someone shows these things graphically.

I always try to picture a collection of train cars that are attached to each other.

---

### Post by gardnan on 2012-02-21
> **JKyleOKC said:**
> 
Your verification routine can be made much simpler by using another library function, "instr()." This searches a string for presence of a substring. 

What is this instr() function? It doesn't seem standard, I don't seem to have it on my system, and I cannot find any documentation on it.  

To the OP, if you did want to use a technique similar to the one JKyleOKC described, then you can use the strchr, strrchr, or strstr functions, in case you, like me, don't have this  'instr' library function.

---

### Post by JKyleOKC on 2012-02-21
My memory obviously failed me on the function's name; I suspect I was thinking of strchr or more likely, strstr. It's been a few years since I did serious C programming...

---

### Post by ClientAlive on 2012-02-21
> **dwhitney67 said:**
> 
Anyhow, I have not had the time to read this entire thread, so I'm still unsure if the OP wants to insert at the front of the list or at the end, or perhaps somewhere in the "middle" so as to maintain a sorted list.

If at the beginning, then only one pointer to the head node is required.  If inserting at the end, then a tail pointer is needed.



This is clearly something I need to think about more and take steps to diagram exactly the algorithm I think will solve my problem. Sorry I went mia for a bit there. I began to see myself getting stalled and just spinning my wheels. I was stiting there staring at the code and the the more I did the more confuse I became. I needed to step away from it for a moment. I'm sure glad I did because now I have all this great feedback in these posts and my mind is fired up again.   :popcorn:  I'm making a separate diagram right now that I will attach to this post before pushing the submit button.

In a nutshell, I wanted to insert to the end of the list but not the end end of the list - the second to the end while maintaining the last thing in the list as NULL. Perhaps my terminology is skewed when describing it like that. I was just thinking about the situation where you get a few of them in a list. At that point you couldn't say the "end" of the list because that would leave it without NULL at that end. It would have to be between the NULL at the end and the last item before inserting.

I haven't taken time to seriously consider how my linkages and the type of list I chose to go after ties into the search function. I know I wanted to use a function call to the search function in my print function to make it (the print function) simpler. I have tossed some ideas around regarding a search algorithm though.

One thing that seems to pop up is to assign some sore of unique id based on the content of one of the string (the "Name" string perhaps). Then, when I think about that, I come to a conslusion that's probably redundant, inneficient, and prone to error (if not begging to break the program with it).

Then, and I like this idea, I think of sorting directly on the data. If I have a NULL at both ends, I can start at either end simulteosly and go both directions at the same time. One direction corresponds to the first character in every string (string in every node) and the other corresponds to the second. Then, when both sorts reach the opposite end of where they started, they switch directions and one is on character 3 and the other on character 4, etc. Back and forth they go, ripping through the data and sorting it. Each one stops when they reach the end of the shortest string or second to the end of the shortes string, respectively? No, better that they have a way to determine when enough is enough and just stop then.

Now I have to be very careful, because there is a time limit; but, if the results of that sort were to be placed in a table... Well you could have the sort run after every insert then update the table with the new results, then search on the table. This is way, way more than I can accomplish in the next 3 days. If there is some small part of that idea I could implement though - OOO'WIE!! the awsomeness that program would exude! Just smokin' hot!  :D


> **JKyleOKC said:**
> When I mention writing to permanent storage, the addresses involved were not RAM addresses but actually disk addresses. That was the implementation in which I learned how to manipulate doubly linked lists; it was a text editor written in assembly language and later ported into C. The data portion of each node was a text buffer. Using a linked list allowed for insertion of new text in the middle of a buffer, by splitting it and inserting a new node, and the Prev and Next pointers were actual disk addresses, not RAM.

This was on a mainframe system some 10 years before PCs came into existence; things were rather primitive in those days!

For tutorial purposes, the OP's assignment is to be done entirely in RAM and requires use of "the current" node as the reference point, so the code has to be able to handle insertion at either end of the list, or in the middle.

I wouldn't give such an assignment with double linkage until after a full introduction to string handling and single linkage, but I didn't set up the lesson plan...


The assignment is to be done entirely in ram. It dosn't require anywhere near the complexity I've brought into it. A singly linked list would be perfectly acceptable. I purposely beat myself like this because I think it's the best way to really learn a lot. I like taking things to the maximum of my potential and beyond, really creating a challenge. And, "awsomeness" in a program never hurt anyone  :D

Diagram coming:
----------------

Edit:

Diagrams attached

---

### Post by Vaphell on 2012-02-22
sorting can be done right off the bat, at the insertion time.
you simply start at the entry pointer, check the node located there to evaluate the relation between the node and new data. If condition is not met, you go to next node, check, ... and when you find proper place you rip the plugs between the 2 nodes where your new one is to be located, insert the node and replug everything. If you do that, you have a guarantee that your list is always sorted.

You simply have to consider if it's more advantageous to insert data in dummy mode and spend more time to seek through the unsorted structure (or sort it at once when it's big which also takes time) or to waste some cpu cycles at insertion time to find proper place for new nodes in exchange for luxury of predictability which saves time in the long run.
Programming is all about such compromises, there is no such thing as a free lunch and it's your responsibility to pick the right structure for the task at hand, knowing advantages and disadvantages of available solutions.

---

### Post by jwbrase on 2012-02-22
> **ClientAlive said:**
> 
In a nutshell, I wanted to insert to the end of the list but not the end end of the list - the second to the end while maintaining the last thing in the list as NULL. 

NULL is not the last item in a linked list. It's a value we give to the next item pointer for the last item to tell ourselves "there is no next item". 

Remember that the next item pointer isn't the next item itself: it's an address that *points* (thus the term "pointer") to the next item. NULL is a special address reserved by the operating system and the compiler to mean "nowhere". So when the next item pointer is NULL, that means "the next item is nowhere, it doesn't exist".

---

### Post by ClientAlive on 2012-02-22
This thing is acting very, very strangely. It has some kind of bug that I can't seem to find and I'm eating up hours trying to find it. It seems it's taking anything that happens to be a selection from the menu (or, I guess, a case in my switch statement) and applying it as a selection. I attached a screenshot that shows this a little.

I select a for [A]dd an entry and am prompted with both of the printf lines in a row with no regard for the newline that's in the code for them. It just races past the first fgets, appartently, and prints the next line asking for the phone number. You enter somthing and press enter and just get a newline. You enter something again and press enter and it repeats (printing the request for both name and number - thought they are two separate printf lines in the code). If you happen to enter pp (maybe just p) it enters case 'p': and you see the prinf in that block of code printed to the screen.

I'm afraid I'll end up wasting what precious little time I have left on this crap. I'm still looking but I haven't seen anything that might be causing it. It reminds me of the thing I described before with my menu function. Where adding a newline to one of the printf in it had no effect on the output. Yes it's inside the parenthesis.  :)

```
/*
Objective: Create a doubly linked list. Use a design in which it is the
current node that is used to create a new node or to delete. Prev and Next
are there for navigation and searching.

Tip: 

Status: <Content censored>

Next steps: 
*/

#include <ctype.h> //for tolower(), among other things?
#include <stdio.h>
#include <stdlib.h>
#include <string.h> //for strcopy

struct Node
{
	char Name[32];
	char Phone[18];
	struct Node *Prev;
	struct Node *Next;
};

struct Node *Curr = NULL;

void Menu(); //Done
//char ValidSelection(char S); //Done
void Insert(char N[], char P[]); //Done
//Delete();
//Search();
void Print(char Selection); //Done

int main(void)
{
	Menu();
	char Selection = ' ';

	while(Selection != 'Q' || Selection != 'q')
	{
		scanf("%c", &Selection);
		//ValidSelection(Selection);

		switch(tolower(Selection))
		{
			case 'a':
			{
				//insert

				char Name[32];
				char Phone[18];

				printf("Enter name...  \n");
				fgets(Name, sizeof(Name), stdin);
				printf("Enter phone number...  \n");
				fgets(Name, sizeof(Name), stdin);

				Insert(Name, Phone);

				break;
			}

			case 'd':
			{
				//delete
				break;
			}

			case 's':
			{
				//search
				break;
			}

			case 'p':
			{
				//print

				int SubSelection = 0; //initialize to zero?

				printf("Would you like to: Print [A]ll or Print [E]ntry ?\n");
				SubSelection = getchar();
				//ValidSelection(Selection);
				Print(Selection);

				break;
			}
		} //end switch
	} //end while

return 0;
} //end main

void Menu()
{
	//display menu to user

	printf("Please select one of the following...\n\n");
	printf("[A]dd an entry\n");
	printf("[D]elete an entry\n");
	printf("[S]earch for an entry\n");
	printf("[P]rint entries\n");
	printf("[Q]uit\n");
	printf("\n");
} //end function

//char ValidSelection(char S)
//{	//accept user's selection - include validation

//	const char ValidSelection[13] = {'E', 'e', 'A', 'a', 'D', 'd', 'S', 's', 'P', 'p', 'Q', 'q', '\0'};
//	int i;

//	if(isalpha(S))
//	{
//		while(ValidSelection[i] != '\0')
//		

//			if(S == ValidSelection[i])
//			{
//			S = S;
//			}

//			else
//			{
//				printf("Invalid selection. Please enter your selection again...\n");
//				printf("\n");
//			}

//			++i;
//		}
//	}

//	else
//	{
//		printf("Invalid Selection. Please enter your selection again...\n");
//		printf("\n");
//	}

//	return S;
//} //end function

void Insert(char N[], char P[])
{
	//create a new node with data entered by user

	struct Node *Temp;
	Temp = (struct Node *)malloc(sizeof(struct Node));

	if(Temp != NULL)
	{
		strcopy(Temp->Name, *N);
		strcopy(Temp->Phone, *P);

		if(Curr == NULL)
		{
			Curr = Temp; //insert to curr - first entry
			Curr->Prev = NULL; //make this the beginning of the list
			Curr->Next = NULL; //make this the end of the list
		}

		else
		{
			Curr->Next = Temp;
			Temp->Prev = Curr;
			Curr = Temp;
			Curr->Next = NULL;
		}
	}
} //end function

//Delete()
//{
	//removwe an existing struct instance
//} //end function

//Search()
//{
	//search for a specific, existing instance and print the entire instance
//} //end function

void Print(char Selection)
{
	struct Node *Pointer = Curr;

	if(Selection == 'A' || Selection == 'a') //user entered [A[ll)
	{
		//Print entire list

		while(Pointer != NULL)
		{
			printf("%s", Pointer->Name);
			printf("%d", *Pointer->Phone);
		}
	}

	else if(Selection == 'E' || Selection == 'e')//user entered [E]ntry
	{
		//code to print a single entry - use search function call
	}

	else
	{
		printf("Invalid entry\n");
		printf("Please enter your selection again...\n");
	}
} //end function

```
---------------------

Edit:

Ta hell with it!

At every turn this stinkin thing bites me. Can't pass an array into the sob, acts completely bizare for no appartent reason that I can see. I completely started over on in another file, trying to get somwhere with this absolute horror of a program. I'm wasting my time with this little garbage crap and not even get to focus on the linked list at all.

---

### Post by Vaphell on 2012-02-22
you know you can copy paste from terminal, right? highlight-select/middleclick-paste or ctrl+shift+c/ctrl+v? ;-)

---

### Post by Arndt on 2012-02-22
> **ClientAlive said:**
> This thing is acting very, very strangely. It has some kind of bug that I can't seem to find and I'm eating up hours trying to find it. It seems it's taking anything that happens to be a selection from the menu (or, I guess, a case in my switch statement) and applying it as a selection. I attached a screenshot that shows this a little.

I select a for [A]dd an entry and am prompted with both of the printf lines in a row with no regard for the newline that's in the code for them. It just races past the first fgets, appartently, and prints the next line asking for the phone number. You enter somthing and press enter and just get a newline. You enter something again and press enter and it repeats (printing the request for both name and number - thought they are two separate printf lines in the code). If you happen to enter pp (maybe just p) it enters case 'p': and you see the prinf in that block of code printed to the screen.

I'm afraid I'll end up wasting what precious little time I have left on this crap. I'm still looking but I haven't seen anything that might be causing it. It reminds me of the thing I described before with my menu function. Where adding a newline to one of the printf in it had no effect on the output. Yes it's inside the parenthesis.  :)

```
/*
Objective: Create a doubly linked list. Use a design in which it is the
current node that is used to create a new node or to delete. Prev and Next
are there for navigation and searching.

Tip: 

Status: <Content censored>

Next steps: 
*/

#include <ctype.h> //for tolower(), among other things?
#include <stdio.h>
#include <stdlib.h>
#include <string.h> //for strcopy

struct Node
{
	char Name[32];
	char Phone[18];
	struct Node *Prev;
	struct Node *Next;
};

struct Node *Curr = NULL;

void Menu(); //Done
//char ValidSelection(char S); //Done
void Insert(char N[], char P[]); //Done
//Delete();
//Search();
void Print(char Selection); //Done

int main(void)
{
	Menu();
	char Selection = ' ';

	while(Selection != 'Q' || Selection != 'q')
	{
		scanf("%c", &Selection);
		//ValidSelection(Selection);

		switch(tolower(Selection))
		{
			case 'a':
			{
				//insert

				char Name[32];
				char Phone[18];

				printf("Enter name...  \n");
				fgets(Name, sizeof(Name), stdin);
				printf("Enter phone number...  \n");
				fgets(Name, sizeof(Name), stdin);

				Insert(Name, Phone);

				break;
			}

			case 'd':
			{
				//delete
				break;
			}

			case 's':
			{
				//search
				break;
			}

			case 'p':
			{
				//print

				int SubSelection = 0; //initialize to zero?

				printf("Would you like to: Print [A]ll or Print [E]ntry ?\n");
				SubSelection = getchar();
				//ValidSelection(Selection);
				Print(Selection);

				break;
			}
		} //end switch
	} //end while

return 0;
} //end main

void Menu()
{
	//display menu to user

	printf("Please select one of the following...\n\n");
	printf("[A]dd an entry\n");
	printf("[D]elete an entry\n");
	printf("[S]earch for an entry\n");
	printf("[P]rint entries\n");
	printf("[Q]uit\n");
	printf("\n");
} //end function

//char ValidSelection(char S)
//{	//accept user's selection - include validation

//	const char ValidSelection[13] = {'E', 'e', 'A', 'a', 'D', 'd', 'S', 's', 'P', 'p', 'Q', 'q', '\0'};
//	int i;

//	if(isalpha(S))
//	{
//		while(ValidSelection[i] != '\0')
//		

//			if(S == ValidSelection[i])
//			{
//			S = S;
//			}

//			else
//			{
//				printf("Invalid selection. Please enter your selection again...\n");
//				printf("\n");
//			}

//			++i;
//		}
//	}

//	else
//	{
//		printf("Invalid Selection. Please enter your selection again...\n");
//		printf("\n");
//	}

//	return S;
//} //end function

void Insert(char N[], char P[])
{
	//create a new node with data entered by user

	struct Node *Temp;
	Temp = (struct Node *)malloc(sizeof(struct Node));

	if(Temp != NULL)
	{
		strcopy(Temp->Name, *N);
		strcopy(Temp->Phone, *P);

		if(Curr == NULL)
		{
			Curr = Temp; //insert to curr - first entry
			Curr->Prev = NULL; //make this the beginning of the list
			Curr->Next = NULL; //make this the end of the list
		}

		else
		{
			Curr->Next = Temp;
			Temp->Prev = Curr;
			Curr = Temp;
			Curr->Next = NULL;
		}
	}
} //end function

//Delete()
//{
	//removwe an existing struct instance
//} //end function

//Search()
//{
	//search for a specific, existing instance and print the entire instance
//} //end function

void Print(char Selection)
{
	struct Node *Pointer = Curr;

	if(Selection == 'A' || Selection == 'a') //user entered [A[ll)
	{
		//Print entire list

		while(Pointer != NULL)
		{
			printf("%s", Pointer->Name);
			printf("%d", *Pointer->Phone);
		}
	}

	else if(Selection == 'E' || Selection == 'e')//user entered [E]ntry
	{
		//code to print a single entry - use search function call
	}

	else
	{
		printf("Invalid entry\n");
		printf("Please enter your selection again...\n");
	}
} //end function

```

Why do you still use scanf?

---

### Post by dwhitney67 on 2012-02-22
> **ClientAlive said:**
> 
I select a for [A]dd an entry and am prompted with both of the printf lines in a row with no regard for the newline that's in the code for them. It just races past the first fgets, ...

As Arndt questioned, why are you using scanf() to read in raw input from a user?

When you are prompted to enter a character, say the letter 'a', not only must you enter that letter on the keyboard but also the <return> key, which in effect also adds a newline character ('\n') to the input stream.

Thus scanf() is satisfied with collecting the first character entered, but it leaves the newline character sitting in the input stream for the next input operation (if any).  In your case, fgets() is called.  It is immediately satisfied because it has detected the end-of-line marker (ie. the newline), thus giving you the illusion that it skipped the prompt.

The moral of all this is to avoid scanf() at all costs for raw input.  Consider using fgets() for reading in entire strings, and then picking it apart, if necessary, using sscanf(), which should NOT be confused with scanf().

Also, as I attempted to indicate to you earlier, fgets() reads up to one byte less than the size of the buffer specified OR up to the first encountered newline character.  If the latter occurs first, then the newline character is included in the resulting string that is read.

This means that you need to scan the input string for a newline character, and if one is present, remove it.  This is how I do it:
```

void remove_newline(char* str)
{
    char* nl = strchr(str, '\n');
    if (nl != NULL)
    {
        *nl = '\0';
    }
}

...

// somewhere else in the code...

printf("Enter your name: ");
fgets(name, sizeof(name) - 1, stdin);

remove_newline(name);

...

```
Call the function above, if desired, after calling fgets().

Lastly, I have a question about **strcopy**().  I'm an old-school programmer, and personally I have never seen this function in the standard C library.  Is this something that you conjured up, or did you really mean to use **strcpy**()?

If the latter, bear in mind that it is also considered a reckless function to use.  Use strncpy() so that you can specify the length of the destination buffer.  Otherwise, when using strcpy(), it is possible to incur a buffer overrun when copying a big amount of data into a small amount of space.

---

### Post by ofnuts on 2012-02-22
> **jwbrase said:**
> NULL is not the last item in a linked list. It's a value we give to the next item pointer for the last item to tell ourselves "there is no next item". 

Remember that the next item pointer isn't the next item itself: it's an address that *points* (thus the term "pointer") to the next item. NULL is a special address reserved by the operating system and the compiler to mean "nowhere". So when the next item pointer is NULL, that means "the next item is nowhere, it doesn't exist".In Python its equivalent is even more appropriately called "None".

---

### Post by JKyleOKC on 2012-02-22
> **ClientAlive said:**
> Ta hell with it!

At every turn this stinkin thing bites me. Can't pass an array into the sob, acts completely bizzare for no apparent reason that I can see. I completely started over on in another file, trying to get somewhere with this absolute horror of a program. I'm wasting my time with this little garbage crap and not even get to focus on the linked list at all.Jake, that's the problem with programming, and it's always present. If we try to do the whole thing at once, we get lost in the details and go racing down a blind alley.

Try doing just exactly what the assignment calls for, no more, and tracing out each thing that goes wrong. As others have pointed out, some of the standard library functions are quite tricky to use and can have totally unexpected results. C's original inventors were about as geeky as you can get, and based the language on the requirements of a quite primitive computer. They also built their system to emulate what was, at the time, the most complicated computer system in existence anywhere -- and one which never did get finished, or worked in all its intended roles! One result was that the language has lots of loopholes where things don't do what you expect -- as you've been experiencing.

The best trick I ever learned for determining what is going wrong is to insert "print" statements all over the place, so that the machine gives you a running report of what it is doing. That is, putting printf("About to get input\n"); between the prompt and the input request, and printf("got %s", inputstring); right after it. This might have shown you immediately that the scanf() call was not doing what you expected it to do. Once everything works, you can take out those extra printf statements so they don't clutter up the code.

If you can find a copy anywhere, the book "Software Tools" by Brian Kernighan and P. J. Plauger is the best introduction to good programming practices that I've ever seen. It emphasizes the need to get the little things working right before trying to put them together into bigger projects, and describes how the C language was built without mentioning it even once. The authors were both at Bell Labs with Thompson and Ritchie, and both played major roles in the development of Unix and its tools.

Don't get too discouraged at this point. Stick with it, and things will eventually fall into place!

---

### Post by ClientAlive on 2012-02-22
> **Vaphell said:**
> you know you can copy paste from terminal, right? highlight-select/middleclick-paste or ctrl+shift+c/ctrl+v? ;-)


Oh, yeah, I know better. I guess I just didn't think of it as a superior alternative. Sorry.

> **Arndt said:**
> Why do you still use scanf?


Because I don't know what else to do. As of this point I'm aware of functions:

scanf()
getchar()
fgets()
and most recently (though very very little experience with it) strcpy()

scanf is the last thing, in a long list of stabs in the dark, I had tried in order to correct the twilight zone, strange behavior that program was exhibiting. Changing the choice of function to use wasn't the only thing I tried either. Ultimately I spent several hours trying everything I could think of to fix the bug. I suppose the most honest thing I could say is "I just don't know what the source of the problem is - I simply do not know."

Now here is where the majority of my time ends up going in these projects. Not to learning the concept we're on, but trying to figure out and correct some ridiculously stupid bug. It just gripes me!

> **dwhitney67 said:**
> 

Lastly, I have a question about **strcopy**().  I'm an old-school programmer, and personally I have never seen this function in the standard C library.  Is this something that you conjured up, or did you really mean to use **strcpy**()?

If the latter, bear in mind that it is also considered a reckless function to use.  Use strncpy() so that you can specify the length of the destination buffer.  Otherwise, when using strcpy(), it is possible to incur a buffer overrun when copying a big amount of data into a small amount of space.

I must have gotten confused in my spelling of the function name. I was thinking of strcpy(). Anyhow, thank you so much for explaining those things. It isn't the first time someone has tried to explain it to me but it is the first time it has really sunk in. I get the ins and out of it more clearly; And - I was given some tools for dealing with it. Whether it's out there or not, I haven't happen to see a resource that pertains to which are better functions to use than others for certian operations. Only so much as has been shared with me on the forums here.

Thanks for sticking with me when I get fed up and frustrated and blow my stack  :o Thanks for sharing that code with me too (the stuff about removing newline).

> **JKyleOKC said:**
> Jake, that's the problem with programming, and it's always present. If we try to do the whole thing at once, we get lost in the details and go racing down a blind alley.

Try doing just exactly what the assignment calls for, no more, and tracing out each thing that goes wrong. As others have pointed out, some of the standard library functions are quite tricky to use and can have totally unexpected results. C's original inventors were about as geeky as you can get, and based the language on the requirements of a quite primitive computer. They also built their system to emulate what was, at the time, the most complicated computer system in existence anywhere -- and one which never did get finished, or worked in all its intended roles! One result was that the language has lots of loopholes where things don't do what you expect -- as you've been experiencing.

The best trick I ever learned for determining what is going wrong is to insert "print" statements all over the place, so that the machine gives you a running report of what it is doing. That is, putting printf("About to get input\n"); between the prompt and the input request, and printf("got %s", inputstring); right after it. This might have shown you immediately that the scanf() call was not doing what you expected it to do. Once everything works, you can take out those extra printf statements so they don't clutter up the code.

If you can find a copy anywhere, the book "Software Tools" by Brian Kernighan and P. J. Plauger is the best introduction to good programming practices that I've ever seen. It emphasizes the need to get the little things working right before trying to put them together into bigger projects, and describes how the C language was built without mentioning it even once. The authors were both at Bell Labs with Thompson and Ritchie, and both played major roles in the development of Unix and its tools.

Don't get too discouraged at this point. Stick with it, and things will eventually fall into place!


Talk about hitting my nail on the head. More than anything else, if I could just learn to plan my design a little more before starting, draw it out, and especially, especially just do a little bit then test, little bit then test. Not jump in all gung ho with some half cooked, crack pot notion of a design and write 150 lines of code before I find out it won't work. If I could just learn that...

For starters, I did insert a printf statement just below my function call to menu. Because of that, when I saw it is never printed to the screen, I realized it's hanging on that menu function. It isn't even making it beyond that function call. I thought for a minute that it was because I needed to move the function call into the while loop (the outer and only one I have at this point) but doing that didn't fix anything. I had moved it before trying the printf line.

:D

---

### Post by JKyleOKC on 2012-02-22
Here's one place that lists some of the i/o functions: [http://crasseux.com/books/ctutorial/String-output-and-input.html#String%20output%20and%20input](http://crasseux.com/books/ctutorial/String-output-and-input.html#String%20output%20and%20input) 

What compiler are you using? If it's "gcc" (which is what you get in the build-essentials package) then the best one for input would be getline. However since you have almost no time left to get things working, just use "gets" for now and be sure to strip the newline off the end of the input as shown in an earlier message in this thread.

The link above has links to details about all the functions available in the Gnu standard libraries, but most of them aren't really crystal clear, so don't hesitate to ask here about anything you find confusing...

---

### Post by ClientAlive on 2012-02-22
I am using gcc. Thanks for the link. I have a few sites bookmarked; but, at this point, I haven't looked around enough to find especially good ones. I think choosing some different (better) functions is going to make a tremendious difference for me. I'll be able to see for myself in just a few minutes here  :)


@dwhitney67

Some of what you said really got me thinking about the importance of choosing the best functions for what you're trying to accomplish. Up to recently things have been simple enough to not have to worry about it.

I noticed that some of the functions you mentioned as being better choices are one's in which you seem to have more control over what goes on. I've gotten to wondering whether a person could make a general rule for themself about this. A guideline that would be a good place to start in any situation. Perhaps a person could say that whenever they're unsure what the better library function is to use - that using the one that gives you the most control is the place to start?

Just a thought.
---------------------

Edit:

I looked at the definition for strncpy(). It looks like you're intended to use sizeof() with it? I haven't seen what "size_t" is all about except for just right now but it looks like "size_t" is actually a data type and one that is meant to be used with sizeof()?

---

### Post by JKyleOKC on 2012-02-22
> **ClientAlive said:**
> I did insert a printf statement just below my function call to menu. Because of that, when I saw it is never printed to the screen, I realized it's hanging on that menu function. It isn't even making it beyond that function call. I thought for a minute that it was because I needed to move the function call into the while loop (the outer and only one I have at this point) but doing that didn't fix anything. I had moved it before trying the printf line.I just looked at your code for the function and saw why it's hanging up. Talk about totally unexpected gotchas!!!

The cause (I think) is a combination of a single omitted character in your while loop's test, and the absence of a length limit in scanf. The first condition in the "while" test is apparently for the zero byte at the end of the string, but it's looking for '0' rather than '\0' and won't stop until it finds the character for zero (ASCII 0x30) which won't be in your input buffer.

I usually code this kind of "everlasting" program loop like this: ```
while true{
  // do things
  if (time-to-quit)
    break;
}
```

That's lots less typing, and also makes it perfectly clear that a near-endless loop action is intended.

I would also create a small "get_input" function something like this, using the remove_newline idea posted earlier:```
void get_input(char *str){
    char *nl;
    fgets(str, sizeof(str) - 1, stdin);
    nl = strchr(str, '\n');
    if (nl != NULL){
        *nl = '\0';
    }
}
```This would combine the fgets call and the remove_newline action; I would call it as "get_input(Name);" where Name is your 32-byte buffer in the Node struct. Again, this makes it more clear just what you intend the code to do, and reduces the amount of typing (and consequent risk of fat-fingering things).

Hope this helps!

---

### Post by ClientAlive on 2012-02-23
Well hopefull I'm on the right track...

```
	
while(Selection != 'Q' && Selection != 'q')
	{
		Menu(); //moved it here from outside/above my while loop

		printf("Enter your selection\n");
		fgets(&Selection, sizeof(Selection) - 1, stdin);
		StripNewline(&Selection);

         ...

```

But, infinite loop...


> 
[A]dd an entry
[D]elete an entry
[S]earch for an entry
[P]rint entries
[Q]uit

Enter your selection
Please select one of the following...

[A]dd an entry
[D]elete an entry
[S]earch for an entry
[P]rint entries
[Q]uit

Enter your selection
Please select one of the following...

[A]dd an entry
[D]elete an entry^C


Interestingly...

```

printf("Please select one of the following...\n\n");

```

...is inside the Menu() function. It's the first line of code in it.

I think if I keep working on it I'll be ok.

---

### Post by Arndt on 2012-02-23
I thought scanf was already mentioned somewhere in this thread, but that must have been another thread, whether yours or not I don't know.

For parsing line-based user input, read one line with fgets, and then
look at the contents in the most suitable way, which may be char by char,
or sscanf, or something else.

---

### Post by dwhitney67 on 2012-02-23
> **ClientAlive said:**
> 
But, infinite loop...


Your exercise is to learn and become familiar with Linked Lists.  Hopefully at this stage you are familiar with loops, whether for-loops, while-loops, or do-while-loops.  You should also attempt to get familiar with the nuances of capturing raw data from the terminal, and the only way I can recommend that you do this is to focus exclusively on the topic (without worrying about Linked Lists).  But undoubtedly you do not have time for this, or you can't focus.

Here's how one could implement the menu-selection loop:
```

#include <stdio.h>
#include <ctype.h>

void displayMenu();

int main(void)
{
    int quit = 0;

    while (!quit)
    {
        displayMenu();

        int selection = getchar();
        getchar();                   // used to capture newline that is in stream

        if (selection == EOF)
            continue;

        switch (toupper((char) selection))
        {
            case 'A':
                break;

            case 'D':
                break;

            case 'S':
                break;

            case 'P':
                break;

            case 'Q':
                quit = 1;
                break;

            default:
                fprintf(stderr, "Invalid input!  Try again...\n\n");
                break;
        }
    }

    return 0;
}

void displayMenu()
{
    printf("\n\nMenu:"
           "\n\t[A]dd an entry"
           "\n\t[D]elete an entry"
           "\n\t[S]earch for an entry"
           "\n\t[P]rint entries"
           "\n\t[Q]uit"
           "\n"
           "\nEnter your selection... ");
}

```

As for your utility function StripNewline(), I'm not sure how you defined it, but I'm certain that it does not require the address of the pointer to the string that you want to manipulate.  Again, consider this example:
```

char name[32];

printf("Enter your name: ");
fgets(name, sizeof(name) - 1, stdin);

stripNewline(name);    <---- Note the address is not required!

...


void stripNewline(char* str)
{
    char* nl = strchr(str, '\n');

    if (nl != NULL)
    {
        *nl = '\0';
    }
}

```

---

### Post by dwhitney67 on 2012-02-23
> **JKyleOKC said:**
> ```
void get_input(char *str){
    char *nl;
    fgets(str, sizeof(str) - 1, stdin);
    nl = strchr(str, '\n');
    if (nl != NULL){
        *nl = '\0';
    }
}
```

Your function is missing one critical argument to the parameter list; the length of the str buffer.  Using sizeof(str) will yield a mere 4 bytes on a 32-bit archictecture, and 8-bytes on a 64-bit architecture.

Consider:
```

char name[32];

getInput("Enter your name: ", name, sizeof(name));

...

void getInput(const char* prompt, char* str, const size_t size)
{
    if (prompt != NULL && str != NULL && size > 0)
    {
        puts(prompt);

        fgets(str, size - 1, stdin);

        char* nl = strchr(str, '\n');

        if (nl)
        {
            *nl = '\0';
        }
    }
}

```

---

### Post by ClientAlive on 2012-02-23
I sat here a little while ago typing out this long winded, logical proposition to elucidate a certain confusion pointers I've held. Until now I haven't had to deal with it and it was just a curiosity. Now, I find myself really stuggling to grasp this concept (linked lists), and it happens to be something that makes heavy use of pointers. Well, something happened. I clicked a wrong button or something and it whiped out what I had written. Thankfully, just having done that exercise was enought to help me think of some ways to test for answers. I think if I share the code I've made a start with it will explain a lot more quickly, and easily, where my confusion lies and what I was trying to discover - way more quickly than I could have with what I wrote earlier.

I wrote and ran two pieces of code with only a very subtle varition between them:

A)

```

#include <stdio.h>

int main ()
{
int x = 1;
int y = 2;
int *px;
int *py;

px = &x;
py = &y;

printf("The value of x is %d\n", x);
printf("The value of y is %d\n", y);

printf("The address of x is stored in px: %p\n", px);
printf("The address of y is stored in py: %p\n", py);

px = py;

printf("px has been set equal to py\n");
printf("Now the value of px is: %p\n", px);
printf("Now the value of py is: %p\n", py);

x = 3;

printf("x was just set equal to 3 - note that this was after setting px = py\n");
printf("Now the value of x is: %d\n", x);
printf("Now the value of y is: %d\n", y);
printf("Has the value of y changed as well? Only x was set equal to a new number (three), not x and y.\n");

return 0;
}

```


B)

```

#include <stdio.h>

int main ()
{
int x = 1;
int y = 2;
int *px;
int *py;

px = &x;
py = &y;

printf("The value of x is %d\n", x);
printf("The value of y is %d\n", y);

printf("The address of x is stored in px: %p\n", px);
printf("The address of y is stored in py: %p\n", py);

px = py;

printf("px has been set equal to py\n");
printf("Now the value of px is: %p\n", px);
printf("Now the value of py is: %p\n", py);

y = 3;

printf("y was just set equal to 3 - note that this was after setting px = py\n");
printf("Now the value of x is: %d\n", x);
printf("Now the value of y is: %d\n", y);
printf("Has the value of x changed as well? Only y was set equal to a new number (three), not x and y.\n");

return 0;
}

```


What is going on here? After setting "px = py" did I then still have two variables "px" and "py" in two separate locations within physical RAM? There must be two addresses associated with each variable then.

Example:

px has an address and px stores an address (that's two addresses).

What could this mean for my structs then?

When I say "struct Node *Head" or "struct node *Temp" or "struct Node *Anything" ... Well something similar must be going on. At that point, without reading any more code into it, this thing must not be an instance of the struct I defined. It's just a variable that stores the address of the data type "struct Node" right?

Then if I go: "Temp = (Node *)malloc(sizeof(struct Node));"
I'm what? Storing the address of the first, what, bit? byte? of memory, allocated in the size of the struct I defined earlier? But that struct definition may have members in it (surely it would or what would be the point?). So this pionter to the beginning of memory in the size of the struct can't just be this hazy, undefined lump of memory because we can do things like "Temp->x = ..." (assuming one of the struct's members is "x"). So there is some kind of definition (read 'to take form, take shape, or have shape -> definition) to this chunk of memory we allocated with malloc. What on earth is going on here?

So this is where my head is at. And I can see other distinctions which could be drawn from this as well. Distinctions which I hadn't mentioned like the difference between a member that's defined in the struct as a pionter and a one that isn't - and how that affects concept and application in practice. So when we ran malloc, what did we get? an a chunk of memory that contained more than one address? A chunk of memory that contained as many addresses as there are members in the struct plus one for the struct itself? Otherwise how could we access a member in the struct by referrning to the struct pointer's member (I mean the one created with malloc) and have anything meaningful come from it?

I'm rambling. I'm trying to spill out what's on my mind. I wonder what people will say...

---

### Post by dwhitney67 on 2012-02-23
Every variable, whether a pointer or not, exists somewhere in RAM.  RAM is divided into two regions:  the stack and the heap.

When you declare a pointer, such as **int* px**, this variable resides on the stack, and hence the address of that pointer is located within the stack.  In this example, the pointer is currently "dangling", that is, it is not assigned to point to any address.

Consider this code and comments:
```

// unassigned pointer declared on the stack.
int* px;


// another pointer declared on the stack, however it points to
// a region in the heap.
int* py = malloc(sizeof(int));


// variable z declared on the stack.
// pointer pz declared on the stack, and points to the address
// where z is located.
int  z;
int* pz = &z;

```

I should further add that memory is addressable at the byte boundary.

As for a Linked List, the "next" pointer resides in a location in memory (generally the heap), and it points to either NULL or to another memory location.

---

### Post by ClientAlive on 2012-02-23
> **dwhitney67 said:**
> Your exercise is to learn and become familiar with Linked Lists.  Hopefully at this stage you are familiar with loops, whether for-loops, while-loops, or do-while-loops.  You should also attempt to get familiar with the nuances of capturing raw data from the terminal, and the only way I can recommend that you do this is to focus exclusively on the topic (without worrying about Linked Lists).  But undoubtedly you do not have time for this, or you can't focus.

Here's how one could implement the menu-selection loop:
```

#include <stdio.h>
#include <ctype.h>

void displayMenu();

int main(void)
{
    int quit = 0;

    while (!quit)
    {
        displayMenu();

        int selection = getchar();
        getchar();                   // used to capture newline that is in stream

        if (selection == EOF)
            continue;

        switch (toupper((char) selection))
        {
            case 'A':
                break;

            case 'D':
                break;

            case 'S':
                break;

            case 'P':
                break;

            case 'Q':
                quit = 1;
                break;

            default:
                fprintf(stderr, "Invalid input!  Try again...\n\n");
                break;
        }
    }

    return 0;
}

void displayMenu()
{
    printf("\n\nMenu:"
           "\n\t[A]dd an entry"
           "\n\t[D]elete an entry"
           "\n\t[S]earch for an entry"
           "\n\t[P]rint entries"
           "\n\t[Q]uit"
           "\n"
           "\nEnter your selection... ");
}

```

As for your utility function StripNewline(), I'm not sure how you defined it, but I'm certain that it does not require the address of the pointer to the string that you want to manipulate.  Again, consider this example:
```

char name[32];

printf("Enter your name: ");
fgets(name, sizeof(name) - 1, stdin);

stripNewline(name);    <---- Note the address is not required!

...


void stripNewline(char* str)
{
    char* nl = strchr(str, '\n');

    if (nl != NULL)
    {
        *nl = '\0';
    }
}

```

Oh, well "Selection" in my code is just a char, not an array.

I won't always be under the pressure of a deadline and if I can learn to keep the assigments simple like they're meant to be I'll have time for other goodies like what you suggest.  :)

---

### Post by ClientAlive on 2012-02-23
> **dwhitney67 said:**
> Every variable, whether a pointer or not, exists somewhere in RAM.  RAM is divided into two regions:  the stack and the heap.

When you declare a pointer, such as **int* px**, this variable resides on the stack, and hence the address of that pointer is located within the stack.  In this example, the pointer is currently "dangling", that is, it is not assigned to point to any address.

Consider this code and comments:
```

// unassigned pointer declared on the stack.
int* px;


// another pointer declared on the stack, however it points to
// a region in the heap.
int* py = malloc(sizeof(int));


// variable z declared on the stack.
// pointer pz declared on the stack, and points to the address
// where z is located.
int  z;
int* pz = &z;

```

I should further add that memory is addressable at the byte boundary.

As for a Linked List, the "next" pointer resides in a location in memory (generally the heap), and it points to either NULL or to another memory location.

I was going to share some other thought that come from this, what you showed here. I can't tell how much is taking shape in my head right now. I mean. These things have either been told to me before or I read them in our book, but I never really took the time to think of the implications.

Well, shoot...

So then if, when I declare a pointer varialbe, it has it's own location in memory, it's not going anywhere. It's written into the code and it's there to stay. What I assign to it is yet another entity, another thing.

That puts a pointer, as a type of variable, more in a class with things like stdin and stdout. I mean, in the sense that they all refer to a particular source. In the case of stdin the source is the keyboard (parhaps other input devices, I'm not sure at this point). In the case of stdout the source is maybe a file or a value or values stored in RAM. And in the case of a pointer variable the source is hardware (well maybe it the operating system assigns it, but it referrs to hardware).

So why am I thinking about this kind of thing anyway? Well, when I'd sit there trying to pull code from these diagrams I was making (for linked lists) and I couldn't, maybe still can't, understand where a list item goes when you put the next one into the list. In other words, if there is no unique name attached to each and every list item, what becomes of the previous one after you use introduce another? Without a concrete label of some sort attached to it, it just fades into the void right? And then how do you ever find it again? This is what I was thinking.

But now I have this inkling of an idea. An idea that this prior list item is still there, sitting in memory, as long as you haven't specifically coded for it to be freed. It's sitting there and you can find it again because of the next and/ or prev links that are members of your struct. You may not imediataly know what it contains (I mean the specific value(s) of it's members) but you can test for that. You can find it by traversing the list and you can test at each list item for the specific contents of it's member or members.

I know how silly all this must sound. Honestly, I hadn't really, seriously thought about all this. And I'm the type that learns by talking to others, not just sitting there thinking. You know?

---

### Post by trent.josephsen on 2012-02-23
You're doing great.  Just thought I'd mention it because learning C can be very frustrating (I know from experience) and it sounds like you could use some encouragement.  You have grasped the core idea of pointers, and while there are a few nuances you could stand to understand better, you're miles closer to understanding the code you're writing (and writing code you don't understand is the worst).

The Wikipedia page on pointers might be helpful, and writing test programs like the ones you did a few posts back will probably help you understand better too.

---

### Post by dwhitney67 on 2012-02-23
> **ClientAlive said:**
> 
But now I have this inkling of an idea. An idea that this prior list item is still there, sitting in memory, as long as you haven't specifically coded for it to be freed. It's sitting there and you can find it again because of the next and/ or prev links that are members of your struct. You may not imediataly know what it contains (I mean the specific value(s) of it's members) but you can test for that. You can find it by traversing the list and you can test at each list item for the specific contents of it's member or members.

A light bulb must have just illuminated over your head.  I think you got it.  The allocated memory block is there, somewhere on the heap, and you have a pointer that you can use to reference it.  This memory block in turn may have a "next" pointer that references yet another chunk of memory, or possibly NULL.

Anyhow, go back to my previous post where I described how to insert a new node into either the beginning of a List, or at the end of the List.  Your most recent attempt that I saw will not work.

---

### Post by JKyleOKC on 2012-02-23
As dwhitney67 said, it looks like the light has dawned for you. The "malloc" function gets some space from the heap, and returns the address where that space starts. The name is an abbreviation of "memory allocator" which may help you remember what it does. If you store that address in a variable somewhere, you can go back to it at any time, and eventually can return it to the heap with the "free" function. Until you give it back, it will keep whatever you put into it.

Each time you malloc an instance of a Node struct, you've created a brand new space on the heap. The first time you do this, you save its address somewhere (I use a pointer named Home) and set its Prev and Next pointers both to NULL to indicate that there are no more instances in the list.

The next time, though, you move Home's Next pointer into the Next pointer of the new instance, and put the new instance's address into Home's Next pointer to replace it. You then copy the address stored in Home into the Prev pointer of the new instance. The two instances are now doubly linked to each other.

After that, you can put other instances anywhere in the list that you want. That's where the Curr pointer comes into play. You can copy the address from Home into Curr and then Curr will point to the start of the list. If you then copy Curr->Next into Curr, Curr will point to the second item. When Curr->Next contains NULL you're at the last item and can go no farther. This is how you can print the entire list, or search it.

Writing your insert function to use Curr instead of Home makes it work no matter where in the list you want to put the new item, though.

I hope this helps a bit more. Sorry for giving you bad code in the previous message; it's been years since I actually used C and I'm a bit rusty about some of the details...

---

### Post by jwbrase on 2012-02-23
> **ClientAlive said:**
> 
Then if I go: "Temp = (Node *)malloc(sizeof(struct Node));"
I'm what? Storing the address of the first, what, bit? byte? of memory, allocated in the size of the struct I defined earlier? But that struct definition may have members in it (surely it would or what would be the point?). So this pionter to the beginning of memory in the size of the struct can't just be this hazy, undefined lump of memory because we can do things like "Temp->x = ..." (assuming one of the struct's members is "x").

It is and it isn't. All malloc does is reserve a chunk of memory of the requested size and give you a pointer to the beginning of that memory. You tell the compiler to treat that memory as a structure of a given type by casting the pointer you get from malloc to that type (e.g: in "Temp = **(Node *)**malloc(sizeof(struct Node));" the "(Node *)" part tells the compiler we're using this pointer to point to an instance of the "Node" struct).

When you define a struct, the compiler gives each variable in the struct an offset from the beginning of the struct. For instance, if you define struct Foo as follows:

```
struct Foo
{
    int a, b, c;
}
```

the compiler might decide (depending on factors such as sizeof(int) for the computer architecture and OS you're compiling for) to place a at the beginning of the struct (offset 0), b at offset 4 into the struct, and c at offset 8 into the struct.

Then, let's say that we do:

```

struct Foo *Bar;
Bar=(struct Foo *)malloc(sizeof(struct Foo));
int *ap = &(Bar->a);
int *bp = &(Bar->b);
int *cp = &(Bar->c);
```

and then check where ap, bp, and cp are pointing to. We'd find that ap points to the same place as Bar, bp points to a memory location 4 bytes beyond Bar, and cp point to 8 bytes beyond bar. If Bar is 0x00100000, then ap would also be 0x00100000, bp would be 0x00100004, and cp would be 0x00100008.

So the memory itself is a "hazy, undefined lump of memory", but the scheme we use to access it gives it structure.

---

### Post by ClientAlive on 2012-02-23
Edit:

@jwbrase (and all).

When I'm replying to these I'm sort of going through in a a linear fashion, just writing down my thoughts to one post then the next. That's partly why my responses seem like I'm not getting it in their beginning but hopefully, as they move closer to the end, they reflect something very different. I just thought I should mention that. Truth is, yes, I am getting it - thanks to you all.
---------------------------------------


> **trent.josephsen said:**
> You're doing great.  Just thought I'd mention it because learning C can be very frustrating (I know from experience) and it sounds like you could use some encouragement.  You have grasped the core idea of pointers, and while there are a few nuances you could stand to understand better, you're miles closer to understanding the code you're writing (and writing code you don't understand is the worst).

The Wikipedia page on pointers might be helpful, and writing test programs like the ones you did a few posts back will probably help you understand better too.

Well thanks Trent. That is very encouraging and I appreciate it. I do want to be good at this. I finally found something I like  :D

I've seen the wiki page; but, you know, sometimes a person doesn't really get what's being said until they go over it a few time - don't ask me why, I just know that happens with me sometimes.


> **dwhitney67 said:**
> A light bulb must have just illuminated over your head.  I think you got it.  The allocated memory block is there, somewhere on the heap, and you have a pointer that you can use to reference it.  This memory block in turn may have a "next" pointer that references yet another chunk of memory, or possibly NULL.

Anyhow, go back to my previous post where I described how to insert a new node into either the beginning of a List, or at the end of the List.  Your most recent attempt that I saw will not work.

I will do that (review these posts). I'm hoping something is going to jump out at me now. I'm sure it will  :D  At this moment though, not having done that yet... 

If that's so (that it's there somewhere) then that puts this almost on par with religion - you have to just have faith that it's there. I didn't think computer science (or any science for that matter) required you to have "faith" that something was so. As for computer science, at it's most foundational level, it comes down to physical, tangible hardware components, right? I can walk across my room right now and pick up a stick of old RAM I have sitting there, it's real, it's solid, and it's innards make the code, it's binary, and ultimately everything else in computer science possible.

Anyhow, so this an odd experience for me - I have to have faith that something is there even if I have no way to reference it directly. All I can do is make hops from one of them to the next and maybe I'll find it there (if I just believe). Kinda like walking on water  :P

If there is a way to put your finger on the connection with the code, it must be in the pointer(s) which are elements of the struct - specifically them. There must be a connection one can put their finger on or how can you write the code for it? (Without an unbroken path of understanding).


> **JKyleOKC said:**
> 
Each time you malloc an instance of a Node struct, you've created a brand new space on the heap. The first time you do this, you save its address somewhere (I use a pointer named Home) and set its Prev and Next pointers both to NULL to indicate that there are no more instances in the list.


HUGE! I kept coming back to something I think is tied to that notion. The idea that there's a difference in what you get because of a difference in two things in the code. (1) the location of your struct pointer declaration and (2) whether you are or aren't using malloc on it.

I may be off in what follows, but I'm going to take a stab at this. Here goes...

(1) Temp is being declared inside the function. Every time the function is called it runs that line of code that declares Temp and the line below it that allocates a chunk of memory to it. That's what makes it a brand new piece of memory (over and over, every time the function is called). Head is not declared inside a function. It declared outside of main near your struct definiation (global) so it is created one time and that's it. It stays the same one forever.

(2) The fact that we use mallac on Temp is why there's an actual peice of memory created for it in the size of the struct we defined. If we were not to use malloc, as with Head, it would not be a chunk of memory that size. There is some memory associated with Head but I don't think it's the same size and possibly not the same layout. For Head, I think it's smaller and sufficient only for storing addresses. Suffice it to say, there's a difference, an importand one; that, if not recognized, this linked list thing will never make sense to a person.


I just had an odd notion pop into my head and I want to get it down...

If there is a difference between using malloc and not using malloc when creaing a struct pionter, then I wonder if the following is true?...

When using malloc: the chunk of memory allocated has not internal definition. It may have a size but our struct definition contains members. What malloc creates does not have that detail within it.

Head is not being used with malloc. Head has the internal defition to it. It's definition contains a way to reference the members in the struct's definition. These are storage containers within it that are able to hold addresses, not just for the entire struct, but for it's members as well.

Head and Temp are used together. They compliment one another. That chunk of memory malloc gave us relies on the definition (definition - same as my earlier meaning for the term - to have shape/ form) that Head can provide.

Again, I may be way off but I'm trying to lay down some sort of framework with wich to explore what may actaully be true.


> **JKyleOKC said:**
> 
The next time, though, you move Home's Next pointer into the Next pointer of the new instance, and put the new instance's address into Home's Next pointer to replace it. You then copy the address stored in Home into the Prev pointer of the new instance. The two instances are now doubly linked to each other.

After that, you can put other instances anywhere in the list that you want. That's where the Curr pointer comes into play. You can copy the address from Home into Curr and then Curr will point to the start of the list. If you then copy Curr->Next into Curr, Curr will point to the second item. When Curr->Next contains NULL you're at the last item and can go no farther. This is how you can print the entire list, or search it.

Writing your insert function to use Curr instead of Home makes it work no matter where in the list you want to put the new item, though.

I hope this helps a bit more. Sorry for giving you bad code in the previous message; it's been years since I actually used C and I'm a bit rusty about some of the details...

It does. Thank you for helping me explore this topic.


> **jwbrase said:**
> It is and it isn't. All malloc does is reserve a chunk of memory of the requested size and give you a pointer to the beginning of that memory. You tell the compiler to treat that memory as a structure of a given type by casting the pointer you get from malloc to that type (e.g: in "Temp = **(Node *)**malloc(sizeof(struct Node));" the "(Node *)" part tells the compiler we're using this pointer to point to an instance of the "Node" struct).

When you define a struct, the compiler gives each variable in the struct an offset from the beginning of the struct. For instance, if you define struct Foo as follows:

```
struct Foo
{
    int a, b, c;
}
```

the compiler might decide (depending on factors such as sizeof(int) for the computer architecture and OS you're compiling for) to place a at the beginning of the struct (offset 0), b at offset 4 into the struct, and c at offset 8 into the struct.

Then, let's say that we do:

```

struct Foo *Bar;
Bar=(struct Foo *)malloc(sizeof(struct Foo));
int *ap = &(Bar->a);
int *bp = &(Bar->b);
int *cp = &(Bar->c);
```

and then check where ap, bp, and cp are pointing to. We'd find that ap points to the same place as Bar, bp points to a memory location 4 bytes beyond Bar, and cp point to 8 bytes beyond bar. If Bar is 0x00100000, then ap would also be 0x00100000, bp would be 0x00100004, and cp would be 0x00100008.

So the memory itself is a "hazy, undefined lump of memory", but the scheme we use to access it gives it structure.


All I can say is... "And there it is! The nitty gritty, down and dirty." Looks like I've got some thinking to do...

:D

---

### Post by ClientAlive on 2012-02-23
This has got me thinking about two things that aren't always mentioned together, but which I think need to be accunted for together...

That the assignmant of a variable has a location in memory (the variable itself apart from any value it stores) and the value it stores must also have a location in memory. Perhaps it depend on the programming language or some other factor when it comes to how these factors are treated, but conceptually I think they need to be recognized independently. Once that is done, then the way they are treated by a particular language (or other factor) can be addressed.

Here, on this page of this thread we were talking about the heap and stack:

[http://ubuntuforums.org/showthread.php?t=1927762&page=5](http://ubuntuforums.org/showthread.php?t=1927762&page=5)

And I found these:

[http://stackoverflow.com/questions/79923/what-and-where-are-the-stack-and-heap](http://stackoverflow.com/questions/79923/what-and-where-are-the-stack-and-heap)

[http://soonstudios.wordpress.com/2011/04/26/does-malloc-allocate-a-block-of-memory-on-the-heap-or-should-it-be-called-virtual-adress-space/](http://soonstudios.wordpress.com/2011/04/26/does-malloc-allocate-a-block-of-memory-on-the-heap-or-should-it-be-called-virtual-adress-space/)

Surely this is the key!
--------------------------

Edit:

> **dwhitney67 said:**
> Every variable, whether a pointer or not, exists somewhere in RAM.  RAM is divided into two regions:  the stack and the heap.

When you declare a pointer, such as **int* px**, this variable resides on the stack, and hence the address of that pointer is located within the stack.  In this example, the pointer is currently "dangling", that is, it is not assigned to point to any address.

Consider this code and comments:
```

// unassigned pointer declared on the stack.
int* px;


// another pointer declared on the stack, however it points to
// a region in the heap.
int* py = malloc(sizeof(int));


// variable z declared on the stack.
// pointer pz declared on the stack, and points to the address
// where z is located.
int  z;
int* pz = &z;

```

I should further add that memory is addressable at the byte boundary.

As for a Linked List, the "next" pointer resides in a location in memory (generally the heap), and it points to either NULL or to another memory location.


If malloc allocates to the heap but merely declaring a variable allocates to the stack...

That must mean that there are pointers that behave in at least two different ways...


```

int *px = (int *)malloc(sizeof(int));
int *ppx = &px;

//Thats a pointer to something on the heap. px is on the heap, ppx is on
//the stack. We are now forming a connection between the two.

```

Further, if there is a difference between how memory is treated on the stack or on the heap...

```

//the address of ppx may change during program execution
//the address of px will not change during the entire time the program executes.

```

What's more...

```

int x;
int *px = &x;

```

That is a completely different situation than the first example. In this example both x and px are on the stack. As a result, the address of both of them can change during program execution.

Come scope... ?
---------------------

Edit:

My bad. Sorry dwhitney67. I guess it just shows I'm following.

---

### Post by JKyleOKC on 2012-02-23
You're close, here, but the variable and its value aren't really two separate things. A variable is always a memory location of some defined size, and as such always has an address. That address always contains a value, even before you store one there -- when you first power up, the machine's self-test code stores zeroes in each available memory location so the initial value is zero. However as memory gets used and released, other values get stored and nothing automatically erases them. The result is that you have no idea what the value of any variable is, until you set some known value in it. This is what "initialization" does, and using an uninitialized pointer is something that often causes a program to "go crazy" and produce totally unexpected (and inexplicable) actions.

Incidentally, I got curious about the problem I built into that "get_input" function a few pages back, so coded up a test program for it and confirmed dwhitney67's comments about it. I ALSO discovered that the "fgets" function has the same potential problem that has already bitten you with "scanf" -- that is, if you type in too many characters, the surplus are NOT discarded, but instead show up as another immediate input.

For your linked-list assignment, just be careful not to type too much, but it's good to be aware of this for future reference. There's got to be a way to handle this situation, but it's a bit advanced for where you are at the moment. Maybe "getline" will work better...

---

### Post by ClientAlive on 2012-02-23
[B]
Edit:

Don't give up on me now guys. Please! This is it. This is the one right here. The be all end all to the lot of it. (Bolded at the end).
[/B]
------------------

> **JKyleOKC said:**
> You're close, here, but the variable and its value aren't really two separate things. A variable is always a memory location of some defined size, and as such always has an address. That address always contains a value, even before you store one there -- when you first power up, the machine's self-test code stores zeroes in each available memory location so the initial value is zero. However as memory gets used and released, other values get stored and nothing automatically erases them. The result is that you have no idea what the value of any variable is, until you set some known value in it. This is what "initialization" does, and using an uninitialized pointer is something that often causes a program to "go crazy" and produce totally unexpected (and inexplicable) actions.

Incidentally, I got curious about the problem I built into that "get_input" function a few pages back, so coded up a test program for it and confirmed dwhitney67's comments about it. I ALSO discovered that the "fgets" function has the same potential problem that has already bitten you with "scanf" -- that is, if you type in too many characters, the surplus are NOT discarded, but instead show up as another immediate input.

For your linked-list assignment, just be careful not to type too much, but it's good to be aware of this for future reference. There's got to be a way to handle this situation, but it's a bit advanced for where you are at the moment. Maybe "getline" will work better...


It occurst to me that this "buffer" thing is an issue with C. That perhaps the issue does not exist in some other languages. I get to wondering if a person can code something that dynamic in size but clears everything from the buffer after some point. Not just that you place after a certian line of code like fgets or something, but that you encapsulate the entire program with. In other words, a way to correct the behavior of the language with a few lines of code that could be included in every program you ever write in C. Never have to worry about the buffer issue again.  :D
----------------------

[B]Edit:

I wrote what follows on a piece of paper. I wrote the code and then I began to add comments to each line. I didn't make it all the way to the end of the code with my comments. The last comment I wrote is a question I think I need to find an answer to.

```

#include <stdio.h>

struct Node
{
   int x;
   struct Node *Next;
};

struct Node *Head = NULL; //is on the stack

void Insert(int Y);

int main()
{
int Value;

printf("Enter a value\n");
Value = getchar();

Insert(Value);

return 0;
}

void Insert(int Y)
{
struct Node *Temp; //is on the stack
Temp = (struct Node *)malloc(sizeof(struct Node); //is on heap

   if(Temp != NULL //memory was available and was allocated
   {
      Temp->x = Y; //store passed in value in Temp's member "x"

   if(Head == NULL) //starting with an empty list
   {
      Head = Temp; //Head points to the memory on the heap (result of malloc being called)
      Head->Next = NULL;
/*where is NULL? On the heap (because it's still Head's Next) or on the stack
because it's now Temp's Next after the assignment "Head = Temp was made in the line
directly above)? What I'm really asking though, what is more important, is whether
the lvalue is still Head's Next or if it has now become Temp's Next.*/
   }

   else
   {
      Temp->Next = Head;
      Head = Temp;
   }
}
}

```
[/B]

-------------------------

[B]
Edit:

To really draw this out a little batter...

If we were to say...

```

Temp->Next = NULL;
Head = Temp;

```

Would that yeild an identical result to... ?

```

Head = Temp;
Head->Next = NULL;

```

There are three way's "result" could be taken: (1) result in the binary and thus the program that's produced. (2) Result in the way memory is allocated at a hardware level. (3) Result in the behaviour of the program.

I suppose I mean any an/or all of those; but, mainly, just result in program behavior. The symantic level I suppose would be the place that's most practical here. It's nice if maybe the way the end result is acheived is slightly different at the lower levels, but is the end result the same?

The reason this question is important is because then, when we say...

```

else
{
   Temp->Next = Head;
   Head = Temp;
}

```

In that line "Head = Temp;" it becomes important to know whether the previous assignment in the line above it carries. In that case, it would mean your result is equal to Head's Next pointing to Head. That's doesn't make sense. Do you see where I'm going with this?

Or does it make sense? In the context of previous items in the list just existing somewhere without having a direct reference to them once they have passed. Perhaps in that context it does make sense for Head's Next to point to Head. Perhaps that is like saying the "old" Head's Next point's the the "new" Head. Is that right? Is that normal?
[/B]

---

### Post by ClientAlive on 2012-02-24
Whatever the problem is, this program is apparently not going to allow me to loop it. It simply refuses to accept the input in that various place. Unfortunately, this isn't the type of program that can fucntion if it ends after each thing you do with it. Whatever list entry was stored in memory will be lost and there will be no way to display it's functionality. I'll go back over this thread again and see what solutions mey be there. All I know is this thing is fighting me tooth and nail to just do a simple while loop around the entire program and allow the user to enter a set character to quit. Just fighting me tooth and nail.
--------------------

```

/*
Question: 

Tip: 

Status: 

Next steps: 
*/

#include <ctype.h> //tolower()
#include <stdio.h>

struct Node
{
char Name[32];
char Phone[18];
struct Node *Next;
};

struct Node *Head = NULL;

//void Menu();
void Insert(char Array1[], char Array2[]);
//void Delete(int Selection, //?); //delete all or delete entry
//struct Node Search(struct Node); //used internally - Print() is what will call this and will print either the whole shebang or just the entry that Search() returns
void Print();//int Selection, //?); //print all or print entry

int main()
{
	char Selection[2] = {0};

	while(Selection[0] != 'q')
	{
		char Name[32]; //arrays are pointers by nature, remember
		char Phone[18];
		char Junk;

printf("Line 39: Selection[0] is: %c\n", Selection[0]);

		printf("Enter your selection now...\n");
	if(Selection[1] == '\n')
	{
		Selection[1] == '\0';
	}

printf("Line 47: Selection[0] is: %c\n", Selection[0]);


		fgets(Selection, sizeof(Selection) - 1, stdin);
		//Junk = getchar();

printf("Line 53: Selection[0] is: %c\n", Selection[0]);


		if(Selection[0] != 'q');
		{
printf("Line 58: Selection[0] is: %c\n", Selection[0]);
			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);
			printf("Enter a phone number...\n");
			fgets(Phone, sizeof(Phone), stdin);

			Insert(Name, Phone);

			Print();
		}
	} //end while

	return 0;
} //end main

//void Menu()
//{
//printf("Please select from the following...\n\n");
//printf("[I]nsert entry\n");
//printf("[D]elete entry\n");
//printf("[P]rint\n");
//printf("\n");
//}

void Insert(char Array1[], char Array2[])
{
	struct Node *Temp = (struct Node *)malloc(sizeof(struct Node));
	strncpy(Temp->Name, Array1, sizeof(Temp->Name));
	strncpy(Temp->Phone, Array2, sizeof(Temp->Phone));

	if(Temp != NULL)
	{
		if(Head == NULL)
		{
			Head = Temp;
			Head->Next = NULL;
		}

		else
		{
			Temp->Next = Head;
			Head = Temp;
		}
	}
}

//void Delete(int Selection, //?) //delete all or delete entry
//{

//}

//struct Node Search(struct Node)
//{

//}

void Print()//int Selection, //?) //print all or print entry
{
	struct Node *Curr = Head;

	if(Curr == NULL)
	{
	printf("There are no items in the list\n");
	}

	else
	{
		while(Curr != NULL)
		{
			printf("Name: %s", Curr->Name);
			printf("Phone: %s", Curr->Phone);
			Curr = Curr->Next;
		}
	}
}


```


Output:

```

shine@BashBox ~/Programming/ProgrammingPlayground/LabPads > ./LabPad[01].binLine 39: Selection[0] is: 
Enter your selection now...
Line 47: Selection[0] is: 
Line 53: Selection[0] is: 
Line 58: Selection[0] is: 
Enter a name...

```
---------------------

```

/*
Question: 

Tip: 

Status: 

Next steps: 
*/

#include <ctype.h> //tolower()
#include <stdio.h>

struct Node
{
char Name[32];
char Phone[18];
struct Node *Next;
};

struct Node *Head = NULL;

//void Menu();
void Insert(char Array1[], char Array2[]);
//void Delete(int Selection, //?); //delete all or delete entry
//struct Node Search(struct Node); //used internally - Print() is what will call this and will print either the whole shebang or just the entry that Search() returns
void Print();//int Selection, //?); //print all or print entry

int main()
{
	**char** Selection[2] = {0};

	while(Selection[0] != 'q')
	{
		char Name[32]; //arrays are pointers by nature, remember
		char Phone[18];
		char Junk;

printf("Line 39: Selection[0] is: %c\n", Selection[0]);

		printf("Enter your selection now...\n");
	if(Selection[1] == '\n')
	{
		Selection[1] == '\0';
	}

printf("Line 47: Selection[0] is: %s\n", Selection[0]);


		fgets(Selection, sizeof(Selection) - 1, stdin);
		//Junk = getchar();

printf("Line 53: Selection[0] is: %s\n", Selection[0]);


		if(Selection[0] != 'q');
		{
printf("Line 58: Selection[0] is: %c\n", Selection[0]);
			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);
			printf("Enter a phone number...\n");
			fgets(Phone, sizeof(Phone), stdin);

			Insert(Name, Phone);

			Print();
		}
	} //end while

	return 0;
} //end main

//void Menu()
//{
//printf("Please select from the following...\n\n");
//printf("[I]nsert entry\n");
//printf("[D]elete entry\n");
//printf("[P]rint\n");
//printf("\n");
//}

void Insert(char Array1[], char Array2[])
{
	struct Node *Temp = (struct Node *)malloc(sizeof(struct Node));
	strncpy(Temp->Name, Array1, sizeof(Temp->Name));
	strncpy(Temp->Phone, Array2, sizeof(Temp->Phone));

	if(Temp != NULL)
	{
		if(Head == NULL)
		{
			Head = Temp;
			Head->Next = NULL;
		}

		else
		{
			Temp->Next = Head;
			Head = Temp;
		}
	}
}

//void Delete(int Selection, //?) //delete all or delete entry
//{

//}

//struct Node Search(struct Node)
//{

//}

void Print()//int Selection, //?) //print all or print entry
{
	struct Node *Curr = Head;

	if(Curr == NULL)
	{
	printf("There are no items in the list\n");
	}

	else
	{
		while(Curr != NULL)
		{
			printf("Name: %s", Curr->Name);
			printf("Phone: %s", Curr->Phone);
			Curr = Curr->Next;
		}
	}
}


```


Compiler Output:

```

shine@BashBox ~/Programming/ProgrammingPlayground/LabPads > gcc LabPad[01].c -o LabPad[01].bin
LabPad[01].c: In function ‘main’:
LabPad[01].c:47: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
LabPad[01].c:53: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
LabPad[01].c: In function ‘Insert’:
LabPad[01].c:84: warning: incompatible implicit declaration of built-in function ‘malloc’
LabPad[01].c:85: warning: incompatible implicit declaration of built-in function ‘strncpy’

```

I'm going to end up failing this assignment solely because of this crap! It'll have nothing to do with whether or not I can create a linked list. Hell, there'll be no way to evaluate that in the first place!

I tried including the "-std=c99" flag for my compiler too. It gives the same output just with a little different wording where lines 84 and 85 are concerned => but it's the same.
-------------------

```

int main(int argc, char **argv)

```

Makes no difference expects type 

16 hrs left and counting ...\

---

### Post by JKyleOKC on 2012-02-24
I'll only address the "where is NULL" comment...

NULL is a value, so it's the value of at least one variable. In a singly linked list, only one variable in the entire collection that make up the list will have a value of NULL (except for very brief intervals while you are modifying the list). At the start of the program, before anything gets added, you should initialize Head by setting its value to NULL. This tells you that you have nothing at all in the list.

Later, use malloc to create an instance of the struct on the heap, and store the address that it returns into Temp initially. Copy the value of Head into Temp->Next, then copy the value of Temp into Head. Now Head points to the one and only instance of the struct, and the value of Head->Next is NULL (copied there from the original value of Head, and Head now points to the same location in the heap as Temp).

From here on, start by copying the value of Head into Curr, and checking the value of Curr->Next. If it's not NULL, put it into Curr and repeat the test with the (new) Curr->Next. This walks you through the list, instance by instance, until you reach the one where Curr->Next has a value of NULL. That's the last one in the list, so you now use malloc to create a new instance, save its address in Temp, copy Curr->Next's value into Temp->Next, and then copy the value of Temp into Curr. This ties the new instance to the end of the list. Notice that Head never changes during this process, and nothing specifically mentions the value NULL. It just gets copied, like any other value.

For doubly linked lists, it's the same procedure except that you have to also handle the Prev pointers, but best leave those alone until you're totally comfortable with the singly linked version.

Once you're comfortable with singly linked list principles, adding the Prev linkage is pretty simple. When that's done, searching the list involves checking the data portion of each instance for a match, and reporting failure if you get to the end without matching your search term. With searching in place, it becomes easy to create a sorted list by searching for the right place to put a new entry and doing the insert there rather than at the end.

Notice that each of these increases in functionality depends on the previous one being in place. That's the "divide and conquer" principle at work, aka "eating the elephant one bite at a time."

You ask whether the sequence matters; it definitely DOES matter. Any time you assign a value to a variable, everything associated with that variable (except its own fixed address) may change. While functions and procedures may have side effects, such as we've seen with scanf and fgets, in general the machine is going to do exactly what you tell it to, in the sequence that you tell it...

---

### Post by JKyleOKC on 2012-02-24
> **ClientAlive said:**
> Whatever the problem is, this program is apparently not going to allow me to loop it. It simply refuses to accept the input in that various place. Unfortunately, this isn't the type of program that can fucntion if it ends after each thing you do with it. Whatever list entry was stored in memory will be lost and there will be no way to display it's functionality. I'll go back over this thread again and see what solutions mey be there. All I know is this thing is fighting me tooth and nail to just do a simple while loop around the entire program and allow the user to enter a set character to quit. Just fighting me tooth and nail.The "main()" in your most recent message doesn't include a loop at all. You should be able to wrap the whole thing in a "while (1)" enclosure and add a "if (Value=='q') break;" line right after the "getchar" line, to make it loop.

The way you've coded it, it will insert new entries at the front of the list rather than at the end, but it looks as if it ought to work...

---

### Post by JKyleOKC on 2012-02-24
> **ClientAlive said:**
> Whatever the problem is, this program is apparently not going to allow me to loop it. It simply refuses to accept the input in that various place. Unfortunately, this isn't the type of program that can fucntion if it ends after each thing you do with it. Whatever list entry was stored in memory will be lost and there will be no way to display it's functionality. I'll go back over this thread again and see what solutions mey be there. All I know is this thing is fighting me tooth and nail to just do a simple while loop around the entire program and allow the user to enter a set character to quit. Just fighting me tooth and nail.The "main()" in your most recent message (prior to the one I quote here) doesn't include a loop at all. You should be able to wrap the whole thing in a "while (1)" enclosure and add a "if (Value=='q') break;" line right after the "getchar" line, to make it loop.

The way you've coded it, it will insert new entries at the front of the list rather than at the end, but it looks as if it ought to work...

---

### Post by JKyleOKC on 2012-02-24
Ignore the first one of my duplicate posts above; it's late here!

Your program doesn't seem to be getting any input into "Selection" before Line 47; looks as if that critical function call got left out!

EDIT: you need to include stdlib.h also, to get declarations for malloc and other functions...

---

### Post by ClientAlive on 2012-02-24
did this just to see what the compiler would say...  It's been complaining nonstop no matter how I format it.


```

/*
Question: 

Tip: 

Status: 

Next steps: 
*/

#include <ctype.h> //tolower()
#include <stdio.h>
#include <stdlib.h> //malloc()
#include <string.h> //strncpy()

struct Node
{
char Name[32];
char Phone[18];
struct Node *Next;
};

struct Node *Head = NULL;

//void Menu();
void Insert(char Array1[], char Array2[]);
//void Delete(int Selection, //?); //delete all or delete entry
//struct Node Search(struct Node); //used internally - Print() is what will call this and will print either the whole shebang or just the entry that Search() returns
void Print();//int Selection, //?); //print all or print entry

int main(int argc, char **argv)
{
	char Selection[2] = {0};

	while(Selection[0] != 'q')
	{
		char Name[32]; //arrays are pointers by nature, remember
		char Phone[18];
		//char Junk;

**printf("Line 41: Selection[0] is: %c\n", Selection[0]);**

		printf("Enter your selection now...\n");
	if(Selection[1] == '\n')
	{
		Selection[1] == '\0';
	}

**printf("Line 49: Selection[0] is: %s\n", Selection[0]);**


		fgets(Selection, sizeof(Selection) - 1, stdin);
		//Junk = getchar();

**printf("Line 55: Selection[0] is: %c\n", &Selection);**


		if(Selection[0] != 'q');
		{
**printf("Line 60: Selection[0] is: %s\n", Selection[0]);**
			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);
			printf("Enter a phone number...\n");
			fgets(Phone, sizeof(Phone), stdin);

			Insert(Name, Phone);

			Print();
		}
	} //end while

	return 0;
} //end main

//void Menu()
//{
//printf("Please select from the following...\n\n");
//printf("[I]nsert entry\n");
//printf("[D]elete entry\n");
//printf("[P]rint\n");
//printf("\n");
//}

void Insert(char Array1[], char Array2[])
{
	struct Node *Temp = (struct Node *)malloc(sizeof(struct Node));
	strncpy(Temp->Name, Array1, sizeof(Temp->Name));
	strncpy(Temp->Phone, Array2, sizeof(Temp->Phone));

	if(Temp != NULL)
	{
		if(Head == NULL)
		{
			Head = Temp;
			Head->Next = NULL;
		}

		else
		{
			Temp->Next = Head;
			Head = Temp;
		}
	}
}

//void Delete(int Selection, //?) //delete all or delete entry
//{

//}

//struct Node Search(struct Node)
//{

//}

void Print()//int Selection, //?) //print all or print entry
{
	struct Node *Curr = Head;

	if(Curr == NULL)
	{
	printf("There are no items in the list\n");
	}

	else
	{
		while(Curr != NULL)
		{
			printf("Name: %s", Curr->Name);
			printf("Phone: %s", Curr->Phone);
			Curr = Curr->Next;
		}
	}
}


```



Compiler Output:

```

gcc LabPad[01].c -std=c99 -o LabPad[01].bin
LabPad[01].c: In function &#8216;main&#8217;:
LabPad[01].c:49: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 2 has type &#8216;int&#8217;
LabPad[01].c:55: warning: format &#8216;%c&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;char (*)[2]&#8217;
LabPad[01].c:60: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 2 has type &#8216;int&#8217;

```

Why would it say that?! line 40: **char Selection[2];** is a char and it is a pointer because it's an array. Line 55: **"%c"** is the conversion character for a **char not an int.** Why would it say %c "expects an int" that's insane!

Am I just tired and forgetting thigs? This was covered almost on day one (nearly 6 mos ago). Conversion characters, printf, etc.

---

### Post by Vaphell on 2012-02-24
> char Selection[2]; is a char and it is a pointer because it's an array
well, it can't be both, can it? when you work on Selection, treat it as a char *, when you work on Selection[int] - char/int

```
#include <stdio.h>

int main()
{
  char chr = 'a';
  char arr[] = "ABCDEF";
  
  printf( "&chr: %p   chr: %c\n", &chr, chr );
  printf( "&arr: %p   (ptr)arr: %p   (char*)arr: %s   *arr: %c\n", &arr, arr, arr, *arr );
  printf( "arr[0]: %c   (ptr)&arr[0]: %p   (char*)&arr[0]: %s\n", arr[0], &arr[0], &arr[0] );
  printf( "arr[1]: %c   (ptr)&arr[1]: %p   (char*)&arr[1]: %s\n", arr[1], &arr[1], &arr[1] );

  return 0;
}
```
output:
```
&chr: 0x7fff37d18a0f   chr: a
&arr: 0x7fff37d18a00   (ptr)arr: 0x7fff37d18a00   (char*)arr: ABCDEF   *arr: A
arr[0]: A   (ptr)&arr[0]: 0x7fff37d18a00   (char*)&arr[0]: ABCDEF
arr[1]: B   (ptr)&arr[1]: 0x7fff37d18a01   (char*)&arr[1]: BCDEF

```

---

### Post by ClientAlive on 2012-02-24
I've narrowed it down. This line:

```


while(*Selection != 'q');
{

```

Was

```


if(*Selection != 'q');
{

```

...is not being checked at all. printf at lines 55 and 60 reveal that the value of my "char" Selection[2]; is indeed set to "q" before hitting that line and it is also "q" after that line. Whether it's a "while" or an "if" that line is not being executed.

using "&Selection" in my printf line gives me a compile error. Written precisely as you gave it - compile error. Written "*Selection" clears up errors and yeild the correct data type value (a char).
---------------------------------

Edit:

```

/*
Question: 

Tip: 

Status: 

Next steps: 
*/

#include <ctype.h> //tolower()
#include <stdio.h> //fgets()
#include <stdlib.h> //malloc()
#include <string.h> //strncpy()

struct Node
{
char Name[32];
char Phone[18];
struct Node *Next;
};

struct Node *Head = NULL;

//void Menu();
void Insert(char Array1[], char Array2[]);
//void Delete(int Selection, //?); //delete all or delete entry
//struct Node Search(struct Node); //used internally - Print() is what will call this and will print either the whole shebang or just the entry that Search() returns
void Print();//int Selection, //?); //print all or print entry

int main(int argc, char **argv)
{
	char Selection[2];

	while(*Selection != 'q')
	{
		char Name[32]; //arrays are pointers by nature, remember
		char Phone[18];
		//char Junk;

printf("Line 41: Selection[0] is: %c\n", *Selection);

		printf("Enter your selection now...\n");

printf("Line 49: Selection[0] is: %c\n", *Selection);

*Selection = getchar();
		//fgets(Selection, sizeof(Selection), stdin);
		//Junk = getchar();

printf("Line 55: Selection[0] is: %c\n", *Selection);

		while(*Selection != 'q');
		{
printf("Line 60: Selection[0] is: %c\n", *Selection);
			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);
			printf("Enter a phone number...\n");
			fgets(Phone, sizeof(Phone), stdin);

			Insert(Name, Phone);

			Print();
		}
	} //end outer while

	return 0;
} //end main

//void Menu()
//{
//printf("Please select from the following...\n\n");
//printf("[I]nsert entry\n");
//printf("[D]elete entry\n");
//printf("[P]rint\n");
//printf("\n");
//}

void Insert(char Array1[], char Array2[])
{
	struct Node *Temp = (struct Node *)malloc(sizeof(struct Node));
	strncpy(Temp->Name, Array1, sizeof(Temp->Name));
	strncpy(Temp->Phone, Array2, sizeof(Temp->Phone));

	if(Temp != NULL)
	{
		if(Head == NULL)
		{
			Head = Temp;
			Head->Next = NULL;
		}

		else
		{
			Temp->Next = Head;
			Head = Temp;
		}
	}
}

//void Delete(int Selection, //?) //delete all or delete entry
//{

//}

//struct Node Search(struct Node)
//{

//}

void Print()//int Selection, //?) //print all or print entry
{
	struct Node *Curr = Head;

	if(Curr == NULL)
	{
	printf("There are no items in the list\n");
	}

	else
	{
		while(Curr != NULL)
		{
			printf("Name: %s", Curr->Name);
			printf("Phone: %s", Curr->Phone);
			Curr = Curr->Next;
		}
	}
}

```


Compiler Output:

```

shine@BashBox ~/Programming/ProgrammingPlayground/LabPads > gcc LabPad[01].c -std=c99 -Wall -Werror -o LabPad[01].bin
shine@BashBox ~/Programming/ProgrammingPlayground/LabPads > ./LabPad[01].binLine 41: Selection[0] is: 
Enter your selection now...
Line 49: Selection[0] is: 
q
Line 55: Selection[0] is: q
Line 60: Selection[0] is: q
Enter a name...
Enter a phone number...

Name: 
Phone: 
shine@BashBox ~/Programming/ProgrammingPlayground/LabPads > 

```

It stops (as it should) after printing "Line 49: Selection[0] is: " to the screen. It's waiting for input.

I enter "q" (without the quotes obviously). I press enter. It prints the rest of what you see after the aforementioned line.

I hit <enter> a second time. It exits the program.

---

### Post by Vaphell on 2012-02-24
you need to mow through input buffer with getchar to consume everything that's there. Newline messes up things later

maybe something like this
```
char choiceInput( void )
{
  char ch, val;
  val = ch = getchar(); //get first char
  while( ch != '\n' ) //consume excessive chars
    ch = getchar();
  return val;
}
``` first char will be returned and the rest consumed and will not pollute the input.

your while inside while doesn't seem to be a good idea. Program flow tends to get funky with such constructs. When whiles embedded one in another share common control logic, you will get lost quickly.

imo it should be one main loop, switch/case inside
```
while ( 1 ) //main loop
{
  <present options here>
  char selection=choiceInput();  //read option

  switch ( tolower(selection) ) //
  {
    case 'n':
      printf("new entry\n");
      <new entry stuff here>;
      break;
    case 'p':
      printf("print list\n");
      <print list stuff here>;
      break;
    case 'q': printf("quit\n"); return 0;
    default: printf("invalid option\n"); break;
  }
}
```
things are tidy, one while loop iteration means exactly one choice/operation


you really need to break the program into smaller, easier to bite pieces, even if they are 2 lines long initially. With time they can grow with support for corner cases and such, so having things contained in an autonomous piece of code right off the bat makes everything easier to manage.
In my example user input is handled with a dedicated function that hides ugly details in its body, the rest of the program doesn't need to know anything about it. Main logic cares only about the sanitized value describing the option.
As complexity of the program grows well designed functional pieces with tidy interfaces save you a lot of pain.

---

### Post by ClientAlive on 2012-02-24
This thing about the input buffer... wow.

Somehow I managed to get on track with this thing. I reverted to an earlier, known, working version and built from there. It's coming along but slowly. I have been trying especially hard to test more regularly and not get too far ahead of myself. It seems to be helping a lot. So far I can enter items into the list and print the entire list. I've been working on Search() and have been attempting to use strcasecmp(). I'm not really sure where my problem lies but it tells me the item isn't found no matter what I enter. I may have an error in my logic somewhere, I'm trying to find that out. I think I may have to create my own function to compare the strings; but, if I do that I fear it may not work as well and/ or could introduce bugs/ unexpected results. Here's what I have now though...

```

/*
Question: 

Tip: 

Status: Issues with printing an item in the list. Possibly in Search(), possibly in Print().

Next steps: 
*/

#include <ctype.h> //tolower()
#include <stdio.h> //fgets()
#include <stdlib.h> //malloc()
#include <string.h> //strncpy(), strcasecmp()

struct Node
{
char Name[32];
char Phone[18];
struct Node *Next;
};

struct Node *Head = NULL;

//void Menu();
void Insert(char Array1[], char Array2[]);
//void Delete(int Selection, //?); //delete all or delete entry
struct Node *Search(char Array1[]); //used internally - Print() is what will call this and will print either the whole shebang or just the entry that Search() returns
void Print(int A); //print all or print entry

int main()
{
	int Selection = ' ';

	while(tolower(Selection) != 'q')
	{
		char Name[32]; //arrays are pointers by nature, remember
		char Phone[18];

		printf("Enter your selection: ");
		Selection = getchar();
		getchar();

		if(tolower(Selection) != 'q')
		{
			int PrintSelect = ' ';

			switch(tolower(Selection))
			{
				case 'a':
				{
					printf("Enter a name...\n");
					fgets(Name, sizeof(Name), stdin);
					printf("Enter a phone number...\n");
					fgets(Phone, sizeof(Phone), stdin);

					Insert(Name, Phone);

					break;
				}

				case 'p':
				{
					printf("Would you like to print [L]ist or [I]tem?\n");
					printf("Enter your selection: ");
					PrintSelect = getchar();
					getchar();

					Print(PrintSelect);

					break;
				}
			} //end switch
		} //end if
	} //end while

	return 0;
} //end main

//void Menu()
//{
//printf("Please select from the following...\n\n");
//printf("[A]dd entry\n");
//printf("[D]elete entry\n");
//printf("[P]rint\n");
//printf("\n");
//}

void Insert(char Array1[], char Array2[])
{
	struct Node *Temp = (struct Node *)malloc(sizeof(struct Node));
	strncpy(Temp->Name, Array1, sizeof(Temp->Name));
	strncpy(Temp->Phone, Array2, sizeof(Temp->Phone));

	if(Temp != NULL)
	{
		if(Head == NULL)
		{
			Head = Temp;
			Head->Next = NULL;
		}

		else
		{
			Temp->Next = Head;
			Head = Temp;
		}
	}
}

//void Delete(int Selection, //?) //delete all or delete entry
//{

//}

[B]struct Node *Search(char Array1[])
{
	struct Node *Found = NULL;
	struct Node *Curr = Head;

	while(Curr != NULL)
	{
		

		if((strcasecmp(Curr->Name, Array1)) == 0) //order of args?
		{
			Found = Curr;
		}

		else
		{
			Found = 0;
		}

		Curr = Curr->Next;
	}

	return Found;
}[/B]

void Print(int A) //print all or print entry - status: printing entire list is printing lifo
{
	struct Node *Curr = Head;

	if(Curr == NULL)
	{
		printf("There are no items in the list\n");
	}

	else
	{
		if(tolower(A) == 'l')
		{
			while(Curr != NULL)
			{
				printf("Name: %s", Curr->Name);
				printf("Phone: %s", Curr->Phone);
				Curr = Curr->Next;
			}
		}

		[B]else if(tolower(A) == 'i')
		{
			char Name[32];

			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);

			if((Search(Name)) != 0) //possibility - this condidtion is always false
			{
				Curr = Search(Name);
			}


			else
			{
				printf("The item is not in the list\n");
			}
		}[/B]
	}
}

```

---

### Post by dwhitney67 on 2012-02-24
> **ClientAlive said:**
> I've been working on Search() and have been attempting to use strcasecmp(). I'm not really sure where my problem lies but it tells me the item isn't found no matter what I enter. I may have an error in my logic somewhere...


Once you find a match in the list, you should consider the search as completed.  In your code, you do not... and that is the problem.  Perhaps you could augment the conditional for the while-loop to something like:
```

...

while(Curr != NULL **&& found == NULL**)
{
    ....
}

...

```
This will cause the loop to exit once you have found an item in the list, and ensure that you return the appropriate node within the list (if it exists).


P.S.  Do you realize that you are storing names and phone numbers with a newline character?  Similarly when you prompt for a search name.

---

### Post by ClientAlive on 2012-02-24
> **dwhitney67 said:**
> Once you find a match in the list, you should consider the search as completed.  In your code, you do not... and that is the problem.  Perhaps you could augment the conditional for the while-loop to something like:
```

...

while(Curr != NULL **&& found == NULL**)
{
    ....
}

...

```
This will cause the loop to exit once you have found an item in the list, and ensure that you return the appropriate node within the list (if it exists).


P.S.  Do you realize that you are storing names and phone numbers with a newline character?  Similarly when you prompt for a search name.


[Sight] Newline...  grrr...

So much appreciated dwhitney67. I asked you guys to go with me one mile and you've gone with me ten. I don't know what more I can expect and I don't want to pester. I'll certain keep up here at this thread as long as you all are willing but I don't blame you at all though if that's not the case. As things stand I'll be awake for a full 24 hrs or more before I get things I need to accomplished (this CSC lab isn't my only obligation). I'll look at incorporating this into my code. Thank you.

Jake

---

### Post by Vaphell on 2012-02-24
yup, it's clear that you got \n's there. When you print names and numbers, lines end even though you have no \n in printf("Name: %s", Node->Name), printf("Phone: %s", Node->Phone). That means \n is inside the variable placed at %s

after reading you need to iterate through Name/Phone to find \n and replace it with \0, and then insert data into the list

---

### Post by ClientAlive on 2012-02-24
Oh my! Search() is working. Stupidest thing - it was working for a while but I had no code in Print() to actually print the result that was returned. I must be getting tired.

[Sigh] Newlines... grrr...

---

### Post by Tony Flury on 2012-02-24
> **ClientAlive said:**
> I've narrowed it down. This line:

```


while(*Selection != 'q');
{

```

Was

```


if(*Selection != 'q');
{

```

...is not being checked at all. printf at lines 55 and 60 reveal that the value of my "char" Selection[2]; is indeed set to "q" before hitting that line and it is also "q" after that line. Whether it's a "while" or an "if" that line is not being executed.


Look at the code exactly as written above, and where the semi colons are - hint : What do you think this does : 

```

while( true )
    ;

```

---

### Post by ClientAlive on 2012-02-24
> **Tony Flury said:**
> Look at the code exactly as written above, and where the semi colons are - hint : What do you think this does : 

```

while( true )
    ;

```


Oh my goodness!! That's cra'zee! A semicolon does not belong there. You know how much time, effort, and greif that stupid little character cose me? And I never noticed it until you pointed that out.

Well, so I'm aaaallmost there. Everyting is working except for one teensie weensie little issue (famous last words eh').

Everything works well enough except after I delete something from the list and then print the entire list after that, nothing to do with it should appear in the list. More than that, it should execut my printf line that says the item isn't in the list. I've fiddled and fiddled with it and I fear I may break what I have if I push too hard.

What happens is the items seem to genuinely be deleted, and the name in that item is not there, but the headings "Name:" and "Phone:" and the content of the phone string still appear in the list. I've been focusing on getting the printf line that says the item is not in the list (in Print()) to execute but haven't had sucess yet.

If I can get this one little thing worked out I can bring Menu() on line and pray to god nothing breaks when I do.

It's kinda depressing. I really though I could do better than this.

```

/*
Question: 

Tip: 

Status: Issue with what appears in the list after an item is deleted.

Next steps: 
*/

#include <ctype.h> //tolower()
#include <stdio.h> //fgets()
#include <stdlib.h> //malloc()
#include <string.h> //strncpy(), strcasecmp()

struct Node
{
char Name[32];
char Phone[18];
struct Node *Next;
};

struct Node *Head = NULL;

//void Menu();
void Insert(char Array1[], char Array2[]);
void Delete(int A); //delete all or delete entry
struct Node *Search(char Array1[]); //used internally
void Print(int A); //print all or print entry

int main()
{
	int Selection = ' ';

	while(tolower(Selection) != 'q')
	{
		char Name[32]; //arrays are pointers by nature, remember
		char Phone[18];

		printf("Enter your selection: ");
		Selection = getchar();
		getchar();

		if(tolower(Selection) != 'q')
		{
			int PrintSelect = ' ';
			int DeleteSelect = ' ';

			switch(tolower(Selection))
			{
				case 'a':
				{
					printf("Enter a name...\n");
					fgets(Name, sizeof(Name), stdin);
					printf("Enter a phone number...\n");
					fgets(Phone, sizeof(Phone), stdin);

					Insert(Name, Phone);

					break;
				}

				case 'd':
				{
					printf("Would you like to delete [L]ist or [I]tem?\n");
					printf("Enter your selection: ");
					DeleteSelect = getchar();
					getchar();

					Delete(DeleteSelect);

					break;
				}

				case 'p':
				{
					printf("Would you like to print [L]ist or [I]tem?\n");
					printf("Enter your selection: ");
					PrintSelect = getchar();
					getchar();

					Print(PrintSelect);

					break;
				}
			} //end switch
		} //end if
	} //end while

	return 0;
} //end main

//void Menu()
//{
//printf("Please select from the following...\n\n");
//printf("[A]dd entry\n");
//printf("[D]elete entry\n");
//printf("[P]rint\n");
//printf("\n");
//}

void Insert(char Array1[], char Array2[])
{
	struct Node *Temp = (struct Node *)malloc(sizeof(struct Node));
	strncpy(Temp->Name, Array1, sizeof(Temp->Name));
	strncpy(Temp->Phone, Array2, sizeof(Temp->Phone));

	if(Temp != NULL)
	{
		if(Head == NULL)
		{
			Head = Temp;
			Head->Next = NULL;
		}

		else
		{
			Temp->Next = Head;
			Head = Temp;
		}
	}
}

void Delete(int A) //delete all or delete entry
{
	struct Node *Curr = Head;

	if(Curr == NULL)
	{
		printf("There are no items in the list\n");
	}

	else
	{
		if(tolower(A) == 'l')
		{
			while(Curr != NULL)
			{
				free(Curr);
				Curr = Curr->Next;
			}

			Head = NULL;
		}

		else if(tolower(A) == 'i')
		{
			char Name[32];

			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);

			if((Search(Name)) != 0) //possibility - this condidtion is always false
			{
				Curr = Search(Name);
				free(Curr);
			}


			else if((Search(Name)) == 0)
			{
				printf("The item is not in the list\n");
			}
		}
	}
}

struct Node *Search(char Array1[])
{
	struct Node *Found = NULL;
	struct Node *Curr = Head;

	while(Curr != NULL && Found == NULL)
	{
		if((strcasecmp(Curr->Name, Array1)) != 0) //order of args?
		{
			Found = 0;
		}

		else
		{
			Found = Curr;
		}

		Curr = Curr->Next;
	}

	return Found;
}

void Print(int A) //print all or print entry - status: printing entire list is printing lifo
{
	struct Node *Curr = Head;

	if(Curr == NULL)
	{
		printf("There are no items in the list\n");
	}

	else
	{
		if(tolower(A) == 'l')
		{
			while(Curr != NULL)
			{
				printf("Name: %s", Curr->Name);
				printf("Phone: %s", Curr->Phone);
				Curr = Curr->Next;
			}
		}

		else if(tolower(A) == 'i')
		{
			char Name[32];

			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);

			if((Search(Name)) != 0)
			{
				Curr = Search(Name);
				printf("Name: %s", Curr->Name);
				printf("Phone: %s", Curr->Phone);
			}


			else if((Search(Name)) == 0)
			{
				printf("The item is not in the list\n");
			}
		}
	}
}

```


Output:

```

shine@BashBox ~/Programming/ProgrammingPlayground/LabPads > ./LabPad[01].binEnter your selection: a
Enter a name...
jake
Enter a phone number...
887
Enter your selection: a
Enter a name...
jen
Enter a phone number...
978
Enter your selection: a
Enter a name...
adam
Enter a phone number...
677
Enter your selection: a
Enter a name...
tim
Enter a phone number...
999
Enter your selection: p
Would you like to print [L]ist or [I]tem?
Enter your selection: l
Name: tim
Phone: 999
Name: adam
Phone: 677
Name: jen
Phone: 978
Name: jake
Phone: 887
Enter your selection: p
Would you like to print [L]ist or [I]tem?
Enter your selection: i
Enter a name...
jen
Name: jen
Phone: 978
Enter your selection: d
Would you like to delete [L]ist or [I]tem?
Enter your selection: i
Enter a name...
monster
The item is not in the list
Enter your selection: d
Would you like to delete [L]ist or [I]tem?
Enter your selection: i
Enter a name...
jen
Enter your selection: p
Would you like to print [L]ist or [I]tem?
Enter your selection: l
Name: tim
Phone: 999
Name: adam
Phone: 677
Name: Phone: 978
Name: jake
Phone: 887
Enter your selection: p
Would you like to print [L]ist or [I]tem?
Enter your selection: i
Enter a name...
jen
The item is not in the list
Enter your selection: q
shine@BashBox ~/Programming/ProgrammingPlayground/LabPads > 

```


I've been thinking I need to call malloc in Delet(). Something like...

```

Curr = (struct Node *)malloc(sizeof(struct Node));

```

This way perhaps what is deleted will be the entire thing? Idk.
--------------------

Edit:

Good lord, what a bloated mess!

I think that's what I'll name it. That's what I'll name the file... "bloatski". "BloatskiMax".

Not.

---

### Post by JKyleOKC on 2012-02-24
Again, very close. However, you don't want to call malloc again in delete. That would only ADD an entry, not delete it.

What you've missed in the delete() function is to fix the pointer so it no longer points to the instance you've given back. This is where the Prev pointer in a doubly linked list becomes so helpful. In the singly linked version, you have to remember the preceding instance's address during the search (with another global pointer named Prev, for example) just before moving to the next instance. That is, something like:```
Prev = Curr;
Curr = Curr->Next;
```Then in delete(), replace the "free(Curr)" call with this:```
Prev->Next = Curr->Next;
free(Curr);
Curr = Prev->Next;
```Now Curr will point to the entry that followed the one you deleted, or will be NULL indicating that nothing followed the deleted one. Test it by deleting from the middle of the list, from the front, and from the end. All three should work with no need for special code at either end.

And yes, you're definitely getting tired, and tired programmers overlook critical details. Much of the bad code that gets into "professional" programs got there during "death march" pushes. I once worked on a project that insisted on minimum 100-hour weeks. By the time it got cancelled, absolutely NO useful output was being generated!

---

### Post by dwhitney67 on 2012-02-24
My additional $0.02:

Is it not a little too late to be checking if Temp is NULL?  You use Temp before you even check!
```

void Insert(char Array1[], char Array2[])
{
	struct Node *Temp = (struct Node *)malloc(sizeof(struct Node));
[B]	strncpy(Temp->Name, Array1, sizeof(Temp->Name));
	strncpy(Temp->Phone, Array2, sizeof(Temp->Phone));

	if(Temp != NULL)[/B]
	{
                ...
        }
        ...
}

```
Here, unnecessary declarations and major problem with relying on Search() as principal means to delete a node.
```

void Delete(int A) //delete all or delete entry
{
	**//NOT NEEDED struct Node *Curr = Head;**

	if(Curr == NULL)
	{
		printf("There are no items in the list\n");
	}

	else
	{
		if(tolower(A) == 'l')
		{
			**while(Head != NULL)**
			{
                                **Node* Curr = Head;**
                                **Head = Head->Next;**
				free(Curr);
			}

			// NOT NEEDED Head = NULL;
		}

		else if(tolower(A) == 'i')
		{
			char Name[32];

			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);
[B]
                        // DON'T SEARCH MULTIPLE TIMES!  And besides,
                        // the code below will BREAK your linked list.
                        // You do not want this.
                        /*
			if((Search(Name)) != 0) //possibility - this condidtion is always false
			{
				Curr = Search(Name);
				free(Curr);
			}


			else if((Search(Name)) == 0)
			{
				printf("The item is not in the list\n");
			}
                        */[/B]
		}
	}
}

```

Search() can be simplified:
```

struct Node *Search(char Array1[])
{
	struct Node *Found = NULL;
	struct Node *Curr = Head;

	while(Curr != NULL && Found == NULL)
	{
[B]		if((strcasecmp(Curr->Name, Array1)) == 0)
		{
			Found = Curr;
		}[/B]

		Curr = Curr->Next;
	}

	return Found;
}

```
And lastly (see comments in the code that I have added):
```

void Print(int A) //print all or print entry - status: printing entire list is printing lifo
{
[B]	// Why this fascination with Curr at the beginning of each function??
        // struct Node *Curr = Head;

	//if(Curr == NULL)
        if (Head == NULL)[/B]
	{
		printf("There are no items in the list\n");
	}

	else
	{
		if(tolower(A) == 'l')
		{
                        **Node* Curr = Head;**

			while(Curr != NULL)
			{
				printf("Name: %s", Curr->Name);
				printf("Phone: %s", Curr->Phone);
				Curr = Curr->Next;
			}
		}

		else if(tolower(A) == 'i')
		{
			char Name[32];

			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);

[B]                        // Again, no need to call Search() multiple times.
                        /*
			if((Search(Name)) != 0)
			{
				Curr = Search(Name);
				printf("Name: %s", Curr->Name);
				printf("Phone: %s", Curr->Phone);
			}


			else if((Search(Name)) == 0)
			{
				printf("The item is not in the list\n");
			}
                        */

                        Node* Found = Search(Name);

                        if (Found)
                        {
				printf("Name: %s", Found->Name);
				printf("Phone: %s", Found->Phone)
                        }
                        else
                        {
				printf("The item is not in the list\n");
                        }

[/B]
		}
	}
}

```

---

### Post by ClientAlive on 2012-02-24
> **JKyleOKC said:**
> Again, very close. However, you don't want to call malloc again in delete. That would only ADD an entry, not delete it.

What you've missed in the delete() function is to fix the pointer so it no longer points to the instance you've given back. This is where the Prev pointer in a doubly linked list becomes so helpful. In the singly linked version, you have to remember the preceding instance's address during the search (with another global pointer named Prev, for example) just before moving to the next instance. That is, something like:```
Prev = Curr;
Curr = Curr->Next;
```Then in delete(), replace the "free(Curr)" call with this:```
Prev->Next = Curr->Next;
free(Curr);
Curr = Prev->Next;
```Now Curr will point to the entry that followed the one you deleted, or will be NULL indicating that nothing followed the deleted one. Test it by deleting from the middle of the list, from the front, and from the end. All three should work with no need for special code at either end.

And yes, you're definitely getting tired, and tired programmers overlook critical details. Much of the bad code that gets into "professional" programs got there during "death march" pushes. I once worked on a project that insisted on minimum 100-hour weeks. By the time it got cancelled, absolutely NO useful output was being generated!


It took me forever and a lot of trial and error. I eventually did implement something similar. It "Link()" fixes the borked link.


> **dwhitney67 said:**
> My additional $0.02:

Is it not a little too late to be checking if Temp is NULL?  You use Temp before you even check!
```

void Insert(char Array1[], char Array2[])
{
	struct Node *Temp = (struct Node *)malloc(sizeof(struct Node));
[B]	strncpy(Temp->Name, Array1, sizeof(Temp->Name));
	strncpy(Temp->Phone, Array2, sizeof(Temp->Phone));

	if(Temp != NULL)[/B]
	{
                ...
        }
        ...
}

```
Here, unnecessary declarations and major problem with relying on Search() as principal means to delete a node.
```

void Delete(int A) //delete all or delete entry
{
	**//NOT NEEDED struct Node *Curr = Head;**

	if(Curr == NULL)
	{
		printf("There are no items in the list\n");
	}

	else
	{
		if(tolower(A) == 'l')
		{
			**while(Head != NULL)**
			{
                                **Node* Curr = Head;**
                                **Head = Head->Next;**
				free(Curr);
			}

			// NOT NEEDED Head = NULL;
		}

		else if(tolower(A) == 'i')
		{
			char Name[32];

			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);
[B]
                        // DON'T SEARCH MULTIPLE TIMES!  And besides,
                        // the code below will BREAK your linked list.
                        // You do not want this.
                        /*
			if((Search(Name)) != 0) //possibility - this condidtion is always false
			{
				Curr = Search(Name);
				free(Curr);
			}


			else if((Search(Name)) == 0)
			{
				printf("The item is not in the list\n");
			}
                        */[/B]
		}
	}
}

```

Search() can be simplified:
```

struct Node *Search(char Array1[])
{
	struct Node *Found = NULL;
	struct Node *Curr = Head;

	while(Curr != NULL && Found == NULL)
	{
[B]		if((strcasecmp(Curr->Name, Array1)) == 0)
		{
			Found = Curr;
		}[/B]

		Curr = Curr->Next;
	}

	return Found;
}

```
And lastly (see comments in the code that I have added):
```

void Print(int A) //print all or print entry - status: printing entire list is printing lifo
{
[B]	// Why this fascination with Curr at the beginning of each function??
        // struct Node *Curr = Head;

	//if(Curr == NULL)
        if (Head == NULL)[/B]
	{
		printf("There are no items in the list\n");
	}

	else
	{
		if(tolower(A) == 'l')
		{
                        **Node* Curr = Head;**

			while(Curr != NULL)
			{
				printf("Name: %s", Curr->Name);
				printf("Phone: %s", Curr->Phone);
				Curr = Curr->Next;
			}
		}

		else if(tolower(A) == 'i')
		{
			char Name[32];

			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);

[B]                        // Again, no need to call Search() multiple times.
                        /*
			if((Search(Name)) != 0)
			{
				Curr = Search(Name);
				printf("Name: %s", Curr->Name);
				printf("Phone: %s", Curr->Phone);
			}


			else if((Search(Name)) == 0)
			{
				printf("The item is not in the list\n");
			}
                        */

                        Node* Found = Search(Name);

                        if (Found)
                        {
				printf("Name: %s", Found->Name);
				printf("Phone: %s", Found->Phone)
                        }
                        else
                        {
				printf("The item is not in the list\n");
                        }

[/B]
		}
	}
}

```


After noticing a couple things you show me here, I was able to cleam my code up a tiny bit (the way I was using fuction calls in my args and how convoluted I had it). I wasn't sure if I would have to declare "struct Node *Curr" globally in order to just make use of it in my function definitions (without declaring it over and over). For now I decided to stick with that part of it as it was. I'd like to experiment with it more in the future.

Anyhoo...

Here's what I came up with. As long as you play nicely with it it'll hold together.

Peace  :D


```

/*
Phone book program. Store names and phone numbers. Add and delete entries, print the
list or a single entry. Thanks for helping me learn. I'm so glad I have somewhere
to come  :)
*/

#include <ctype.h> //tolower()
#include <stdio.h> //fgets()
#include <stdlib.h> //malloc()
#include <string.h> //strncpy(), strcasecmp()

struct Node
{
char Name[32];
char Phone[18];
struct Node *Next;
};

struct Node *Head = NULL;

void Menu();
void Insert(char Array1[], char Array2[]);
void Delete(int A);
struct Node *Search(char Array1[]); //used internally
void Print(int A);

int main()
{
	int Selection = ' ';

	while(tolower(Selection) != 'q')
	{
		char Name[32];
		char Phone[18];

		Menu();

		printf("\nEnter your selection: ");
		Selection = getchar();
		getchar();

		if(tolower(Selection) != 'q')
		{
			int PrintSelect = ' ';
			int DeleteSelect = ' ';

			switch(tolower(Selection))
			{
				case 'a':
				{
					//Add an entry to the list

					printf("Enter a name...");
					printf("\n\n");
					fgets(Name, sizeof(Name), stdin);
					printf("Enter a phone number...");
					printf("\n\n");
					fgets(Phone, sizeof(Phone), stdin);

					Insert(Name, Phone);

					break;
				}

				case 'd':
				{
					//Delete an entry or delete the entire list

					printf("Would you like to delete [L]ist or [I]tem?\n");
					printf("\nEnter your selection: ");
					printf("\n");
					DeleteSelect = getchar();
					getchar();

					Delete(DeleteSelect);

					break;
				}

				case 'p':
				{
					//Print an entry of print the entire list

					printf("Would you like to print [L]ist or [I]tem?\n");
					printf("\nEnter your selection: ");
					printf("\n");
					PrintSelect = getchar();
					getchar();

					Print(PrintSelect);

					break;
				}
			}
		}
	}

	return 0;
} //end main

void Menu()
{
printf("Please select from the following...\n\n");
printf("[A]dd entry\n");
printf("[D]elete entry\n");
printf("[P]rint\n");
//printf("\n");
}

void Insert(char Array1[], char Array2[])
{
	struct Node *Temp = (struct Node *)malloc(sizeof(struct Node));

	if(Temp != NULL)
	{
		strncpy(Temp->Name, Array1, sizeof(Temp->Name));
		strncpy(Temp->Phone, Array2, sizeof(Temp->Phone));

		if(Head == NULL)
		{
			Head = Temp;
			Head->Next = NULL;
		}

		else
		{
			Temp->Next = Head;
			Head = Temp;
		}
	}
}

void Delete(int A) //delete all or delete entry
{
	struct Node *Curr = Head;
	struct Node *Link = Head;

	if(Curr == NULL)
	{
		printf("There are no items in the list\n");
	}

	else
	{
		if(tolower(A) == 'l')
		{
			while(Head != NULL)
			{
				Curr = Head;
				Head = Head->Next;
				free(Curr);
			}

			Head = NULL;
		}

		else if(tolower(A) == 'i')
		{
			char Name[32];

			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);

			if(Search(Name))
			{
				Curr = Search(Name);

					while(Link->Next != Curr)
					{
						Link = Link->Next;
					}

				Link->Next = Curr->Next;
				free(Curr);
			}

			else
			{
				printf("The item is not in the list\n");
			}
		}
	}
}

struct Node *Search(char Array1[])
{
	struct Node *Found = NULL;
	struct Node *Curr = Head;

	while(Curr != NULL && Found == NULL)
	{
		if(strcasecmp(Curr->Name, Array1)) //order of args?
		{
			Found = 0;
		}

		else
		{
			Found = Curr;
		}

		Curr = Curr->Next;
	}

	return Found;
}

void Print(int A) //print all or print entry - status: printing entire list is printing lifo
{
	struct Node *Curr = Head;

	if(Curr == NULL)
	{
		printf("\nThere are no items in the list\n");
	}

	else
	{
		if(tolower(A) == 'l')
		{
			while(Curr != NULL)
			{
				printf("Name: %s", Curr->Name);
				printf("Phone: %s", Curr->Phone);
				Curr = Curr->Next;
				printf("\n");
			}

			printf("\n");
		}

		else if(tolower(A) == 'i')
		{
			char Name[32];

			printf("Enter a name...\n");
			fgets(Name, sizeof(Name), stdin);

			if(Search(Name))
			{
				Curr = Search(Name);
				printf("Name: %s", Curr->Name);
				printf("Phone: %s", Curr->Phone);
				printf("\n");
			}


			else
			{
				printf("\nThe item is not in the list\n");
			}
		}
	}
}


```

---

### Post by JKyleOKC on 2012-02-25
This whole thread got me re-interested in how to protect against buffer overruns and avoid having the excess input show up unexpectedly later; my solution was to re-invent the wheel in the form of the following function and test program:```
#include <stdio.h>

char tmp[10];

void get_input(char *str, size_t sz){
    int c, i;

    for (i = 0; 1; i++){	// loop forever
	c = getchar();		// get one char from stdin
	if (c == '\n'){		// if it's newline...
	    if (i < sz) str[i] = '\0';	// store EOL
	    else str[sz-1] = '\0';
	    break;		// and get out
	}
	if (i < sz)		// otherwise if still in buffer
	    str[i] = c;		// store it and loop for more
    }
}

int main(){
    while (1) {
	if (tmp[0] == 'q') break;
	puts("input stuff--");
    	get_input(tmp, sizeof(tmp));
    	puts(tmp);
    }
    return 0;
}
```It's pretty straightforward, using the single-character input function to remove each character in turn from the stdin stream, but not storing them once the buffer is full. It takes advantage of the fact that an array's name is identical to a string pointer to that array, so it uses the pointer as an array, successfully. It also does not bother to typecast the incoming character variable "c" from "int" to "char" but neither of these tricks triggers a warning from the compiler.

Hopefully this can be useful in future assignments...and congratulations, jake, on making the breakthrough and moving ahead!

---

### Post by Bachstelze on 2012-02-25
You assume that the "excess input" is not useful and may just be discarded. That's... not a good assumption at all. Your code is only useful to guard against incompetent or malicious users that just enter gibberish at a prompt. In most cases, however, you just don't know in advance how large input is, and since you still have to allocate a buffer, the input may be too large for it, but that doesn't mean you can just discard everything that doesn't fit.

---

### Post by JKyleOKC on 2012-02-25
It all depends on the specific needs of the program. Consider a data entry routine that provides a 30-character buffer for "Name" followed by a 15-character buffer for "Phone" with the two loaded from fgets() calls with size limits of 30 and 15 respectively.

Now along comes a clerk who types in the customer's name, "Wilberforce Q. Abercrombie-Fitch" at the first prompt, intending to put the phone number at the second. However, the "Name" buffer gets only the first 30 characters of that name, and the phone buffer gets "ch" without waiting for more input.

I wouldn't call that either incompetent or malicious on the part of the clerk. Of course proper input verification on the phone number would throw an error since "ch" isn't valid for that field, but it's nice to have a way to prevent the situation; discarding the two excess characters is one way to do so. Seems to me that the system assumption of "overflow is intended and should be returned for the next call" is equally invalid...

Perhaps a better solution would be to always bring keyboard input into a max-sized buffer (apparently 4095 characters currently) and then either discard or save overflow, as desired. That would also allow better validation of all input, and when programming for SQL is almost a necessity to prevent injection. However at the entry level with which this thread has been dealing, that's a bit of overkill!

Thanks for bringing up the point, though. It's good to remember that there's never a "one size fits all" solution to any programming problem.

---

### Post by Bachstelze on 2012-02-25
> **JKyleOKC said:**
> Seems to me that the system assumption of "overflow is intended and should be returned for the next call" is equally invalid...


No, it is not. ;) A lot more programs read arbitrary data on their standard input (sed, awk, grep, you name it) than use prompts. Clearly, you don't want grep to just read the first sizeof(buf) characters and discard the rest.

*EDIT:* This is probably why prompts are such a pain in C, that's just not what it was made for. It was made for writing programs like sed and awk and grep.

---

### Post by ofnuts on 2012-02-25
> **JKyleOKC said:**
> It all depends on the specific needs of the program. Consider a data entry routine that provides a 30-character buffer for "Name" followed by a 15-character buffer for "Phone" with the two loaded from fgets() calls with size limits of 30 and 15 respectively.

Now along comes a clerk who types in the customer's name, "Wilberforce Q. Abercrombie-Fitch" at the first prompt, intending to put the phone number at the second. However, the "Name" buffer gets only the first 30 characters of that name, and the phone buffer gets "ch" without waiting for more input.

I wouldn't call that either incompetent or malicious on the part of the clerk. Of course proper input verification on the phone number would throw an error since "ch" isn't valid for that field, 
You can tell you overflowed the first line because you didn't get  a LF at the end... No need to read the second one.

---

### Post by JKyleOKC on 2012-02-26
> **ofnuts said:**
> You can tell you overflowed the first line because you didn't get  a LF at the end... No need to read the second one.My point is that the call intended to read the phone number, gets the overflow instead.

Sure, it would be possible to detect absence of the "\n" on the initial read, then perform a second read to clear the stream buffer -- but that adds complexity to the program.

The whole idea behind free (as in libre) software is to allow choices. My intent was to provide an option for keyboard input that would allow one to choose to ignore overflow in the first place, rather than adding complexity to detect it and throw it away, since the standard libraries appear to deny users that choice. Apparently a few folk believe that some choices are more free than others. Guess I had better shut up and quit posting to this thread...

---

### Post by Bachstelze on 2012-02-26
> **JKyleOKC said:**
> 
The whole idea behind free (as in libre) software is to allow choices. My intent was to provide an option for keyboard input that would allow one to choose to ignore overflow in the first place, rather than adding complexity to detect it and throw it away, since the standard libraries appear to deny users that choice. Apparently a few folk believe that some choices are more free than others. Guess I had better shut up and quit posting to this thread...

I guess so too, because you're just spouting nonsense now. What does "free" have to do with anything?

---

### Post by ClientAlive on 2012-02-26
> **JKyleOKC said:**
> This whole thread got me re-interested in how to protect against buffer overruns and avoid having the excess input show up unexpectedly later; my solution was to re-invent the wheel in the form of the following function and test program:```
#include <stdio.h>

char tmp[10];

void get_input(char *str, size_t sz){
    int c, i;

    for (i = 0; 1; i++){	// loop forever
	c = getchar();		// get one char from stdin
	if (c == '\n'){		// if it's newline...
	    if (i < sz) str[i] = '\0';	// store EOL
	    else str[sz-1] = '\0';
	    break;		// and get out
	}
	if (i < sz)		// otherwise if still in buffer
	    str[i] = c;		// store it and loop for more
    }
}

int main(){
    while (1) {
	if (tmp[0] == 'q') break;
	puts("input stuff--");
    	get_input(tmp, sizeof(tmp));
    	puts(tmp);
    }
    return 0;
}
```It's pretty straightforward, using the single-character input function to remove each character in turn from the stdin stream, but not storing them once the buffer is full. It takes advantage of the fact that an array's name is identical to a string pointer to that array, so it uses the pointer as an array, successfully. It also does not bother to typecast the incoming character variable "c" from "int" to "char" but neither of these tricks triggers a warning from the compiler.

Hopefully this can be useful in future assignments...and congratulations, jake, on making the breakthrough and moving ahead!


Thanks Kyle. It's been interesting.  ;)


> **Bachstelze said:**
> You assume that the "excess input" is not useful and may just be discarded. That's... not a good assumption at all. Your code is only useful to guard against incompetent or malicious users that just enter gibberish at a prompt. In most cases, however, you just don't know in advance how large input is, and since you still have to allocate a buffer, the input may be too large for it, but that doesn't mean you can just discard everything that doesn't fit.


I don't know why seeing this reminded me of this. Maybe this is entirely off base to what's being talked about but I learned once that you can make and array that gets sized based on user input during runtime. Maybe if the user is required to specify the size of their input it creates a scenario condusive to this sort of thing?

```

#include <stdio.h>

//Some function that clears everything after the specified size

int main()
{
int Array[SizeOfArray];

printf("Enter the size of your input\n");
SizeOfArray = getchar();

//call the function

return 0;
}

```

---

