---
title: "follow up question on a problem I have with C"
date: 2007-10-21
forum: Programming Talk
---

### Post by nite owl on 2007-10-21
Hi around 2 days ago I put up a post asking about binary conversion of a normal text file and how to do it.

Well just so I am sure I actually have to do that, I wouldn't want to get it wrong the question actually states:

Convert the data in the file(normal .txt file) into record structured format and store in a binary file.

Now is this what I thought it was, converting all the data in the file to binary or is it something simpler? Just a little curious. Because it doesnt actually say convert to binary, it only says convert to record structured format?

Does anyone have any insight on this? Or am I just totally wrong :) lol anyway just making sure I dont get anything wrong. Thanks.

---

### Post by gradedcheese on 2007-10-21
That means: read some text, store it in memory in some structs, then write those structs to an output file.  The output is binary because it's no longer ASCII text data.  An application that knows the format (ie: your struct) can then read that file directly into structs in memory without needing to parse any text.

Hypothetically:

```

struct person_record {
   char name[128];
   unsigned int age;
} p;

/* fill in p's fields, like */
p.age = 20;

/* write the contents of p directory to a file */
write(outfile, &p, sizeof(struct person_record);

```

Do you see how this is different from a text file?  What would the output 'look' like in a text editor?

---

### Post by nite owl on 2007-10-21
thanks for the reply, basically the original text file is a bunch of records set up like this. Each new record is represented by a new line.


2, 31, drums
3, 10, car
7, 18, guitar
...etc

3 distinct fields of the record; itemID, customerID and description of the Item. Then that needs to be converted into record structured format i.e.

typedef struct RECORD_T
{
  int itemID;
  int customerID;
  char description[10];
} RECORD_TYPE;

....Then stored in a binary file. Later the fields are to be converted into a binary tree. Also just a lminor matter, how would you differentiate between records in the txt file. Meaning how would you get the C program to recognise "ok this is a new line, meaning new record".

---

### Post by gradedcheese on 2007-10-21
Well, "new line" is just a character, '\n' to be specific (on Windows systems it's two characters, "\r\n").  You can therefore parse the file by looking for '\n' or take a look at existing routines that read a line of input...

---

### Post by nite owl on 2007-10-21
> **gradedcheese said:**
>  You can therefore parse the file by looking for '\n' or take a look at existing routines that read a line of input...

Hi thanks for that, of course I knew about \n, but just wasnt sure if it would still work when reading from a text file or it just needed something else to symbolise a new line. Thanks for the confirmation.

---

### Post by j_g on 2007-10-21
See the post I made in your other thread. You pad out that 10 char array with spaces if the description is less than 10 spaces. Then, you _always_ write out those 10 chars. There's no need to terminate the array with a '\n' (nor even a '\0') at all, nor write such a terminator to the file.

A "record" implies that every entry in your data file is the same size. That means that every description _must_ be exactly 10 chars, no more or less. You truncate longer descriptions to only 10 chars. You pad out (with spaces) any description less than 10 chars.

---

### Post by DavidBell on 2007-10-21
If your problem is parsing the files, use fgets() and strtok(). I think gcc also supports getline() as a non-standard C function. DB

---

### Post by nite owl on 2007-10-21
I thought I would put up all that I have so far so I can be clearer.

```

#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>

struct record {
  int customerID;
  int itemID;
  char description[10];
};

int main() {

  //Setup a pointer to the struct
  struct record* data;
  data = (struct record*) malloc(sizeof(struct record));
  
  char c;     /* declare a char variable */
  FILE *file; /* declare a FILE pointer  */

  file = fopen("sales.txt", "r");
  /* open a text file for reading */

  if(file==NULL) {
    printf("Error: can't open file.\n");
    /* fclose(file); DON'T PASS A NULL POINTER TO fclose !! */
    return 1;
  }
  else {
    printf("File opened successfully. Contents:\n\n");

    while(1) {     /* keep looping... */
      c = fgetc(file);
      if(c!=EOF) {
        printf("%c", c); /*this would be replaced with the code for organising the data in the file into the record structure*/
        .
        .
        .
        .
         .......etc
        /* print the file one character at a time */
      }
      else {
        break;     /* ...break when EOF is reached */
      }
    }

    printf("\n\nNow closing file...\n");
    fclose(file);
    system("PAUSE");
    return 0;
  }
}


```

So I guess I have made some progress but am now stuck on actually feeding the program into my file and organizing each line in my .txt file into the record structure I have created and creating an array to hold each of the record entries. Then simply copy the array to a binary file. So as soon as I figure out how to feed what I have on each line of the txt file into my record structure and then into an array I should be able to de-stress lol

---

### Post by Compyx on 2007-10-21
A few comments, meant to be helpful, not bashing ;)

Your loop will run forever since you've declared 'c' as char. EOF is guaranteed to be a value that doesn't fit in a char. fgetc() returns an int, so declare 'c' as an int.

Get rid of 'system("PAUSE")', that's non-portable.

Don't use // comments unless you're writing C99 (portability again).

Don't cast malloc()'s return value, it will hide errors. The way I always call malloc() is like this:
```

data = malloc(sizeof *data);

```
This way, should you ever decide to change the type of 'record', you don't have to change the 'sizeof ..' portion.

Also keep in mind that a compiler might add padding to struct-members, so writing a struct to a file on one machine and reading it on another might cause problems.
You should look into serializing/deserializing data. (look it up with Google or whatever).

---

### Post by nite owl on 2007-10-21
ok I have made some improvements with my code, I realise I was way off with reading in one char at a time. So now I am using fgets and it is displaying a single line on the screen which is great since its only reading in one line now; which is " 5,18,drum". Could anyone let me know now how I would put that into my record structure so that 
customerID = 5
itemID = 18
description = drum

```
#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>

struct record {
  int customerID;
  int itemID;
  char description[10];
};

int main() {

  //Setup a pointer to the struct
  struct record* data;
  data = (struct record*) malloc(sizeof(struct record));

  char string[11];     /* declare a char variable */
  FILE *file; /* declare a FILE pointer  */

  file = fopen("sales.txt", "r");
  /* open a text file for reading */

  if(file==NULL) {
    printf("Error: can't open file.\n");
    /* fclose(file); DON'T PASS A NULL POINTER TO fclose !! */
    return 1;
  }
  else {
    printf("File opened successfully. Contents:\n\n");
    fgets (string , 10 , file);
    puts (string);
     fclose (file);
    }

    printf("\n\nNow closing file...\n");
    fclose(file);
    system("PAUSE");
    return 0;

}
```

---

### Post by dwhitney67 on 2007-10-21
A couple of comments:

1) When you declare a variable, always initialize it.  Thus something like the following is more appropriate:

```
struct record *data = malloc( sizeof *data );
FILE *file = fopen("sales.txt", "r" );
char string[11] = {0};
```

2) Do not add comments to your code that indicate the obvious.  For example,

```
char string[11]; /* declare a char variable */
```

3) For a small program like yours, this next tidbit does not really apply, however it is good practice to declare a variable at the closest point as to where it will be used; it makes the code easier to read and it does not require the review to jump back to a "declarations area" to see a variable's declaration type.

4) Try to minimize the number of return points in a function.

5) Declare complex objects (e.g. structures) with a name that makes it stand-out differently from a regular variable declaration.  Thus in lieu of "struct record", consider using "struct Record".


Anyhow, from your code, you are missing a few things:

1) you need to open another file that will be used for storing the binary data

2) you are not reading _all_ of the contents of the input file; consider using a while-loop construct, checking for EOF by using feof() before entering the loop.

3) I would suggest you make your 'string' variable larger.  There needs to be enough space to not only store the visible text contained in each line of the input data file, but also for the carriage return at the end of each line, and then a null character.  Pick an arbitrary length, say 80.

4) When you use fgets(), do not hard-code the data size, use of sizeof( string ) instead.

5) Once you have read in the text string, consider using sscanf() to break it apart into individual components, using care not to overflow any string buffer.

6) Finally, use fwrite() to output your Record(s) to the binary file.

I think that should be enough info above to get you going.  Use the "man-pages" to get info on any of the C library functions mentioned above.

Good luck.

---

### Post by mjwood0 on 2007-10-22
> **dwhitney67 said:**
> 
3) For a small program like yours, this next tidbit does not really apply, however it is good practice to declare a variable at the closest point as to where it will be used; it makes the code easier to read and it does not require the review to jump back to a "declarations area" to see a variable's declaration type.


Please take this with some caution.  A strict ANSII C compiler will not let any executable line of code come before a declaration.  Therefore, all declarations MUST come at the beginning.

Just something to note.  C++ does allow defining variables more liberally.

---

### Post by dwhitney67 on 2007-10-22
Can you provide an example of a strict C compiler that you are referring to.  I hope it's not Visual Studio?

If one uses *gcc* with the *-ansi* option, it allows one to declare variables anywhere in their code.  This is based on ISO C standards from 1990 (note that a newer standard was released in 1999, which shares many of the same features as its predecessor).

So please let me know which compiler you are referring to.  If anything is needed, it is to put pressure on the vendors of these non-compliant compilers to upgrade so that they are compliant.

---

### Post by mjwood0 on 2007-10-22
> **dwhitney67 said:**
> Can you provide an example of a strict C compiler that you are referring to.  I hope it's not Visual Studio?

If one uses *gcc* with the *-ansi* option, it allows one to declare variables anywhere in their code.  This is based on ISO C standards from 1990 (note that a newer standard was released in 1999, which shares many of the same features as its predecessor).

So please let me know which compiler you are referring to.  If anything is needed, it is to put pressure on the vendors of these non-compliant compilers to upgrade so that they are compliant.

Interesting.  The gcc compiler here at work on the UNIX system allows definitions anywhere.  However, the IDE we use definitely does not!  

One more example of why I really need to learn another language and get out the embedded development once and a while...:(

---

### Post by dwhitney67 on 2007-10-22
If you are working in an embedded environment, it is not uncommon for vendors to provide cross-compilers that are a generation or two old.  These compilers has been optimized to support the particular CPU that the vendor has chosen to support.

In the past (over 4 years ago) I used GCC (ver 3.2?) to cross-compile for the RAD750, which is a radiation-hardened PowerPC.  I had no trouble declaring variables in between executable lines of code during that period either.

One thing that is annoying is seeing a variable that has been declared but not initialized.  And in most cases, the only way to initialize a variable is to include executable code.  For example:
```
int i;
int j;
int k;
i = 5;
j = i;
k = 10;
```

becomes
```
int i = 5;
int j = i;
int k = 10;
```

Anyhow, in your case, until you are provided with an updated compiler, I guess you are stuck with declaring variables at the beginning of a function and then implementing code afterwards.

---

### Post by mjwood0 on 2007-10-22
> **dwhitney67 said:**
> Anyhow, in your case, until you are provided with an updated compiler, I guess you are stuck with declaring variables at the beginning of a function and then implementing code afterwards.

In a way, I quite like this approach.  I really think it makes it clear at the beginning of a function exactly what is being declared locally.  But then again, I guess I'm so used to it.

Actually, I think I figured out what it was.  Most of our compilers are used with the MISRA C Rules.  For a good description, see [here]("http://www.embedded.com/story/OEG20020625S0040").

---

