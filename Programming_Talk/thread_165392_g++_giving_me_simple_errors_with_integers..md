---
title: "g++ giving me simple errors with integers."
date: 2006-04-24
forum: Programming Talk
---

### Post by Knowledge2012 on 2006-04-24
Hi. I just started programming this week, so this may be  a simple error on my part,  but i dont think it is, i think there is something wrong with my g++ installation. If i try and compile the code below.

#include <iostream>
using namespace std;
int name;
int main()
{
            name = andre;
            cout << "My name is " << name <<"\n";
            return (0)
}

When trying to compile the code i get this error 
"error: ‘andre’ was not declared in this scope" .

This seems like a very simple problem, i was able to get my first hello world program runing, after figure out that i had to use namespace std; with g++, maybe there is something else i need to do to get intergers to work?

---

### Post by cgjones on 2006-04-24
Ignore what I originally said here, I need to have my eyes checked.

---

### Post by jazzmuzik on 2006-04-24
It's been a while since I played with C++, but some obvious problems:

int name;

Here you declare an integer, which is a number. And then later you try to assign a string (text) to it. That won't work. 'name' needs to be declared as a string (or char). If the libraries are available via iostream.h, you might try:

String name;

or is it 

string name;

??

Also, andre needs to be in quotes:

name = "andre";

If it's not in quotes C++ thinks it is a variable.

---

### Post by gborzi on 2006-04-24
Tha variable name is an int, while andre has no type, i.e. it was not declared. If you wanted to print "My name is andre" where andre is a string you want to change, your program should read as

[I]#include <iostream>
#include <string>
using namespace std;

int main()
{
string name = "andre";
cout << "My name is " << name << endl;
return (0)
}

[/I]

---

### Post by Knowledge2012 on 2006-04-24
Ok, i figured out what was wrong due to your posts of my obvious mistake :). I should have known what to put there as the guide that im reading off of just went over char, i guess i was to busy thinking int ruled everything or somthing, anyways i corrected the simple mistake, But i am getting one error still that i cant figure out. The new program looks ike

#include <iostream>
char name;
int main()
{

             name = 'andre';
             cout << "My name is " << name <<"\n";
             return (0);
}

after compiling i get one error "warning: character constant too long for its type" , given the content of the error it seems that there is somthing wrong with the char?

BTW, thnx for such a quick reply

---

### Post by jazzmuzik on 2006-04-24
char only stores a single character. If you want to assign a bunch of characters you need to declare a string, something like:

char name[10];

But I wouild try gborzi's suggestion and just substitute 'string' for 'char' and see if that works. string is easier to work with as it does a lot of things for you like setting the proper buffer size and null terminating the text, etc.

---

### Post by cgjones on 2006-04-24
The type char represents a single character, you'll have to use a string. And you should be declaring name within main().

---

### Post by Knowledge2012 on 2006-04-24
Thnx guys for helping on creating my second program. I didnt use string, because it is not covered in the O'reilly practicle programming guide yet, so i just used char and int. Its exiting to see a program run for the first time, even if it is just simple code. 

Thanks again. on to next chapter.

---

### Post by gborzi on 2006-04-24
you can also declare name as
char name[] = "andre";
or
char *name = "andre";
but I'm not sure if a char const instead of a simple char is needed.

---

### Post by rplantz on 2006-04-25
[QUOTE=Knowledge2012]Thnx guys for helping on creating my second program. I didnt use string, because it is not covered in the O'reilly practicle programming guide yet, so i just used char and int. Its exiting to see a program run for the first time, even if it is just simple code. 

Thanks again. on to next chapter.[/QUOTE]

As a retired cs professor, I want to avoid giving you solutions that go beyond the guide you are following. It can be confusing. Here is an example I've created that should illustrate the differences between int and char for you.

```

// name.cc

#include <iostream>
using namespace std;

int main() {
  char name1 = 'a';
  char name2 = 'n';
  char name3 = 'd';
  int n = 3;

  cout << "Here are the first " << n;
  cout << " letters of my name:\n";
  cout << name1 << name2 << name3 << "\n";

  return 0;
}

```
Notice that single quotes designate a single character. Double quotes designate a sequence of characters that end with the NUL character. (This is a C-style string; the C++ string type is much more complex.)

If you don't know the ascii code yet, type "man ascii" in a terminal window and you will see how characters are represented. Notice that the character 'a' is represented as the (8-bit) integer 97 (in decimal). The character '\n' (yes, that resolves to only one character in the program) is represented by 10 (decimal). So the C-style string "\n" takes up two character positions in your program. The first is 10 and the second is 0.

---

