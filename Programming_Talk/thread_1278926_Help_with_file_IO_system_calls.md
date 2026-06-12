---
title: "Help with file I/O system calls"
date: 2009-09-30
forum: Programming Talk
---

### Post by Dark-Byte on 2009-09-30
Hello I am writing a program for my h/w in C which involves using open,read, write system calls:
The problem is that the program is not leting me enter the marital status; am I misiing something about the write system call?
```

#include<stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include<unistd.h>
#include<string.h>

struct Student
{
  char name[21];
  char id[11];
  char DOB[9];
  char gender[2];
  char status[2];
};

struct Student myArr[5];//An array of Struct Student  
// // int main()
{
  int x, y, z;
  char newline[2] = { "\n" };
  char sep[5] = { "    " };
  char buf1[] = { "Please enter the name of the student's:" };
  char buf2[] = { "Please enter the student's id:" };
  char buf3[] = { "Please enter the student's DOB:" };
  char buf4[] = { "Please enter the student's gender:" };
  char buf5[] = { "Please enter the student's marital status:" };

  //O_CREAT requires a third argument the mode which specifies the access permission bits
  //S_IRWXU indicates that the user has read, write and execute permissions
  x = open( "/home/user/Desktop/Labsheets/Labsheet4/input.dat", O_RDWR | O_CREAT | O_TRUNC, S_IRWXU );
  //note that fd is 1 since it is the standard input
  //will read from standard input and place data in the buffer
  //read return number of bytes read
  int i;
  for( i = 0; i < 5; i++ )
  {
    write( 1, buf1, strlen(buf1) );
    read( 0, myArr[i].name, 20 );//read from standard input and place data in buffer
    write( 1, buf2, strlen(buf2) );;
    read( 0, myArr[i].id, 10 );
    write( 1, buf3, strlen(buf3) );
    read( 0, myArr[i].DOB, 9 );
    write( 1, buf4, strlen(buf4) );
    read( 0, myArr[i].gender, 1 );
    write( 1, buf5, strlen(buf5) );
    read( 0, myArr[i].status, 1 );
  }
  for(  i = 0; i < 5; i++ )
  {
    write( x, myArr[i].name, strlen(myArr[i].name) );
    write( x, sep, 4 );
    write( x, myArr[i].id, strlen(myArr[i].id) );
    write( x, sep, 4 );
    write( x, myArr[i].DOB, strlen(myArr[i].DOB) );
    write( x, sep, 4 );
    write( x, myArr[i].gender, strlen(myArr[i].gender) );
    write( x, sep, 4 );
    write( x, myArr[i].status, strlen(myArr[i].status) );
    write( x, newline, 4 );
  
  }
 
  return 0;
}

```

---

### Post by Arndt on 2009-09-30
> **Dark-Byte said:**
> Hello I am writing a program for my h/w in C which involves using open,read, write system calls:
The problem is that the program is not leting me enter the marital status; am I misiing something about the write system call?
```

#include<stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include<unistd.h>
#include<string.h>

struct Student
{
  char name[21];
  char id[11];
  char DOB[9];
  char gender[2];
  char status[2];
};

struct Student myArr[5];//An array of Struct Student  
// // int main()
{
  int x, y, z;
  char newline[2] = { "\n" };
  char sep[5] = { "    " };
  char buf1[] = { "Please enter the name of the student's:" };
  char buf2[] = { "Please enter the student's id:" };
  char buf3[] = { "Please enter the student's DOB:" };
  char buf4[] = { "Please enter the student's gender:" };
  char buf5[] = { "Please enter the student's marital status:" };

  //O_CREAT requires a third argument the mode which specifies the access permission bits
  //S_IRWXU indicates that the user has read, write and execute permissions
  x = open( "/home/user/Desktop/Labsheets/Labsheet4/input.dat", O_RDWR | O_CREAT | O_TRUNC, S_IRWXU );
  //note that fd is 1 since it is the standard input
  //will read from standard input and place data in the buffer
  //read return number of bytes read
  int i;
  for( i = 0; i < 5; i++ )
  {
    write( 1, buf1, strlen(buf1) );
    read( 0, myArr[i].name, 20 );//read from standard input and place data in buffer
    write( 1, buf2, strlen(buf2) );;
    read( 0, myArr[i].id, 10 );
    write( 1, buf3, strlen(buf3) );
    read( 0, myArr[i].DOB, 9 );
    write( 1, buf4, strlen(buf4) );
    read( 0, myArr[i].gender, 1 );
    write( 1, buf5, strlen(buf5) );
    read( 0, myArr[i].status, 1 );
  }
  for(  i = 0; i < 5; i++ )
  {
    write( x, myArr[i].name, strlen(myArr[i].name) );
    write( x, sep, 4 );
    write( x, myArr[i].id, strlen(myArr[i].id) );
    write( x, sep, 4 );
    write( x, myArr[i].DOB, strlen(myArr[i].DOB) );
    write( x, sep, 4 );
    write( x, myArr[i].gender, strlen(myArr[i].gender) );
    write( x, sep, 4 );
    write( x, myArr[i].status, strlen(myArr[i].status) );
    write( x, newline, 4 );
  
  }
 
  return 0;
}

```

I think what happens is that when you read one byte (the gender), the newline which you also entered remains in the input buffer and is read by the next 'read' call.

---

### Post by Dark-Byte on 2009-09-30
Well if it is the newline that remains in the input queue I should not have been able to input the previous details but I can input the name, Id, DOB and gender. Isn't it?

---

### Post by Arndt on 2009-09-30
> **Dark-Byte said:**
> Well if it is the newline that remains in the input queue I should not have been able to input the previous details but I can input the name, Id, DOB and gender. Isn't it?

It depends on how much you input, but in the case of gender, you have to input one character and one newline, which is two bytes, whereas you read only one.

Look at what the 'read' calls return, that may clarify things.

---

