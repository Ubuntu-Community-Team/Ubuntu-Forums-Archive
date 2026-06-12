---
title: "C-Warning: Code has no effect (Pointers)"
date: 2008-08-01
forum: Programming Talk
---

### Post by systemarpi on 2008-08-01
Hi, I am working in my own file compress algorithm, but I have a problem in my code, the compiler gives me a “Code has no effect” warning, and yes, actually the code doesn’t work at all.

Here is a part of it:
[PHP]
#define LINT unsigned long int
int main(int argc, char *argv[]){
…
 int i,j;
 LINT bytecount=0;
 readfile(argv[1],&bytecount);
…
}

void readfile(char *file, LINT *bytecount){
// File is opened here, that works ok
// I print each byte of the file here, so the way to look for the bytes its ok (I guess)
//Inside the code that print each byte at once I put:
*bytecount++; // This is what gives me the “Code has no effect”
…
printf("\nThe file has %d Bytes",*bytecount); //This gives me a number is not ok
}
[/PHP]

I tried with local variables with success but that’s the wrong way to go:
[PHP]
void readfile(char *file, LINT *bytecount){
…
int try=0;
//Inside the code that print each byte at once I put:
try++;
printf("\nThe file has %d Bytes",try);
}
[/PHP]

These are the outputs:
```

The function that prints bytes: 61736B2061736B2E2E
The function that prints by the pointer: The file has 29541 Bytes
The function that prints by local variable: The file has 9 Bytes

```

Thanks in advance, any help will be really appreciated.

---

### Post by orphean on 2008-08-01
What happens when you define bytecount as a long int?  LINT might be a structure in which case the post-increment operator would have no effect on it.

---

### Post by Trumpen on 2008-08-01
The dereference operator (*) comes after the postfix increment one (++),so *pointer++ increment the pointer and references to *pointer. It can be used for a quick array copy:
[php]
int source[10],target[10];
/* .. */
for (i=0;i<10;i++)
      *source++ = *target++;
[/php]

To increment the value pointed by bytecount, what you need is parentheses:
(*bytecount)++;

---

### Post by systemarpi on 2008-08-01
> **orphean said:**
> What happens when you define bytecount as a long int?  LINT might be a structure in which case the post-increment operator would have no effect on it.

LINT is not a structure, its defined as a “unsigned long int”, so as far as I know each LINT is going to be replaced in compile time for “unsigned long int”

Any way I tried, just to remove the “unsigned” part, but nothing, same result.

---

### Post by systemarpi on 2008-08-01
Thanks a lot now is solved, just to make it easier for someone else:

```

*bytecount++ MUST be replaced by (*bytecount)++ to get the same result as in the local variable.

```

---

### Post by dwhitney67 on 2008-08-01
> **systemarpi said:**
> Hi, I am working in my own file compress algorithm, but I have a problem in my code, the compiler gives me a “Code has no effect” warning, and yes, actually the code doesn’t work at all.

Here is a part of it:
[PHP]
#define LINT unsigned long int
int main(int argc, char *argv[]){
…
 int i,j;
 LINT bytecount=0;
 readfile(argv[1],&bytecount);
…
}

void readfile(char *file, LINT *bytecount){
// File is opened here, that works ok
// I print each byte of the file here, so the way to look for the bytes its ok (I guess)
//Inside the code that print each byte at once I put:
*bytecount++; // This is what gives me the “Code has no effect”
…
printf("\nThe file has %d Bytes",*bytecount); //This gives me a number is not ok
}
[/PHP]

I tried with local variables with success but that’s the wrong way to go:
[PHP]
void readfile(char *file, LINT *bytecount){
…
int try=0;
//Inside the code that print each byte at once I put:
try++;
printf("\nThe file has %d Bytes",try);
}
[/PHP]

These are the outputs:
```

The function that prints bytes: 61736B2061736B2E2E
The function that prints by the pointer: The file has 29541 Bytes
The function that prints by local variable: The file has 9 Bytes

```

Thanks in advance, any help will be really appreciated.
In C, the read() and fread() functions return the number of bytes successfully read from the file stream.  I presume you are using one of these.

Why not consider declaring a local variable within readfile(), to maintain the byte count in there, and before the function finishes, just return this count?  For example:
[PHP]size_t readfile( char *filename )
{
  // open the file

  size_t bytesread = 0;    // will always be unsigned

  // read all data in the file (one byte at a time or whatever) until
  // EOF reached.
  while ( !feof(fd) )
  {
    char buf;
    bytesread += fread( &buf, 1, sizeof(buf), filep );
  }

  ...

  return bytesread;
}[/PHP]

P.S.  I would also recommend that you break up readfile() to do less.  For instance, instead of passing a filename to readfile(), pass the file descriptor.  Attempt to open the file and verify that it is open *before* calling readfile().

---

### Post by systemarpi on 2008-08-04
> **dwhitney67 said:**
> 
Why not consider declaring a local variable within readfile(), to maintain the byte count in there, and before the function finishes, just return this count?

Well, wouldnt it be the same just less efficient about memory management? (Notice: it&#8217;s a question, not a challenge)

> **dwhitney67 said:**
> 
P.S.  I would also recommend that you break up readfile() to do less.  For instance, instead of passing a filename to readfile(), pass the file descriptor.  Attempt to open the file and verify that it is open *before* calling readfile().

By the way, thanks for the recommendation, I would do exactly that, will split that function.

---

### Post by dwhitney67 on 2008-08-04
> **systemarpi said:**
> Well, wouldnt it be the same just less efficient about memory management? (Notice: it&#8217;s a question, not a challenge)

I'm not quite sure I understand the question.  The function, as I presented earlier, will have a local variable that consumes 4-bytes on the program stack.  Once the function returns, these 4-bytes are no longer an issue because they are returned to the stack.

In the main() (or wherever), there would be another 4-bytes needed to hold the return value of the function.  For example:
[PHP]int main()
{
  ...

  size_t bytesInFile = readFile( "./myText.txt" );

  ...
}[/PHP]
Whether this is more efficient or not, is not too relevant.  What is important is the simplification of the code.  If you want to pass the pointer of 'bytesInFile' into the function, then up to you, but it looks quirky.

---

### Post by systemarpi on 2008-08-04
> **dwhitney67 said:**
> 
Whether this is more efficient or not, is not too relevant.  What is important is the simplification of the code.  If you want to pass the pointer of 'bytesInFile' into the function, then up to you, but it looks quirky.

Yes, but as you said, the 4bytes will available again after the function returns its value, so I will loose that value.

The next step is Dynamic Memory Allocation, that’s why I want that value, that’s going to be another function, so I was thinking play with the pointer, instead local variables.

Then, when the original file be compressed, and I would like to get the compression ratio, I wont have that value that tells me how much bytes where in uncompressed form.

---

### Post by Roptaty on 2008-08-04
> **systemarpi said:**
> Yes, but as you said, the 4bytes will available again after the function returns its value, so I will loose that value.

You can save the value in a local variable in the function calling your readfile...
```
 

LINT readfile(int fd) 
{

  LINT bytesRead = 0;
  // read file

  return bytesRead;
}

int main(int argc, char** arv) 
{
...
LINT bytesread = readfile(filedescriptor); 
...
}


```

---

### Post by dwhitney67 on 2008-08-04
> **systemarpi said:**
> Yes, but as you said, the 4bytes will available again after the function returns its value, so I will loose that value.

The next step is Dynamic Memory Allocation, that&#8217;s why I want that value, that&#8217;s going to be another function, so I was thinking play with the pointer, instead local variables.

Then, when the original file be compressed, and I would like to get the compression ratio, I wont have that value that tells me how much bytes where in uncompressed form.
From what you wrote, I am lost/confused as to what your requirements are.  Needless to say, the best way to return the number of bytes read from a file, whether it be in ascii or binary format, is how I have shown you.

The interface I have shown is essentially a wrapper emulating the fread() interface.  I would strongly suggest that when reading a file that one avoid reading one byte at a time, and instead read in a block of bytes at a time (say 1024+ characters at a time).

Here's a complete example, minus of course the bit about what to do with the data in the file:
[PHP]#include <stdio.h>


// readfile()
//
// Accepts pre-validated file pointer;
// Returns number of bytes in the file.
//
size_t readFile( FILE *filep )
{
  size_t bytesread = 0;

  while ( !feof(filep) )
  {
    char buf[1024] = {0};

    // attempt to read sizeof(buf) bytes
    bytesread += fread( buf, 1, sizeof(buf), filep );

    // do something with 'buf'????
  }

  return bytesread;
}


int main( int argc, char **argv )
{
  // filename comes from the command line; else use this executable.
  const char *filename = (argc > 1 ? argv[1] : argv[0] );

  // open the file (read-only mode).
  FILE *fp = fopen( filename, "r" );

  // verify the file has been opened.
  if ( fp )
  {
    // read the file to get its size.
    const size_t filesize = readFile( fp );

    // display information.
    printf( "Sizeof file '%s' is %d bytes.\n", filename, filesize );
  }
  else
  {
    // error; cannot open file.
    printf( "Error:  File '%s' does not exist or cannot be opened for reading.\n", filename );
  }

  return 0;
}[/PHP]

---

