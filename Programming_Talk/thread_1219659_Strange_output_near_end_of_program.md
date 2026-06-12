---
title: "Strange output near end of program"
date: 2009-07-22
forum: Programming Talk
---

### Post by blackmonjd on 2009-07-22
First off:

I don't know much about programming; it's just a hobby/interest, and one I don't practice at often. Feel free to laugh at my code.

Anyways, I have no clue why I'm getting strange characters output to the screen.

```
#include<stdlib.h>
#include<iostream>
#include<iomanip>
#include<fstream>
#include<string>

using namespace std;

int main()
{
    int count=0;
    int row=0; //position within various character arrays initialized to starting point of array
    int targSize, workSize, destSize; //TBD size of character array for working, target, destination paths
    char temp[100]; //temporary character array

    cout << "Enter directory containing files to be moved:" << endl;
    cin.get(temp[row]);

    while(temp[0]!='/') //make certain path starts in proper place
    {
        cin.ignore(9999,'\n');
        cout << "\n\nUnknown path.\nEnter directory containing files to be moved:\n";
        cin.get(temp[row]);

    }
    while(temp[row]!='\n')
    {
        row++;
        cin.get(temp[row]);
        count++;
    }
    row=0; //reset row
    targSize=count;
    char target_dir[targSize];
    while(count>=0)
    {
        target_dir[row]=temp[row];
        count--;
        row++;
    }

    cout << target_dir << endl << targSize << endl;

    return 0;
}
```And I get this output:

/home/****/*****/
&#65533;&#65533;&#65533;&&#65533;`&#65533;&#65533;&#65533;&#65533;b&#36343;F&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;
21

where the:
 /home/******/*******/
part is correct, and ****'s can be replaced with anything. The size of the array is correctly output (I guess).

Why this:
&#65533;&#65533;&#65533;&&#65533;`&#65533;&#65533;&#65533;&#65533;b&#36343;F&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;

It varies in size, and doesn't seem to relate the size of the input.


Basically I'm going to use this code as a function to reach directories, so right now it doesn't really "do" anything. But I also need to know before I get too far if I can pass char arrays into system().

---

### Post by jero3n on 2009-07-22
> 
Why this:
&#65533;&#65533;&#65533;&&#65533;`&#65533;&#65533;&#65533;&#65533;b&#36343;F&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;

You get this because target_dir is not terminated with '\0' character in the proper place. I think 

while(temp[row]!='\n') is wrong

However I can not understand the rest of the program. What are you trying to do?

---

### Post by MadCow108 on 2009-07-22
why not use strings?
char's just make unecessary problems.
```

string tmp;
cout << "Enter directory containing files to be moved:" << endl;
    getline(cin,tmp,'\n');
    while(tmp[0]!='/') //make certain path starts in proper place
    {
        cin.ignore(9999,'\n');
        cout << "\n\nUnknown path.\nEnter directory containing files to be moved:\n";
        getline(cin,tmp,'\n');

    }
    cout << tmp << endl << tmp.length() << endl;

```

I also have no idea what this code is trying to archive.
It seems you want to find the length of the string and copy it into a smaller array.
just do that (if chars are really necessary):
```

cout << "Enter directory containing files to be moved:" << endl;
    cin.getline(temp,100,'\n');

    while(temp[0]!='/') //make certain path starts in proper place
    {
        cin.ignore(9999,'\n');
        cout << "\n\nUnknown path.\nEnter directory containing files to be moved:\n";
        cin.getline(temp,100,'\n');

    }
    int targSize = strlen(temp);
    char target_dir[targSize];
    strncpy(target_dir,temp,targSize+1);

    cout << target_dir << endl << targSize << endl;

```

also in c++ its #include <cstdlib> if you really need c libraries.

---

### Post by pepperphd on 2009-07-22
> **MadCow108 said:**
> why not use strings?
char's just make unecessary problems.
```

string tmp;
cin >> tmp;

```also in c++ its #include <cstdlib> if you really need c libraries.

 I believe he's not using that form of cin because it will terminate on a whitespace.

---

### Post by MadCow108 on 2009-07-22
yes of course
i changed it to getline which terminates on \n.
I hope thats what is wanted.

note the two different versions: getline takes a string
[http://www.cplusplus.com/reference/string/getline/](http://www.cplusplus.com/reference/string/getline/)
cin.getline takes a char array
[http://www.cplusplus.com/reference/iostream/istream/getline/](http://www.cplusplus.com/reference/iostream/istream/getline/)

---

### Post by MindSz on 2009-07-22
As jero3n pointed out, your string is not NULL terminated.

Just add this line right after the last while loop:

```

    target_dir[row] = '\0';
```

And it should work fine.

You still have many wasted resources in that program so try to catch redundances in your code (e.g. you could print out temp instead of target_dir)

Anyway, have fun coding! :)

---

### Post by blackmonjd on 2009-07-22
Thanks for the replies. 
 
target_dir[row]='\0';
 
works.
 
I'm using char arrays because I've heard people having problems passing strings into system(), ie system(cd /some/string). Eventually I'm going to have the user enter the path to directory, and the program will move to said directory and perform it's operation.
 
Right now the program doesn't do anything other than accept input. I started righting a larger program when I realized I didn't remember how to do most of what I was trying to do, so I just started a smaller program, which I'll just implement as a function in the larger program. But I'm moving temp into a properly sized array to avoid extraneous output, which I got anyways.

---

### Post by MadCow108 on 2009-07-22
c++ strings have the method c_str() which returns a C style char array.
This you can pass to any function which requires char arrays:
```

string str="cd /some/str";
printf("%s\n",str.c_str());
if (!system (str.c_str())) cout << "success" << endl;

```

---

