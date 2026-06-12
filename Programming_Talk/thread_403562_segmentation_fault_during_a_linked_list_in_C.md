---
title: "segmentation fault during a linked list in C"
date: 2007-04-07
forum: Programming Talk
---

### Post by dave_567 on 2007-04-07
I'm having trouble with a linked list in C.    The program reads a list of names and makes two linked lists out of the data,  The program compiles, links, and runs but I keep getting a segmentation fault error at run tiime.  I think it is from the function walkNode.     

What am I missing?  :confused:  

```


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <memory.h>

struct link
{
	struct link *next;
	char word[25];
	int numTimesAppear;
};

typedef struct link Link;

int CreateAllNodes(Link *, Link *, int *, int *);
void WalkNode(Link *);
int DestroyAllNodes(Link *);
void Compare();

int main(int argc, char *argv[])
{
	
	struct link *Dhead = NULL;
	struct link *Compare;
	struct link *Ahead = NULL;
	int Atotal = 0;
	int Dtotal = 0;
	int total;
		
	//call function to creat linked list nodes	
	total = CreateAllNodes(Dhead, Ahead, &Atotal, &Dtotal);

	printf("\nAtotal is: %d", Atotal);
	printf("\nDtotal is: %d", Dtotal);
	printf("\ntotal is: %d\n", total);

	WalkNode(Dhead);

	//Sort lists alphabetically using compare call
	//Compare();

	//Delete lists using DestroyAllNodes call; call twice, once for each list
	DestroyAllNodes(Dhead);
	DestroyAllNodes(Ahead);

	return 0;
}

int CreateAllNodes(Link *Dhead, Link *Ahead, int *pAtotal, int *pDtotal)
{
	int total = 0;
	int x, y, z;   
	char NameBuffer[50];
	char WordBuffer[25]; 
	char a, b, c;
	long iEndFile, iFSize, iBegFile;
	Link *DnewNode = NULL;
	Link *DtmpNode = NULL;
	Link *AnewNode = NULL;
	Link *AtmpNode = NULL;
	Link *tmpNodePtr = NULL;
	FILE *MyFile; 
	iFSize = 0;
	
	//request what file to open 
	printf("What File would you like to open?");
	scanf("%s", NameBuffer );

	//check for file, open file 
	if ((MyFile = fopen( NameBuffer, "r+")) == NULL)
	{
		printf ("\ncould not open the file '%s'\n", NameBuffer);
		printf ("I have failed you...  I'm sorry.\n\n");
		return 0;
	}

	//get file size
	fseek(MyFile, 0L, SEEK_END);
	iEndFile = ftell(MyFile);  // the end of the file is the size of the file
	iFSize = iEndFile;
	rewind(MyFile);

	//read file
	while (ftell(MyFile) < iEndFile)
	{
		//read data from file 
		fscanf (MyFile,"%s",WordBuffer);
		printf("Loading nodes %d\n", ftell(MyFile));

		//load nodes
		//Compare characters to load in proper node using an if-else statement 
		if (WordBuffer[0] == 'd' || WordBuffer[0] == 'D')
		{
			if (*pDtotal == 0)
			{
				//create head node
				Dhead = (Link *)malloc(sizeof(Link));
				memcpy(Dhead->word, WordBuffer,25);
				Dhead->numTimesAppear = 0;
				Dhead->next = NULL;
			}
			else
			{
				//create nodes following head node
				DnewNode = (Link *)malloc(sizeof(Link));
				memcpy(DnewNode->word, WordBuffer,25);
				DnewNode->numTimesAppear = 0;
				DnewNode->next = (Link *) Dhead;
				Dhead = DnewNode;
			}
			*pDtotal = *pDtotal + 1;
		}
		else
		{
			*pAtotal = *pAtotal + 1;
		}
				
	}		
	total = *pAtotal + *pDtotal;
	printf("\nAtotal function is: %d", *pDtotal);
	printf("\nDtotal function is: %d", *pAtotal);
	printf("\ntotal function is: %d", total);

	fclose(MyFile);
	return total;
}

void WalkNode(Link *headNode)
{
	Link *currentNode = headNode;

	printf("\n%d == zero\n", headNode->numTimesAppear); /* what is going on here??? */

	//loop through nodes and print out the info
	while (currentNode->next != NULL)
	{
		printf("\n%s, %d", (char*)headNode->word, headNode->numTimesAppear);
		currentNode = (Link *)currentNode->next;
	}
	
	//testing to make sure I am out of the loop
	printf("\nOut of the loop now.\n");
}

void compare()
{
	printf("I am able to compare two words\n");
}

int DestroyAllNodes(Link *headNode)
{
	Link *currentNode; 
	currentNode = headNode;
	Link *tmpNodePtr = NULL;
	
	while (currentNode->next != NULL)
	{
		//Delete the nodes
		tmpNodePtr = (Link *)currentNode->next;
		free(currentNode);
		currentNode = tmpNodePtr;
	}
	
	return 0;
}


```

---

### Post by Mordred on 2007-04-07
I suggest you use a debugger to step through the program.

I have already used ddd (available in apt) and visual studio (not available in apt) :p
KDevelop has a debugger too.

A segmentation fault means you have tried to access memory that is not yours.
Most probably you try to access a nullpointer or a pointer you have already freed.

---

### Post by WW on 2007-04-07
I think the problem is that after this line
```

	total = CreateAllNodes(Dhead, Ahead, &Atotal, &Dtotal);

```
Dhead and Ahead are still both NULL.  C passes arguments using "call by value", so unless you pass *pointers to* Dhead and Ahead, they will not be changed when the function returns.

Then, when you call WalkNode(Dhead), you get a segfault, because WalkNode doesn't check if its argument is NULL.

By the way, something looks fishy in the WalkNode function.  In the printf statement in the while loop, shouldn't that be currentNode, not headNode?  It looks like this function is just printing the contents of the linked list.  I would expect something more like this:
```

void WalkNode(Link *headNode)
{
	Link *currentNode = headNode;

	//loop through nodes and print out the info
	while (currentNode != NULL)
	{
		printf("\n%s, %d", (char*)currentNode->word, currentNode->numTimesAppear);
		currentNode = (Link *)currentNode->next;
	}
}

```
(I removed the mysterious first printf statement.)  But maybe the first entry in your linked list is somehow "special", and shouldn't be printed the same as the others?

---

### Post by Compyx on 2007-04-09
In addition to the post above, you should get into the habit of using some of GCC's very useful warnings, as the bare minimum, I always compile with:
```
-g -Wall -Wextra -ansi -pedantic -O3
```
Change '-ansi' to '-std=c99' if you're using C99. (-ansi chokes on // comments, as it should)

But in any serious project I always use this in my makefiles:
```
CFLAGS = -Wall -Wextra -Wundef -Wshadow -Wpointer-arith -Wbad-function-cast \
         -Wcast-qual -Wcast-align -Wwrite-strings -Wconversion \
         -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations \
         -Wpadded -Wredundant-decls -Wunreachable-code -Wformat-nonliteral \
         -Wnested-externs -g -pedantic -ansi -O3

```

Also don't cast the return value of malloc(), this can mask errors, such as not having #include'd <stdlib.h>, by putting a cast in front of malloc() you prevent the compiler from warning you about missing prototypes. 

This for example:
```
DnewNode = (Link *)malloc(sizeof(Link));
```
can be written as:
```
DnewNode = malloc(sizeof *DnewNode);
```
This will allow gcc to warn you about missing <stdio.h> and also allows you to change the type of DnewNode without having to worry about changing the argument of malloc().


Another thing I always use is 'valgrind', a very handy tool that can track al sorts of errors when dealing with memory (especially when using malloc and friends). Using valgrind I immediately saw you were dereferencing a NULL-pointer in the printf statement of WalkNode.


Sorry if I sound a bit pedantic, but these sort of things will make your life a lot easier when coding. :)

---

### Post by dave_567 on 2007-04-16
Thanks for all the help. :popcorn:   

This is the final source and it works!  :D 

```


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <memory.h>

typedef struct link
{
	struct link *next;
	char word[24];
	int numTimesAppear;
}Link;


int CreateAllNodes(Link **, Link **);
void WalkNode(Link *);
int DestroyAllNodes(Link *);
int AddToList(Link **pTheHead, char *Word);


/*
This program is designed to read in a file, and sort the data into
two linked lists aplhabetically and display it a screen at a time.

LEGAND FOR MAIN

Dhead	pointer	to struct
Ahead	pointer to struct
*/

int main(int argc, char *argv[])
{
	
	Link *Dhead = NULL;  // caps on struct and deleted struct key word
	Link *Ahead = NULL;
		
	//call function to creat linked list nodes	
	CreateAllNodes(&Dhead, &Ahead);   // used the &

	
	WalkNode(Ahead);
	WalkNode(Dhead);
	

	//Delete lists using DestroyAllNodes call; call twice, once for each list
	DestroyAllNodes(Ahead);
	DestroyAllNodes(Dhead);

	printf("\n\tdone with the program\n\n");

	return 0;
}
/*
This function reads in the file and determines which link list the word should be 
added to based on the beginning letter

LEGAND FOR CREATEALLNODES

NameBuffer	char array
WordBuffer	char array
myFile		File name
Dhead		Dhead in main 
Ahead		Ahead in main 
*/

int CreateAllNodes(Link **Dhead, Link **Ahead)
{
	char NameBuffer[50];
	char WordBuffer[24]; 
	long iEndFile, iFSize;
	FILE *MyFile; 

	
	//request what file to open 
	printf("What File would you like to open?");
	scanf("%s", NameBuffer );
	getchar();

	//check for file, open file 
	if ((MyFile = fopen( NameBuffer, "r+")) == NULL)
	{
    printf ("\ncould not open the file '%s'\n", NameBuffer);
		printf ("I have failed you...  I'm sorry.\n\n");
		return 0;
	}

	//get file size
	fseek(MyFile, 0L, SEEK_END);
	iEndFile = ftell(MyFile);  // the end of the file is the size of the file
	iFSize = iEndFile;
	rewind(MyFile);

	//read file
	while (ftell(MyFile) < iEndFile)
	{
		//read data from file 
		fscanf (MyFile,"%s",WordBuffer);
		
		//load nodes
		//Compare characters to load in proper node using an if-else statement 
		if (WordBuffer[0] == 'd' || WordBuffer[0] == 'D')
		{
			AddToList(Dhead, WordBuffer);
		}
		else
		{
			AddToList(Ahead, WordBuffer);
		}
				
	}		
	
	fclose(MyFile);
	return 1;
}
/*
This function is designed to walk along the nodes and output the data as it is stored
in the link list.  It prints the data to the screen a screen size at a time (assuming 
screen size to be 20 lines)

LEGAND FOR WALKNODES

headNode		Ahead or Dhead in main
currentNode		equal to headNode
lines			int
*/

void WalkNode(Link *headNode)
{
	Link *currentNode = headNode;
	int lines = 0;

	//loop through nodes and print out the info
	while (currentNode != NULL)
	{
		printf("%-24s %5d\n", currentNode->word, currentNode->numTimesAppear);
		lines++;
		if (lines %20 == 19)
		{
      			printf("Press enter for more data\n");
			getchar();
		}
		currentNode = (Link *)currentNode->next;
	}
	
	//testing to make sure I am out of the loop
	printf("\nEnd of list. Press Enter\n");
	getchar();
}
/*
This function deletes all the nodes at the conclusion of the program 

LEGAND FOR DESTROYALLNODES

headNode		Ahead or Dhead in main 
CurrentNode		pointer to head node
tmpNodePtr		temporary pointer for nodes
*/
int DestroyAllNodes(Link *headNode)
{
	Link *tmpNodePtr = NULL;
	Link *currentNode; 
	currentNode = headNode;

	printf("\nClearing out the memory");

	while (currentNode->next != NULL)
	{
		//Delete the nodes
		tmpNodePtr = (Link *)currentNode->next; 
		free(currentNode);
		currentNode = tmpNodePtr;
	
	}
	
	return 0;
}

/*
This function creates the nodes in the linked list and sorts them alphabetically 

LEGAND FOR ADDTOLIST
	
pTheHead		head in Link
Word			word in Link
newNode			new node in List
previousNode	points to previous node
theHead			points to pTheHead
*/
int AddToList(Link **pTheHead, char *Word)
{
	Link *newNode = NULL;
	Link *previousNode = NULL;
	Link *theHead = *pTheHead;
	
	while(1)
	{
    switch(theHead==NULL?-1:strcmp(Word, theHead->word))
			{
			case 0:
				//equal value, add to count
				theHead->numTimesAppear++;
				return 0;
			case 1:
				//greater value, goto next node
				previousNode = theHead;
				theHead = theHead->next;
				break;
			case -1:
		 		//lesser value, add node here
				newNode = (Link *)malloc(sizeof(Link));
				newNode->numTimesAppear = 1;
				strncpy(newNode->word,Word,sizeof(newNode->word));
				newNode->next = theHead;
				if (previousNode == 0)
				{
					*pTheHead = newNode;
					return 0;
				}
				previousNode->next = newNode;
				return -1;
			default:
				printf("Sorry I'm dumb...");
				break;
			}
		}
	
	return 2;
}


```

---

