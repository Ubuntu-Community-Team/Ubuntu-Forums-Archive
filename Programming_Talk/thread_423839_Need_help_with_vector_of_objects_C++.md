---
title: "Need help with vector of objects C++"
date: 2007-04-26
forum: Programming Talk
---

### Post by Phobia on 2007-04-26
I have been work on this all night it is my final program for my introduction to c++ and it is only suppose to be as as hard as you want it to be. It only has to have an vector of objects and one function that uses an iterator. My code compiles but it  has an seg faults. I have been up all night finishing three other labs so sorry if i have bad grammar, my syntax error may be real simple but i don't have the full brain power to see what i did wrong with my code.



--Thanks in advance   

[```

#include <iostream>
#include <string>
#include <vector>
#include <iterator>

using namespace std;

class geterdone
{
public:

    geterdone( string g_name,string g_name2,string g_age )
    {
        name = g_name;
        name2 = g_name2;
        age = g_age;
    }

    geterdone()
    {
        string g_name = "Professor ";
        string g_name2 = "Fingers ";
        string g_age = "300";
    }

    string getname(string g_name,string g_name2)
    {
        cout<<"Enter your first and last name: "<<endl;

        istream_iterator<string> input(cin);

        g_name = *input;
        input++;
        g_name2 = *input;

        setname(g_name,g_name2);

        return g_name;
    }
    void setname(string g_name,string g_name2)
    {
        name = g_name;
        name2 = g_name2;

        return;
    }
    string getage(string g_age)
    {
        cout<<"Enter your age: "<<endl;
        cin>>g_age;

        setage(g_age);

        return g_age;
    }
    void setage(string g_age)
    {
        age = g_age;

        return;
    }
    void output()
    {
        ostream_iterator<string> outputs(cout);

        cout<<"Name: ";
        *outputs = name;
        cout<<" ";
        *outputs = name2;
        cout<<endl;
        cout<<"Age: "<<age<<endl;

    }
    ~geterdone()
    {

        cout<<"GITRDONE!"<<endl;

    }

private:
    string name,name2,age;

};






int main()
{
    string nameit,nameitagin,isage;
    char looper;

    cout<<"Do you wish to continue\"y or n\" :";
    cin>>looper;
    vector<geterdone> g_person;

    while (looper=='y')
    {


    vector<geterdone> g_person;
    
    for (int i=0 ;i<g_person.size()+1;i++)
        {
            g_person[i].getname(nameit,nameitagin);
            g_person[i].getage(isage);
            g_person[i].output();
        }



        cout<<"Agin?: y or n: ";
        cin>>looper;
    }




    return 0;

}

```[

---

### Post by amo-ej1 on 2007-04-26
Well, under linux you have a nifty little thing called gdb, aka the 'gnu debugger'. So when you compile your code you run it withing gdb by starting it as follows (note the -g or -ggdb which means we're compiling it with debugging signals enabled)

```

edb@rogue:/tmp$ emacs test.cpp
edb@rogue:/tmp$ g++ -ggdb test.cpp 
edb@rogue:/tmp$ gdb a.out

```

Then it will show you a welcome message and the gdb  prompt, here you can enter 'run' to start the program (and if you need parameters add them here too)

```

Starting program: /tmp/a.out 
Do you wish to continue"y or n" :y
Enter your first and last name: 
just testing

Program received signal SIGSEGV, Segmentation fault.
0xb7f04ff7 in std::string::assign () from /usr/lib/libstdc++.so.6

```

Next you see the application receives a segmentation fault and you are dumped with a gdb prompt. Here you can enter 'bt' or 'where' to show where you are in the callstack

```

(gdb) bt
#0  0xb7f04ff7 in std::string::assign () from /usr/lib/libstdc++.so.6
#1  0xb7f050e4 in std::string::operator= () from /usr/lib/libstdc++.so.6
#2  0x08048dba in geterdone::setname (this=0x0, g_name=@0xbfa74280, 
    g_name2=@0xbfa7427c) at test.cpp:42
#3  0x080494a9 in geterdone::getname (this=0x0, g_name=@0xbfa742dc, 
    g_name2=@0xbfa742d8) at test.cpp:36
#4  0x08048b86 in main () at test.cpp:108

```

So you see somewhere in main() (line 108 in test.cpp) getname is called, getname calles setname and the result occurs in the setname() function at line 42. Well basicly when thing go wrong they go wrong because of you and you should check the last place in the stacktrace which is under your control. The odds that you discovered a bug in libstdc++ is much lower than the chance YOU made a mistake ;-).

But look at the stacktrace, what looks odd ? Well getname and setname have a first parameter called 'this' and this is a pointer which points to 0x0 (a null pointer). And what happens at line 42 ? You try to assing a value to a member:

```

    void setname(string g_name,string g_name2)
    {
        name = g_name;

```

But the member belongs to an object which doesn't exist ! So C++ panics and you get a segfault.

So this means the object 'geterdone' you try do modify doesn't exist. So we go back and see where the object was gotten. And we end up here:

```

    vector<geterdone> g_person;
    
    for (int i=0 ;i<g_person.size()+1;i++)
        {
            g_person[i].getname(nameit,nameitagin);
            g_person[i].getage(isage);
            g_person[i].output();
        }

```

So first you create a vector. A vector without objects in them but a vector capable of containing 'geterdone' objects. Now in the for loop you iterate over all members+1. So if there are 0 objects in the vector, you will execute the for loop for i=0. So you go outside of the boundaries of your empty vector.

Now if you have and empty vector and you ask him an object it doesn't have, what will it give you ? Indeed nothing and you got a 'null' object.

So how would you fix your main ? 

a) correct the for loop to stay within the boundaries typical vector iteration is done like this:
```

vector<geterdone> vec;
 for(vector<geterdone>::iterator it = vec.begin(); it != vec.end(); vec++) {
   // it is now a pointer to a geterdone object 
   cout << *it << endl;
}

```

b) Create an object and insert it then in the vector afterwards.
```

geterdone myObj;
myObj.getname();
myObj.getage();
myObj.output();
vec.push_back(myObj)

```

hope this helps

---

### Post by ssodhi on 2007-04-26
Edit:
Nevermind, he beat me to it.

---

