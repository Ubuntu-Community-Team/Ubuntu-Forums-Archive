---
title: "C - Looped app without any loop"
date: 2008-08-05
forum: Programming Talk
---

### Post by systemarpi on 2008-08-05
Hi, I have a really weird (at least for me) problem, my app is looping but there's no loops involved, I have detected the instruction that make it loop, so, here we go. Thanks in advance.

What I am (trying) doing is a File Compress Algorithm (starting from nothing).

I have done is:
1) Read a file from a shell parameter (like komp –f filename)
2) Count each byte from the file and print it in HEX notation
3) Dynamically allocate memory to handle the N-bytes of the file to compress
4) Once the memory is allocated I take the N-Bytes and put them in memory (problem here)

I am not really if this is the best way for do step 4, but here is:
[PHP]
#define BYTE unsigned char
#define LINT unsigned long int

void filetomemory(char *file, BYTE *tomemory){
FILE *f;
BYTE k=0;
LINT bytepos=0;
f=fopen(file,"r");
 printf("\nTo tomemory…");
 while(!feof(f)){
	fread(&k,1,1,f);
	tomemory[bytepos]=k; //If this instruction is commented, the code don’t loop anymore
	bytepos++;	
 }
}

void main(int argc, char *argv[]){
…  //No loops in main
filetomemory(argv[1],&tomemory);
…
}
[/PHP]

---

### Post by Lster on 2008-08-05
Hi!

[QUOTE=systemarpi]tomemory[bytepos]=k; //If this instruction is commented, the code don&#8217;t loop anymore[/QUOTE]

This makes me think that you aren't allocating tomemory correctly. Can you post the code in main that allocates tomemory? Also, what is the exact output? Does it just hang or does it keep printing "To tomemory&#8230;".

---

### Post by Tony Flury on 2008-08-05
Maybe i am misunderstanding your question - 
but you have a loop - in your function filetomemory

The line you have marked - if you comment it out, wont stop the loop it will just stop the byte that is read from file from being stored.

what exactly is your programe doing that is confusing you ?

---

### Post by kdorf on 2008-08-05
What Tony Flury said. "while" is a loop.

---

### Post by systemarpi on 2008-08-05
> **Lster said:**
> Hi!
This makes me think that you aren't allocating tomemory correctly. Can you post the code in main that allocates tomemory?

Heres the code, thanks for the help.
[PHP]
void allocatetomemory(BYTE *tomemory, LINT quantity){
LINT tama=0;
*tomemory = malloc(quantity*sizeof(BYTE));
tama=sizeof(*tomemory)*quantity;
 printf("\nThe reserved tomemory is %d Bytes",tama);
}
[/PHP]

> **Lster said:**
> Hi!
Also, what is the exact output? Does it just hang or does it keep printing "To tomemory…".

This repets 15 times:
```

The file to compress is: test
The HEX structure is: 61736B2061736B2E2E
The file has 9 Bytes
The reserved memory is 9 Bytes
To memory: 0...

```

Then, the programs ends (so it doesn't loop forever) with:
```

The file to compress is: test
The HEX structure is: 00
The file has 1 Bytes
The reserved memory is 1 Bytes
To memory: 0... Null pointer assignment

```

---

### Post by systemarpi on 2008-08-05
> **Tony Flury said:**
> 
The line you have marked - if you comment it out, wont stop the loop it will just stop the byte that is read from file from being stored.

what exactly is your programe doing that is confusing you ?

Yes I know, the commented instruction wont stop the loop, but I does, that&#8217;s the thing is confusing me, I know there's a loop there, but that&#8217;s a &#8220;code lope&#8221; it shouldn't loop all the app and that&#8217;s what is happening.  Thanks for the interesting

---

### Post by Lster on 2008-08-05
[QUOTE=systemarpi]Heres the code, thanks for the help.
[PHP]
void allocatetomemory(BYTE *tomemory, LINT quantity){
LINT tama=0;
*tomemory = malloc(quantity*sizeof(BYTE));
tama=sizeof(*tomemory)*quantity;
 printf("\nThe reserved tomemory is %d Bytes",tama);
}
[/PHP]

If tomemory is a BYTE pointer, you setting the first BYTE equal to the memory allocated's address (modulo 255 I would assume). I think what you probably need to do is replace this:

```
*tomemory = malloc(quantity*sizeof(BYTE));
```

With:

```
tomemory = malloc(quantity*sizeof(BYTE));
```

That would be my guess; and by the way, you may need to change how you deal with the variable tama! Perhaps have a look at this as well:

[http://www.cplusplus.com/reference/clibrary/cstdlib/malloc.html](http://www.cplusplus.com/reference/clibrary/cstdlib/malloc.html)

---

### Post by systemarpi on 2008-08-05
This couldn’t be the best way, but work perfect, I move the function code to the main section, and Works perfect there, so maybe will be better to keep it there for a while (even if that makes the code harder to maintain)

[PHP]
…/functions here

… //inside main
while(!feof(f)){
	fread(&k,1,1,f);
	tomemory[bytepos]=k;
	bytepos++;	
 }
 printf("\n Into memory we have: \n");
 for (i = 0; i<(bytecount-1);i++) printf("%02X",tomemory[i]);
…//end code
[/PHP]

Thanks to everyone, I will keep trying in a copy of the code to figure out what was wrong.

---

### Post by nvteighen on 2008-08-05
[PHP]
#define BYTE unsigned char
#define LINT unsigned long int

void filetomemory(char *file, BYTE *tomemory){
FILE *f;
BYTE k=0;
LINT bytepos=0;
f=fopen(file,"r");
 printf("\nTo tomemory&#8230;");
 while(!feof(f)){
	fread(&k,1,1,f);
	tomemory[bytepos]=k; //If this instruction is commented, the code don&#8217;t loop anymore
	bytepos++;	
 }
}
[/PHP]

What is tomemory here in the code below? An array? If so, you should pass it without '&' or you'll be passing the pointer's memory address, not the pointer! You were probably overwriting something in memory and preventing the loop to continue.
[PHP]
void main(int argc, char *argv[]){
...  //No loops in main
filetomemory(argv[1],&tomemory);
...
}
[/PHP]

---

### Post by systemarpi on 2008-08-05
> **nvteighen said:**
> [PHP]
What is tomemory here in the code below? An array? If so, you should pass it without '&' or you'll be passing the pointer's memory address, not the pointer! You were probably overwriting something in memory and preventing the loop to continue.

Hi, tomemory is not an array, is a pointer, well, a pointer could be called an array if you increment its memory address

In core, tomemory is declared in Main as:
[PHP]
BYTE *tomemory;[/PHP]

Then, from Main I call the function that pass the file to memory, this way:
[PHP]
filetomemory(argv[1],&tomemory); //Now commented since I moved the function to main.
//In main works perfect[/PHP]

The filetomemory as descrived before is this:
[PHP]
void filetomemory(char *file, BYTE *tomemory){
FILE *f;
BYTE k=0;
LINT bytepos=0;
f=fopen(file,"r");
 printf("\nTo memory: %d... ",bytepos);
 while(!feof(f)){
	fread(&k,1,1,f);
	tomemory[bytepos]=k;
	bytepos++;	
 }
}[/PHP]

Thanks :).

---

### Post by Lster on 2008-08-05
I think nvteighen is right, but you will (I think) have to do that along with my alteration.

---

### Post by Tony Flury on 2008-08-05
> 
filetomemory(argv[1],&tomemory)


since tomemory is already defined as a BYTE * (i.e. the start of a BYTE array) you don't need to pass it by reference - remove the & and you will be on the right track - since your function assumes it is getting a BYTE *, but effectively you are passing a BYTE * * (i.e. a pointer to a pointer to a BYTE).

I think the fact that the program repeats when you have your function called, and not when code is inline probably means that actually your function is corrupting the stack, and it might well be connected with the way you pass your pointers around.

My guess is that you are overwriting the return address on the stack (which is why when you comment out the code that seems to write to your array the code works). It seems that it just so happens that the corrupted return address points to the start of Main (which is why your code seems to repeat).

---

### Post by hod139 on 2008-08-05
I would suggest when compiling that you use the -Wall flag (it would have caught a lot of these errors and printed nice warnings)
```

gcc -Wall foo.c

```As for your code, your allocatetomemory function is wrong.  It should be 

```

void allocatetomemory(BYTE **tomemory, LINT quantity)

```That is, you want to pass a pointer to the pointer, otherwise you will be allocating memory to a temporary copy of tomemory, that is cleaned up when the function returns.  So, it should look like:

```

void allocatetomemory(BYTE **tomemory, LINT quantity){
    (*tomemory) = malloc(quantity*sizeof(BYTE));
} 

int main(int argc, char *argv[]){
  BYTE *tomemory;
  allocatetomemory(&tomemory, 15);
  return 0;
}  

```Then, as others have said, when calling filetomemory, you should call it like:
```

filetomemory(argv[1], tomemory);

```

**EDIT:** main really should return int, conventionally it does and also the newer C standard requires it to.

---

### Post by systemarpi on 2008-08-05
Thanks a lot, I will fix it all tomorrow and post a final code, to help others to look the right way to do things.

---

### Post by slavik on 2008-08-05
what's with the LINT? gcc/g++ uses 4byte ints (long ints are also 4 bytes).

---

### Post by dwhitney67 on 2008-08-05
Precisely!  What is the purpose of typedefing LINT and BYTE??  There are data types predefined that should meet your needs.  There is uint8_t for unsigned character (byte), and either uint32_t or uint64_t depending on whether you need a 32-bit or 64-bit unsigned integer for representing the file/data size.

One thing to remember is that one of the keys to successful programming is to keep things as simple/concise as possible, in an effort not to obfuscate the actions of the application itself.

Anyhow, I hope you do not mind, but here's one way to solve the program you originally submitted:
[PHP]#include <stdio.h>
#include <inttypes.h>

uint32_t readFile( const char *filename, uint8_t *buf, uint32_t bufSize )
{
  uint32_t bytesRead = 0;

  FILE *fp = fopen( filename, "r" );

  if ( fp )
  {
    // read as many bytes as the buffer will hold... not one lousy byte
    // at a time!
    //
    bytesRead += fread( buf, 1, bufSize, fp );
  }

  return bytesRead;
}


int main( int argc, char **argv )
{
  // Either choose a fixed sized buffer, or better yet, allocate memory
  // so that in case you choose the size poorly, realloc() can be used
  // to allocate more data.  For now, let's choose a fixed-sized buffer.
  //
  uint8_t buffer[1024] = {0};


  // Read the file and expect the buffer to contain the data and the
  // number of bytes read to be returned.
  //
  uint32_t bytesRead = readFile( argv[1], buffer, sizeof(buffer) );


  // Display results
  //
  printf( "bytes read from '%s' = %d\n", argv[1], bytesRead );

  for ( uint32_t i = 0; i < bytesRead; ++i )
  {
    printf( "%c", buffer[i] );
  }
  printf( "\n" );

  return 0;
}[/PHP]

To test:
```
$ gcc -Wall -pedantic -std=gnu99 filereader.c -o filereader
$ ./filereader /etc/hosts
```
Now, if you plan to deal with files of indeterminate size, then you will have to rely on malloc() and realloc() to obtain space for your buffer.

Here's how:
[PHP]#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

uint32_t readFile( const char *filename, uint8_t **buf )
{
  uint32_t bytesRead = 0;
  FILE *fp = fopen( filename, "r" );

  if ( fp )
  {
    const uint32_t BUF_SZ = 64;  // choose a bigger size for better performance

    // Allocate memory and assign the pointer to this memory into
    // the location referenced by buf.
    //
    *buf = malloc( BUF_SZ );

    // Take a first stab at reading BUF_SZ bytes from the file
    // and place the data into the buffer.
    //
    bytesRead += fread( *buf, 1, BUF_SZ, fp );

    // Is there more data in the file??
    while ( !feof(fp) )
    {
      // Yes there is; let's make the buffer a little bigger.
      //
      *buf = realloc( *buf, bytesRead+BUF_SZ );

      // And let's read some more data.
      //
      bytesRead += fread( *buf+bytesRead, 1, BUF_SZ, fp );
    }
  }

  return bytesRead;
}

int main( int argc, char **argv )
{
  uint8_t *buffer = 0;

  // The buffer has not been allocated yet; it will be, and we want it
  // back.  Thus the address to the buffer needs to be passed.
  //
  uint32_t bytesRead = readFile( argv[1], &buffer );

  if ( buffer != 0 )
  {
    printf( "bytes read from '%s' = %d\n", argv[1], bytesRead );

    for ( uint32_t i = 0; i < bytesRead; ++i )
    {
      printf( "%c", buffer[i] );
    }
    printf( "\n" );
  }
  else
  {
    printf( "buffer = 0\n" );
  }

  return 0;
}[/PHP]
A couple of things here that should be explained.  First, note how the address of the buffer pointer is passed to readFile().  The reason for this is so that the allocated memory (and the contents therein) can be returned through the pointer supplied.

The other thing to look at is the realloc() and also the fread() in the while-loop.  The realloc() function simply takes the existing buffer's memory location, moves it (but not necessarily) to another location, and tacks on more space at the end.  The new location is (re)assigned to the buf pointer.

The fread() in the while-loop looks slightly different from the first fread() because we need to adjust the offset from the beginning of 'buf' so that the new data that is read is inserted into the buffer at the correct location.

The realloc() and the fread() are done repeatedly until the entire file has been read.  If you choose a larger BUF_SZ, then fewer reads will be needed to digest the file; hence better performance for the application.

Enjoy!

---

### Post by nvteighen on 2008-08-06
> **Tony Flury said:**
> 
My guess is that you are overwriting the return address on the stack (which is why when you comment out the code that seems to write to your array the code works). It seems that it just so happens that the corrupted return address points to the start of Main (which is why your code seems to repeat).

Very possible: as the tomemory variable is the second function parameter, it is placed in the stack just before the return address (or am I wrong?).

But, of course, such a thing would be mean the OP is very lucky... What are the chances to overwrite the stack precisely that way that it points exactly to main() and not to a random place in memory?

---

