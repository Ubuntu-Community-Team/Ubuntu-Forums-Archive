---
title: "Help Me With This"
date: 2009-10-01
forum: Programming Talk
---

### Post by Dark-Byte on 2009-10-01
Hello people I am writing a program to this question:

                                 Write a program that creates a file called &#8220;input09.dat&#8221;. It then allows you to enter the names and address of a number of persons. For each person it allows you to input the name and address, it computes the length of the names and address and writes in the file &#8220;input09.dat&#8221;, the length of the name, the name, the length of the address and the address.


I need to write the program using only those Unix system calls open, read, write, close and lseek.


Here is what I wrote:

```

#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include<unistd.h>

struct Person
{
  char names[21];
  int ch_in_name;
  char address[21];
  int ch_in_address;
};
  
int main()
{
  struct Person myArr[5];//An array of struct Person
  int x = open( "/home/user/Desktop/Labsheets/Labsheet4/input09.dat", O_RDWR | O_CREAT | O_TRUNC, S_IRWXU );
  char buf = { "Please enter the person's name:" };
  char buf1 = { "Please enter the person's address:" };
  int i;
  
  for( i = 0; i < 5; i++ )
  {
    write( 1, buf, strlen(buf) };
    int a = read( 0, myArr[i].name, 21 );
    myArr[i].ch_in_name = a;
    write( 1, buf1, strlen(buf1) )
    int b = read( 0, myArr[i].address, 21 );
    myArr[i].ch_in_address = b;
    write( x, myArr[i].name, a );
    write( x, myArr[i].address, b );
   
  }
}

 
```The problem is that how do I write a number to a file using write since they are not characters and I can't store the number as an array of char?
Also I have another question for calls such as read or open do they return -1 or 1?Since when I looked in Advanced Unix Programming 2nd Edition it says they return 1 on error and at linux.die.net it says they retiurn -1 on error?

---

### Post by Arndt on 2009-10-01
> **Dark-Byte said:**
> Hello people I am writing a program to this question:

                                 Write a program that creates a file called &#8220;input09.dat&#8221;. It then allows you to enter the names and address of a number of persons. For each person it allows you to input the name and address, it computes the length of the names and address and writes in the file &#8220;input09.dat&#8221;, the length of the name, the name, the length of the address and the address.


I need to write the program using only those Unix system calls open, read, write, close and lseek.


Here is what I wrote:

```

#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include<unistd.h>

struct Person
{
  char names[21];
  int ch_in_name;
  char address[21];
  int ch_in_address;
};
  
int main()
{
  struct Person myArr[5];//An array of struct Person
  int x = open( "/home/user/Desktop/Labsheets/Labsheet4/input09.dat", O_RDWR | O_CREAT | O_TRUNC, S_IRWXU );
  char buf = { "Please enter the person's name:" };
  char buf1 = { "Please enter the person's address:" };
  int i;
  
  for( i = 0; i < 5; i++ )
  {
    write( 1, buf, strlen(buf) };
    int a = read( 0, myArr[i].name, 21 );
    myArr[i].ch_in_name = a;
    write( 1, buf1, strlen(buf1) )
    int b = read( 0, myArr[i].address, 21 );
    myArr[i].ch_in_address = b;
    write( x, myArr[i].name, a );
    write( x, myArr[i].address, b );
   
  }
}

 
```The problem is that how do I write a number to a file using write since they are not characters and I can't store the number as an array of char?
Also I have another question for calls such as read or open do they return -1 or 1?Since when I looked in Advanced Unix Programming 2nd Edition it says they return 1 on error and at linux.die.net it says they retiurn -1 on error?

Do try to give your posts more descriptive titles.

Is your first question how you can go from a number in an 'int' variable, say 4711, to the characters '4', '7', '1' and '1' which make up the text (decimal) representation of it? There are library routines for that, but maybe you're not allowed to use them. Then you have to do it yourself. Think of a one-digit number first. How to output the digit '6'? Look in the ASCII table where '6' is, and what its code is. Now try another number. Then a two-digit number. You will get the idea.

There are probably many faulty sources of information out there. Generally the result indicating an error is different from all possible return values for a correct operation. Since 1 is a conceivable value for a file descriptor (it's stdout), and you can very well read one byte with 'read', the error value 1 is not plausible. It's -1. The man page will tell you so, too.

---

### Post by MadCow108 on 2009-10-01
the standard library routine to convert basic data types to char (if your allowed to use it) would be snprintf (see: man snprintf)
or for direct file output fprintf (but thats probably not allowed as you have to use open/write etc)

---

