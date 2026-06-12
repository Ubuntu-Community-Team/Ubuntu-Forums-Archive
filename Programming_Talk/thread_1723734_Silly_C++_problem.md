---
title: "Silly C++ problem"
date: 2011-04-07
forum: Programming Talk
---

### Post by fallenshadow on 2011-04-07
Can somebody put me out of my misery? 

I already asked a friend of mine but he couldn't see anything wrong with it either. I know its probably simple but I can't see it!

[PHP]
#include <iostream>
#include <string>

#define SIZE 2
using namespace std;

struct studentDetails{
int studentID;
string name;

} student [SIZE];

char DisplayMenu()
{
	string menuValue;

	cout << endl;
    cout << "Please select an option from the menu:" << endl;
    cout << endl;
    cout << "\t\t1. Read in student details" << endl;

    cout << "\t\tQ. Quit from this program" << endl;
    cout << endl;
    cin>>menuValue;
    cout << endl;

	return toupper(menuValue[0]); 
}

void readDetails(student *sArray)

{

	for (int n=0; n<ARRAYSIZE; n++)

                {

                    cout << "Enter studentID" <<endl;
                    cin >> sArray[n]->studentID;

                    cout << "Enter student name" <<endl;
                    cin >> sArray[n]->name;

                }

}

int main()
{
    //create instance of student

    struct studentDetails student[10];

    bool done = false;

	do {
		const char choice = DisplayMenu();

    switch (choice) {
      case'1':
				cout << "Read in student details" << endl;
				cout << endl;

				void readDetails(student *sArray);
        break;

      case'Q':
      	done = true;
       	break;

      default:
      	cout << "Please select a valid option" << endl;
       	break;
    }

   } while (!done);

		cout << "You have now quit the program" << endl;

    return 0;


}

[/PHP]

Errors:
arraystuct.cc:30: error: variable or field &#8216;readDetails&#8217; declared void
arraystuct.cc:30: error: &#8216;sArray&#8217; was not declared in this scope

---

### Post by simeon87 on 2011-04-07
You can't call a function with the return type in front of it:

```
void readDetails(student *sArray);
```
should be
```
readDetails(student *sArray);
```

Also, sArray is not in scope there, in main(), so what exactly did you intend to pass to that function?

---

### Post by GeneralZod on 2011-04-07
```

void readDetails(student *sArray)

```

"student" is the name of a variable, not a type.

---

### Post by fallenshadow on 2011-04-07
Basically I just want to do an array of structs... note that I was on alot of pills to help me get better at the time I was programming this... so im not sure what I was doing. :D

> Also, sArray is not in scope there, in main(), so what exactly did you intend to pass to that function?

I guess I just wanna pass in the struct array... I was told to use a pointer at the time.

> "student" is the name of a variable, not a type.

So what should I do?? Its a struct I wanna pass in, so what type is that?

---

### Post by Arndt on 2011-04-07
> **fallenshadow said:**
> Basically I just want to do an array of structs... note that I was on alot of pills to help me get better at the time I was programming this... so im not sure what I was doing. :D



I guess I just wanna pass in the struct array... I was told to use a pointer at the time.



So what should I do?? Its a struct I wanna pass in, so what type is that?

The type you declared 'student' as: struct studentDetails.

---

### Post by fallenshadow on 2011-04-07
> The type you declared 'student' as: struct studentDetails. 

Now its coming up with a list of about 10 errors. :o

I think I have an older version I will look for... before I messed it up completely. Or could somebody either post a fixed version of what im doing or post an example of a struct array?(with functions)

---

### Post by dwhitney67 on 2011-04-07
You have two 'student' arrays declared; you probably only wanted one, right?
```

...
} student [SIZE];
...
struct studentDetails student[10];

```

In one place (see above) you use SIZE, which is defined to equal 2.  In another place of the code, you use a variable named 'ARRAYSIZE' -- which has not even been declared.

If possible, avoid the use of arrays in C++, especially when they are obviously not needed (in your code, for example).  Use an STL vector.

---

### Post by Arndt on 2011-04-07
> **fallenshadow said:**
> Now its coming up with a list of about 10 errors. :o

I think I have an older version I will look for... before I messed it up completely. Or could somebody either post a fixed version of what im doing or post an example of a struct array?(with functions)

Never think much about how many errors you get. The first may cause all the others.

---

### Post by fallenshadow on 2011-04-08
Ah yes that is a big part of my problem... I didn't see that I was creating 2 arrays when I only want 1 of course. :D

However I still have these 2 errors that I had at the beginning:

arraystuct.cc:30: error: variable or field ‘readDetails’ declared void
arraystuct.cc:30: error: ‘sArray’ was not declared in this scope

Should this line of code:

```
void readDetails(student *sArray)
```

be changed to:

```
void readDetails()
```

?

I mean I don't think I need to pass in anything if im just reading values.

---

### Post by dwhitney67 on 2011-04-08
Avoid the use of global variables!

```

#include <vector>

struct StudentDetails
{
   ...
};

void readDetails(std::vector<StudentDetails>& students)
{
   // Use URL for information about the STL vector
   //
   // http://www.cplusplus.com/reference/stl/vector/
}

int main()
{
   std::vector<StudentDetails> students;

   ...

   readDetails(students);

   ...
};

```

---

### Post by fallenshadow on 2011-04-08
Im sorry dWhitney but I have to use an array of structs and not vectors. :p Yes I know vectors are better but im not allowed to use them.

---

### Post by dwhitney67 on 2011-04-08
Fine; back to the basics:
```

struct Foo
{
   int val;
};

static const int MAX_SIZE = 10;

void readFoo(Foo (&f)[MAX_SIZE])
{
   for (int i = 0; i < MAX_SIZE; ++i)
   {
      ...
   }
}

int main()
{
   Foo foo[MAX_SIZE];

   readFoo(foo);
}

```

or alternatively:
```

struct Foo
{
   int val;
};

void readFoo(Foo* f, const size_t numElements)
{
   for (size_t i = 0; i < numElements; ++i)
   {
      ...
   }
}

int main()
{
   Foo foo[10];

   readFoo(foo, sizeof(foo) / sizeof(Foo));
}

```

---

### Post by fallenshadow on 2011-04-08
I learn't now that I should have not tried any coding while on heavy medication... what I showed ye guys was only a very small part of a big program but im after messing the whole thing up when I worked on it! :lolflag:

However I think I will just start the program again from the basics! :)

dWhitney... I love you! :D but seriously thanks for helping me out of a spot of bother again! :)

---

