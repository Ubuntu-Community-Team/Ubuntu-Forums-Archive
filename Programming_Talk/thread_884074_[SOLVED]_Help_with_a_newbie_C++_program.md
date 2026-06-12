---
title: "[SOLVED] Help with a newbie C++ program"
date: 2008-08-08
forum: Programming Talk
---

### Post by Stoodle on 2008-08-08
Well I'm thoroughly stumped. I'm trying to create a program that will cut up text files into smaller text files and place them in a folder. I'm at the beginning of this program and I keep running into a segfault error and I really don't know what to do. Please help.



```

#include <cstdio>
#include <cstdlib>
#include <iostream>
#include <sys/stat.h>
#include <string>
#include <fstream>

using namespace std;


struct stat fileResults;

//Tests if the file exists
bool fileExists(char fName[])
{
    if(stat(fName,&fileResults)==0)
        return true;
    else
        return false;
}

    
    
int main(int argc, char* argv[])
{
    //Checks to see if there is was an argument through commandline
    char* fileName;
    if(argc>1)
        fileName = *(argv+1);
    long size = 0;
    ifstream inFile;
    //Opens file depending on if there's input from terminal or not.
    try
    {
        if(argc>1)
            if(fileExists(fileName)==true)
            {
                //Outputs size of file and opens it
                inFile.open(fileName);
                size = fileResults.st_size;
                cout << size<<endl;
            }
            else
                throw string("File does not exist.\n");
        //I need help in this else
        else
        {
            cout << "Enter the name of the file:\n";
            //Accepts input for fileName but also allocates 1 more space
            //for a null character
            
            cin >> fileName;
            //Adds space to the character pointer
            fileName = new char[1];
            //Adds a null character to terminate the string
            *(fileName+(sizeof fileName) - 1) = '\0';
            //Outputs file name for testing
            cout << fileName<<endl;
            
            if(fileExists(fileName)==true)
            {
                //Outputs size of file and opens it
                inFile.open(fileName);
                size = fileResults.st_size;
                cout << size<<endl;
            }
            else
                throw string("Why am I getting this error? (File does not exist.)\n");
        }
    }
    
    catch(string error)
    {
        cout << "Error: " << error;
    }
    catch(bad_alloc mError)
    {
        cout <<  "Memory Allocation error";
    }
    //Prints size of file (for testing)
    return 0;
}

```

---

### Post by mike_g on 2008-08-08
Segfaults generally mean that you are trying to use areas of memory outside of what you have allocated in your program. I think this is where your problem is:
>             //Adds space to the character pointer
            [COLOR="DarkRed"]fileName = new char[1];[/COLOR]
            //Adds a null character to terminate the string
            [COLOR="DarkGreen"]*(fileName+(sizeof fileName) - 1) = '\0';[/COLOR]

At the redline you set fileName to point to a newly allocated area of memory 1 char big; it does not reallocate existing memory with an extra byte.

On the green line you would then be writing out of bounds, which, if youre lucky will cause a segfault ;)

---

### Post by Stoodle on 2008-08-08
Yeah I figured that was it. However, I didn't know how to add the space. I thought from reading [http://www.cplusplus.com/doc/tutorial/dynamic.html](http://www.cplusplus.com/doc/tutorial/dynamic.html), maybe I was adding memory to the pointer.

How can I do it?

---

### Post by Stoodle on 2008-08-08
Well, I had an idea. How do I find the size of an array created by a character pointer?

---

### Post by era86 on 2008-08-09
> **Stoodle said:**
> Well, I had an idea. How do I find the size of an array created by a character pointer?

strlen() will do this for you.

Read more on malloc or new and free or delete for memory management.  This can be very tricky and can leave your programs with memory leaks.

---

### Post by catchmeifyoutry on 2008-08-09
Simple answer:

use "string" to read input, you've already included the correct <string> header:
[PHP]
#include <string>
#include <iostream>

using namespace std;

int main()
{
  string filename;
  cout << "Please enter filename: ";
  cin >> filename;
  cout << endl << "You have entered: " << filename << endl;
}
[/PHP]

string takes care of the memory allocation for you, and you don't have to worry about '\0' or having reserved enough memory.


Long answer:

> **Stoodle said:**
> Well, I had an idea. How do I find the size of an array created by a character pointer?

You don't. The trick with arrays is that you need to keep track of the array size yourself.
The character pointer just points to a location in memory, that's it. There is no magic information in the pointer that says that there are x bytes reserved for a string, starting at that location.
So you should fix the size of the array by hard coding its size in the program,
or allocate it dynamically and keep track if the amount of reserved data in some int.
But actually, "string" already does all that stuff for you and automatically reallocates more memory if it needs to.

Now if you don't want to use "string" because this is an exercise for you to work with pointers and character arrays, then take a look at this:

[http://www.cprogramming.com/tutorial/lesson9.html](http://www.cprogramming.com/tutorial/lesson9.html)

which explains the principles of using character arrays for strings, the '\0' delimiter, and why this can result in unsafe situations (or segfaults).

Best.

---

### Post by Stoodle on 2008-08-09
I didn't want to use string because of code I'd have to change. However, there's a lot of code I've had to change already! Some things like ifstream.open() don't accept strings as input however.

What I meant by "How do I find the size of an array created by a character pointer?" was when you do something like
```
char* string = "Hello";
```

Anyway, thanks guys for helping me.

---

### Post by Martin Witte on 2008-08-09
You can use string together with ifstream.open(const char * filename, ios_base::openmode mode = ios_base::in) by using the c_str() method of the string class, e.g:
```
#include <string>
#include <iostream>
#include <fstream>

int main()
{	
	std::ifstream f;
	std::string f_name("test.cpp"), line;
	f.open(f_name.c_str());
	if (f.is_open())
	{
		while (! f.eof() )
		{
			getline (f,line);
			std::cout << line << std::endl;
		}
		f.close();
	}
	
	return 0;
}
```

---

### Post by Martin Witte on 2008-08-09
> **Stoodle said:**
> What I meant by "How do I find the size of an array created by a character pointer?" was when you do something like
```
char* string = "Hello";
```

Like this:
```
#include <stdio.h>
#include <string.h>

int main()
{
	const char* s = "Hello";
	printf ("The sentence entered is %u characters long.\n",strlen(s));
	
	return 0;
}

```

---

### Post by EndOn9 on 2008-08-09
> **Stoodle said:**
> I didn't want to use string because of code I'd have to change. However, there's a lot of code I've had to change already! Some things like ifstream.open() don't accept strings as input however.


No, but calling the string classes handy dandy c_str() function will return the string as 'a pointer to an internal array containing the c-string equivalent of the string content'. 

e.g a format that things like ifstream.open() *will* accept.

I'd heartily recommend using the string class. It will make your life so much easier!

---

### Post by Stoodle on 2008-08-09
Hey, that looks useful. printf() is carried over from C right?

Well, I have solved my problem. I just had to change the input of my function to string, and for fileName.open(), I used string::c_str(). So I'm good! I've been stuck on this for a while.

:KS:KS

---

### Post by Achetar on 2008-08-09
> **Stoodle said:**
> I didn't want to use string because of code I'd have to change. However, there's a lot of code I've had to change already! Some things like ifstream.open() don't accept strings as input however.

What I meant by "How do I find the size of an array created by a character pointer?" was when you do something like
```
char* string = "Hello";
```Anyway, thanks guys for helping me.
Actually, yes they do, in a way. You can use the following to make a string act like a char array:
```

string mystring = "foobar"; //Define the string mystring containing the word *foobar*
ofstream outfile; //Create a new outfile
outfile.open(mystring.c_str(),ios::app); //Open the outfile named *foobar* to append to

```

EDIT: well, I guess I was a minute too late.

---

