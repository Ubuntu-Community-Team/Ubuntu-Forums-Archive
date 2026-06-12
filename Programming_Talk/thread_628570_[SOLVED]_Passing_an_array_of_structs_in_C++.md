---
title: "[SOLVED] Passing an array of structs in C++"
date: 2007-12-01
forum: Programming Talk
---

### Post by totalnub on 2007-12-01
[COLOR="Red"][B]EDIT: I've seemingly found a solution that doesn't include the typedef statement; rather
```

struct PersonData
{
    char sex;
    int answer[NUMQ];
    string name;
} males[15], females[15], errors[15];

```
then passing all occurances of the arrays as type PersonData []

if anyone has a better solution, i'd still like to hear it as i'm learning c++ and this is all new to me :)[/B][/COLOR]

I'm writing a program that processes data in a text file. I'm using 2 parallel arrays containing structs. 

The program works fine (thus far) when i have everything in main(), but when i try to incorporate the same code in a function i get a nasty error log at compile time.

[php]
#include<iostream>
#include<fstream>
#include<string>

using namespace std;

const int NUMQ = 10;
const char ignore = '0';

struct PersonData
{
    char sex;
    int answer[NUMQ];
    string name;
};

typedef PersonData Personlist[15];

void InputWithFilter(	Personlist [15]);

int main()
{
    ifstream inFile;
    Personlist males;
    Personlist females;
...
...
	InputWithFilter(males);
	InputWithFilter(females);
return 0;
}

void InputWithFilter(Personlist group[15])
{
	bool erranswer, nameError;
	
	for (int i = 0; i < 15; i++)
	{
		erranswer = false;
		nameError = false;
etc etc.....
	}
}
[/php]

the error i'm getting is: 
```

 error: cannot convert &#8216;PersonData*&#8217; to &#8216;PersonData (*)[15]&#8217; for argument &#8216;1&#8217; to &#8216;void InputWithFilter(PersonData (*)[15])&#8217;

```

any ideas? i know that it has to do with pointers and how i'm passing my array, but i don't know how to fix it.

---

### Post by geirha on 2007-12-01
I don't see the point of the PersonList typedef. You want males to be a list of 15 person-datas right? so in main() you just do
```

PersonData males[15];
InputWithFilter(males);

```
and InputWithFilter() takes in a list of 15 PersonDatas like
```
void InputWithFilter(PersonData personlist[15]) { 
    personlist[0].name="something"; 
}

```

---

### Post by dwhitney67 on 2007-12-01
> **geirha said:**
> I don't see the point of the PersonList typedef. You want males to be a list of 15 person-datas right? so in main() you just do
```

PersonData males[15];
InputWithFilter(males);

```
and InputWithFilter() takes in a list of 15 PersonDatas like
```
void InputWithFilter(PersonData personlist[15]) { 
    personlist[0].name="something"; 
}

```

Shouldn't that array be passed by reference, especially since it appears that a fixed-sized array will be used?  If the method needs to be more flexible (to handle variably-sized arrays), then another parameter is going to be needed to indicate how big the array is.  Or better yet, the OP should consider utilizing an STL vector or list.

Anyhow, consider this declaration instead.  It forces the parameter that is passed to the function to be exactly 15 elements in size.

```
void InputWithFilter( PersonData (&personList)[15] ) {
...
}
```

---

### Post by Vadi on 2007-12-01
Read up on struct here ([click]("http://www.cplusplus.com/doc/tutorial/structures.html")) and on typedef here ([click]("http://www.cplusplus.com/doc/tutorial/other_data_types.html")).

---

### Post by totalnub on 2007-12-01
thanks for the input guys. for some reason i do recall my teacher telling me that it was standard/required to have a typedef when making arrays of structures. 

all is good though. :)

---

