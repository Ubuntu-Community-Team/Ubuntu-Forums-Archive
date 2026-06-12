---
title: "freeing memory [C]"
date: 2009-04-11
forum: Programming Talk
---

### Post by StOoZ on 2009-04-11
any idea why this crashes?

[http://codepad.org/znQpyL6a]("http://codepad.org/znQpyL6a")


thanks,

---

### Post by dwhitney67 on 2009-04-11
```

typedef struct dListNode {

    int* dataPtr;
    struct dListNode* next;
    struct dListNode* prev;

} DListNode;

{...

DListNode* p = (DListNode*) malloc ( sizeof(DListNode) );
p->dataPtr = (int*) malloc ( sizeof(int) );
p->data = 145;

freeNode( p ); // this function crashes

}

void freeNode( DListNode* pNode ) {

    int* pDataPtr = NULL;
    DListNode* pNodeToDelete = NULL;

    pDataPtr = &(pNode->dataPtr);
    pNodeToDelete = pNode;
    
    free( pDataPtr );
    free ( pNodeToDelete );

}

```

What is the 'data' variable above?  How did you even get the program to compile?  If it is a typo, and should be dataPtr, then you are assigning the address of 145 to dataPtr.

As for freeing memory, try to do it more efficiently:
```

void freeNode( DListNode* pNode ) {
    free(pNode->dataPtr);
    free(pNode);          /* do NOT use pNode after this; not even after freeNode() is called */
}

```
Btw, very few programmers nowadays use the Hungarian notation in naming their variables.  It sometimes leads to confusion, and it makes it problematic to change code should a variable's type change after the initial design.  But do as you please.

---

### Post by lloyd_b on 2009-04-11
```
void freeNode( DListNode* pNode ) {

    int* pDataPtr = NULL;
    DListNode* pNodeToDelete = NULL;

    **pDataPtr = &(pNode->dataPtr);**
    pNodeToDelete = pNode;
    
    free( pDataPtr );
    free ( pNodeToDelete );

}
```

See the highlighted line above - the "&" is a problem.  pNode->dataPtr is an int pointer, which points to a malloc'ed chunk of memory.  &pNode->dataPtr is an element of pNode, and is NOT a pointer to a malloc'ed chunk of memory (It's a *part* of a malloc'ed chunk...).

May I suggest you lose the unnecessary intermediate variables, and do it this way:```
void freeNode( DListNode* pNode ) {

    free(pNode->dataPtr);
    free(pNode);

}
```

Lloyd B.

Edit - looks like dwhitney67 beat me to it...

---

### Post by StOoZ on 2009-04-11
ignore the 'data' , I meant dataPtr.

First I tried what you suggested (before posting this thread...) , it gave me the same error , so I tried the above code , still to no avail.

if I delete only
        free ( pNode );

it works fine , but when both:
    free ( pNode->dataPtr );
    free ( pNode );

it gives segfault for the last free.

---

### Post by lloyd_b on 2009-04-11
> **StOoZ said:**
> ignore the 'data' , I meant dataPtr.

First I tried what you suggested (before posting this thread...) , it gave me the same error , so I tried the above code , still to no avail.

if I delete only
        free ( pNode );

it works fine , but when both:
    free ( pNode->dataPtr );
    free ( pNode );

it gives segfault for the last free.

Please reread dwhitney67's post - you're putting an invalid value into p->dataPtr, with the result being that free() crashes because it's not being given a valid pointer.

That line should read "*p->dataPtr = 145;", not "p->dataPtr = 145;".

Lloyd B.

---

### Post by StOoZ on 2009-04-11
Problem sovled

thanks you all , the problem was indeed me assigning an address instead of a value.
p->dataPtr = 145;
instead of:
*p->dataPtr = 145;

now the question is : I remember when reading about pointers etc , when I use the '->' its like dereferencing it ('*') , so why did it caused a problem in this case?

---

### Post by dwhitney67 on 2009-04-11
> **StOoZ said:**
> Problem sovled

thanks you all , the problem was indeed me assigning an address instead of a value.
p->dataPtr = 145;
instead of:
*p->dataPtr = 145;

now the question is : I remember when reading about pointers etc , when I use the '->' its like dereferencing it ('*') , so why did it caused a problem in this case?

You have two pointers:  p and dataPtr.  You used -> to dereference p, but for dataPtr... well initially nothing; now of course, you are doing it correctly.

---

### Post by StOoZ on 2009-04-11
many many thanks , it solved me not only this problem , but some other I had due to incorrect use of pointers.

:guitar:

---

