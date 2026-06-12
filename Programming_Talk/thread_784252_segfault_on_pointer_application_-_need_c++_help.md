---
title: "segfault on pointer application - need c++ help"
date: 2008-05-06
forum: Programming Talk
---

### Post by tom66 on 2008-05-06
I'm very bad at C++. I'm trying to grip pointers, which I need to understand to go into the complicated areas of C++. Could someone tell me what is wrong with this code? Thank you.

The program outputs:

```

C++ linked list
Enter a value to insert (-1 quits): 123

Segmentation fault

```

This is the code: 

```

#include <stdio.h>

/*
 * My attempt at C++, and the function of pointers. 
 * Stores individual numbers.
 */
 
struct list_item {
	struct list_item *next;
	int value;
};

struct list_item *start;

int insert(struct list_item *item) {
	struct list_item **p;
	
	for(p = &start; *p != NULL; p = &(*p)->next) 
		if(item->value <= (*p)->value) 
			break;
	
	if(*p == NULL) 
		return 0;
		
	item->next = *p;
	*p = item;
	
	return 1;
}

int main() {
	int value;
	
	struct list_item *item;
	struct list_item **p;
	
	printf("C++ linked list\n");
	
	while(value != -1) {
		printf("Enter a value to insert (-1 quits): ");
		scanf("%d", &value);
		printf("\n");
		
		if(value != -1) {
			item->value = value;
			
			if(insert(item) == 1)
				printf("Error inserting! Please try again. \n");
			
			break;
		}
	}
	
	printf("\n");
	printf("You entered: ");
	
	for(p = &start; *p != NULL; p = &(*p)->next) {
		printf("%d ", (*p)->value);
	}
	
	printf("\n\n");
	printf("The application has finished and will now quit. \n");		
}

```

---

### Post by ibuclaw on 2008-05-06
Have a look at this site:
[http://www.cprogramming.com/debugging/segfaults.html](http://www.cprogramming.com/debugging/segfaults.html)

It should get you up to speed with debugging in C or C++.

Regards
Iain

---

### Post by CptPicard on 2008-05-06
You are never actually allocating any memory for your list items :)

---

### Post by ibuclaw on 2008-05-06
If you want a clue. The pointer that starts the seg fault is **&start**.

[PHP]
(gdb) run
Starting program: /home/test 
C++ linked list
Enter a value to insert (-1 quits): 1


Program received signal SIGSEGV, Segmentation fault.
0x080485ae in main ()
Current language:  auto; currently asm
(gdb) list
1       /build/buildd/glibc-2.7/build-tree/i386-libc/csu/crtn.S: No such file or directory.
        in /build/buildd/glibc-2.7/build-tree/i386-libc/csu/crtn.S
(gdb) backtrace
#0  0x080484ce in main ()
(gdb) list
1       in /build/buildd/glibc-2.7/build-tree/i386-libc/csu/crtn.S
(gdb) print start
$1 = 0
(gdb) print *start
Cannot access memory at address 0x0
[/PHP]

Regards
Iain

---

### Post by Npl on 2008-05-06
To nitpick, this is more C-Style than C++, You`d use classes in C++.

But for your bug:

you got ```
struct list_item *item;
	struct list_item **p;
```
in main and afterwards do 
```
item->value = value;
```

item is a uninitialised pointer, you cant except to point it to a valid structure.

You either need to allocate memory dynamically ```
item = (struct list_item *)malloc(sizeof(struct list_item));
``` and free it if unused, or (preferably) dont use a pointer, but a struct itself in main```
struct list_item item;
```, but you then need to modify the insert-function to allocate a new struct, copy the contents of the argument to the newly allocated struct and link it into the list.

Also you then need to make sure you properply free everything you allocated - or you get memleaks

---

### Post by nvteighen on 2008-05-06
Well, that's not C++, just plain C... Glad to give some help.

Your first problem is that you're creating pointers, but they point to nowhere... After declaring a pointer, you must tell to what region of memory it will point. There comes your second problem: you don't have got any memory yet (so, where do you expect to point? ;)).

So, you must get some memory and then tell the pointer to point there.

EDIT: Well, Npl has already posted the same. Follow his clearer explanation.

---

### Post by tom66 on 2008-05-06
I'm a real beginner at C, or C++. The pointers just confuse me. Anyway, I have this book, and it touches on C++ pointers but not much which annoys me. I understand the concept of pointers - boxes pointing to other boxes, I just don't understand how to actually use them correctly, how to use linked lists. I've asked about this before and I've got some tutorials but they all seemed a bit 'vague' to me (I'm great at scripted languages, could this be why?). 

I think I'll just try Python and get a book from my library. 

Thanks for everyone's help. I appreciate it. 
Tom

---

### Post by CptPicard on 2008-05-06
In languages where you have to manually manage the memory on the heap (as opposed to on the stack which is automatic), you have to explicitly ask for the operating system to reserve a block of memory for you to put stuff in. In C you use malloc for this request, in C++ it's the operator "new". The result of the request is a pointer to the beginning of the memory area that was reserved for your use.

A *really* simple analogy you might find useful to consider is the idea that pointers are very much the same thing as indices into a big underlying array. Doing an array[i] is the same thing as *i if i were a pointer (and C arrays actually behave in this kind of way under the hood). It's just that to use the "big memory array" you must first ask the OS permission to do so, so that you don't step on the toes of other processes in the machine.

In linked lists in particular, when you can have an arbitrary number of elements, being able to flexibly allocate memory as needed on the heap is a requirement. Thus, you're pretty much forced to using pointers to manage the structure of your list.

And as was stated, you also must let the OS know that you're done with the memory block so that it can be recycled to some other process, so remember to "delete" your "new"ed pointers and "free" your "malloc"ed memory areas.

---

### Post by Npl on 2008-05-06
Doing a quick search on google yielded that tutorial: [http://gd.tuwien.ac.at/languages/c/programming-bbrown/c_086.htm]("http://gd.tuwien.ac.at/languages/c/programming-bbrown/c_086.htm"). If you follow the next 7-8 pages you will find hints and even full sources on how you do a linked list with dynamic memory allocation.

(I dont wanna know how much time I couldve saved if there was something remotly similar to todays internet 15 years ago)

---

### Post by Mickeysofine1972 on 2008-05-06
Also, you shouldn't be using **p anyway with C or C++ as the linked list stores the next item in the *next pointer within the struct.

By saying **p your saying that its a pointer to another pointer or even a pointer to an array of pointers (*p[]) this is bad because all you have to do is get your indexing logic wrong and boom! yet another segfault!

My advise is keep it simple and only use *p to point to  the struct and them use the *next inside to walk through your list; <== OMG I even punctuate in C! :lolflag:

Mike

---

### Post by Can+~ on 2008-05-06
When you got an existing block associated to a variable, say:

[PHP]int a = 2;[/PHP]

It will reserve a space of memory for it. And create pointers this way:

[PHP]int *ptr_a;[/PHP]

It will also reserve some memory for the pointer. You can access the pointer of that variable with:

[PHP]ptr_a = &a;[/PHP]

This works, it's easy to do, but, it doesn't work inside the local scope. You can pass a pointer of a variable to a function, and it will operate over the pointed variable. But, if you want to create a pointer inside a function, and return it, you'll get an error, since, variables created inside a function die when the function ends, therefore, you can't point to a variable which will die. I know there might be better explanations for this, but you get the idea, you can't point to a local variable.

That's why you use malloc, it saves a space of memory, of a specified size, and returns the pointer to it, and you do a CAST to the type you want. This reserver memory won't go free as function ends, in fact, it won't go free unless you specify it to go free.

[PHP]typedef struct NODE
{
	int value;
	struct NODE *__next__; // Looks pythonish, but that's just me.
}node;

node *newNode()
{
	node *nnode = (node*)malloc(sizeof(node));
	nnode->value = 0;
	nnode->__next__ = NULL;
	return nnode;
}[/PHP]

I'm not sure that making linked lists is the best way to start with pointers, there are other simple examples, like this one:

[PHP]void square(int *value)
{
	*value *= *value;
}

int main()
{
	int x=5;
	printf("value1: %d\n", x);
	square(&x);
	printf("value2: %d\n", x);
	
	return 0;
}[/PHP]

This passes the reference to the variable x (which holds 5) to the square function. You may notice that square does not return anything, it uses the value inside x and edits it on place.

---

