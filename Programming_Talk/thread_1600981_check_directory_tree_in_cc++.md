---
title: "check directory tree in c/c++"
date: 2010-10-19
forum: Programming Talk
---

### Post by abraxas334 on 2010-10-19
I need to check if a directory tree exists.
Essentially i want to check top directory if it doesn't exist create it. Then check if first subdirectory exists if it doesn't create it etc.
I wrote a little test program to try this out. I can verify the existance of the top directory as well as creating it. But if i want to check the subdirectory I fail.  I use chdir() how can i get a right answer for my subdirectory.
I created a directory called test, which has a subdirectory subdir using mkdir on the commandline. Here my program trying to check if subdir actually exists:

[PHP]
#include <iostream>
#include <string>

using namespace std;


int main()
{

        string n = "test";
        if(chdir(n.c_str())==0)
        {
                cout<<"This directory exists "<<endl;
        }
        else
        {
                cout<<"This does not exist"<<endl;
        }
        string n1 = "test/subdir";
        if(chdir(n1.c_str())==0)
        {
                cout<<"Sub dir also exisits "<<endl;
        }
        else
        {
                cout<<"Pustekuchen"<<endl;
        }

}

[/PHP]

---

### Post by Arndt on 2010-10-19
> **abraxas334 said:**
> I need to check if a directory tree exists.
Essentially i want to check top directory if it doesn't exist create it. Then check if first subdirectory exists if it doesn't create it etc.
I wrote a little test program to try this out. I can verify the existance of the top directory as well as creating it. But if i want to check the subdirectory I fail.  I use chdir() how can i get a right answer for my subdirectory.
I created a directory called test, which has a subdirectory subdir using mkdir on the commandline. Here my program trying to check if subdir actually exists:

[PHP]
#include <iostream>
#include <string>

using namespace std;


int main()
{

        string n = "test";
        if(chdir(n.c_str())==0)
        {
                cout<<"This directory exists "<<endl;
        }
        else
        {
                cout<<"This does not exist"<<endl;
        }
        string n1 = "test/subdir";
        if(chdir(n1.c_str())==0)
        {
                cout<<"Sub dir also exisits "<<endl;
        }
        else
        {
                cout<<"Pustekuchen"<<endl;
        }

}

[/PHP]

When you have chdir'ed to "test", you should chdir to "subdir" next, not to "test/subdir", since you are already in "test".

---

### Post by dwhitney67 on 2010-10-19
Use mkdir(), maybe even use stat(), but the latter is not really necessary.

```

man 3 mkdir
man 3 stat

```

---

### Post by abraxas334 on 2010-10-19
thanks, I knew it was something silly like that. And indeed mkdir obviously also checks if it is there, and i am obviously using it to create the directory...coding past 10pm = my brain not functioning :P

---

