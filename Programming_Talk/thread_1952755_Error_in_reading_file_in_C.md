---
title: "Error in reading file in C"
date: 2012-04-04
forum: Programming Talk
---

### Post by skyjuice88 on 2012-04-04
Dear all,

I have this image/video compression project that is to be done in C.  I've been given this source code by my supervisor which is supposed to  be a working one and be compiled in Linux using a .sh file. So to compile I just have to type 'sh prog.sh' , right?

Assuming I have a sequence of 3 images in .pgm format (image141.pgm,  image142.pgm and image143.pgm). Some of the codes involved (only the  important ones) are

```

#define START_FRAME 141 
#define END_FRAME 143 
#define SKIP_FRAME 1 
#define INPUT_STRING "/home/folder/image%03d" 

 int main(){ 
int frameNo = START_FRAME;
int nx=1920, ny=1080;     //image resolution 
char fileName[128];  

 //this is the part of error
sprintf(fileName, INPUT_STRING, frameNo);
readPgm(frm1, fileName, nx, ny);  
} //end of main function  

//function readPGM 
void readPgm(unsigned char *frame, char * fileName, int nx, int ny) {  
int i, j;  
FILE *file;  
char str[128];
  
file = fopen(fileName,"r");
if (file == 0) {  
  printf("Open error in File read \n");
  }

fgets(str, 100, file);
for(j = 0; j < ny; j++) {
   for(i = 0; i < nx; i++) {
   fscanf(file,"%d", &frame[i + nx * j]);
   }
 }
 fclose(file);
}

```The command is supposed to copy the pixel value from the input file
(.pgm picture) to the character array frm1. 
When I tried to compile the code using make file (shell script), I got  this error message "In function 'readPgm' format '%d' expects argument  of type 'int *', but argument 3 has type 'unsigned char *' "
but when I tried to modify this to
fscanf(file,"%c", &frame[i + nx * j]);
the compiler gives no result. Is there something that I'm missing?

---

### Post by ve4cib on 2012-04-05
The problem is that you are trying to store an integer in a char.  "%d" in fscanf means you expect to read in a 4-byte integer.  The argument should therefore be a pointer to an int.

"&frame[i + nx * j]" is a pointer to an unsigned char, which is why you're getting that compiler warning.

When you say "the compiler gives no result" what exactly do you mean?  The warning goes away?  The problem persists?  Please be more specific.

---

### Post by skyjuice88 on 2012-04-05
> **ve4cib said:**
> The problem is that you are trying to store an integer in a char.  "%d" in fscanf means you expect to read in a 4-byte integer.  The argument should therefore be a pointer to an int.

"&frame[i + nx * j]" is a pointer to an unsigned char, which is why you're getting that compiler warning.

When you say "the compiler gives no result" what exactly do you mean?  The warning goes away?  The problem persists?  Please be more specific.
So in this case should I change %d to %c or should I change the function parameter to 
void readPGM (unsigned int *frame, int *fileName, int nx, int ny)? 

The program is supposed to get the pixel values from an input image file (readPGM), compress the image (a series of functions) and the resukt is then copied to a new image file (writePGM). The code is something like this:

```

#define START_FRAME 141
#define END_FRAME 143
#define SKIP_FRAME 1
#define INPUT_STRING "/home/skyjuice/s160-2/image%03d"

int main(int argv, char *argc[]){

int   nx  = 1920, ny = 1080, nxy;
frameNo = START_FRAME;
sprintf(fileName, INPUT_STRING, frameNo);
readPgm(frm1, fileName, nx, ny);


//then after several function operations, we would like to save the output image using 'writePGM'


writePgm(output_image, fileName, nx, ny);

} // end of main function

/read original frame
void readPgm(unsigned char *frame, char * fileName, int nx, int ny) {
  int i, j;
  FILE *file;
  char str[128];

  file = fopen(fileName,"r");
  if (file == 0) {
    printf("Open error in File read \n");
    // return(0);
  }
  fgets(str, 100, file);
  for(j = 0; j < ny; j++) {
      for(i = 0; i < nx; i++) {
    fscanf(file,"%d", &frame[i + nx * j]);
      }
  }
  fclose(file);
}


void writePgm(unsigned char *frame, char *fileName, int nx, int ny){
  int i, j;
  FILE *file;

  file = fopen(fileName, "w");
  fprintf(file, "P2 %d %d 255\n", nx, ny);
  for(j = 0; j < ny; j++) {
    for(i = 0; i < nx; i++) {
      fprintf(file,"%d ", frame[i + nx * j]);
    }
    fprintf(file, "\n");
  }
  fclose(file);
}

```

So if this program compiles successfully, there should be new image files generated under the same directory, am I right?

---

### Post by Tony Flury on 2012-04-05
> So if this program compiles successfully, there should be new image files generated under the same directory, am I right?
No - if the program compiles you will get a executable file - which you then need to run.

If you run it and it is successful, then you will get your image files.

All that compilation does is translate source code into an executable image.

---

### Post by skyjuice88 on 2012-04-05
> **Tony Flury said:**
> No - if the program compiles you will get a executable file - which you then need to run.

If you run it and it is successful, then you will get your image files.

All that compilation does is translate source code into an executable image.
I am using a .sh file to compile the code which looks something like this 
```

#! /bin/sh
gcc main.c func1.c func2.c func3.c -lm

```

and I type sh mkprog.sh in the Terminal. Is this the correct way of doing it? If there is no error message from the Terminal, how do I locate the executable file and how do I run it? Sorry, I'm new to compiling under Linux environment

---

### Post by dwhitney67 on 2012-04-05
> **skyjuice88 said:**
> I am using a .sh file to compile the code which looks something like this 
```

#! /bin/sh
gcc main.c func1.c func2.c func3.c -lm

```

and I type sh mkprog.sh in the Terminal. Is this the correct way of doing it? If there is no error message from the Terminal, how do I locate the executable file and how do I run it? Sorry, I'm new to compiling under Linux environment

Shell scripts are fine, but preferably you should use a Makefile.

But to answer your question, the executable should be located in the current directory where you are running the script.  Based on the contents of the script, your source code resides in the same directory.  After running the script, look for a file named "a.out".  To run it, enter at the terminal:
```

./a.out

```

---

### Post by skyjuice88 on 2012-04-16
Okay, now that I've changed the line to

```
fscanf(file,"%d", (int*)&frame[i + nx * j]);
```

But when I tried to run the code (after compiling using shell script and executing using ./a.out), I encountered the following message error

```

*** glibc detected *** ./a.out: free(): invalid pointer: 0x00007fefc6176010 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7a6e6)[0x7fefda73b6e6]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x6c)[0x7fefda73f9cc]
./a.out[0x408491]
./a.out[0x408565]
./a.out[0x401048]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7fefda6e230d]
./a.out[0x400a59]
======= Memory map: ========
00400000-0040b000 r-xp 00000000 07:00 299109 /home/skyjuice/PROJECT3/a.out
0060a000-0060b000 r--p 0000a000 07:00 299109 /home/skyjuice/PROJECT3/a.out
0060b000-0060c000 rw-p 0000b000 07:00 299109 /home/skyjuice/PROJECT3/a.out
0060c000-059f8000 rw-p 00000000 00:00 0
05ebb000-05ee3000 rw-p 00000000 00:00 0 [heap]
7fefc0000000-7fefc0021000 rw-p 00000000 00:00 0
7fefc0021000-7fefc4000000 ---p 00000000 00:00 0
7fefc59d3000-7fefc59d4000 rw-p 00000000 00:00 0
7fefc5f60000-7fefc5f75000 r-xp 00000000 07:00 2117 /lib/x86_64-linux-gnu/libgcc_s.so.1
7fefc5f75000-7fefc6174000 ---p 00015000 07:00 2117 /lib/x86_64-linux-gnu/libgcc_s.so.1
7fefc6174000-7fefc6175000 r--p 00014000 07:00 2117 /lib/x86_64-linux-gnu/libgcc_s.so.1
7fefc6175000-7fefc6176000 rw-p 00015000 07:00 2117 /lib/x86_64-linux-gnu/libgcc_s.so.1
7fefc6176000-7fefda6c1000 rw-p 00000000 00:00 0
7fefda6c1000-7fefda858000 r-xp 00000000 07:00 904195 /lib/x86_64-linux-gnu/libc-2.13.so
7fefda858000-7fefdaa57000 ---p 00197000 07:00 904195 /lib/x86_64-linux-gnu/libc-2.13.so
7fefdaa57000-7fefdaa5b000 r--p 00196000 07:00 904195 /lib/x86_64-linux-gnu/libc-2.13.so
7fefdaa5b000-7fefdaa5c000 rw-p 0019a000 07:00 904195 /lib/x86_64-linux-gnu/libc-2.13.so
7fefdaa5c000-7fefdaa62000 rw-p 00000000 00:00 0
7fefdaa62000-7fefdaae5000 r-xp 00000000 07:00 904199 /lib/x86_64-linux-gnu/libm-2.13.so
7fefdaae5000-7fefdace4000 ---p 00083000 07:00 904199 /lib/x86_64-linux-gnu/libm-2.13.so
7fefdace4000-7fefdace5000 r--p 00082000 07:00 904199 /lib/x86_64-linux-gnu/libm-2.13.so
7fefdace5000-7fefdace6000 rw-p 00083000 07:00 904199 /lib/x86_64-linux-gnu/libm-2.13.so
7fefdace6000-7fefdad07000 r-xp 00000000 07:00 644102 /lib/x86_64-linux-gnu/ld-2.13.so
7fefdaeeb000-7fefdaeee000 rw-p 00000000 00:00 0
7fefdaf04000-7fefdaf06000 rw-p 00000000 00:00 0
7fefdaf06000-7fefdaf07000 r--p 00020000 07:00 644102 /lib/x86_64-linux-gnu/ld-2.13.so
7fefdaf07000-7fefdaf09000 rw-p 00021000 07:00 644102 /lib/x86_64-linux-gnu/ld-2.13.so
7fff1b020000-7fff1b0ca000 rw-p 00000000 00:00 0 [stack]
7fff1b148000-7fff1b149000 r-xp 00000000 00:00 0 [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0 [vsyscall]
Aborted

```

Is there anything wrong with malloc memory allocation? If yes, how should I address this problem?

---

### Post by dwhitney67 on 2012-04-16
> **skyjuice88 said:**
> 
Is there anything wrong with malloc memory allocation? If yes, how should I address this problem?

The first thing you should do is refer back to the post given by ve4cib.  He indicated the problem, and all you did is mask the problem by utilizing a cast.  You cannot write a 4-byte int into space only reserved to handle a single-byte (char).

Please show how the array "frm" is declared; I see that you pass it to readPgm(), where it them assumes the better name of "frame".

---

### Post by skyjuice88 on 2012-04-19
> **dwhitney67 said:**
> The first thing you should do is refer back to the post given by ve4cib.  He indicated the problem, and all you did is mask the problem by utilizing a cast.  You cannot write a 4-byte int into space only reserved to handle a single-byte (char).

Please show how the array "frm" is declared; I see that you pass it to readPgm(), where it them assumes the better name of "frame".
this is how it is declared
```
frm1       = (unsigned char *) malloc(sizeof(unsigned char) * nxy);
```
frm1 is supposed to store the pixel value from the input image via readPGM

How should I use free() function at the end of the program in this case?

---

### Post by dwhitney67 on 2012-04-19
> **skyjuice88 said:**
> this is how it is declared
```
frm1       = (unsigned char *) malloc(sizeof(unsigned char) * nxy);
```
frm1 is supposed to store the pixel value from the input image via readPGM

So therein lies the problem; the fscanf() in readPGM() is trying to store an int value (4 bytes) into a space that is sized to only store an unsigned char (1 byte) [ btw, see note below].  Fix the format type in fscanf() to be %c in lieu of %d.
```

/* Incorrect...
 * fscanf(file,"**%d**", **(int*)** &frame[i + nx * j]);
 */

/* Correct */
fscanf(file,"**%c**", &frame[i + nx * j]);

```


> **skyjuice88 said:**
> 
How should I use free() function at the end of the program in this case?
You call free() for the memory that was allocated.  For example,
```

someType* ptr = malloc(N * sizeof(someType));
...
free(ptr);

```


P.S.  It is possible to store an int (4-bytes) into every forth byte of memory that has been declared as storage for unsigned char values, however I'm not sure if this is your intent.  For example:
```

static const int MAX = 100;

assert(MAX % sizeof(int) == 0);

unsigned char* array = malloc(MAX);

for (int i = 0; i < MAX / sizeof(int); ++i)
{
    fscanf(fd, "%d", (int*) &array[i * sizeof(int)]);
}

```

---

### Post by skyjuice88 on 2012-04-19
> **dwhitney67 said:**
> So therein lies the problem; the fscanf() in readPGM() is trying to store an int value (4 bytes) into a space that is sized to only store an unsigned char (1 byte) [ btw, see note below].  Fix the format type in fscanf() to be %c in lieu of %d.
```

/* Incorrect...
 * fscanf(file,"**%d**", **(int*)** &frame[i + nx * j]);
 */

/* Correct */
fscanf(file,"**%c**", &frame[i + nx * j]);

```

You call free() for the memory that was allocated.  For example,
```

someType* ptr = malloc(N * sizeof(someType));
...
free(ptr);

Thanks for the useful information. The thing is each element in PGM image format is made of up ASCII value from 0-255, hence the need to use int type. I believe the similar issue is highlighted here http://www.cplusplus.com/forum/general/2393/

Anyway, when I change the line to 
[code]
fscanf(file,"**%c**", &frame[i + nx * j]);

```
I encounter this warning
> 
*** glibc detected *** ./a.out: double free or corruption (out): 0x00007f91023df010 ***

Is this due to malloc where too much memory is allocated?

---

### Post by dwhitney67 on 2012-04-19
> **skyjuice88 said:**
> Thanks for the useful information. The thing is each element in PGM image format is made of up ASCII value from 0-255, hence the need to use int type. I believe the similar issue is highlighted here [http://www.cplusplus.com/forum/general/2393/](http://www.cplusplus.com/forum/general/2393/)

Anyway, when I change the line to 
```

fscanf(file,"**%c**", &frame[i + nx * j]);

```

Forgive me for misleading you earlier.  The correct format type for an unsigned char is "%hhu", not "%c" as I indicated earlier.

> **skyjuice88 said:**
> 
I encounter this warning
```

*** glibc detected *** ./a.out: double free or corruption (out): 0x00007f91023df010 ***

```
Is this due to malloc where too much memory is allocated?

It is hard to say what caused it, but you might have better luck tracking down the cause using valgrind.  Compile your code with the -g option (so that it gets symbolic information in the executable), then run valgrind as such:
```

valgrind -v ./a.out

```

---

