---
title: "C Problem, I am learning"
date: 2008-10-04
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-10-04
What is wrong with this code, its a beginning of a implementation of binary tree
I believe its in the tflat function

[PHP]#include <stdio.h>
#include <stdlib.h>

struct leaf {
	int val;
	struct leaf * less;
	struct leaf * more;
};

void treeadd(const int a, struct leaf *l) {
	if (l == 0) {
		l = malloc(sizeof(struct leaf));;
		l->val = a;
		l->less = 0;
		l->more = 0;
	} else if (a < l->val) {
		treeadd(a, l->less);
	} else if (a > l->val) {
		treeadd(a, l->more);
	}
}

size_t tflat(struct leaf *t, int * array) {
	size_t l, m;
	int i=0;
	int * less;
	int * more;
	
	if (array != 0) free(array);
	
	if (t == 0) return 0;
	
	l = tflat(t->less, less);
	m = tflat(t->more, more);
	array = malloc(sizeof(int) * (l+m+1));
	for (i=0;i<l;i++) {
		array[i] = less[i];
	}
	free(less);
	array[i+1] = t->val;
	for (i=0;i<m;i++) {
		array[i+l] = more[i];
	}
	free(more);
	return l+m;
}

int main() {
	struct leaf * l = 0;
	size_t s;
	int * a = 0;
	int i=0;
	
	treeadd(5, l);
	treeadd(6, l);
	treeadd(11, l);
	treeadd(13, l);
	treeadd(1, l);
	treeadd(3, l);
	
	s = tflat(l, a);
	for (i=0;i<s;i++) {
		printf("%d	", a[i]);
	}
	
	return 0;
}[/PHP]

---

### Post by Greyed on 2008-10-04
What makes you think it isn't working properly?

---

### Post by Mr.Macdonald on 2008-10-04
nothing prints upon execution

---

### Post by dwhitney67 on 2008-10-04
When you call tflat(), you need to pass the array pointer by "reference", and in C, your only choice is to pass the address.  Thus for tflat(), change the function signature and implementation as follows:
[PHP]size_t tflat(struct leaf *t, int ** array)   // note the pointer to a pointer
{
    size_t l, m;
    int i=0;
    int * less;
    int * more;
    
    if (*array != 0) free(*array);   // dereference the pointer
    
    if (t == 0) return 0;
    
    l = tflat(t->less, &less);
    m = tflat(t->more, &more);
    *array = malloc(sizeof(int) * (l+m+1));  // again, dereference the pointer
    ...
}

int main()
{
    ...

    tflat( l, &a );    // pass the address of a

    ...
}[/PHP]

P.S.  You will need to make similar changes to treeadd() as described above.

P.S.S.  I've been testing your code; it has a bug in tflat().  Try to sort it out using ddd.  I will try to find the problem too.

---

### Post by Mr.Macdonald on 2008-10-04
I have narrowed the problem down to the "treeadd" function. It seems to not be writing the data to the "struct leaf * l". Meaning it can be accessed while inside that function but after that function ends, it writes null pointer to the "leaf*" passed into it.

```
thus ... if we execute this

struct leaf * l0 = 0;
treeadd(4, l0);

 ... then

l0 == 0
```


That is not what is supposed to happen??????

And i tried the pointer - pointer thing and it didn't work, your welcome to try again because i probably messed up.

PS can you have const functions?   void func(args) const {   }

---

### Post by dwhitney67 on 2008-10-04
You've got to pass the address of that pointer if you want it back; that is, if you plan to assign a new address to it.  And that is exactly what you are doing when performing a malloc().

P.S.  You should attempt to be a little more creative with your variable names.  'l0'... how about 'leaf0' or 'tree0'?  Single character variables names should be relegated to indexes of for-loops and the such.  Anyhow, my $0.02 of an opinion.

---

### Post by dwhitney67 on 2008-10-04
Btw, I took your program, and rewrote it such that it would yield results.  I personally do not like how I have re-written your tflat() function, but it's Saturday and I really do not want to spend my day working on this problem.

The other issue is managing the recursion.  It's looks great until it bites back.

Anyhow, enjoy the code for what it is worth:
[PHP]#include <stdio.h>
#include <stdlib.h>

typedef struct Leaf
{
    int val;
    struct Leaf * less;
    struct Leaf * more;
} Leaf;


void treeAdd( const int value, Leaf ** leaf )
{
    if ( *leaf == 0 )
    {
        *leaf = malloc( sizeof(Leaf) );

        (*leaf)->val  = value;
        (*leaf)->less = 0;
        (*leaf)->more = 0;
    }
    else if ( value < (*leaf)->val )
    {
        treeAdd( value, &((*leaf)->less) );
    }
    else if ( value > (*leaf)->val )
    {
        treeAdd( value, &((*leaf)->more) );
    }
}

void treeSize( Leaf *leaf, size_t * size )
{
    if ( leaf == 0 )
    {
      return;
    }

    treeSize( leaf->less, size );
    treeSize( leaf->more, size );

    ++(*size);
}


void tflat( Leaf * leaf, int * array, size_t * insertPosition )
{
    if ( array == 0 || leaf == 0 )
    {
        return;
    }

    array[ (*insertPosition)++ ] = leaf->val;
    
    tflat( leaf->less, array, insertPosition );
    tflat( leaf->more, array, insertPosition );
}


int main()
{
    Leaf * tree = 0;
    
    treeAdd( 5,  &tree );
    treeAdd( 6,  &tree );
    treeAdd( 11, &tree );
    treeAdd( 13, &tree );
    treeAdd( 1,  &tree );
    treeAdd( 3,  &tree );
    
    size_t size = 0;

    treeSize( tree, &size );

    printf( "size = %u\n", size );

    int *  array = malloc( sizeof(int) * size );
    size_t insertPosition = 0;

    tflat( tree, array, &insertPosition );

    for ( size_t i = 0; i < size; ++i )
    {
        printf( "%d ", array[i] );
    }
    printf( "\n" );

    free( array );

    // TODO free the tree; note this is not as easy as pie!
    
    return 0;
}[/PHP]

---

