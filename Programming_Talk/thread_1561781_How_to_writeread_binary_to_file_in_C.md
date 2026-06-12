---
title: "How to write/read binary to file in C"
date: 2010-08-26
forum: Programming Talk
---

### Post by gnomefan on 2010-08-26
I need to write 96 bits to a file using C and then read them back in another program and identify which individual bits are set.

The code for writing the bits is:

```

#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>

int main()
{

    int test[12];

    test[0]=0b00100101;  //37 in decimal
    test[1]=0b00110001;   //49
    test[2]=0b10001001;   //137
    test[3]=0b11101011;   //235
    test[4]=0b01100000;     //96
    test[5]=0b01101010;    //106
    test[6]=0b00010100;    //20
    test[7]=0b10010011;    //147
    test[8]=0b01011000;    //88
    test[9]=0b00000001;    //1
    test[10]=0b00110111;    //55
    test[11]=0b00000000;    //0
    
    
    int file = open("/home/andrew/Desktop/test.dat", O_WRONLY|O_CREAT);
    if (file ==-1)
    {
        printf("File could not be opened, this is a fatal error, we cannot continue\n");
        return 1;
    }

    int res = write(file,test,12);
    close(file);
    printf("Wrote %d bytes\n",res);
    return 0;

}

```

I then read them back in another program and use a custom written (and unit tested) function which takes the decimal representing each of the 12 bytes, read from the file and sets an array of 8 ints representing the 8 bits with each element set to either 0 or 1:

```

#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
#include <errno.h>


void convertDecimalToBits(int decimal, int bits[8]);

void convertDecimalToBits(int decimal, int bits[8])
{
    //given an integer,write the binary into the array with individual bits set as 0 or 1
    int x = 7;
    int quotient = decimal;
    int remainder=0;
    while (quotient > 0)
    {
        remainder = quotient%2;
        quotient = quotient/2;
        bits[x]=remainder;
        x--;    
    } 
}

int main()
{

    int file = open("/home/andrew/Desktop/test.dat", O_RDONLY);
    ssize_t filelength=12;
    if (file ==-1)
    {
        printf("Could not open file\n");
        return(1);
    }
    int buff[filelength]; //will store data read from file
    void* position;  //our read position

        ssize_t bytesread=0; //num bytes succesfully read from file
        position=buff;  //set our read pos to beginning of file
        ssize_t bytestoread=filelength; //num bytes left to read
        while(bytestoread !=0 && (bytesread = read(file,position,bytestoread)) !=0)
        {
            if (bytesread==-1)
            {
                //error
                if (errno == EINTR)
                {
                    continue; // if we got an EINTR just try again
                    printf("read() got EINTR\n");
                }
                //fatal error reading file, we could throw dialog to alert user, or not. In any case we
                //probably dont want to stop completely but instead go round and try again
                printf("read() got error\n");
                break;
            }
            bytestoread=bytestoread-bytesread;
            position=position+bytesread;

        }
        printf("Bytes read: %d\n",bytesread);
        //sucessfully read filelength bytes
        //process data
        for (int byte=0; byte<filelength; byte++)
        {
            printf("Processing byte, int value is: ");
            printf("%d\n",buff[byte]); //print out byte as int
            int result[8];
            convertDecimalToBits(buff[byte],result);
            for (int x=0; x< 8; x++)
            {
                printf("%d",result[x]);  //print out individual bit value
                
            }
            printf("\n\n"); //end of this 8 bits so insert new line before going on to next byte

            

        }
        return(0);
}

```

The output from this code is wrong as shown below, it prints out the decimal and the 8 bits, but I cant fathom out what is wrong with the code.

 Ive tested the read& write part by using it to copy a JPEG file so that bit must be OK so I assume its in the bit where I interpret each of the 12 bytes?

Bytes read: 12
Processing byte, int value is: 37
-12158837441100101

Processing byte, int value is: 49
-12158837441110001

Processing byte, int value is: 137
10001001

Processing byte, int value is: -1076059408
10001001

Processing byte, int value is: -1076059240
10001001

Processing byte, int value is: 1688512
11000000

Processing byte, int value is: 1
11000001

Processing byte, int value is: 10381136
01010000

Processing byte, int value is: -1076059408
01010000

Processing byte, int value is: 10381171
01110011

Processing byte, int value is: 11005940
11110100

Processing byte, int value is: 134514430
11111110

Can anyone help me please understand whats wrong. Is there a better way to access the individual bits?

Thanks

---

### Post by smartbei on 2010-08-26
buff is declared as a buffer of integers. The printed values are indeed the integral values of the ints in the buffer.
What you want, I believe, is a buffer of chars (individual bytes). This is also what the read function expects to receive.

An int is an implementation-defined size, usually 32 bits. A char is 8 bits.

---

### Post by Bachstelze on 2010-08-26
1) camelCase is generally frowned upon in C.

2) int main(void)

3) What smartbei said, but you want to use unsigned char, not char.

---

### Post by dwhitney67 on 2010-08-26
> **Bachstelze said:**
> 1) camelCase is generally frowned upon in C.
.
Sorry, but not in my world.

---

### Post by dwhitney67 on 2010-08-26
@ the OP:

The third parameter for the read() function is the number of bytes to be read, not the number of data items to be read.

So if you want to read 12 integers, the proper read() statement would be something like:
```

const int num_vals = 12;
int buf[num_vals];

int bytes_read = read(fp, buf, num_vals * sizeof(int));

```
I personally do not use the low-level read(), write(), and open() functions; the fread(), fwrite(), and fopen() work just as well -- even on binary data.  However, use whatever pleases you.

---

### Post by QIII on 2010-08-26
> **Bachstelze said:**
> 1) camelCase is generally frowned upon in C.

Not in my world, either.

The adoption of ASCII character set in the 60s made the underscore available, so a lot of libraries still use underscore style.

CamelCase was adopted by a large number of C programmers at large in the 70s because it allowed easy to read compound names with fewer characters -- which meant shorter identifiers and fewer keystrokes.

I've been around a while.  I was around then.  I've been using CamelCase for a lot of years.

---

### Post by bcz on 2010-08-26
We are a bit off topic now, but following dWhitney

> 1) camelCase is generally frowned upon in C.


Our programming style hopefully develops over time.  A few years ago, I would have written:

"do_some_common_stuff(){....

now

"doSomeCommonStuff(){....

If the aim is self documenting code, or minimising keystrokes, then I do think that the camelCase is preferred

> 2) int main(void)

old habits die hard

I still write

"main(int argv,char **argc){...

although I seldom use the parameters.  Any comments about the merits here

Rgds Bill

---

### Post by Bachstelze on 2010-08-26
Funny, I have never ever seen a serious project in C that uses camel case. Oh well..

> **bcz said:**
> 

I still write

"main(int argv,char **argc){...

although I seldom use the parameters.  Any comments about the merits here

Rgds Bill

Surely you meant (int argc, char **argv), that's fine also of course, but putting nothing is certainly not fine.

[quote="ANSI C, 2.1.2.2"]   The function called at program startup is named main .  The
implementation declares no prototype for this function.  It can be
defined with no parameters:

         int main(void) { /*...*/ }

or with two parameters (referred to here as argc and argv , though any
names may be used, as they are local to the function in which they are
declared):

         int main(int argc, char *argv[]) { /*...*/ }
[/quote]

---

### Post by dwhitney67 on 2010-08-27
There is no difference between declaring a function with "void" versus without.  In other words, I am willing to be proved wrong if you can show me if there is any evil in the following declaration:
```

int main()
{
   ...
}

```

Btw, the following code generates an error when compiled:
```

int main() {}

int main(void) {}

```
In my 20+ years of s/w development, when I see the term "void" as a *parameter* (and, this is not to be confused with "void *"), it implies that no args are accepted by the function. It is typically/generally used for _clarity_ in documentation.  But there are also benefits to using void in a declaration for functions; without the usage, one could pass an arg to a function.  But then who cares!
```

void foo() {}

int main()
{
   foo(5);   // oops, 5 is ignored... so what.
}

```

In other cases, "void" is used to cast away return values from functions that one does not care about.  Once again, this is not necessary, but some folks do it for completeness, yet at the same time they probably don't do it for simple functions like printf(); go figure!.  Anyhow, for example:
```

int foo()
{
   return 0;
}

int main()
{
   (void) foo();  // note the returned value is not assigned to any variable
}

```
The third case where "void" is used is for defining typeless pointers to *any* object.  Since all objects are addressable, it makes sense that these can be used similarly, regardless of their data type, when performing operations on the memory locations to which they reference.  The function memcpy() is a good example of this.

---

### Post by worksofcraft on 2010-08-27
To all the above discussions about "void" It not just is compiler that has to read your code and I for one really like the use of '_' in Prolog language to say... look you can have something here, yet in this case it can be anything and I don't care about it...

So just putting "void" in there is like telling other people who read your code that, yes, there are parameters, but no, they are not gunna be used.

---

### Post by dwhitney67 on 2010-08-27
> **Bachstelze said:**
> 
Surely you meant (int argc, char **argv), that's fine also of course, but putting nothing is certainly not fine.

There's also this definition, but I rarely ever see anyone use it; in fact, I cannot recall ever seeing it in any project I have ever supported:
```

int main(int argc, char** argv, char** envp) { ... }

```


P.S.  An example:
```

#include <stdio.h>

int main(int argc, char** argv, char** envp)
{
   char* env = 0;

   while ((env = *envp++) != 0)
   {
      printf("%s\n", env);
   }

   return 0;
}

```

---

### Post by dwhitney67 on 2010-08-27
> **worksofcraft said:**
> 
So just putting "void" in there is like telling other people who read your code that, yes, there are parameters, but no, they are not gunna be used.
I would not go as far as stating that there *are* parameters, because there isn't.  If you specifically declare a function with a void in lieu of a parameter list, and attempt to pass a parameter to when calling the function, the compiler will let you know about the error.
```

void foo(void) {}

int main()
{
   foo(5);
   return 0;
}

```
So there is merit in declaring a function's parameter list as void, but personally I don't bother.  You're right... without the "void" in the declaration, the parameter is ignored.  No harm, no foul.

---

### Post by Ferrat on 2010-08-27
This discussion fun as it may be doesn't really help the OP does it? on a two page thread there is just one that's actually responded to what he wanted to know? 

Here is a text on basic read and write 
[http://tools.devshed.com/c/a/Web-Development/C-File-IO-and-Binary-File-IO/](http://tools.devshed.com/c/a/Web-Development/C-File-IO-and-Binary-File-IO/)

---

### Post by dwhitney67 on 2010-08-27
I agree, but the OP is MIA.  And if it was easy for you to Google for information on how to deal with binary files in C, you think the OP could have done that as well.

Sometimes I wonder why this forum does not separate the programming forum into three areas:  *Discussion*, *Beginner*, and *Advanced/Useful*.

Most of the diatribe on the programming forum should be filed under *Discussion*.  My favorites... "What is the best programming language?" or "What is the best IDE?".

---

### Post by nvteighen on 2010-08-27
> **dwhitney67 said:**
> There's also this definition, but I rarely ever see anyone use it; in fact, I cannot recall ever seeing it in any project I have ever supported:
```

int main(int argc, char** argv, char** envp) { ... }

```


P.S.  An example:
```

#include <stdio.h>

int main(int argc, char** argv, char** envp)
{
   char* env = 0;

   while ((env = *envp++) != 0)
   {
      printf("%s\n", env);
   }

   return 0;
}

```

Hum... then... why the hell do we insist in using getenv()??

EDIT: Nevermind... I've thought one sec. and I got why getenv() is more practical #-o

---

### Post by gnomefan on 2010-08-27
Thanks. Declaring the buffer in both the reader and writer as unsigned char has caused the integer values to be interpreted correctly, the only problem now is my function  convertDecimalToBits which takes an int as its first argument is spewing out garbage when called in any of the following ways:

convertDecimalToBits(buff[byte],result);
==========================
int toConvert = atoi((const char*)&buff[byte]);
convertDecimalToBits(toConvert,result);
==========================
 int toConvert = (int)buff[byte];
 convertDecimalToBits(toConvert,result);

I would have thought either of those 3 methods would result in a standard int which could be passed to the function?

As I said before, when it was tested by giving it a straightforward int it worked.

The output now looks like this:

Bytes read: 12
Processing byte, int value is: 37
0-1216584160100101

Processing byte, int value is: 49
0-1216584160110001

Processing byte, int value is: 137
10001001

Processing byte, int value is: 235
11101011

Processing byte, int value is: 96
11100000

Processing byte, int value is: 106
11101010

Processing byte, int value is: 20
11110100

Processing byte, int value is: 147
10010011

Processing byte, int value is: 88
11011000

Processing byte, int value is: 1
11011001

Processing byte, int value is: 55
11110111

Processing byte, int value is: 0
11110111

---

### Post by dwhitney67 on 2010-08-27
We all (well, at least the smart ones) know that this is a homework assignment.

So you have a problem with completing the assignment.  I could tell you the answer (ie provide a solution) to the problem, but then you will have learned nothing.

Think about how numbers are stored internally within a register (hint: they are stored as a sequence of 1's and 0's).  Parse through the value in that register, one bit at a time, to deduce whether it contains a 1 or a 0.  If you parse head-on, then your resulting list of 1's and 0's will be backwards; this is not a problem -- just reverse the results and you have your answer.

P.S.  A good way to test whether a bit is a 1 or a 0 is to use the modulus "%" operator and the value 2.  For example:
```

unsigned char value = 5;
unsigned char bit_value = value % 2;  // result is a 1

```

To examine the next bit, you can rely on the shift-operator, or ">>".  This operator takes as an arg the number of bits you want to shift to the right.  In your case, use a 1.
```

unsigned char value = 5;   // value contains the number 5 (or 0000 0101 in binary)
value = value >> 1;        // value now contains the number 2 (or 0000 0010 in binary)

// the statement above is equivalent to...
value >>= 1;

// or
value /= 2;    // ie. value = value / 2

```

---

