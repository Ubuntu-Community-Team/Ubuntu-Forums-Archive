---
title: "[SOLVED] C language - How to concatenate?"
date: 2008-07-04
forum: Programming Talk
---

### Post by tekkenlord on 2008-07-04
Hello all,

I have the following problem: I have created a matrix in C using

double ** my_matrix;

and I have allocated (with malloc) space for 2 rows and 3 columns.

I want to insert an extra row to this matrix while keeping the previous rows as they are. I know how I can do this by creating a new matrix with more rows, copying from the old one and then freeing the old one but it is very inefficient.

Can I do it efficiently? Any help will be greatly appreciated!

Regards

---

### Post by balagosa on 2008-07-04
One Idea I can Give to you is using Pointers. From your 2nd Row, Point to a new 3rd Row to add one extra row.

e.g.
2nd_row->next=3rd_row;

Note: This is just an idea of mine and it is not full-proof. It has been 3 years since I coded in C.

---

### Post by jim_24601 on 2008-07-04
Well, yes and no. If you want to keep the convenient 2D-array-like features of the matrix, then there isn't any alternative to reallocating the array and copying. (You can just use realloc() for that). It's not quite as bad as all that, though, because you only have to copy the row pointers, not the whole row.

You could always allocate some extra rows when you create the matrix, but leave the row pointers NULL until you need them:

```

my_matrix = malloc(4*sizeof(double*)); /* actually, we only need 2 */
my_matrix[0] = malloc(3*sizeof(double));
my_matrix[1] = malloc(3*sizeof(double)); /* allocate 2 rows of 3 */
my_matrix[2] = NULL;
my_matrix[3] = NULL;
/* ... do stuff with my_matrix. Oops, now we need a 3rd row */
my_matrix[2] = malloc(3*sizeof(double)); /* now it is 3x3 */

```

Of course, if you don't know how many rows you'll need in the end, you will have to keep track of how many rows are allocated and how many are used, and grow the matrix as needed. And if you need to insert rows in the middle, you will need to move stuff about to make room. (But again, you only need to shuffle the row pointers about, not the row data).

If you need really efficient insertion/deletion, you want some sort of linked list. But that will make accessing the elements of the matrix *much* more complicated, and you are likely to access a matrix much more often than you change its size.

---

### Post by tekkenlord on 2008-07-04
Thank you very much for your answers. The truth is I do not know how many rows I will need for the matrix. The thing is that this matrix appears in a while loop and I want each iteration of the loop to increase the row dimension by one. I will think of what you said with the NULL pointers and see if it works. 

Thanks again!

---

### Post by jim_24601 on 2008-07-04
I see. In that case, why not use something like (**warning: untested code**):

```

/* assume start matrix size is num_rows x num_columns */
int row;
/* This allocates the next higher power of 2 number of rows */
int rows_alloc = 1;
while (rows_alloc <= num_rows) rows_alloc *= 2;
/* Initialise the matrix */
my_matrix = malloc(rows_alloc * sizeof(double*));
for (row = 0; row < rows_alloc; ++row)
{
  if (row < num_rows)
  {
    my_matrix[row] = malloc(num_columns * sizeof(double));
    /* initialise the row in some way */
  }
  else
  {
    /* spare row */
    my_matrix[row] = NULL;
  }
}
/* This is the big while loop */
while (not_finished)
{
  /* do stuff */
  ++num_rows;
  if (num_rows > rows_alloc)
  {
    /* Need to make some more room */
    rows_alloc *= 2;
    my_matrix = realloc(my_matrix, rows_alloc * sizeof(double*));
    for (row = num_rows; row < rows_alloc; ++row)
    {
      my_matrix[row] = NULL;
    }
  }
  /* Allocate space for the new row */
  my_matrix[num_rows - 1] = malloc(num_columns * sizeof(double));
  /* Initialise the new row in some way */
}

```

You're doubling the size of the pointers list each time, so you may have as many as twice the pointers allocated as the number of rows, but the number of actual rows allocated at any time is only as many as you need. realloc() will automatically move the array if necessary--this will take a little bit of time, but the moves get less frequent as the matrix grows, so you aren't wasting that much.

Of course, I've not provided you with any error handling.

---

### Post by tekkenlord on 2008-07-04
Hmm, this looks like a good idea, I will try that. I am pretty sure though that there must be a way of doing this in the exact way, ie using as much space as required and without the use of realloc (which actually copies-pastes-frees). 

Thank you very much Jim_24601!

---

### Post by slavik on 2008-07-04
> **tekkenlord said:**
> Hello all,

I have the following problem: I have created a matrix in C using

double ** my_matrix;

and I have allocated (with malloc) space for 2 rows and 3 columns.

I want to insert an extra row to this matrix while keeping the previous rows as they are. I know how I can do this by creating a new matrix with more rows, copying from the old one and then freeing the old one but it is very inefficient.

Can I do it efficiently? Any help will be greatly appreciated!

Regards
the easiest way without changing much code, use realloc() which will attempt to extend the current memory pointed to by a pointer, or it will find it elsewhere and copy the lements by itself.

although the best way is to have a linked list of pointers ...

---

### Post by skeeterbug on 2008-07-04
Hey Jim,
In your code:

```

my_matrix = malloc(4*sizeof(double*)); /* actually, we only need 2 */

```

Shouldn't it be malloc(4*sizeof(double))? I thought sizeof double* would return 4 bytes (the size of a 32 bit pointer). sizeof double should be 8 bytes.

---

### Post by jim_24601 on 2008-07-04
> **skeeterbug said:**
> Hey Jim,
In your code:

```

my_matrix = malloc(4*sizeof(double*)); /* actually, we only need 2 */

```

Shouldn't it be malloc(4*sizeof(double))? I thought sizeof double* would return 4 bytes (the size of a 32 bit pointer). sizeof double should be 8 bytes.

Actually, they're both 8 bytes on my computer. But no--my_matrix is a double**, and so points to a double* or an array of double*. So if I want 4 rows, I must allocate space for 4 double*.

---

### Post by jim_24601 on 2008-07-04
> **tekkenlord said:**
> Hmm, this looks like a good idea, I will try that. I am pretty sure though that there must be a way of doing this in the exact way, ie using as much space as required and without the use of realloc (which actually copies-pastes-frees).

There is--as balagosa and slavik said, you would use a linked list. If you define a

```

typedef struct tag_matrix_row
{
  double* data;
  struct tag_matrix_row* next;
} matrix_row;

```

then each time you need a new row, you allocate it (and its data) and stick it onto the 'next' of the last existing row. Keep a pointer to the last row and you don't have to traverse the entire list each time.

It's less efficient in terms of space, though, because you now have two pointers for every row, while in my example you only got up to that many in the pathological case. Plus you get the additional overhead of a separate malloc block for each row, which will probably be another 2 or 3 pointers' worth.

It's not even any more efficient in terms of time, since if you use realloc() but double the size of the array each time, each element will be copied once, on average. Proof of this is left as an exercise for the reader ;)

Of course, unless your matrix is going to get very large, it makes no practical difference anyway.

---

### Post by tekkenlord on 2008-07-04
I think this is what I need. Jim_24601 can you elaborate a bit more? You typed

> 
typedef struct tag_matrix_row
{
  double* data;
  struct tag_matrix_row* next;
} matrix_row;


Should not it be like this:

typedef struct
{
/*some stuff*/
} matrix_row;

Perhaps, I am confused. Can you please give an example? I am not a newbie in C but this is the first time I hear about linked lists...Thanks!

---

### Post by jim_24601 on 2008-07-04
> **tekkenlord said:**
> Should not it be like this:

typedef struct
{
/*some stuff*/
} matrix_row;


Usually that would work, but in this case matrix_row needs to contain a pointer to another matrix_row, and at the point where it's declared the compiler has not yet "seen" the typedef. So you would get a compiler error.

(An aside about structs: You do not have to typedef a struct to use it. You can say

```

struct foo { /* some stuff */ };

```

but then you would have to always refer to it as 'struct foo'. So for convenience we usually set up a typedef so that we don't need to write the 'struct' every time.

Now as a shorthand you can define the typedef in the same place as the struct itself.

```

typedef struct tag_foo { /* some stuff */ } foo;

```

As far as the compiler is concerned, the struct is really 'struct tag_foo' and 'foo' is another name for it. As a further shorthand, if you're only ever going to refer to the struct by its typedef, you can leave off the tag (the compiler may generate one internally).

But if the struct needs to contain a pointer to another struct of the same type, we run into a problem. *Within the body of the struct definition* (where the /* some stuff */ is in my example above), the compiler knows that there exists a 'struct tag_foo' and that we are going to typedef it to something, but it does not know what that something is going to be. A C compiler cannot look ahead; it processes its input strictly in order. So you must refer to the struct as 'struct tag_foo' and not by the typedef. And, of course, you can't omit the tag or you will have no way of defining the member. End aside.)

> 
Perhaps, I am confused. Can you please give an example? I am not a newbie in C but this is the first time I hear about linked lists...Thanks!

A linked list is not specific to C, but is a general computer science concept. Google "linked list" to find out more about them than you ever wanted to know. Basically it's like an array, but instead of each element following directly after the one before in memory, the elements themselves contain a pointer to the next in the list. The last element has a NULL 'next' pointer so you know it's the end. You store a pointer to the first element.

It's like a chain of paper clips--you hold one end and add new clips onto the other. Like

```

typedef struct tag_node
{
  /* your data goes here */
  struct tag_node* next;
} node;

node* head;
node* tail;

```

It's not strictly necessary to keep the tail pointer there, but it makes adding to the end more efficient. Initially the list is empty and both pointers are NULL. Then to add a node to the end of the list:

```

/* we have a new node in new_node */
new_node->next = NULL; /* end of list */
if (head == NULL)
{
  head = new_node;
  tail = new_node;
}
else
{
  /* tail can't be NULL if head isn't */
  tail->next = new_node;
  tail = new_node; /* new end of list */
}

```

Going to a specific node is less efficient than for an array, since with an array you know where everything is in memory, but for a linked list you have to follow all the pointers until you get to the one you want. Similarly, deleting from the end is inefficient, because you have to search through to update the next pointer of the next-to-last node. But deleting from the front is very efficient. So to delete the entire list, do

```

node* cur_node = head;
node* next_node;
while (cur_node)
{
  next_node = cur_node->next;
  /* delete the contents of cur_node, if necessary */
  delete cur_node;
  cur_node = next_node;
}
head = NULL;
tail = NULL; /* if you're keeping a tail pointer */

```

And that's pretty much it. Iterating through the list is very simple:

```

node* cur_node = head;
while (cur_node)
{
  /* do stuff with cur_node */
  cur_node = cur_node->next;
}

```

You can also have a doubly-linked list where every node has a pointer to the one before as well as the one after--that makes inserting and removing stuff from the middle of the list very efficient.

---

### Post by jim_24601 on 2008-07-04
That will probably be the last you'll hear of me until next week, since it is now the weekend in my time zone and my internet connection at home isn't working at the moment :( :( But good luck, anyway.

---

### Post by tekkenlord on 2008-07-07
Thank you very much for your help Jim! I think that this will work for me.

---

