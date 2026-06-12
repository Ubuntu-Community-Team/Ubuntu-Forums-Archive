---
title: "Dereferencing Variable Contained in Pointer to a Struct Inside a Pointer to a Struct"
date: 2007-10-17
forum: Programming Talk
---

### Post by ankursethi on 2007-10-17
I'm doing a cursed linked list implementation in C as a data structure exercise, and I'm *not* liking it at all. (I know, I know. Python is easier and blah. That's why I learned it before C :)).

Anyway, I have in my hands this evil struct which is my linked list. It has a pointer to another struct inside it, which is a node in the list. So we have something like this :
struct List {
    struct Node* header ;
    // other related stuff here ...
}

struct Node {
    // related stuff here ...
}

Now to add a node at a specified index, I pass a pointer to this list to a function called add_node(). Now the structure Node contains a variable called index. To get the value of index in my function, I need to do list->node->index, since both list and node are pointers to structures.

When I try to do that I get a core dump. GDB says that I cannot access the variable "index". Specifically, when I try to run my program and do list->node->index, GDB says that I cannot access the memory at 0xc (strangely enough, it's *always* 0xc).

I've given up on this hideous program. Anybody has any ideas?

PS : I could have posted the code, but it's a bit long. If somebody is willing to take the pain of reading it, I'll upload it here.

---

### Post by Wybiral on 2007-10-17
If I can see some code I can probably help.

---

### Post by dwhitney67 on 2007-10-17
Probably got yourself a segmentation violation (SIGSEGV) when attempting to peek at address 0xC.

It looks to me that either you did not allocate a node, or that you failed to assign it properly prior to examining it's index.

---

### Post by ankursethi on 2007-10-17
There are 3 files. linkedlib.c and linkedlib.h contain the library itself. I compiled linkedlib.c to produce an object file, which I linked with the third file, linkedlb_test.c to produce my executable.

Error occurs on line 62 in linkedlib.c.

(I added .txt to the end to make UbuntuForums happy)

---

### Post by dwhitney67 on 2007-10-17
right off the bat I can see that your malloc's are using the wrong size.  As you currently have it, you are only allocating 4 bytes each for the nodes and the list.

You want this:

[FONT="Courier New"]struct Node* nn = malloc( sizeof( struct Node ) );[/FONT]

and

[FONT="Courier New"]struct List* nl = malloc( sizeof( struct List ) );[/FONT]

---

### Post by dwhitney67 on 2007-10-17
Just ran your code after making the malloc() fixes I suggested earlier.

While stepping through the code using a debugger, I noticed that during initialization of the List, the header-node that is passed in is not set within the List, yet the size of the List is incremented by one.

When you attempt to print the contents of the List.... kaboom!

If you do not already have it, get DDD:

[FONT="Courier New"]$ sudo apt-get install ddd[/FONT]

To use it:
[FONT="Courier New"]
$ gcc -g myCode.c -o myProgram
$ ddd ./myProgram &[/FONT]

The -g option adds symbolic info to the executable so that it can be debugged.  Once all is well, remove the -g for your final product to reduce the bloat added to the executable.

---

### Post by mjwood0 on 2007-10-17
As other's have made mention, there are a few problems.

```

struct Node* nn = NULL;
nn = malloc (sizeof(nn));

```

Here, you have a pointer to a node named nn.  Since it's defined as a pointer, it's 4 bytes (32-bits) long.  Therefore, as someone else mentioned you are simply allocating 4 bytes during the malloc.

In all actuality, the code could be re-written as:
```
struct Node* pNode = malloc(sizeof Node);
```

Note, I've used pXXX as the variable name for pointers to clarify.  Old habit but it does help with ANSII C.

The same could be said for your list initialization.

The other curious item is that you're using a void* for data.  I think you'll be better off not having your list point to data as in this way, you'll have to specifically allocate memory for the data item.

---

### Post by ankursethi on 2007-10-17
Phew. Thanks, guys, for looking at that code :). I wonder what I'd do without the programming section back here.

So the problem is that malloc() is allocating only 4 bytes for the list. And what was that about the header node not being set inside the list? Didn't quite get it.

Is there a better way to store generic data in the list (int, char ... anything) without using a void pointer?

BTW, I was using GDB to debug my program. I'll check out DDD when Nexuiz finishes downloading :p (128K connections are akin to a night in Hell).

When it comes to programming skills, I can see many books, suggestions etc. out there. But can anybody tell me a nice book/tutorial/HOWTO for learning how to fix broken programs? Sadly, I've *never* been able to track down my errors myself. I just have a rudimentary knowledge of working with GDB, that's all.

---

### Post by mjwood0 on 2007-10-17
Debugging is one of those skills that is really not teachable.  You really have to just get dirty with the debugger.  If all else fails, simply start at the beginning and step your way through, verifying everything one step at a time.

After a while, you will be able to more effectively set break points at the beginning / end of functions where they are needed and jump right to problems.  But it does take some practice.

---

### Post by spookware on 2007-10-17
```

struct List* nl = NULL ;
	nl = malloc (sizeof(nl)) ;
	
	if (nl != NULL && nl->header != NULL) { <-- here is the problem 
		nl->header = header ;
		nl->type = type ;
		nl->header->index = 0 ;
	}

```

I think this is the problem the other fellow was talking about. you are examining nl->header but you have not set it to a value. So it is whatever was in the memory that malloc allocated for you. i.e. nl->header is just some random value in your if clause.

---

### Post by ankursethi on 2007-10-18
Hmm ... all right. Thanks a lot everybody :)

---

