---
title: "A simple stack in C"
date: 2009-09-09
forum: Programming Talk
---

### Post by descendency on 2009-09-09
I am in an OS class and I have to write a simple stack program (the main function just determines what the user is asking you to do). If this were not required to be in C, I would have had this done ages ago, but because I am not very good at C coding, it has "a bug"... The bug so far is that it just continues to "pop" the same value off. (It's not actually popping anything off). I think it's because I don't understand how structures and pointers really work. Or is it a not so obvious coding mistake?

```
#include <stdio.h>

struct node {
	int data;
	struct node *next;
	struct node *prev;
} first;

void push(int);
void pop();

int main(void)
{
	int command = 0;
	
	while (command != 3)
	{
		printf("Enter your choice:\n1) Push integer\n2) Pop Integer\n3) Quit.\n");
		scanf("%d",&command);
		if (command == 1)
		{
			// push
			int num;
			scanf("%d",&num);
			push(num);
		}
		else
		{
			if (command == 2)
			{
				pop();
			}
			else
			{
				if (command != 3)
				{
					printf("Command not understood.\n");
				}
			}
		}
	}

	return 0;
}

void push (int x)
{
	struct node newNode;
	newNode.data = x;
	newNode.prev = NULL;
	newNode.next = &first;
	first = newNode;
	printf("%d was pushed onto the stack.\n", first.data);
}

void pop()
{
 	if (first.data == NULL)
	{
		printf("Error: Stack Empty.\n");
		return;	
	}
	printf("%d was popped off the stack.\n", first.data);
	first = *(first.next);
	first.prev = NULL;
}
```

Any help would be appreciated.

---

### Post by apmcd47 on 2009-09-09
You need to use malloc() and free() to create and release the newNode element:
[PHP]void push (int x)
{
	struct node *newNode = (struct node*)malloc(sizeof struct node);
	newNode->data = x;
	newNode->prev = NULL;
	newNode->next = &first;
	first = newNode;
	printf("%d was pushed onto the stack.\n", first.data);
}

[/PHP]
A simpler stack program would be to use an array:

[PHP]int arr(100), ptr=0;
void push(int val) {
   arr[ptr++] = val;
}
int pop(void) {
   return arr[--ptr];
}[/PHP]
Or have you been specifically asked to use structs?

Andrew

---

### Post by lswb on 2009-09-09
There needs to be some permanent storage for the stack somewhere, typically an array would be used or memory could be allocated/freed by the push/pop functions. As it is now, in push(), the local variable "newnode" will not persist once push() returns.

The stack pointer needs to really be a pointer; Your global struct node first is declaring a struct, not a pointer to struct, C allows assignment using the = operator from one struct type to another, so in push, the line " first=newNode " is just copying data from the newNode struct to the first struct. That is why the same data appears to keep popping off.

There are a few different approaches you could take to implement a stack, depending on which you take there are different problems with the code you are presenting. 

It shouldn't be difficult to google up some working examples of coding a stack, back in the old days, we had to use a book!

Good luck.

---

### Post by apmcd47 on 2009-09-09
Yes, I wasn't thinking when I wrote my reply. I'd missed that fact that first was an instance of struct node.
[PHP]
struct node *first=NULL, *last=NULL;
void push (int x)
{
    struct node *newNode = (struct node*)malloc(sizeof struct node);
    newNode->data = x;
    if (first == NULL)
    {
        first = newNode;
        last = newNode;
        newNode->prev = NULL;
        newNode->next = NULL;
    }
    else
    {
        newNode->prev = last;
        last->next = newNode;
        newNode->next = NULL;
    }
    printf("%d was pushed onto the stack.\n", first.data);
} [/PHP] 
I'll let you figure out pop().

This is basically a linked list rather than a stack. Personally I'd put the variables first and last in a separate "header" struct. That way you can use several linked lists in your code and reuse the push/pop functions with a little modification.

Unless your assignment asked for use of structures and linked lists I'd stick to the simpler array method in my previous post. Just add range checking and think of a way to make it easier to change the array size when the current one gets too small.

Andrew

---

### Post by dwhitney67 on 2009-09-09
One can use a list to implement a stack.  One should insert at the head, and then obviously when required, pop from the head.  A stack is modeled as a LIFO (last-in, first-out).

There is no need to maintain a doubly-linked list, much less a tail pointer.  A null pointer should suffice in marking the end of the data.

So...
```

#include <stdlib.h>
#include <assert.h>   // for testing

typedef struct StackNode
{
   int data;
   struct StackNode* next;
} Stack;

void push(Stack** stack, int data)
{
   Stack* node = malloc(sizeof(Stack));

   // add new node to head of stack
   node->data = data;
   node->next = *stack;   // important!  Initially stack must be 0.

   // reset head of stack
   *stack = node;
}

int pop(Stack** stack)
{
   int data = -99999;   // for lack of a better value

   if (*stack != 0)
   {
      // get the data from the head node of the stack
      Stack* tmp = *stack;
      data = tmp->data;

      // reset the head node of the stack
      *stack = tmp->next;

      // deallocate the popped node
      free(tmp);
   }

   return data;
}

int main()
{
   Stack* stack = 0;

   push(&stack, 10);
   push(&stack, 30);
   push(&stack, 20);

   assert(stack != 0);
   assert(pop(&stack) == 20);
   assert(pop(&stack) == 30);
   assert(pop(&stack) == 10);
   assert(stack == 0);
   assert(pop(&stack) == -99999);

   return 0;
}

```

P.S.  I defined the push() and pop() functions to accept a Stack object; one never knows... an application may need to support more than one stack, and thus the use of a global stack object is plain hideous.

---

