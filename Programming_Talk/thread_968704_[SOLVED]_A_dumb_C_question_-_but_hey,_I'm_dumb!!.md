---
title: "[SOLVED] A dumb C question - but hey, I'm dumb!!"
date: 2008-11-02
forum: Programming Talk
---

### Post by anewguy on 2008-11-02
I have some code I'm working with that has the following items:

extern char keydesc[255][128];
extern unsigned char key[255][2][128];


I need to preload these with some items from other tables, defined the same way except static in the function and containing values at definition.

I apparently can't go the following:

keydesc = pv2keydesc

--or --

keydesc[0] = pv2keydesc[0];


What I want to do is just copy one table, defined exactly the same but with values preloaded, to the table declared extern.

I'm sure this must be simple........but...........

Thanks in advance!!

Dave :)

---

### Post by shimmey on 2008-11-02
I don't know what you really want to do.
But in C language, the array data is sharing, you can read the data through a pointer which point to them.
If you have to store the original data, prevent them from modifying, you can read and copy the data one by one when you need to do.
For copying all the data in array one time, the C method is use the "for". Indeed, it is done by copying the records in array one by one, too...
See what you want to do...

---

### Post by anewguy on 2008-11-02
While the tables with the values are defined the same way, there are only 14 active values in them.  I just want an easy way to load the key ande keydesc with the values from pv2key and pv2keydesc tables.  I was hoping there was some kind of single "move" or "copy" I could use.  I'm really not knowledgeable in terms of the programming in C (I understand the concepts, etc., from many years of experience in other languages) in how to handle these arrays.

What would a sample piece of code to copy a 3 dimensional array to another 3 dimentional array look like - pseudo code is okay if you don't want to provide the actual statements.  Do I have to copy each element of pv2key[x][x][y] to key[x][x][y], then increment y?  Can I copy pv2key[x][y] to key[x][y], increment y to get the second def, then increment x and do it all over again?

Hope that explains where I'm at - not a novice to programming by any means, and really not a novice at C either, but it's been like 12 or 13 years since I really did anything, so I just don't remember stuff anymore.

Think you can help an old duffer out?  :)

Thanks!
Dave :)

---

### Post by Npl on 2008-11-02
Try with
extern char keydesc**[255][128]**;
extern unsigned char key[2]**[255][128]**;

keydesc = key[0];

I havent run that code, but I think it should work. Array Dimensions must match in C and key[0] has the same dimension if you define it as above.

If it doesnt work, then you can also define a struct which will work for sure.

---

### Post by dribeas on 2008-11-03
> **anewguy said:**
> I have some code I'm working with that has the following items:

extern char keydesc[255][128];
extern unsigned char key[255][2][128];


You cannot copy the whole array from one place to another with some kind of copy operation on arrays. You can copy elements one by one (and iterate over the whole array), or you can copy whole memory locations.

Iterate over the arrays:
```

#define DIM1 256
#define DIM2 128
char origin[DIM1][DIM2];
char dest[DIM1][DIM2]; 

// Load data into origin
int i, j;
for ( i = 0; i < DIM1; ++i )
{
   for ( j = 0; j < DIM2; ++j )
   {
      dest[i][j] = origin[i][j];
   }
}

```

This has the flexibility of being able to control iterators on origin and destination arrays. You could, for example transpose if the dimensions were interchanged quite easily, or add new dimensions:
```

char origin[DIM1][DIM2];
char dest[DIM2][2][DIM1];
int i,j;
for ( i = 0; i < DIM1; ++i )
{
   for ( j = 0; j < DIM2; ++j )
   {
      dest[j][0][i] = origin[i][j];
   }
}

```

Copy memory areas:
```

#define DIM1 256
#define DIM2 128
char origin[DIM1][DIM2];
char dest[DIM1][DIM2]; 

memcpy( dest, origin, DIM1*DIM2*sizeof(char) );

```

This is more concise and probably faster, but will only make exact copies of memory, that is, you cannot change dimension ordering (switch first and second dimensions), and origin and destination must be compact memory areas (there cannot be one other dimension in either origin or destination to the right of DIM1.

---

### Post by anewguy on 2008-11-03
Given these 2 source tables (truncated values as noted to post here):


static unsigned char pv2keys[255][2][128] = 
{
	{
		{ // *** LAMSSMAL Challenge Key
		0x67, 0x45, 0x23, 0x01, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00 },
		{ // *** LAMSSMAL Response Key
		0x4c, 0x61, 0x4d, 0x53, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
		0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00 }
	},{...rest of values in table -> but for this example I only need the 1st main entry anyway



static char pv2keydesc[255][128] = 
{ 
	{'R','e','s','e','t',0},
  ...rest of values in table -> but for this example I only need the 1st main entry anyway



And these 2 destination tables:

extern char keydesc[255][128];
extern unsigned char key[255][2][128];



And these statements:

	key = pv2keys[0];
        keydesc = pv2keydesc[0];


I get the following errors at compilation:

error: incompatible types in assignment
error: incompatible types in assignment


I admit I'm an idiot here, so thanks for the suggestion.  Unfortunately I'm still getting the errors.

I also tried:

	key[0] = pv2keys[0];
        keydesc[0] = pv2keydesc[0];

and I still get the same error.  I was hoping I could do just do:

	key = pv2keys;
        keydesc = pv2keydesc;

but that doesn't work either.

I know it's got to be something simple and stupid - I just don't know what!  :)

---

### Post by anewguy on 2008-11-03
Got around it by doing the following:

	memcpy(key[0][0], pv2keys[0][0],128);
	memcpy(key[0][1], pv2keys[0][1],128);
        strcpy(keydesc[0], (char *)pv2keydesc[0]);


I think I understand the 1st 2 - copying memory for 128 bytes in pv2keys[x][y] to key[x][y], but I don't understand what the (char *) is doing on the 3rd line - I mean I know as much as knowing it's a character pointer, but I don't understand the bit about being in parens, nor do I understand why I can't just strcpy pv2keydesc[0]. If someone could explain to me more just exactly what these are doing and WHY they have to be that way - in particular the (char *) stuff on line 3, I would GREATLY appreciated it!

Thanks again,
Dave

---

### Post by Tony Flury on 2008-11-03
> 
Got around it by doing the following:

memcpy(key[0][0], pv2keys[0][0],12;
memcpy(key[0][1], pv2keys[0][1],12;
strcpy(keydesc[0], (char *)pv2keydesc[0]);


I think I understand the 1st 2 - copying memory for 128 bytes in pv2keys[x][y] to key[x][y], 

using memcpy is a safe way of doing what you want - although you are missing a close bracket on both calls.

> 
but I don't understand what the (char *) is doing on the 3rd line - I mean I know as much as knowing it's a character pointer, but I don't understand the bit about being in parens

Putting (char *) in front of a value is called casting - effectively telling the compiler to ignore what it might think the type is, and to treat it as a char *.

> 
 nor do I understand why I can't just strcpy pv2keydesc[0]. 

Because strcpy requires arguments of type char * to work - and pv2keydesc is not a char *.

Actually memcpy is a far safer thing to do than strcpy - strcpy is for copying strings - and relies on the memory being Null terminated - it might work correctly in your case, but it is a very bad habit to get into to copy around memory.

> 
If someone could explain to me more just exactly what these are doing and WHY they have to be that way - in particular the (char *) stuff on line 3, I would GREATLY appreciated it!


I hope that explains it.

---

### Post by ad_267 on 2008-11-03
+1 for memcpy. It's a lot simpler and faster than using for loops.

---

### Post by anewguy on 2008-11-04
Thank you tony Flury!!!  I think I understand it better now - thanks for an explanation I could follow!!

Dave

---

