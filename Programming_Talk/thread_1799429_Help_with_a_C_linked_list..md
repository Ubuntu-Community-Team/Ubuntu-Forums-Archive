---
title: "Help with a C linked list."
date: 2011-07-07
forum: Programming Talk
---

### Post by skytreader on 2011-07-07
I'm trying to create a linked list with this structure:

```
typedef struct LinkedList linkedlist;
typedef int ListElement;

struct LinkedList{
	ListElement data;
	linkedlist *next;
};
```

However, when I tried to create an addFirst (add to the head of the list) function, I'm not getting the behavior I want.

```
void addFirst(linkedlist *list, ListElement forAdding){
	linkedlist *NewNode = (linkedlist *) malloc(sizeof(linkedlist));
	NewNode->data = forAdding;
	NewNode->next = list;
	list = NewNode;
	printf("\n");
	printf("From addFirst: ");
	displayList(list);
}

int main(){
	linkedlist *l = (linkedlist *) malloc(sizeof(linkedlist));
	CreateList(l, 0); //Just initialize
	int a_list[5] = {1, 2, 3, 5, 6};
        //Put everything in a_list into list l
	List(a_list, l, sizeof(a_list)/sizeof(a_list[0]));
	printf("A list of five elements: ");
	displayList(l);
	addFirst(scheme, -1);
	printf("\nAdded something at the head of the list: ");
	displayList(l);
}

```

I get the output:

```

A list of five elements: (0 1 2 3 5)
From addFirst: (-1 0 1 2 3 5)
Added something at the head of the list: (0 1 2 3 5)

```

How come the -1 is appended to the list while still inside addFirst but disappears at main? I know that this is a pointer problem but I don't know where I went wrong. Any hints?

Thanks!

---

### Post by dwhitney67 on 2011-07-07
You are passing by value the list 'l' to addFirst() function.  Thus when you reassign the list within the function to the newly allocated list-element, you will not see that new address when the function returns.

Your choices to rectify the problem are to either pass the address of the list pointer, or return the new list pointer from addFirst().

Choice 1:
```

void addFirst(linkedlist** list, ListElement forAdding)
{
   ...  /* here you would need to dereference list before assigning a value to it */
}

```
Choice 2:
```

linkedlist* addFirst(linkedlist* list, ListElement forAdding)
{
   ...

   return list;
}

```

P.S.  Please post all of your code so that it can be properly analysed.

---

