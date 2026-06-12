---
title: "C++ command line arguement question"
date: 2007-02-27
forum: Programming Talk
---

### Post by &lt;EggMan&gt; on 2007-02-27
I need some help in converting a command line arguement into a character array for comparison to another character array. How would i do so?

---

### Post by WW on 2007-02-27
In C++, the command line arguments are already character arrays. Here is a pretty standard  example:
```
#include <iostream>
using namespace std;

int main(int argc, char* argv[])
{
   cout << "argc = " << argc << endl;
   for(int i = 0; i < argc; i++)
      cout << "argv[" << i << "] = " << argv[i] << endl;
   return 0;
}
```
Do you mean you want to convert the command line argument to a C++ string?

---

### Post by &lt;EggMan&gt; on 2007-02-27
No, i need to set a string equal to the input from the command line arguement so I can get into some if statements that depend on what the string is.

I have it set to check to see if anything was done to the command line, if not it asks the user for input from a cin, if something is in the command line it sets the string one would enter in the cin equal to argv.

---

### Post by lnostdal on 2007-02-27
hm, like this: [http://nostdal.org/~lars/programming/c/argc-v.c](http://nostdal.org/~lars/programming/c/argc-v.c) ..?

(converting to c++ should be easy)

---

### Post by Wybiral on 2007-02-27
> ... Do you mean you want to convert the command line argument to a C++ string?

> No, i need to set a string equal to the input from the command line arguement ...

That's exactly what he asked you!

It's easy... WW's example was showing you how to access all of the command line arguments. It's very very easy to move them over to a C++ string type if you know how to access them...

```

#include <iostream>
#include <string>

using namespace std;

int main(int argc, char** argv)
{
   string arg_buffer;
   if(argc==1)
   {
      cout << "No arguments given!";
   }
   else
   {
      for(int i=1; i<argc; ++i)
      {
         arg_buffer = argv[i];
         cout << arg_buffer << endl;
      }
   }
}

```

"argv" is an array that holds all of the command line arguments. First it holds the program title, so if they enter:
```

./a.out a b c

```

then "argv" would hold:

```

argv[0] = "a.out"
argv[1] = "a"
argv[2] = "b"
argv[3] = "c"

```

"argc" tells you how many arguments there are... If it is 1, then there are NO arguments because the first argument is the program title... Get it?

---

### Post by &lt;EggMan&gt; on 2007-02-27
Yeah, thanks for all the help guys, but i managed to figure it out of my own accord. 

Much appreciated though.

---

### Post by thumper on 2007-02-27
Take a look at the boost library for command line parsing.

It takes a little while to get your head around it, but it is well worth the time and effort to learn if you are wanting to do anything non-trivial with command line options.

---

