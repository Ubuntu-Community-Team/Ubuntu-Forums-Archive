---
title: "Structs and defining within struct."
date: 2010-02-10
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-10
Here's a quick question with hopefully a yes or no answer. I've looked through various tutorials and I haven't found an answer to this question. 

struct charStats 
{
    string name;
    int lvl;    //Level of character
    int end;    //Endurance of character
    int str;    //Strength of character
    int exp;    //Experience of character
    int hp;        //Health of character
    **int atk = str * lvl;**    //Attack of character
    **int def = end * lvl;**  //Defence of character
} player, npc , enemy;

I am aware that the rest is okay, but the bit in bold is what I'm looking at. If I summoned

player.charStat 

then would its atk be = to the str * lvl of that player?

---

### Post by Zugzwang on 2010-02-10
> **Ravenshade said:**
> 
I am aware that the rest is okay, but the bit in bold is what I'm looking at. If I summoned

player.charStat 

then would its atk be = to the str * lvl of that player?

What do you mean by "summoning"? Furthermore "placer.charStats" doesn't make sense - The compiler already knows the type of "player", so why adding it again?

Anyway, the code you posted is not valid C or C++. Familiarize yourself with the concept of getters and setters if you are using C++. Then you can encode your computation of "atk" into the respective getter.

---

### Post by Ravenshade on 2010-02-10
Valid or not, it compiles ^_^

```

struct charStats 
{
    string name;
    int lvl;    //Level of character
    int end;    //Endurance of character
    int str;    //Strength of character
    int exp;    //Experience of character
    int hp;        //Health of character
    **int atk = str * lvl;**    //Attack of character
    **int def = end * lvl;**  //Defence of character
} player, npc , enemy;

void printStat (charStats stats);

int main()
{

player.lvl = 2;
player.str = 20;


}

void  printStat (charStats stats)
{

cout  << player.atk;

}

```

This code would in theory output 40, unless the str*level didn't work. In which case I'll probably define a function to do the same thing. (if anyone has a better idea?)

---

### Post by Zugzwang on 2010-02-10
> **Ravenshade said:**
> Valid or not, it compiles ^_^


How?

I've copied and pasted your code and added missing #include lines. The result is:

[PHP]
#include <iostream>

using namespace std;

struct charStats 
{
    string name;
    int lvl;    //Level of character
    int end;    //Endurance of character
    int str;    //Strength of character
    int exp;    //Experience of character
    int hp;        //Health of character
    int atk = str * lvl;    //Attack of character
    int def = end * lvl;  //Defence of character
} player, npc , enemy;

void printStat (charStats stats);

int main()
{

player.lvl = 2;
player.str = 20;


}

void  printStat (charStats stats)
{

cout  << player.atk;

}
[/PHP]

Running "g++ test.cpp" gives:

```

test.cpp:13: error: 'charStats::str' cannot appear in a constant-expression
test.cpp:13: error: 'charStats::lvl' cannot appear in a constant-expression
test.cpp:13: error: ISO C++ forbids initialization of member 'atk'
test.cpp:13: error: making 'atk' static
test.cpp:13: error: ISO C++ forbids in-class initialization of non-const static member 'atk'
test.cpp:14: error: 'charStats::end' cannot appear in a constant-expression
test.cpp:14: error: 'charStats::lvl' cannot appear in a constant-expression
test.cpp:14: error: ISO C++ forbids initialization of member 'def'
test.cpp:14: error: making 'def' static
test.cpp:14: error: ISO C++ forbids in-class initialization of non-const static member 'def'

```

Which compiler are you using?

---

### Post by Ravenshade on 2010-02-10
g++ and you're missing a few more includes ^_^ like string and sstream for a start. 

That and I haven't included atk = str*lvl and def = end*lvl at the moment. I'm not sure why your compiler isn't allowing lvl or str while it allows end.

edit

The question was whether the two lines in bold would work. It does seem that they won't.

---

### Post by Zugzwang on 2010-02-10
> **Ravenshade said:**
> That and I haven't included atk = str*lvl and def = end*lvl at the moment.


Then please make this clear the next time. You posted some code and said that it compiles. It's nowhere stated in your posts that you actually left out some part.

In C/C++, you must wrap code into functions (object instantiations are OK, though). Thus, your code cannot work. As already said, look into "getters" and "setters" for C++. They do what you want!

---

### Post by Ravenshade on 2010-02-10
You would have thought that it would have been in the same section of the tutorial >_< no matter, thanks for the information.

edit

Actually, it seems more like classes might be preferred here as I can't find anything on struct setters and getters.

---

### Post by Zugzwang on 2010-02-10
> **Ravenshade said:**
> 
Actually, it seems more like classes might be preferred here as I can't find anything on struct setters and getters.

Actually, struct and classes are the same (this information can be found in every good C++ book), except that for structs, you might want to add the "typedef" keyword and elements in structs default to public accessibility, whereas in classes, the default accessibility context is private.

---

### Post by Ravenshade on 2010-02-10
If I use classes instead, I can define a function within a class where as with a struct I cannot do the same. Therefore I should be able to achieve what I want to do...

```

#include<iostream>
using namespace std;

class charStats 
{
    string name;
    int lvl;    //Level of character
    int end;    //Endurance of character
    int str;    //Strength of character
    int exp;    //Experience of character
    int hp;        //Health of character
    
    public:
       void statSetup (int, int, int, int, int);
       int  attackCalc() 
       {
           return (str * lvl);
       }
       int defenceCalc()
       {
           return (def * lvl);
       }
} player, npc , enemy;

void charStats::calcSetup (int a, int b, int c, int d, int e) 
{
      lvl = a;
      end = b;
      str = c;
      exp = d;
      hp = e;

}



int main()
{

player.calcSetup = ( 2, 10, 20, 0, 100);
cout << attackCalc();


}






```

I'm assuming if I declare them as functions without doing getting and setting... (which I probably have without realising) that the above code should work with a few extra files included.

---

### Post by johnl on 2010-02-10
> **Ravenshade said:**
> If I use classes instead, I can define a function within a class where as with a struct I cannot do the same. 

In C++, there is only one difference between a class and a struct, and that is the default member visibility.  For classes, it is private.  For structs, it is public.

So the following -- again, in C++ -- are equivalent:

```

class MyClass {
  /* default visibility is private */
    int x;
    int y;
  public:
    int getSum() { return x + y; }
};

struct MyStruct {
  /* default visibility is public */
    int getSum() { return x + y; }
  private:
    int x;
    int y;
};

```

This is not true in C, of course, since C 1) doesn't include classes, and 2) doesn't allow member functions in structures.

---

### Post by Ravenshade on 2010-02-10
Not that I'm saying your wrong, but the tutorials by Juan Soulie suggested that functions couldn't be used within structs. If it is possible to use functions in structs as well then there is no advantage to using one or the other, more of where you want to put the code.

---

### Post by dwhitney67 on 2010-02-10
> **Ravenshade said:**
> Not that I'm saying your wrong, but the tutorials by Juan Soulie suggested that functions couldn't be used within structs.

Well, he's wrong... or, he was referring to the C language.

> **Ravenshade said:**
> 
If it is possible to use functions in structs as well then there is no advantage to using one or the other, more of where you want to put the code.
By convention, the class-type is used, because by default it does privatize everything, except for what you explicitly declare as public (or protected, in the case of inheritance).

However, as indicated in previous posts, a struct and a class are practically identical, and each supports the similar features.

P.S.  One does not need to typedef the name of a struct in C++; the compiler interprets a struct and a class the same.

---

### Post by MadCow108 on 2010-02-10
if you put a function in a struct, it is a class with default access public.
this code is equivalent:
```

struct bla {
  void dostuff(void);
};
// is the same as:
class bla {
  public:
  void dostuff(void);
};

```

this is a feature of c++, you can't do it in C (directly at least, you could over use of function pointers).

because default is public, struct syntax is often used for function objects (=less typing overhead), but it doesn't really matter what you use.

---

### Post by Ravenshade on 2010-02-10
>_> can't seem to escape from those pointers... (even though I have nothing to use them for yet) 

thanks for the information whitney and madcow.

---

### Post by Ravenshade on 2010-02-10
Okay, I've got this class set up but I don't think it's going to work on run time, but I'm not certain why. 

where I state "return atk = (str * lvl)"

I want it to make the atk variable for that particular character change. £100 bets that it won't return the value where I want it to. Can I have a line of code please? (Or is this where I'm gonna need pointers?)

```

class charStats 
{
        string name;
        int lvl;    //Level of character
        int end;    //Endurance of character
        int str;    //Strength of character
        int exp;    //Experience of character
        int hp;        //Health of character
    int atk;    //The attack of character
    int def;    //The defence of character
    
    public:
        void statSetup (int, int, int, int, int, string, int, int);
        int  attackCalc() 
        {
            return atk = (str * lvl);
        }
        int defenceCalc()
        {
            return def = (end * lvl);
               }
        int hpCalc()
        {
            return hp += (end / 4);
        }
} player, npc , enemy;

void charStats::calcSetup (int a, int b, int c, int d, int e, string f, int g, int i) 
{
    lvl = a;
          end = b;
          str = c;
          exp = d;
          hp = e;
    name = f;
    atk = g;
    def = h
}


```

---

### Post by nvteighen on 2010-02-10
> **Ravenshade said:**
> Okay, I've got this class set up but I don't think it's going to work on run time, but I'm not certain why. 

where I state "return atk = (str * lvl)"

I want it to make the atk variable for that particular character change. £100 bets that it won't return the value where I want it to. Can I have a line of code please? (Or is this where I'm gonna need pointers?)

...


Ugh...

Let's see. You better don't do that **class Something { ... } instance;** thing... OOP makes global variables redundant.

You define your classes outside all functions (at "file level", as IIRC g++ calls it), but then that class becomes like a type and you can do **Something mySomething;** inside a function in order to instantiate it.

Now, about setting atk... You don't need the return. Inside a class definition, the defined attributes are visible for you to manipulate, unless you do the stupid thing to use a name of one of them in the method's parameters list or declare a local variable like that. So, if you have declared an attribute **int atk**, you just do atk = something in order to set it. Exactly as you did in the calcSetup method.

Another thing is that defining the methods inside the class definition or by just declaring the method's signature and then defining using the classname::methodname notation at "file level" is just a matter of style... What you better don't do is to mix both styles, so you could place calcSetup inside the class definition... or place everything outside of it. Nothing of this affects what I said above attributes above.

Now, the usual thing you do is to create a constructor method. The constructor method is always implicitly executed at the creation of a class's instance (*instantiation*). There's also a destructor method which is called at the object's destruction, but that's useless for you right now. Anyway, please take a read at [http://cplusplus.com/doc/tutorial/classes/](http://cplusplus.com/doc/tutorial/classes/)

---

### Post by Ravenshade on 2010-02-10
I'm reading the tutorials by Juan Soulie except...they return numerous errors once I start introducing constructors, on the other hand I think I understand the reasoning behind them. 

Thanks for your help. My errors are listed on another topic, but when I include constructors or change things, everything goes awyre

---

