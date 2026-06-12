---
title: "[SOLVED] [C] Pointer + Struct + I/O"
date: 2008-08-05
forum: Programming Talk
---

### Post by carbon-12 on 2008-08-05
I read the tutorials and everything seems to make sense but when I actually have to write a program everything falls apart :(

The exercise is pretty simple (not to me :( ) : create a Person data type, input user defined values into the data type, then print it out.

Note:
1.) Yeah I know I forgot to check to see if malloc fails but it shouldn't matter in a trivial app, right?

2.) I know that when I'm outputting the info that its not printing the name and address but the actual memory address instead, since p->name and p->addr are just the pointers. I wasn't sure what to do.

```

#include <stdio.h>
#include <string.h>

int main()
{
    typedef struct {
            char *name;
            char *addr;
            int age;
            } Person;
            
    Person *p;
    p = (Person *) malloc(sizeof(Person));

    printf("Enter Name, Address, and Age : ");
    
    char *temp_name, *temp_addr;
    int temp_age;
    scanf("%s %s %d",temp_name,temp_addr,&temp_age);
    
    p->name = (char *) malloc(sizeof(strlen(temp_name) + 1));
    p->addr = (char *) malloc(sizeof(strlen(temp_addr) + 1));
    p->name = &temp_name;
    p->addr = &temp_addr;
    p->age = temp_age;
  
    printf("\nName: %s\nAddress: %s\nAge: %d \n\n",p->name, p->addr, p->age);
    system("pause");
    
    free(p);
    free(p->name);
    free(p->addr);
    
    return 0;
} 

```

---

### Post by anubhavrocks on 2008-08-05
Instead of 
```
char *temp_name, *temp_addr;
```

use 
```
char temp_name[32],temp_addr[168];
```



Also get a good book on C.

---

### Post by carbon-12 on 2008-08-05
> **anubhavrocks said:**
> Instead of 
```
char *temp_name, *temp_addr;
```

use 
```
char temp_name[32],temp_addr[168];
```



Also get a good book on C.

I'd like the app to take as much space as needed. If I did 'temp_name[32]' and the user inputs a value greater than 31 characters (+1 for '\o') then wouldn't it start corrupting memory?

---

### Post by hod139 on 2008-08-05
You were causing a buffer overflow into 
  char *temp_name, *temp_addr;
since you were not allocating any space for them.  You can use scanf to allocate for you, and you also do not need to create any temporaries.  In the future, if you want to copy two string, you cannot use the = operator, you must use strncpy (please don't use strcpy).  Lastly, you were not freeing in the correct order.

[php]
int main()
{
    typedef struct {
            char *name;
            char *addr;
            int age;
            } Person;
            
    Person *p;
    p = (Person *) malloc(sizeof(Person));

    printf("Enter Name, Address, and Age : ");    
    
    // use the 'a' delimiter and pass the address of the pointer to have scanf allocate the space for you
    scanf("%as %as %d",&p->name,&p->addr,&p->age);
    
    printf("\nName: %s\nAddress: %s\nAge: %d \n\n",p->name, p->addr, p->age);
    
    // not portable
    //system("pause");
    
    // The order of freeing is important, you cannot free p before p->name and p->addr
    free(p->name);
    free(p->addr);
    free(p);
    
    return 0;
}
[/php]

---

### Post by dwhitney67 on 2008-08-05
> **carbon-12 said:**
> I read the tutorials and everything seems to make sense but when I actually have to write a program everything falls apart :(

Not all books/tutorials are created to be equally worthy of reading.  In my opinion, learning about structures is an important facet of C (and C++) programming, however combining the teaching of these with memory allocation is a poor choice.

Let's stick to the basics for now so that you understand what is going on.  Here's a program that hopefully you will be able to get a handle on:
[PHP]#include <stdio.h>    // for printf(), fgets(), and scanf()
#include <string.h>   // for strlen()

int main( int argc, char **argv )
{
  typedef struct
  {
    char         name[80];     // declare fixed-sized array
    char         addr[256];    // declare fixed-sized array
    unsigned int age;          // age can not ever be less than zero
  } Person;


  Person p;    // declare a variable called 'p' of type Person

  printf( "Enter the person's name: " );
  fgets( p.name, sizeof(p.name), stdin );
  p.name[ strlen(p.name) - 1 ] = '\0';     // remove the carriage return

  printf( "Enter the person's address: " );
  fgets( p.addr, sizeof(p.addr), stdin );
  p.addr[ strlen(p.addr) - 1 ] = '\0';     // remove the carriage return

  printf( "Enter the person's age: " );
  scanf( "%d%*c", &p.age );

  // print results
  //
  printf( "name: %s\n", p.name );
  printf( "addr: %s\n", p.addr );
  printf( "age : %u\n", p.age );

  return 0;
}[/PHP]
Ok, when reading in a string _always_ use fgets().  Do not use any other function such as scanf(), fscanf(), etc. because these a prone to buffer overflows.

When you understand the basics shown above, then you can migrate to using dynamic memory allocation in lieu of fixed-sized buffers.  But the tact used above to get the user input pretty much remains the same.  Only the syntax of accessing the structure varies, and of course, the use of malloc() and free().

Here's an example:
[PHP]#include <stdio.h>     // for printf(), fgets(), and scanf()
#include <string.h>    // for strlen()
#include <stdlib.h>    // for malloc() and free()


int main( int argc, char **argv )
{
  typedef struct
  {
    char         *name;
    char         *addr;
    unsigned int age;
  } Person;


  // allocate memory
  Person *p = malloc( sizeof(Person) );
  p->name = malloc(80);
  p->addr = malloc(256);

  // get user input
  printf( "Enter the person's name: " );
  fgets( p->name, 80, stdin );
  p->name[ strlen(p->name) - 1 ] = '\0';     // remove the carriage return

  printf( "Enter the person's address: " );
  fgets( p->addr, 256, stdin );
  p->addr[ strlen(p->addr) - 1 ] = '\0';     // remove the carriage return

  printf( "Enter the person's age: " );
  scanf( "%u%*c", &p->age );

  // print results
  printf( "name: %s\n", p->name );
  printf( "addr: %s\n", p->addr );
  printf( "age : %u\n", p->age );

  // deallocate memory
  free( p->name );
  free( p->addr );
  free( p );

  return 0;
}[/PHP]

---

### Post by dwhitney67 on 2008-08-06
> **hod139 said:**
> 
[php]
...
    // use the 'a' delimiter and pass the address of the pointer to have scanf allocate the space for you
    scanf("%as %as %d",&p->name,&p->addr,&p->age);
...
[/php]
On what platform or compiler is the information you provided above true?  Is it a Windoze thing, thus in essence not portable?

Edit -- Take 2 -- It appears the 'a' option is not supported by ISO C; if the C program is compiled with the -Wall option, then the following warning message is presented:
```
file.c:7: warning: ISO C does not support the 'a' scanf flag

```

---

### Post by hod139 on 2008-08-06
> **dwhitney67 said:**
> ]Ok, when reading in a string _always_ use fgets().  Do not use any other function such as scanf(), fscanf(), etc. because these a prone to buffer overflows.


While incorrect use of scanf can lead to buffer overflows, it makes reading non string input so much easier.  But yes you have to be extra careful when using it to read strings, never use the "%s" modifier alone.

This code is just as save as fgets, but it takes extra work
```

char buffer[10];

if ( scanf( "%9s", buffer ) == 1 )
  // success
else
 // fail


```[COLOR=#000000][COLOR=#007700]

[/COLOR][/COLOR]

---

### Post by carbon-12 on 2008-08-06
> **hod139 said:**
> You were causing a buffer overflow into 
  char *temp_name, *temp_addr;
since you were not allocating any space for them.  You can use scanf to allocate for you, and you also do not need to create any temporaries.  In the future, if you want to copy two string, you cannot use the = operator, you must use strncpy (please don't use strcpy).  Lastly, you were not freeing in the correct order.

[php]
int main()
{
    typedef struct {
            char *name;
            char *addr;
            int age;
            } Person;
            
    Person *p;
    p = (Person *) malloc(sizeof(Person));

    printf("Enter Name, Address, and Age : ");    
    
    // use the 'a' delimiter and pass the address of the pointer to have scanf allocate the space for you
    scanf("%as %as %d",&p->name,&p->addr,&p->age);
    
    printf("\nName: %s\nAddress: %s\nAge: %d \n\n",p->name, p->addr, p->age);
    
    // not portable
    //system("pause");
    
    // The order of freeing is important, you cannot free p before p->name and p->addr
    free(p->name);
    free(p->addr);
    free(p);
    
    return 0;
}
[/php]

I just tried that and got the following output:
```

Enter Name, Address, and Age : josh fakestreet 22

Name: &#9492;&#9830;=
Address: &#9492;&#9830;=
Age: 1380205901

Press any key to continue . . .

```

My linux machine is at home, this is on WinXP SP2/Dev-C++ 4.9.9.2 Isn't:

```
printf("\nName: %s\nAddress: %s\nAge: %d \n\n",p->name, p->addr, p->age);
```

just outputting the memory address of name and addr?

---

### Post by hod139 on 2008-08-06
> **dwhitney67 said:**
> On what platform or compiler is the information you provided above true?  Is it a Windoze thing, thus in essence not portable?

Edit -- Nevermind... it just appears that it is not usable with the -std=gnu99 C compiler option.  I wonder why the man-page doesn't mention the 'a' option??

It's not portable, but it's a gnu extension, not windows.  I'm surprised though that it doesn't work with std=gnu99.  I will have to look into that.

---

### Post by hod139 on 2008-08-06
> **carbon-12 said:**
> 
My linux machine is at home, this is on WinXP SP2/Dev-C++ 4.9.9.2 
The "%as" trick will only work with gcc, not on windows.  And apparently only with the c89 standard.  Best bet is to preallocate and use what dwhitney67 showed, or be very careful with scanf and use "%Ns", where N is the size of allocated array.

---

### Post by hod139 on 2008-08-06
> **dwhitney67 said:**
> 
Edit -- Take 2 -- It appears the 'a' option is not supported by ISO C; if the C program is compiled with the -Wall option, then the following warning message is presented:
```
file.c:7: warning: ISO C does not support the 'a' scanf flag

```

I don't get that warning, I always use the -Wall option.  gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

---

### Post by dwhitney67 on 2008-08-06
> **hod139 said:**
> It's not portable, but it's a gnu extension, not windows.  I'm surprised though that it doesn't work with std=gnu99.  I will have to look into that.
I found out it is not the -std=gnu99... the option is merely not supported by ISO C standards.  I edited my previous post where I questioned the validity of the option.

---

### Post by carbon-12 on 2008-08-06
> **dwhitney67 said:**
> Not all books/tutorials are created to be equally worthy of reading.  In my opinion, learning about structures is an important facet of C (and C++) programming, however combining the teaching of these with memory allocation is a poor choice.

Let's stick to the basics for now so that you understand what is going on.  Here's a program that hopefully you will be able to get a handle on:
[PHP]#include <stdio.h>    // for printf(), fgets(), and scanf()
#include <string.h>   // for strlen()

int main( int argc, char **argv )
{
  typedef struct
  {
    char         name[80];     // declare fixed-sized array
    char         addr[256];    // declare fixed-sized array
    unsigned int age;          // age can not ever be less than zero
  } Person;


  Person p;    // declare a variable called 'p' of type Person

  printf( "Enter the person's name: " );
  fgets( p.name, sizeof(p.name), stdin );
  p.name[ strlen(p.name) - 1 ] = '\0';     // remove the carriage return

  printf( "Enter the person's address: " );
  fgets( p.addr, sizeof(p.addr), stdin );
  p.addr[ strlen(p.addr) - 1 ] = '\0';     // remove the carriage return

  printf( "Enter the person's age: " );
  scanf( "%d%*c", &p.age );

  // print results
  //
  printf( "name: %s\n", p.name );
  printf( "addr: %s\n", p.addr );
  printf( "age : %u\n", p.age );

  return 0;
}[/PHP]
Ok, when reading in a string _always_ use fgets().  Do not use any other function such as scanf(), fscanf(), etc. because these a prone to buffer overflows.

When you understand the basics shown above, then you can migrate to using dynamic memory allocation in lieu of fixed-sized buffers.  But the tact used above to get the user input pretty much remains the same.  Only the syntax of accessing the structure varies, and of course, the use of malloc() and free().

Here's an example:
[PHP]#include <stdio.h>     // for printf(), fgets(), and scanf()
#include <string.h>    // for strlen()
#include <stdlib.h>    // for malloc() and free()


int main( int argc, char **argv )
{
  typedef struct
  {
    char         *name;
    char         *addr;
    unsigned int age;
  } Person;


  // allocate memory
  Person *p = malloc( sizeof(Person) );
  p->name = malloc(80);
  p->addr = malloc(256);

  // get user input
  printf( "Enter the person's name: " );
  fgets( p->name, 80, stdin );
  p->name[ strlen(p->name) - 1 ] = '\0';     // remove the carriage return

  printf( "Enter the person's address: " );
  fgets( p->addr, 256, stdin );
  p->addr[ strlen(p->addr) - 1 ] = '\0';     // remove the carriage return

  printf( "Enter the person's age: " );
  scanf( "%u%*c", &p->age );

  // print results
  printf( "name: %s\n", p->name );
  printf( "addr: %s\n", p->addr );
  printf( "age : %u\n", p->age );

  // deallocate memory
  free( p->name );
  free( p->addr );
  free( p );

  return 0;
}[/PHP]

Thanks dwhitney, this works perfectly!

---

### Post by dwhitney67 on 2008-08-06
> **hod139 said:**
> I don't get that warning, I always use the -Wall option.  gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
On my Ubuntu system, running the same gcc as you, it takes the -pedantic to spew out the warning.
```
$ /usr/bin/gcc -Wall -pedantic test.c 
test.c: In function ‘main’:
test.c:7: warning: ISO C does not support the 'a' scanf flag
```
The other test I performed earlier was on my Fedora 9 system; it sports GCC version 4.3.0.  All it took was the -Wall to spew out the warning.

---

### Post by hod139 on 2008-08-06
Cool, thanks for the info.  Looks like gcc is trying to start discouraging the use of the "%as" modifier.  I've always found it convenient the few times I ever have to do stdin input in C, though portability was never a concern in those cases.  It just seems to make sense to me that the function reading the unknown string input should have the ability to allocate the buffer it is reading into, if desired.

---

### Post by dwhitney67 on 2008-08-06
I slapped the following entry into my ~/.bashrc file so that I am always reminded of warnings when I compile with 'gcc':
```
alias gcc='/usr/bin/gcc -Wall -pedantic -std=c99'
```

---

