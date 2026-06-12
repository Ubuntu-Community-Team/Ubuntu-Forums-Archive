---
title: "Initializing a pointer to a structure"
date: 2010-01-05
forum: Programming Talk
---

### Post by bhaskar_goel on 2010-01-05
I have been unable to figure out how the following pointer to structure lp was initialized:
  struct list
		{
		int item;
		struct list *next;
		};
    
    struct list *lp, *prevlp;  //pointer to struct list lp
     for(lp = list; lp != NULL; lp = lp->next) //**initialized as struct name???**
		{
		if(lp->item == i)
			{
			if(lp == list)
				list = lp->next;
			else	prevlp->next = lp->next;
			break;
			}
		prevlp = lp;
		}
	}

As the comment states lp=list. is such an initialization possible because i have been unable to come up with other refs. Any help will be appreciated**[B]**[/B]**[SIZE="3"][/SIZE]**

---

### Post by Axos on 2010-01-06
I'm not a C expert (haven't used it in years) but I believe structs have a separate namespace. So somewhere outside that code snippet there could be a variable or parameter declared like this:

struct list *list;

---

### Post by LKjell on 2010-01-06
Please use the code block code to get prober format on codes. And tell us which language it is. Could be some new alien language :)
I will assume it is C.

Well I assume that you will get some problems compile that code.
That is because you cannot have a variable list assigned to struct list.
That is you cannot write struct list *list;

---

### Post by nvteighen on 2010-01-06
You have **only one** way on how to intialize **any** pointer: You make the pointer point to something already allocated by getting that object's memory address.

```

int myint = 8;
int *pointer_to_int = &myint;

int *myint2 = (int)malloc(sizeof(int));

```

A struct is actually the same, with the peculiarity that the type name consists in two keywords instead of one.
```

struct List
{
    int node;
    struct List *next;
};

struct List myList; /* Allocated in stack. */
myList.node = 1;
myList.next = NULL;

/* Or... */
struct List *myOtherList = (struct List *)malloc(sizeof(struct List));
myOtherList->node = 1;
myOtherList->next = &myList; /* Because myList is *not* a pointer! */

```

Of course, using malloc() requires you to free() the memory afterwards and to be careful of not leaking any memory.

---

