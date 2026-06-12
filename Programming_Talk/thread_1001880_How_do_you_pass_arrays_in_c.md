---
title: "How do you pass arrays in c?"
date: 2008-12-04
forum: Programming Talk
---

### Post by lems on 2008-12-04
I'm learning C and I'm getting confused on how to pass arrays to and from functions. In fact, I'm a little confused on the pointers itself. Here's what I have.
```
#include <stdio.h>
void main(){
	int *a;
	noreturn();
	a = yesreturn();
	printf("%d",a[1]);
}

void noreturn(){
	int a,b,c;
}

int yesreturn(){
	int a[10]={0,1,2,3,4,5,6,7,8,9};
	
	return &a;
}

```

---

### Post by snova on 2008-12-04
It won't work. The array in yesreturn() is allocated on the stack, which would look quite different by the time printf() gets to printing its contents.

Try this, I think it will work:

[PHP]
**int** main(){ /* main() should always return int */
    int* a;
    a = yesreturn();
    printf("%d",a[1]);pointer
}

int yesreturn(){
    /* Allocates memory */
    int* a = malloc( sizeof( int ) * 10 );
    int i;
    /* Sets array */
    for( i = 0; i < 10; i++ )
        a[i] = i;
    /* Returns *pointer*. */
    return a;
}
[/PHP]

Arrays and pointers are really quite similar. Where one is needed, most of the time, the other is equivalent.

Nobody said C was easy. ;) Have you learned a more friendly language first?

---

### Post by dwhitney67 on 2008-12-04
A couple of problems with the code in the OP.

First, it appears that you are trying to return the address of an array that is locally declared within a function.  Once that function returns, the array is toast, and hence not accessible any more.

The other issue is the declaration of the yesreturn() function.  If you want it to return a pointer, then you need to change the return type to int*.

Since you are learning C, and it appears that you are new to the language, I would recommend that you consider declaring an array in your main function, then passing it to a function where it can be used in there.

If you wish to pursue what you are working on now, then the only option you have available would be to allocate memory from the heap for the array in yesreturn(), and then return it.  Note that when returning the address of an array, it is not necessary to place an & in front of the array name.

---

### Post by CptPicard on 2008-12-04
In "yesreturn", your array is on the stack, so it is deallocated by the time you return from the function. Whether the return value is meaningful after that is debatable and probably depends on the compiler. Nevertheless, the value you're returning should no longer be used.

If you want to return an array from a function, you should allocate it on the heap using malloc. In that case, within the scope of the calling function, you also need to know how big that memory block is... and that number in turn should be passed into the allocating function.

---

