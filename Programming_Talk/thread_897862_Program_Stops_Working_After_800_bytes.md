---
title: "Program Stops Working After 800 bytes"
date: 2008-08-22
forum: Programming Talk
---

### Post by systemarpi on 2008-08-22
Program Stops Working After 800 bytes

We (I and a lot more nice people have help in this forum) are working in the new file compress algorithm, so far what it’s done is:
1) Read a file name from the command line parameter
2) Count the number of bytes
3) Dynamically allocate memory to take the file to main memory
4) Print the Hex structure of the given file

The program works perfect with small files, but stops to work just while reading the byte #800, I check the hex structure of the given file with a hex editor, to be sure there's more byte in it.

Heres all the code:
[PHP]
#include <stdio.h>
#include <stdlib.h>

#define uint8_t unsigned char
#define uint32_t unsigned long int

uint32_t readFile( const char *filename, uint8_t **buf )
{
  uint32_t bytesRead = 0;
  FILE *fp = fopen( filename, "r" );

  if (fp)
  {
    const uint32_t BUF_SZ = 1024;  // Buffer Size
    *buf = malloc( BUF_SZ ); //Allocate memory and point the location
    bytesRead += fread( *buf, 1, BUF_SZ, fp ); //Read BUF_SZ bytes from file and buffer it

    // Is there more data in the file??
    while ( !feof(fp) )
    {
      *buf = realloc( *buf, bytesRead+BUF_SZ ); //Make the buffer greater, to save more data
      bytesRead += fread( *buf+bytesRead, 1, BUF_SZ, fp ); //Save the data into buffer
    }
  }
  return bytesRead;
}

int main( int argc, char **argv )
{
  uint8_t *buffer = 0;
  uint32_t i = 0;

  uint32_t bytesRead = readFile( argv[1], &buffer ); //Read the file and return how much bytes it has

  if ( buffer != 0 )
  {
    printf( "The file '%s' has a total of %d Bytes\n", argv[1], bytesRead );
	printf( "The HEX structure is: ");
    for ( i = 0; i < bytesRead; ++i ) printf( "%02X", buffer[i] ); //Printing in Hex notation the file content
  }
  else
  {
    printf( "\nBuffer = 0\n" );
  }

  return 0;
}  
[/PHP]

---

### Post by Reiger on 2008-08-22
First thing that comes to mind is... buffering?

---

### Post by jinksys on 2008-08-22
> **systemarpi said:**
> Program Stops Working After 800 bytes

I changed one line,

printf( "%02X Byte:%d\n", buffer[i], i );

so that it would tell me how many bytes have been printed, and your code seems to be working correctly - at least on my machine.  I opened a jpg with your code and this is what I got...

```

. . . .
FE Byte:70591
1E Byte:70592
7F Byte:70593
C1 Byte:70594
AE Byte:70595
BF Byte:70596
A3 Byte:70597
C3 Byte:70598
DB Byte:70599
FF Byte:70600
00 Byte:70601
E6 Byte:70602
FF Byte:70603
D9 Byte:70604

```

And as you can see the bytes match the size of the jpg...

```

-rw-r--r-- 1 steve steve 70605 2008-08-22 00:25 ../../Pictures/Lego_Hawking.jpg

```

---

### Post by dwhitney67 on 2008-08-22
The code you presented looks awfully familiar!

Anyhow, it works for me.  The only that you are missing is a call to free() when you are done with the 'buffer' in the main() function.

Also, your code generates warnings with respect to printf() because you elected to use uint32_t for the 'bytesRead' variable.  Perhaps consider using size_t.

After compiling your program, I ran it like:
```
$ sudo a.out /var/log/messages
```
P.S.  The 'sudo' is not required on Ubuntu systems for the command shown above; any user can access /var/log/messages (*nix security violation??).

---

### Post by jinksys on 2008-08-22
I'd like to add that I see practically NO error checking.  The success of malloc, realloc, fread, etc are being assumed.  Just say no to lazycode.

---

### Post by mujambee on 2008-08-22
Just in case, try opening the file in binary mode:

[COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]FILE [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000BB]fp [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]fopen[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#0000BB]filename[/COLOR][COLOR=#007700], [/COLOR][COLOR=#DD0000]"rb" [/COLOR][COLOR=#007700]);[FONT=Verdana]

[/FONT][/COLOR][/COLOR]

---

### Post by tageiru on 2008-08-22
> **mujambee said:**
> Just in case, try opening the file in binary mode:

[COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]FILE [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000BB]fp [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]fopen[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#0000BB]filename[/COLOR][COLOR=#007700], [/COLOR][COLOR=#DD0000]"rb" [/COLOR][COLOR=#007700]);[FONT=Verdana]

[/FONT][/COLOR][/COLOR]

b is ignored on POSIX systems.

---

### Post by dwhitney67 on 2008-08-22
> **jinksys said:**
> I'd like to add that I see practically NO error checking.  The success of malloc, realloc, fread, etc are being assumed.  Just say no to lazycode.
Yes, malloc() and realloc() can fail, but if they do, I think the issue is not with the application but with the system under which it is running.  In other words, if there is no memory available on the heap for an application to allocate, then there are bigger problems to worry about!

As for fread(), it returns the number of bytes read from the file-stream; if an error occurs or if no data is read, then zero is returned.  The OP (using code I believe I originally wrote) is using it in the correct manner.

> **mujambee said:**
> Just in case, try opening the file in binary mode:

[COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]FILE [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000BB]fp [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]fopen[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#0000BB]filename[/COLOR][COLOR=#007700], [/COLOR][COLOR=#DD0000]"rb" [/COLOR][COLOR=#007700]);[FONT=Verdana]

[/FONT][/COLOR][/COLOR]
This has nothing to do with the "problem"... in fact there isn't a problem!  The code works fine.  The OP should add a call to free() to de-allocate memory that was allocated in readFile(), and also cleanup the warnings generated by the printf() in the main() function, but other than that, everything is fine.  Perhaps the OP was comparing "apples" and "oranges" when examining the file-size and the number of bytes reported by the application.

To the OP:
I use the following command to dump the contents of a file in hexadecimal format:
```
/usr/bin/od -A d -x -v  someFile
```

---

### Post by mujambee on 2008-08-22
> **tageiru said:**
> b is ignored on POSIX systems.

Great to learn that after 10 years :(

---

### Post by dwhitney67 on 2008-08-22
> **mujambee said:**
> Great to learn that after 10 years :(
From the manpage for fopen():
```
...
       The mode string can also include the letter ’b’ either as a last character or as  a
       character  between  the  characters  in  any of the two-character strings described
       above.  This is strictly for compatibility with C89 and has no effect; the  ’b’  is
       ignored on all POSIX conforming systems, including Linux.  (Other systems may treat
       text files and binary files differently, and adding the ’b’ may be a good  idea  if
       you  do I/O to a binary file and expect that your program may be ported to non-Unix
       environments.)
...
```

---

### Post by drubin on 2008-08-22
> **mujambee said:**
> Great to learn that after 10 years :(

> **dwhitney67 said:**
> From the manpage for fopen():
```
...
       you  do I/O to a binary file and expect that your program may be ported to non-Unix
       environments.)
...
```

Have you been coding for Windows Systems? :)

---

### Post by dwhitney67 on 2008-08-22
Last I heard was that M$ touts its operating systems as being POSIX compliant.  Have I ever developed software under Windows?... briefly (6 months), using Rational Rose.  As for the last 21 years, I've used *nix systems.

---

### Post by mujambee on 2008-08-23
> **rubinboy said:**
> Have you been coding for Windows Systems? :)

Not much, only for the last 20 years... :)

---

### Post by wgrant on 2008-08-23
> **dwhitney67 said:**
> *snip*
P.S.  The 'sudo' is not required on Ubuntu systems for the command shown above; any user can access /var/log/messages (*nix security violation??).

No, only members of adm can view such logs. That's the point of the group.

---

### Post by red_Marvin on 2008-08-23
> **dwhitney67 said:**
> Yes, malloc() and realloc() can fail, but if they do, I think the issue is not with the application but with the system under which it is running.  In other words, if there is no memory available on the heap for an application to allocate, then there are bigger problems to worry about!

But it is the responsibility of your program to make sure the program exits as gracefully as possible should such an event occur, instead of causing a non descriptive segfault (or whatever) because it tries to use an invalid pointer.

---

