---
title: "[SOLVED] passing an array by reference in c?"
date: 2008-11-29
forum: Programming Talk
---

### Post by Bulletbeast on 2008-11-29
Look, I thought it worked like this:

```

int tune(note **tuning, int *strings, const char *tunestr)
{
 ...
}

int main(int argc, char** argv)
{
 int strings;
 note tuning[8];
 ...
 tune(&tuning, &strings, "DADGAD");
 ...
}
```

However, this warns me for:
[b]chord.c: In function ‘main’:
chord.c:246: warning: passing argument 1 of ‘tune’ from incompatible pointer type[/b]
and segfaults at runtime. What am I doing wrong?

---

### Post by slavik on 2008-11-29
umm, arrays are always passed as references, so I suggest changing tune to accept note * and pass it tunning.

arrays are not copied when passed to functions. only stand alone things are (int, float, double, char).

---

### Post by slavik on 2008-11-29
umm, arrays are always passed as references, so I suggest changing tune to accept note * and pass it tunning.

arrays are not copied when passed to functions. only stand alone things are (int, float, double, char).

---

### Post by Nemooo on 2008-11-29
The ampersand (&) is not needed, it's just:

```
int tune(note ***tuning**, int *strings, const char *tunestr)
{
 ...
}

int main(int argc, char** argv)
{
 int strings;
 note tuning[8];
 ...
 tune(**tuning**, &strings, "DADGAD");
 ...
}
```

---

### Post by WitchCraft on 2008-11-29
> **Nemooo said:**
> The ampersand (&) is not needed, it's just:

```
int tune(note ***tuning**, int *strings, const char *tunestr)
{
 ...
}

int main(int argc, char** argv)
{
 int strings;
 note tuning[8];
 ...
 tune(**tuning**, &strings, "DADGAD");
 ...
}
```

Correct, and make the 8 a variable, so you can pass it as argument to the function, just in case  you want to resize your tuning array.

---

### Post by albandy on 2008-11-29
note **tunning is an array of note arrays. It's the same but I prefer to define it in this way:

int (note *tunning[] ....)

and in main section:

main ()
{
note tunning[n][m]; /* 0 < m,n <= max_array_size */

}



There is a lot of time I'm not programming in C, but I  recommend you the Kerningan and Ritchie book.

---

### Post by dwhitney67 on 2008-11-29
Boy oh boy... lots of bad/incorrect advice in this thread!

The following is an example function definition for passing an array by value:
[php]
int tune(note* tuning, ...)
{
  ...
}
[/php] 

The following is an example that allows for the passing of an array by reference (that is, a reference of the address of the array):
[php]
int tune(note** tuning, ...)
{
  ...
}
[/php]

The latter definition is helpful if passing a pointer to an array that has not been initialized.  If memory is allocated for the array in the function tune(), the only way to return the pointer to the newly allocated memory location is to accept the pointer to the array as shown above.  This is common, for instance, when implementing a linked list when the head node is initially null.

The issue the OP is encountering has to do with the lack of casting; he needs to be specific as to which type of pointer he wishes to pass.  Thus when calling tune() as described in the OP, the following adjustment needs to be made:
[php]
tune((note**) &tuning, &strings, "DADGAD");
[/php]
Now the program should compile without any warning wrt to the incompatible pointer type.  Now whether this solves the seg-fault is unknown.  The OP would have to post more code in his tune() method for an assessment to be made.

---

### Post by Bulletbeast on 2008-11-29
One way or another, I got my arguments passed. But a memcpy in my tune function seems to misfire.

```

/* that's my note type */
typedef enum {
NO_NOTE=-1, A=0, As=1, Bb=1, B=2, C=3, Cs=4, Db=4, D=5, Ds=6, Eb=6, E=7, F=8, Fs=9, Gb=9, G=10, Gs=11, Ab=11
} note;

/* and that's an utility function used below */
char* nstr(note n, int flats)
{
  /* Turn a note into string form */
  char* c;
  switch (n)
  {
    case A: c="A"; break;
    case B: c="B"; break;
    case C: c="C"; break;
    case D: c="D"; break;
    case E: c="E"; break;
    case F: c="F"; break;
    case G: c="G"; break;
    case As: if (flats) c="Bb"; else c="A#"; break;
    case Cs: if (flats) c="Db"; else c="C#"; break;
    case Ds: if (flats) c="Eb"; else c="D#"; break;
    case Fs: if (flats) c="Gb"; else c="F#"; break;
    case Gs: if (flats) c="Ab"; else c="G#"; break;
  }
  return c;
}

```

```

#define MAX_STRINGS 8

int tune(note *tuning, int* strings, const char *tunestr)
{
  int newstrings=0, i;
  note newtuning[MAX_STRINGS];
  for (i=0; i<strlen(tunestr); i++)
  {
    printf("%s",tunestr+i);
    if (i>=MAX_STRINGS) return INVALID_TUNING;
    if (strncmp(tunestr+i,"A#",2)==0 || strncmp(tunestr+i,"Bb",2)==0) {newtuning[newstrings]=As; newstrings++; i++;} else
    if (strncmp(tunestr+i,"C#",2)==0 || strncmp(tunestr+i,"Db",2)==0) {newtuning[newstrings]=Cs; newstrings++; i++;} else
    if (strncmp(tunestr+i,"D#",2)==0 || strncmp(tunestr+i,"Eb",2)==0) {newtuning[newstrings]=Ds; newstrings++; i++;} else
    if (strncmp(tunestr+i,"F#",2)==0 || strncmp(tunestr+i,"Gb",2)==0) {newtuning[newstrings]=Fs; newstrings++; i++;} else
    if (strncmp(tunestr+i,"G#",2)==0 || strncmp(tunestr+i,"Ab",2)==0) {newtuning[newstrings]=Gs; newstrings++; i++;} else
    if (strncmp(tunestr+i,"A",1)==0) {newtuning[newstrings]=A; newstrings++;} else
    if (strncmp(tunestr+i,"B",1)==0) {newtuning[newstrings]=B; newstrings++;} else
    if (strncmp(tunestr+i,"C",1)==0) {newtuning[newstrings]=C; newstrings++;} else
    if (strncmp(tunestr+i,"D",1)==0) {newtuning[newstrings]=D; newstrings++;} else
    if (strncmp(tunestr+i,"E",1)==0) {newtuning[newstrings]=E; newstrings++;} else
    if (strncmp(tunestr+i,"F",1)==0) {newtuning[newstrings]=F; newstrings++;} else
    if (strncmp(tunestr+i,"G",1)==0) {newtuning[newstrings]=G; newstrings++;} else
    return INVALID_TUNING;
  }
  for (i=0; i<newstrings; i++) printf("%s",nstr(tuning[i],0)); printf(" ");
  for (i=0; i<newstrings; i++) printf("%s",nstr(newtuning[i],0)); printf(" ");
  memcpy(tuning, newtuning, MAX_STRINGS);
  for (i=0; i<newstrings; i++) printf("%s",nstr(tuning[i],0)); printf("\n");
  return 0;
}

int main(int argc, char** argv)
{
  int strings=0;
  note tuning[MAX_STRINGS];

  tune(tuning, &strings, "EADGBE");

...

  tune(tuning, &strings, "DADGAD");

...
}

```

The printfs result in:

```

EADGBEADGBEDGBEGBEBEEAAAAA EADGBE EAAAA
DADGADADGADDGADGADADDEAAAA DADGAD DAAAA

```

when I expect:
```

EADGBE EADGBE EADGBE
EADGBE DADGAD DADGAD

```

I think I grasp why this may happen, but.. how do I do it right?

---

### Post by Bulletbeast on 2008-11-30
Any help?

---

### Post by Nemooo on 2008-11-30
> **dwhitney67 said:**
> Boy oh boy... lots of bad/incorrect advice in this thread!

The following is an example function definition for passing an array by value:
[php]
int tune(note* tuning, ...)
{
  ...
}
[/php]

Wrong. Arrays are always passed by reference. If it was passed by value (as you say) this wouldn't print zbc, but abc:

[php]#include <stdio.h>

void func(char *arr)
{
	arr[0] = 'z';
}

int main(void)
{
	char arr[] = "abc";

	func(arr);
	puts(arr);
}[/php]

> **dwhitney67 said:**
> ...
[php]
tune((note**) &tuning, &strings, "DADGAD");
[/php]...

Can you provide a working example for this?

---

### Post by CptPicard on 2008-11-30
> **dwhitney67 said:**
> Boy oh boy... lots of bad/incorrect advice in this thread!

IMO only because there is an underlying non-understanding of relationship between C arrays and pointers, plus a weird mix-up of C++ references into the picture. :)

For me, "passing an array by value", if the pointer/array-duality is not further explained, would mean making a copy of the entire contents of the array on the stack, which is a completely logical way of looking at it.

Of course, if you *know* beforehand that a C array *is**a pointer to the first member, then of course you're passing *that* by value the usual way, but the conceptual "entire" array is the one that is being referred to by that pointer...

---

### Post by Sydius on 2008-11-30
I got schooled on this in ##c++ a couple weeks ago.

An array isn't a pointer, but it can degrade to one.  So when you have a function that takes a pointer to the same data type as the array contains, the array (when passed as that parameter) will silently turn into a pointer to the first element.  It's no longer an array at that point (in the scope of the function), but just a pointer (and there is a difference).

Since it is just a pointer to the first element, you are indeed accessing the same memory that the array (from the scope that called the function) is using, though you didn't really pass the array at all.  You just degraded it to a pointer, and passed that instead.

[php]
void someFunc(char *str)
{
  // str is not an array, but just a pointer.
}

int main(int argc, char **argv)
{
  char something[256];
  someFunc(something);
  return 0;
}
[/php]

Note that this is according to the C++ standard, not C.  But I assume it's the same.

---

### Post by nvteighen on 2008-12-01
Some facts:

1) In C **everything is passed by value**. So, if you pass a pointer, you're copying its value to another place. That's it. Don't overthink this!

2) **There are no arrays in C** (as there are no strings either). Forget that. What you have is a pointer to an element and some allocated memory you access to by using an offset with respect to the pointer. Of course, we **conceptually** can think of them as arrays, and C's syntax sugar (a[x]) makes it look as an array, when you actually are doing (*(a + x)). The problem with C is that you have to learn these implementation details to know your way in it.

So, always think in terms of copying values. When passing an "array" you're copying a pointer... that's why you don't need the & operator. But, as the pointer is a pointer (:p), you can dereference it to set/get whatever it is pointing to. That's why you get the illusion of "pass by reference".

Summary: just pass the "array" variable and don't fiddle with double-pointers. Usually you won't use double-pointers for this unless you are using a 2D matrix or need to modify the array's allocation place.

---

### Post by Bulletbeast on 2008-12-02
Thanks. In fact, I know that, but it doesn't help me at all with my second problem. Or should I start a new thread?

---

