---
title: "An odd bug, probably due to my inexperience with pointers - C"
date: 2008-09-03
forum: Programming Talk
---

### Post by Yes on 2008-09-03
I'm making a text based clone of the game Nibbles (example here: [http://www.gamesgnome.com/action/topnibbles/](http://www.gamesgnome.com/action/topnibbles/)).  The problem I'm working on now (heh, it has lots of problems) is that sometimes when I try turning, the first joint keeps turns, but the rest of them just keep moving in the old direction.  The way I manage turning is this - when the user hits a key, the direction variable in the first joint (each joint is a struct) is changed, and it's x and y coordinates are put into two different arrays, and it's new direction in a third array.  Before each move, I check (through a recursive method) if each joint has gotten to the "pivot" point, and if it has, I change it's direction to the corresponding direction.  If the joint "pivoting" is the last joint, the pivot coordinates are set to -1.  Here's the code:

```
#include <stdlib.h>
#include <ncurses.h>

struct nibbler {
	int direction, x, y;
	bool hasNext, skipMove;
	struct nibbler *nextNibbler;		
};

bool checkBoundries (struct nibbler *);
void moveNibbler (struct nibbler *);
void pivot (struct nibbler *, int *[], int *[], int *[]);
void printNibbler (struct nibbler *);
void addNibbler (struct nibbler *);
bool checkCollision (struct nibbler *, struct nibbler *);

int main(int argc, char** argv)
{
	
	int targetX, targetY, key, score; //direction - 1 == left, 2 == up, 3 == right, 4 == down
	
	int pivotZ [10];
	int pivotX [10];
	int pivotY [10];
	int pivotDir [10];
	int pivotNum, i;
	
	struct nibbler *firstNibbler;
	
	initscr ();
	curs_set (0);
	keypad (stdscr, TRUE);
	halfdelay (3);
	
	srand (time(NULL));
	targetX = (rand()%COLS-1) + 1;
	targetY = (rand()%LINES-1) + 1;
	firstNibbler = malloc (sizeof (struct nibbler));
	firstNibbler->x = COLS/2;
	firstNibbler->y = LINES/2;
	firstNibbler->direction = -1;
	firstNibbler->hasNext = FALSE;
	firstNibbler->skipMove = FALSE;
	
	score = 0;
	pivotNum = -1;
	
	for (i = 0; i < 10; i++) {
		pivotY[i] = -1;
		pivotX[i] = -1;
		pivotDir[i] = -1;
	}
	
	while (1) {
	
		key = getch ();
		if (key == 'q') {
			clrtoeol ();
			endwin ();
			exit (0);
		}
		
		else if (key == KEY_UP) 
			firstNibbler->direction = 2;
		else if (key == KEY_DOWN) 
			firstNibbler->direction = 4;
		else if (key == KEY_LEFT) 
			firstNibbler->direction = 1;
		else if (key == KEY_RIGHT) 
			firstNibbler->direction = 3;
		
		
		if (key == KEY_UP || key == KEY_DOWN || key == KEY_LEFT || key == KEY_RIGHT) {
			pivotNum++;
			pivotX [pivotNum] = firstNibbler->x;
			pivotY [pivotNum] = firstNibbler->y;
			pivotDir [pivotNum] = firstNibbler->direction;
		}
		
		pivot (firstNibbler, &pivotX, &pivotY, &pivotDir);
		moveNibbler (firstNibbler);
		
		if (firstNibbler->hasNext) {
			if (checkCollision (firstNibbler, firstNibbler->nextNibbler) || checkBoundries (firstNibbler)) {
				mvprintw ((LINES-9)/2, COLS/2, "Game Over");
				refresh ();
				system ("sleep 2"); //BAD!!!
				clrtoeol ();
				endwin ();
				exit (0);
			}
		}
		
		if (firstNibbler->x == targetX && firstNibbler->y == targetY) {
			score++;
			mvprintw (targetY, targetX, " ");
			srand (time(NULL));
			targetX = (rand()%COLS) + 1;
			targetY = (rand()%LINES) + 1;
			addNibbler (firstNibbler);
		}
		
		//mvprintw (1, 1, "targetY: %d targetX: %d", targetY, targetX);
		mvprintw (targetY, targetX, "#");
		
		printNibbler (firstNibbler);
			
		mvprintw (LINES-1, (COLS-8)/2, "Score: %d", score);
		
		//mvprintw (5, 1, "targetY: %d targetX: %d playerX: %d playerY: %d", targetY, targetX, playerX, playerY);
		
		refresh ();
			
	}
	
	return 0;
}

bool checkBoundries (struct nibbler *node) {
	if (node == NULL)
		return FALSE;
	else if (node->x < 0 || node->x > COLS-1 || node->y < 0 || node->y > LINES-1)
		return TRUE;
	else if (node->hasNext == TRUE)
		checkBoundries (node->nextNibbler);
	else 
		return FALSE;
}

void moveNibbler (struct nibbler *node) {
	
	if (node == NULL)
		return;
	if (node->skipMove) {
		node->skipMove = FALSE;
		return;
	}
	
	mvprintw (node->y, node->x, " ");
	
	switch (node->direction) {
		case 1: //left
			node->x--;
			break;
		case 2: //up
			node->y--;
			break;
		case 3: //right
			node->x++;
			break;
		case 4: //down
			node->y++;
			break;
		default:
			break;
	}
	
	if (node->hasNext)
		moveNibbler (node->nextNibbler);
	else
		return;
}

void pivot (struct nibbler *node, int *pivotX[], int *pivotY[], int *pivotDir[]) {
	if (node == NULL)
		return;
	int i;
	for (i = 0; i<10; i++) {
		if (node->x == pivotX[i] && node->y == pivotY[i]) {
			node->direction = pivotDir[i];
			if (!node->hasNext) {
				pivotX[i] = -1;
				pivotY[i] = -1;
				pivotDir[i] = -1;
			}		
			break;
		}
	}
	
	if (node->hasNext) 
		pivot (node->nextNibbler, pivotX, pivotY, pivotDir);
	else 
		return;
}
			
void printNibbler (struct nibbler *node) {
	if (node == NULL)
		return;
		
	mvprintw (node->y, node->x, "@");
	
	if (node->hasNext)
		printNibbler (node->nextNibbler);
	else
		return;
}

void addNibbler (struct nibbler *node) {
	if (node->hasNext)
		addNibbler (node->nextNibbler);
	else {
		struct nibbler *newNibbler = malloc (sizeof (struct nibbler));
		node->hasNext = TRUE;
		node->nextNibbler = newNibbler;
		newNibbler->hasNext = false;
		newNibbler->x = node->x;
		newNibbler->y = node->y;
		newNibbler->direction = node->direction;
		newNibbler->skipMove = TRUE;
	}		
}


bool checkCollision (struct nibbler *firstNibbler, struct nibbler *node) {
	if (firstNibbler->x == node->x && firstNibbler->y == node->y)
		return TRUE;
	else if (node->hasNext)
		checkCollision (firstNibbler, node->nextNibbler);
	else
		return FALSE;
}
```

Does anyone have any idea what's going on?  I'm a little new to the concept of pointers so I thought it might be something to do with that, but I really have no idea.  Thanks!

---

### Post by theDaveTheRave on 2008-12-16
Dear YES

I notice that you haven't had any replies? did you sort out your problem, did you find it was a pointer issue??

I only ask because I am suffering from serious headaches regarding pointers!

I initially learnt Java, but I'm doing a Msc and it includes various "programming" stuff, and it is in C - so it's pointers everywhere, and it's not something they have in Java.

I did manage to get my head around very simple pointers (eg a pointer to a set of numbers), and decided that they behaved in a way not too dissimilar to an array variable in Java, enabling me to retrieve the character at any point in the variable.

But I am stil suffering from serious brain ache when it comes to pointers to Structs (which for me are like a java class - and oddly enough is how I write them! - along with the varous getter and setter methods for the struct variables).

Anyway did you ever find a good explanation of them? As I think I'm going to need to really understand them for my Msc.

cheers for the advice.


David

---

### Post by PandaGoat on 2008-12-16
Just think of a program as having its own special place in the computer's memory to store its own memory (its address space).  Moreover, think of this address space as a table of values.  Each value is one byte (in C, a byte is a char).  

Let me force the first question into your mind to be "but how do we access a value in this table?!"  Well each value has a location in the table (obviously).  Each location is referenced by a 4 byte hexadecimal number.  This hexadecimal number is, indeed, called the reference, which you have probably heard of.  


```

PAUSE:
Now, obviously each variable has its own place in the address space and this is the tricky part with C.  
C does not actually deal with references like C++ or something.  
&variable returns a pointer to the 4 byte hexadecimal location not really the actual number.  
But you can actually get this number.  
To be explicit, you do this to store it: long loc = (long)&some_variable.

```

Anyway, you access the value at a location using a pointer that points to the location.  A pointer is declared using the *: int* s;.  Now, quick, what does this pointer point to?  Correct, nothing;  it is a null pointer.  Lets say you wanted it to point to some value, int i = 5;, you would do int* s = &i;  Now when you modify the value that s points to, you modify the value of i.  Now you ask, "how do you modify the value that a pointer points to?"  You would dereference s, again, using *: *s = 1; changes the value that s points to.  Quick, does this change the value of i?  Correct, yes it does!  We changed **only** the value that s points to--which **is** i.

A pointer can be incremented to point to the next value in the table or decremented to point to the previous value.  To do this you just add numbers to the pointer: s+1, s++, s+4, etc. In this way it is an array.  Doing int i[50]; is pretty much the same as int* i = (int)malloc(sizeof(int));.  The only difference is where the memory is allocated.  But anyway, *i is the first indec, *(i+1) is the second, etc.  The [] operator just abstracts dereferencing.

Pointers are the same for structs as the examples showed.  But more importantly, think of a struct as an array of bytes that represents the variables you declared in the same order as you declared them.  In fact you can convert a struct into a char*.  Structs are just an abstract way to make a structure (lists) of variables and handle them easily.


Anyway, sorry I do not know the OPs problem, and to be honest, this post was out of boredom.  I could be wrong on some things, but hopefully someone will correct me or expand on this to help you.

Peace, ):P

---

### Post by Kazade on 2008-12-16
> **theDaveTheRave said:**
> Dear YES
I only ask because I am suffering from serious headaches regarding pointers!


I'll see if I can help with an analogy...

Imagine a street of houses, one of these houses contains something that you want, but all you have is a house number.

If you imagine the pointer as a house number. Then you can think of the member-by operator ( -> ) as the act of walking to the house that the house number points to.

If you have an object on the stack, or a reference. Then it is like actually being at the house so you just use the "." operator coz you don't have to get there ;)

If you always remember that a pointer is just a number which stores an address it will all make sense quite quickly.

> 
I did manage to get my head around very simple pointers (eg a pointer to a set of numbers), and decided that they behaved in a way not too dissimilar to an array variable in Java, enabling me to retrieve the character at any point in the variable.


Hmm, OK be careful here. A pointer doesn't always point to an array of data, some pointers do, but some just point to a single object instance.

> 
But I am stil suffering from serious brain ache when it comes to pointers to Structs (which for me are like a java class - and oddly enough is how I write them! - along with the varous getter and setter methods for the struct variables).


This is my argument against Java being taught as a sole first language. Don't(!) think of C++ like Java, don't try and compare them you'll just confuse yourself more. OK, firstly don't ever write a getter or setter for a struct. It's totally against what "struct"s are for...

A struct is like a class whose members are implicitly public (as opposed to classes which are implicitly private). They are designed specifically to hold combined state. For example, you might have a struct for a 3D point in space:
```

struct Vertex {
 float x, y, z;
};

```

You might chose a struct in this situation because you don't need to keep any invariants here or anything. You are just using it as a new base type which combines 3 floating point elements. Anyway, someone could just circumvent your getter/setter by accessing the elements directly.

It only makes sense to write a getter/setter in a class where the data is private. And in this case please do, getters and setters provide a single point of access to your members so getters and setters are a good idea. Just not with structs.

Regarding your pointer to struct problem, just think of the address thing. Here's some code using the Vertex structure above that might help:

```

Vertex myVertex; //Create a vertex on the STACK

Vertex* vertexPtr = &myVertex; 
//Create a pointer to vertex using the "address-of" operator(&). 
//Think back to the house analogy, this is the same as 
//getting the house number from the house

float x = vertexPtr->x; //Go to the address, pull out the x member
float y = myVertex.y; //myVertex is the object directly, so no member-by operator ( -> )

//This one uses the dereference operator to get the instance
//from the pointer first, then accesses the x member
float z = (*vertexPtr).x;

//Allocate memory for a vertex on the HEAP and store the address to it!
Vertex* heapVertex = new Vertex();
//heapVertex behaves like vertexPtr from now on.

int myarray[10]; //Create an array on the stack
int* array = myarray;  //This line does the same as
array = &myarray[0]; //this one.

```

Notice that in the case of the array there is no need to use the address-of operator. An array variable acts like a pointer, however, the last line gets the address of the first element in the array.

Anyway I hope that helps.

---

### Post by theDaveTheRave on 2008-12-16
I hate to say this... it didn't help!


Why would you even want to bother doing

```


Vertex myVertex; //Create a vertex on the STACK
Vertex* vertexPtr = &myVertex; 

```

when doing this

```


Vertex* heapVertex = new Vertex();
//heapVertex behaves like vertexPtr from now on.


```

is essentially the same thing? and in my mind seems "easier" than having to mess about with the pointer?

But I have learnt that the pointers are an essential part of C (and part of its "power" apparently :confused: ? ).

I have tried to "not think of it like java"

but we had to write some stuff for Uni the other day during the class.

I got home and did the same thing in Java in half the time, and it worked, straight off the bat (OK only sort of, but I could debug it and extend it as I pleased) - it made me feel less of a complete twit.

I do get the "abstract idea" of pointers, it is retrieving the data that they point to that realy gets me.

If I create a variable (let say like your heap vertex), I then have to create a pointer to it? 

Using your house analagy, in my mind it is like saying I know where I need to get to, but I have to visit another house first to get the keys, and that first house doesn't have to be anywhere near where my final destiation is, surely that must be expensive in processor terms "go here to find out how to go there"

I'm not sure if I'm just managing to talk myself around in circles (which seems to be the effect of a pointer!), I read somewhere

... a pointer is a variable is a pointer... which didn't really seem very helpfull, a bit like a friend of mine who use to insist I should take the 3rd right when I was on a roundabout with 7 exits and my response would be "there are no right hand turns on a round about they are all on the left!" (for thos of us in the UK any how).

I will get around to playing with this over christmas, and if I get it straight somehow I'll drop a post on here somewhere just to make sure I have understood properly?

thanks for the time and effort so far.

David

---

### Post by Kazade on 2008-12-16
OK. There is actually a big difference between:

```

Vertex* myVertex = new Vertex();

```

and 
```

Vertex myVertex;

```

The first version allocates an instance of a Vertex on the heap. The call to new returns a pointer to the memory where that Vertex was created and then it is assigned to the myVertex pointer. You have to manually delete the memory allocated by a call to new. The other version creates the object on the stack and is destroyed automatically when it goes out of scope. My example:

```

Vertex* vertexPtr = &myVertex;

```

was simply to show you how to get a pointer to the variable that was on the stack. I can see how this might confuse you a bit coz Java makes this odd differentiation been base types and classes to determine whether or not something needs "new". 

C++ is a lot more difficult to learn than Java because it requires a more low level understanding of what is actually going on, but once you grasp it - it will really help you in other languages too.

---

### Post by theDaveTheRave on 2008-12-17
Hello again.

I have been reading a few things on the Net as to why pointers are uesfull.

It seems as though the idea was created to get around a variety of problems (principly being the lack of 'array' structures). I know understand why they are in use, but it is going to take a while for the penny to drop on this one... I guess it will eventually!

I do realise that there are some interesting things about how computers function and that c is much closer to this than Java. Hence the concentration on using c and understanding machine language.

I just keep going around in circles on pointers though.

I'm sure if I keep plugging away at it I'll get there, hopefully over christmas.

David

---

### Post by dribeas on 2008-12-17
I have just briefly skipped through the post and answers. One of the things that just popped to mind is the following phrase:

> 
I have tried to "not think of it like java"


To me it is just the opposite: do try to think of it like in Java. While you will hear and read that Java has no pointers, what it lacks (whether defect or feature) is pointer arithmetic.

Java references are just plain pointers. Now, the differences in Java/C# with C/C++ are related to memory management and pointer arithmetic. Think of pointers as references and just consider those two differences.

In managed languages (duh) like C#/Java, you request memory with new and the memory is automatically released sometime after the last reference/pointer is lost. In C/C++ the programmer is responsible for releasing the memory allocated with new.

The second difference is pointer arithmetic, which is disallowed in managed languages. The idea with pointer arithmetic is that if you have a number of elements of a given type that sit together in a region of memory (an array for example), once you know the reference/pointer to one of the elements you can move to the next element by incrementing the pointer. Initially the pointer refers to element X, after incrementing it, the pointer will refer to the element that sits in memory just after X.

That is, once you have a pointer into the first element of the array, the second element can be accessed through the pointer (ptr+1). Basic arithmetic can be performed with pointers: incrementing/decrementing/addition/substraction with that semantic. It is important to note that the system will not check whether the operation you performed makes sense or not. If you decrement a pointer to the first element in a container you will get a pointer to nowhere.

---

