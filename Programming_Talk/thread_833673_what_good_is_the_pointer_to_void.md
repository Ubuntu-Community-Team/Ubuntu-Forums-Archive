---
title: "what good is the pointer to void?"
date: 2008-06-18
forum: Programming Talk
---

### Post by techmarks on 2008-06-18
Trying to understand the pointer to void I did this;

```

#include <iostream>

using namespace std;

//the function prototype
void printstring(void *ptrvoid);

int main()
{

const int LEN = 80;
char str[LEN];


strcpy(str, "text");

printstring(str);



}

void printstring(void *ptrvoid)
{

cout<< "the string is "<< ptrvoid <<endl;

}


```

So I thought it would print like this;

the string is text

but doesn't work instead I got;

the string is 0xbfbfebb0

Can this work?

---

### Post by slavik on 2008-06-18
a void* is called "a pointer to anything" ...

for example: if you want to have a function that takes a pointer to anything and then treats it differently depending on other parameters. This is extremely useful in C because there is no overloading (or when you don't want to use it in C++).

if you look at some of the C I/O functions, they ask for a void*

---

### Post by sq377 on 2008-06-18
An example of this, libcurl.  It has a function to set a callback to view the progress of a download.  So whenever it gets data, it runs whatever function you give it.  If you do not want to use global variables (as it is generally bad practice), you can pass it  a void * containing whatever you need. It really can't be any other type, because libcurl doesn't know what I want to send it.  I might want to send it just a normal type (int, char*), or a structure that I created and it would have no idea about.  There are probably other uses, but this is generally how I see it used.

---

### Post by techmarks on 2008-06-18
hooray!

I finally got it to work

```


#include <iostream>

using namespace std;

//the function prototype
void printstring(void *ptrvoid);

int main()
{

const int LEN = 80;
char str[LEN];


strcpy(str, "text");

printstring(str);



}

void printstring(void *ptrvoid)
{

 //the  void pointer needs to be cast to work!!

cout<< "the string is "<< (const char *)ptrvoid <<endl; 

}


```


just need to cast it right and it printed right!

notice the line is now;

cout<< "the string is "<< (const char *)ptrvoid <<endl;

---

### Post by WW on 2008-06-19
> **techmarks said:**
> 
just need to cast it right and it printed right!

notice the line is now;

cout<< "the string is "<< (const char *)ptrvoid <<endl;
OK, but that is an "old style" C cast. You are using C++, so you should get in the habit of using [C++ casts](http://www.acm.org/crossroads/xrds3-1/ovp3-1.html).  In this case:
```

cout << "the string is " << static_cast<char*>(ptrvoid) << endl; 

```

---

### Post by JupiterV2 on 2008-06-19
I like to think of C's void pointer as C++'s templates. Since C doesn't have templates, the only way (as other posters have already noted) to represent multiple types of data is via void*.

If the significance isn't immediately obvious, an example would be a linked list, vector, or some other object which you don't want to have predefined data in. If you need a variable to store any kind of data you throw at it, void* is the way to go. There are drawbacks, like casting it properly, but sometimes its the only answer.

As WW noted, in C++ it is much better to cast with C++ style casts.

Generally speaking though, I would think its better to use function overloading or templates in C++ rather than a void* but ultimately, its up to you to decide what will work best for a particular situation.

---

