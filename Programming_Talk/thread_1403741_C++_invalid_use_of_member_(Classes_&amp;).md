---
title: "C++ invalid use of member (Classes &amp;)"
date: 2010-02-10
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-10
```

In function void game()
main.cpp:190: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
main.cpp:190: error: invalid use of member (did you forget the ‘&’ ?)
main.cpp:265: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
main.cpp:265: error: invalid use of member (did you forget the ‘&’ ?)


```Here's the code that is on those lines...

```

player.statSetup = { 2, 10, 20, 0, 100, "player" };
enemy.statSetup = { 1, 5, 15, 0, 100, "Dark Elf" }; 
```I have a feeling its to do with me trying to put information into strings

I'm doing something that's not covered in any of the tutorials I've visited, putting text into a string while the string is inside a class... I thought it'd be simple, I've tried no speech marks, apostrophes and speech marks. I get an error either which way. 

On the other hand & is indicating pointing errors...

---

### Post by dwhitney67 on 2010-02-10
You need to implement a constructor for your class.  In C++, you cannot initialize a class as you would a struct in C.

For example:
```

#include <string>

class Foo
{
public:
   // declare constructor
   //
   Foo(const std::string& str);

   // set/get accessor methods
   //
   std::string getStr() const { return myStr; }

   void setStr(const std::string& str) { myStr = str; }

private:
   std::string myStr;
};

Foo::Foo(const std::string& str)
   : myStr(str)
{
}

int main()
{
   Foo f("wood");         // ok

   std::string s = "another";

   Foo f2(s);             // ok

   Foo f3 = "wrong";      // not ok
   Foo f4 = { "wrong" };  // also not ok
}

```

---

### Post by Ravenshade on 2010-02-10
Getters and Setters I assume? Didn't realize the problem was that, I thought I'd screwed up the syntax somewhere.

Oh one slight issue, 

I have integers in that class as well... (I'll look through my code but i think I have another question)...

Here's my class so far (without any alterations from dwhitney)

```

class charStats 
{    
    public:
        
        //constructing the class
        
        
        string name;
            int lvl;    //Level of character
            int end;    //Endurance of character
            int str;    //Strength of character
            int exp;    //Experience of character
            int hp;        //Health of character
        int atk;    //The attack of character
        int def;    //The defence of character
    
        //Declare constructor
    
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
} player, npc, npc1 , enemy;

void charStats::statSetup (int a, int b, int c, int d, int e, string f, int g, int h) 
{
    lvl = a;
          end = b;
          str = c;
          exp = d;
          hp = e;
    name = f;
    atk = g;
    def = h;
}
```

---

### Post by dwhitney67 on 2010-02-10
Ravenwood, here's "your" handiwork with some modifications:

Note:
1.  I renamed the class and variables; try to be specific when creating names.  Nothing sucks more when reading a variable and not having a clue as to what it represents.

2.  I moved the class data to the private section.

3.  I separated the code into separate header and implementation files.

4.  I moved the declaration of your CharacterStats objects to a "main" module.  There is absolutely no reason for your application to have global variables.


CharacterStats.h
```

#ifndef CHARACTER_STATS_H
#define CHARACTER_STATS_H

#include <string>

class CharacterStats
{    
public:
   CharacterStats(const std::string& name,
                  int level,
                  int endurance,
                  int strength,
                  int experience,
                  int health,
                  int attack,
                  int defence);

   int attackCalc();
   int defenceCalc();
   int healthCalc();

private:
   std::string myName;
   int         myLevel;         //Level of character
   int         myEndurance;     //Endurance of character
   int         myStrength;      //Strength of character
   int         myExperience;    //Experience of character
   int         myHealth;        //Health of character
   int         myAttack;        //The attack of character
   int         myDefence;       //The defence of character
};

```

CharacterStats.cpp
```

CharacterStats::CharacterStats(const std::string& name,
                               int level,
                               int endurance,
                               int strength,
                               int experience,
                               int health,
                               int attack,
                               int defence)
   : myName(name),
     myLevel(level),
     myEndurance(endurance),
     myStrength(strength),
     myExperience(experience),
     myHealth(health),
     myAttack(attack),
     myDefence(defence)
{
}

int
CharacterStats::attackCalc()
{
   return myAttack = myStrength * myLevel;
}

int
CharacterStats::defenceCalc()
{
   return myDefence = myEndurance * myLevel;
}

int
CharacterStats::healthCalc()
{
   return myHealth += (myEndurance / 4);
}

```

Main.cpp:
```

#include "CharacterStats.h"

int main(void)
{
   CharacterStats player("Salt", 1, 2, 3, 4, 5, 6, 7);
   CharacterStats enemy("Pepper", 7, 6, 5, 4, 3, 2, 1);

   ...

   if (player.attackCalc() > enemy.defenceCalc())
   {
      // enemy is dead!
   }
}

```

Consider dropping this quest to develop a game until you have a better understanding of C++.  Whether you like it or not, you have to read a god-damn book.  Grow up!

---

### Post by Ravenshade on 2010-02-11
Thanks for the help -_-; I'll be putting half of that data back where it was and renaming a number of variables back to what they were. I know what they were even if you don't. I had stripped numerous comments from the code for readability. 

I'll also be removing stuff from that header file. Unfortunately I don't think there's enough data for a header file just yet and like I've been told it'd be best to stick everything in the same file to start off with. 

and above all, all of those "changes" you made, I don't care how perfect you think that code is, it's being shoved back. 

And I'm afraid I don't understand your code (most likely due to my inexperience), thus I'm not using it. 

Thanks again for the hard work however. 

I'll mark the thread as solved and instead find my own way out of the problem.

---

### Post by CptPicard on 2010-02-11
Wow. Dwhitney67 was being a saint and you just choose not to like what he did, because you don't understand it, and don't want to.

Way to learn.

---

### Post by Ravenshade on 2010-02-12
That's not the point. The point is, I don't understand the code so why use something you don't understand and thus can't implement. 

My program can't use the information above as it's written, I got a whole stream of errors. Since I' not sure what's wrong as I don't understand it I can't therefore use it. 

I asked why wasn't the string working and got a whole rewrite of my code. While I appreciate dwhitney's work and it's given me a different perspective on C++ classes, I just don't understand how it functions. Thereby returning to my original statement.

---

### Post by Zugzwang on 2010-02-12
> **Ravenshade said:**
> I asked why wasn't the string working and got a whole rewrite of my code. While I appreciate dwhitney's work and it's given me a different perspective on C++ classes, I just don't understand how it functions. Thereby returning to my original statement.

The point here is: dwhitney's solution is so basic that you *should* understand it before trying any project in C++ of reasonable size. Seriously, read a book, like for example Bruce Eckel's "Thinking in C++", which you can download as pdf for free. This will *really* help you and also save you development time and frustration in the long run (except if you drop your project anyway, of course).

---

### Post by Ravenshade on 2010-02-12
This thread has been marked solved. 

I can't afford the damn books .... part of the reason why I have linux (even if it does run better). 

The END. Yeesh.

---

### Post by Zugzwang on 2010-02-12
> **Ravenshade said:**
> 
I can't afford the damn books .... part of the reason why I have linux (even if it does run better). 


So download that book I mentioned for *free* (and even more important, that's legal in this case as the author himself put it on the web).

---

### Post by Ravenshade on 2010-02-12
Finally truly solved. I'd duplicated a variable and I have undone the error in my programming. Also means that all of dwhitney's work is no longer needed. Sorry.

---

### Post by bapoumba on 2010-02-12
Closing the thread. Thanks all :)

---

