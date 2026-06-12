---
title: "segmentation fault in fwrite"
date: 2010-02-01
forum: Programming Talk
---

### Post by gagraf on 2010-02-01
For program from C How To Program, 3rd Ed., I get run time error segmentation fault fwiite ( fprintf) in library libc.so.6.  I used gcc version : 4.2.3 (ubuntu 4.3.2-2umbuntu7).  The same code works fine on cygwin: gcc version 3.4.4(cygwin special, gdc 0.12).  The code works in Windows (Win98, WinNt and Windows Vista using microsoft VC.

---

### Post by Some Penguin on 2010-02-01
Have you considered showing the actual code and a stack trace?

---

### Post by lisati on 2010-02-01
> **gagraf said:**
> For program from C How To Program, 3rd Ed., I get run time error segmentation fault fwiite ( fprintf) in library libc.so.6.  I used gcc version : 4.2.3 (ubuntu 4.3.2-2umbuntu7).  The same code works fine on cygwin: gcc version 3.4.4(cygwin special, gdc 0.12).  The code works in Windows (Win98, WinNt and Windows Vista using microsoft VC.

Without actually seeing the program code that you were actually using, it's difficult for us to see what is likely to be causing the problem. My best guess at the moment is that you have prepared a string to print, and somehow it has ended up without the binary zero that C often uses to mark the end of strings.

---

### Post by gagraf on 2010-02-02
> **gagraf said:**
> For program from C How To Program, 3rd Ed., I get run time error segmentation fault fwiite ( fprintf) in library libc.so.6. I used gcc version : 4.2.3 (ubuntu 4.3.2-2umbuntu7). The same code works fine on cygwin: gcc version 3.4.4(cygwin special, gdc 0.12). The code works in Windows (Win98, WinNt and Windows Vista using microsoft VC.
 
After more study, I found 2 programs, one worked and the other failed with segmentation fault in fwrite.
 
Bad one:
. . . 
if ( ( fpin = fopen( arg[1], "r" ) ) == NULL )
printf( "File could not be opened\n" );
 
out_file = strtok(arg[1], ".");
strcat(out_file, ".pos");
if ( ( fpout = fopen( out_file, "w" ) ) == NULL )
printf( "File could not be opened\n" );
 
for ( i=1; i<10; i++ )
fscanf(fpin, "%d %d %d %d %d %d %d %d %d",
&A[i][1], &A[i][2], &A[i][3], &A[i][4], &A[i][5],
&A[i][6], &A[i][7], &A[i][8], &A[i][9] );
. . . 
fprintf( fpout, "Possible values (* means original value of cell):\n");
 
Good one:
. . .
if ( ( fpin = fopen( arg[1], "r" ) ) == NULL )
printf( "File could not be opened\n" );
 
for ( i=1; i<10; i++ )
fscanf(fpin, "%d %d %d %d %d %d %d %d %d",
&A[i][1], &A[i][2], &A[i][3], &A[i][4], &A[i][5],
&A[i][6], &A[i][7], &A[i][8], &A[i][9] );
. . . 
out_file = strtok(arg[1], ".");
strcat(out_file, ".pos");
if ( ( fpout = fopen( out_file, "w" ) ) == NULL )
printf( "File could not be opened\n" );
. . . 
fprintf( fpout, "Possible values (* means original value of cell):\n");
 
 
The only difference is where the file fpout is opened.

---

### Post by Some Penguin on 2010-02-02
foo = NULL

sets foo to NULL, not tests whether foo is NULL at that time.

---

### Post by dwhitney67 on 2010-02-02
> **Some Penguin said:**
> foo = NULL

sets foo to NULL, not tests whether foo is NULL at that time.

@ the OP - 

In other words, there are issues in the code with statements like:
```

if ( ( fpin = fopen( arg[1], "r" ) ) = NULL )

```
It should be:
```

if ( ( fpin = fopen( arg[1], "r" ) ) **==** NULL )

```

---

### Post by Habbit on 2010-02-02
A common solution to the problem dwhitney pointed is making the comparison the other way around, i.e. writing "NULL == (my complicated expression here)" instead of "(something) == NULL". That way, if you get it wrong and actually write "NULL = (whatever)", the compiler will throw an error along the lines of "assignment to a constant", thus making the problem detectable at compile time.

---

### Post by gagraf on 2010-02-02
> **gagraf said:**
> After more study, I found 2 programs, one worked and the other failed with segmentation fault in fwrite.
 
Bad one:
. . . 
if ( ( fpin = fopen( arg[1], "r" ) ) == NULL )
printf( "File could not be opened\n" );
 
out_file = strtok(arg[1], ".");
strcat(out_file, ".pos");
if ( ( fpout = fopen( out_file, "w" ) ) == NULL )
printf( "File could not be opened\n" );
 
for ( i=1; i<10; i++ )
fscanf(fpin, "%d %d %d %d %d %d %d %d %d",
&A[i][1], &A[i][2], &A[i][3], &A[i][4], &A[i][5],
&A[i][6], &A[i][7], &A[i][8], &A[i][9] );
. . . 
fprintf( fpout, "Possible values (* means original value of cell):\n");
 
Good one:
. . .
if ( ( fpin = fopen( arg[1], "r" ) ) == NULL )
printf( "File could not be opened\n" );
 
for ( i=1; i<10; i++ )
fscanf(fpin, "%d %d %d %d %d %d %d %d %d",
&A[i][1], &A[i][2], &A[i][3], &A[i][4], &A[i][5],
&A[i][6], &A[i][7], &A[i][8], &A[i][9] );
. . . 
out_file = strtok(arg[1], ".");
strcat(out_file, ".pos");
if ( ( fpout = fopen( out_file, "w" ) ) == NULL )
printf( "File could not be opened\n" );
. . . 
fprintf( fpout, "Possible values (* means original value of cell):\n");
 
 
The only difference is where the file fpout is opened.
 
 
I MADE A TYPO:
 
The actual code has: == NULL .

---

### Post by Maz_ on 2010-02-02
I hope the filename which you provide as argument has 3 characters wide file extension.

---

### Post by gagraf on 2010-02-03
> **Maz_ said:**
> I hope the filename which you provide as argument has 3 characters wide file extension.
 
Yes, I used jan.dat for argument and the output file is jan.pos.

---

### Post by ibuclaw on 2010-02-03
I think you really do need to provide more information on the Bad one.

If it seg faults, it sounds like fpout gets unreferenced somewhere along the line, as this example:
```

#include <stdio.h>
#include <string.h>

int main(int argc, char **arg)
{
    FILE *fpin, *fpout;
    char A[10][10];
    char *out_file;
    int i;

    if ( ( fpin = fopen( arg[1], "r" ) ) == NULL )
        printf( "File could not be opened\n" );

    out_file = strtok(arg[1], ".");
    strcat(out_file, ".pos");
    if ( ( fpout = fopen( out_file, "w" ) ) == NULL )
        printf( "File could not be opened\n" );

    for ( i=1; i<10; i++ )
        fscanf(fpin, "%d %d %d %d %d %d %d %d %d",
                &A[i][1], &A[i][2], &A[i][3], &A[i][4], &A[i][5],
                &A[i][6], &A[i][7], &A[i][8], &A[i][9] );

    fprintf( fpout, "Possible values (* means original value of cell):\n");
}

```
Has no issues.

Regards
Iain.

---

### Post by dwhitney67 on 2010-02-03
> **tinivole said:**
> 
Has no issues.

Regards
Iain.

There would be an issue if the file could not be opened.  Surely, if either fpin or fpout are NULL, you do not wish for the program to continue?

Anyhow, a lot more error checking ought to be inserted into the program, including checking to see if argv[1] is supplied, or whether strtok() return a valid pointer or NULL.

As for the array A, why is the first element not referenced whatsoever?  The for-loop with the fscanf() starts with i being set to 1, not 0 (zero).

Hopefully the OP (gagraf) will post a complete listing of his code, rather than snips that leave too much to the imagination.

---

### Post by ibuclaw on 2010-02-03
> **dwhitney67 said:**
> There would be an issue if the file could not be opened.  Surely, if either fpin or fpout are NULL, you do not wish for the program to continue?


Of course ... I should have really appended 'given that you run it with the correct permissions and parameters' onto the previous post.

---

### Post by resander on 2010-02-04
Looks as fpout could be corrupted between its fopen and its use.

Check by two printfs, the first after fopen definition 
and the second after fscanf.

```

if ( ( fpout = fopen( out_file, "w" ) ) == NULL )
  printf( "File could not be opened\n" );
printf ( "1: fpout=%d\n" ,(int)fpout) ;

for ( i=1; i<10; i++ )
fscanf(fpin, "%d %d %d %d %d %d %d %d %d",
&A[i][1], &A[i][2], &A[i][3], &A[i][4], &A[i][5],
&A[i][6], &A[i][7], &A[i][8], &A[i][9] );
printf ( "2: fpout=%d\n" ,(int)fpout) ;
. . .
fprintf( fpout, "Possible values (* means original value of cell):\n");

```

If the printfs show different fpout values, then fscanf is causing the problem.

I have never used fscanf, but I think the datatypes in the format string
and the datatypes of the receiving variables must match. In the code 
above the data type of the A array must be int since the format is %d. 
If the data type of A is char then fscanf would soon begin to overwrite
other data, which might be fpout depending on the order of declarations.

---

### Post by Maz_ on 2010-02-04
yes. The array indexing and size of A. Well spotted. Betting my left testicle on bug being there!

---

### Post by gagraf on 2010-02-04
**Yes, fscanf has changed the value of fpout.  And, after changing the type of A from short to int, the changed bad program now works!  Thank you very much!**

---

