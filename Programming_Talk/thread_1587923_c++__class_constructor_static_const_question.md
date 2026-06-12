---
title: "c++  class constructor/ static const question"
date: 2010-10-04
forum: Programming Talk
---

### Post by abraxas334 on 2010-10-04
I have a question about class structures in c++.

i have a manager class cManager. Within this class a private variable is an instance of an other class cProtein.

roughly looks like this:

[PHP]
#include "cProtein.h"



class cManager { 
public:
    //this is all that needs to be public
    cManager();
    cManager(const cMonteCarloManager& orig);
    virtual ~cManager();
    void setup_run(string, string);
    
private:
    //functions
    readConfig assignConfigValues(string);

    //variables
    cProtein cP;
    cProtein tP;
    int begN;
    int endN;

};


[/PHP]
cProtein cP calls the default constructor correct? At the moment cP has a const static  int length variable, which I would like to be able to change through my config file. I guess it is not valid to write sokething like:
[PHP]
     .
     .
    //variables
    cProtein tP(int length);
[/PHP]

if length is only defined after the config file has beed read this is not legal i guess. My question is how do i make the variable length generally available to cProtein and cManager without having a const static int like i do at the moment.

This is cProtein.h/cpp
[PHP]
public:
class cProtein{
public:
    cProtein();
    cProtein(int);
    virtual ~cProtein();
    
    //functions
 

    //variables


private:
    //functions
   

    //variables
    static const int spaceSize = 256;
    static const int length = 48;
    int *** space;
};

cProtein::cProtein() {

    int b1 = -1;
    int b2 = -1;
    srand((unsigned int) time(0));

    std::cout << "Allocating space...\n";
    space = new int**[spaceSize];
    std::cout << "great!\n";
    for (int i = 0; i < spaceSize; i++)
    {
        space[i] = new int*[spaceSize];
        for (int j = 0; j < spaceSize; j++)
        {
            space[i][j] = new int[spaceSize];
        }
    }
    std::cout << "Allocated space!\n";
    resetSpace() //this function needs a valid length (int)
   
}

[/PHP]

Just to summarize: What I want to be able to do is read my config  file which gives me a value for length. And then I want to assign that length value to my cProtein object.
So my solution for this was that I'd have cProtein cP declared in the class but let it call the empty construcotr cProtein::cProtein(){}
and then sometime in my setup_run fuction after reading the config file do something like
[PHP]
    int length = 48;
    cProtein test(length);
    cP = test;
    std::cout<< cP.length<<std::endl;
[/PHP]
This does not actually assing the length to the now public length variable in my cProtein class.
In the new constructor I write something like this:
[PHP]
cProtein::cProtein(int len)
{
    ....//some other stuff assinging space etc
    len = this->length;
    len = length;
    //I have tried both ways but cP.length never returns 48. 

}
[/PHP]

I am lost with this. Any ideas where I am going wrong? I guess pointers would be more appropriate here too?

---

### Post by Sub101 on 2010-10-04
If you define cProtein in the header it does not create it.

You would need to create the object in the cManager class.

---

### Post by GeneralZod on 2010-10-04
> **abraxas334 said:**
> 
cProtein cP calls the default constructor correct? 


Construction of an instance of cManager will construct the data members cP and tP via the cProtein default constructor.

> 
At the moment cP has a const static  int length variable, which I would like to be able to change through my config file.


You can't change a const static at runtime.  You could assign during the static initialisation phase of the program by reading the config file then, but this doesn't seem at all wise.

> 
 I guess it is not valid to write sokething like:
[PHP]
     .
     .
    //variables
    cProtein tP(int length);
[/PHP]


Afraid not :(

What you can do is use the member initialiser list to use the cProtein::cProtein(int length) constructor instead of the default one: something like 

[PHP]
cManager::cManager(int length)
     : cP(length),
       tP(length)
// other members
{
// other stuff
}
[/php]

for example, but I'm not sure if this is what you want given your focus on having some kind of static int in cProtein.

---

### Post by abraxas334 on 2010-10-04
the idea is to get rid of the static in cProtein, so i dont need to recompile everytime I want to change the length!

---

### Post by Sub101 on 2010-10-04
> **abraxas334 said:**
> the idea is to get rid of the static in cProtein, so i dont need to recompile everytime I want to change the length!

Simple example:


```

//cManager header

cProtein* tP;

```

```

//cManager class

tP = new cProtein(length, length);

```

---

### Post by abraxas334 on 2010-10-04
Ah specifiying the constructor worked like magic :) Thanks alot!

---

