---
title: "[c++] Is this the best way to do it? (Public versus Private variables)"
date: 2009-06-23
forum: Programming Talk
---

### Post by ash.rossy on 2009-06-23
Ok, I started c++ about 2 weeks ago, with little experience in programming beforehand.
I had never learnt anything Object orientated so c++ was my intro.

As an exercise I made a "simple" game (not going into GUI till I know Commandline backwards)
The player encounters a monster, battles it, moves on to the next monster.

Monster and player both inherit from class living_thing.

I've decided to rewrite this code to be more efficient and include more features (A plot, easy to add monsters)

Whilst defining my class living_thing, i noticed a flaw in my previous code, I had a setstats(health,mana,level,name) function, but if I needed to change any (private) variable such as those, I had created a seperate function, and yet another seperate function to print those stats.

I decided to try to create a function, where I could define what stats I want to set (and their value).

It was

```

setattr(attribute,int val)
{[INDENT]attribute = val;
[/INDENT]};

```That obviously failed (as I hadn't declared attribute);

I searched google for a while to find a way to do it, then just as I was writing a topic here, had a brainwave.

I just declared them public values, so I could set health as living_thing.health = 20 as an example.


Is it advised to have these as public variables? or should I move them to private and create a function to set/display those variables

UPDATE 1:

Solved that problem (left it up for people to read).

My next challenge: Thinking up what methods to include in living_thing.
Writing out the base for Player and Monster classes.

I have plans on posting this game when it's done!

---

### Post by blackxored on 2009-06-23
OOP->Encapsulation.

As a golder rule, mark *all* your variables private. Only except it in some cases when you'll use static and const fields. I haven't sticked to public with vars, only when API has forced it somehow, which is not a common case if you're using a OOP library. 

I hope that has answered your question. 

So, you should of course have accessor methods, and manipulate the object's state only through them.

---

### Post by ash.rossy on 2009-06-23
Ok, I get that public variables are bad practice (same as globals in non-oo programming?)

How do you propose I set an attribute without creating quite a lot of methods? I currently have 22 variables, which would be 44 methods (one for input, one for output) That, to me seems like a lot more bad practice.

---

### Post by asdfhjkla on 2009-06-23
> **ash.rossy said:**
> I just declared them public values, so I could set health as living_thing.health = 20 as an example.


Is it advised to have these as public variables? or should I move them to private and create a function to set/display those variables.

I have plans on posting this game when it's done!

In my opinion, it's bad object-oriented practice. In this type of example it's not really a big deal, but as you expand on your idea it could cause problems.

Encapsulation is the OOP concept of hiding the way something works from certain objects. You provide an interface to other objects through *public* or *protected* methods (are those the correct C++ keywords? I'm used to Java...) rather than allow those other objects to directly change attributes.etc

For example say at the moment each living_thing has an attribute named *health*, and you have two instances of living_thing - *human* and *monster*. When human attacks monster for 20 damage, you could either subtract the damage amount from health via monster.health -= 20, or you could use a method named attacked which takes the damage as a parameter: monster.attacked(20)

Both of these will achieve the same thing - subtracting 20 damage from the health of *monster*.

In future you decide that instances of living_thing are allowed to use armour. You give living_thing an attribute named *armour*. Now, if we do what you do now - you have to go back and change your code. You may have to change monster.health -= 20 to something like

[PHP]if (monster.armour < 0) {
    monster.health -= 20
} else ...
[/PHP]

This could be a bit of a nuisance to go back and change everything which causes a monster to lose health. However, if we encapsulated everything - you could change the logic inside the *attacked* method and not have to bother making changes to any other objects.


Reading that back, I realised I rambled quite a lot. I hope it makes sense.

---

### Post by TheBuzzSaw on 2009-06-23
When creating objects, you need to think about the overall goals of the object. Don't get all hung up on one variable inside an object until you have decided on the master design of the object.

If all you want is a logical collection of variables (for passing to certain functions, for example), use a **struct** and keep everything public.

```
struct coordinates
{
    int x;
    int y;
    int z;
};
```

In making a class, your goal should have something to do with creating a **new data type**. Don't think of an object in terms of its internal parts; think of it as a whole new creation. Design its **behavior** *before* you implement its variables.

You have the right idea so far with Player and Monster both inheriting from a parent class LivingThing. I obviously don't know how the rest of your program works, but let me take you through a quick example of how I'd approach class design. Let's think about a few things that LivingThings need in terms of a programming interface.

```
class LivingThing
{
    public:
        void setHealth(int inHealth);
        int getHealth();
        void die();
        void attack(LivingThing inThing);
};
```

You're probably asking yourself: Why have setHealth and getHealth functions when I could just make a public health variable and save myself the trouble??? Well, this is all about leaving your options open. Imagine later you design a creature whose health has unique properties. For instance, what if a ghost has magical health that is based on the player's health? Well, with this design, you can have Ghost extend LivingThing and *redefine* how getHealth() operates. You could also redefine setHealth(int) to also alter the main player's health!

This is kind of goofy example, but I'm just making a point. *After* you have defined the rules for how the rest of the program is allowed to interact with the object, *then* you go back in and make all the complicated inner workings private. You want stuff private that the outer program doesn't "care" about. For instance, when you drive your car, do you care how the steering wheel makes your tires turn? Probably not. You just want those tires to turn when you turn that wheel, right? Same goes here. When you call myLivingThing.die(), you don't care *how* it gets done; you just want that thing to die, right?

---

### Post by ash.rossy on 2009-06-23
Thanks, having things explained in clearer terms makes it a lot easier for me!
I often wondered why the examples never had the complete method inside the class...

So my next question:

I want a pretty easy way to add new "monsters" to this game. It used to be:

```

    monster slug,snail,snaketroll,wormdragon,zombie,hlbt,cow,vampirebat,flyingcat;
    void initmonsters() // Could do with finding a way to make this into an easy database. Write a program to create new monsters in spare time?
    {
        slug.initstats(1,50,0,3,2,"Slug","An evil, smelly, slug");
        snail.initstats(2,60,10,3,4,"Snail","A garden variety snail. Cute.");
        snaketroll.initstats(3,65,35,5,4,"Snake Troll","A Troll with scaley skin");
        wormdragon.initstats(4,80,45,6,7,"Worm Dragon","A Segmented Dragon");
        zombie.initstats(5,100,0,7,5,"Zombie","I shall call it, Phil.");
        hlbt.initstats(6,85,45,9,6,"Hairy Legged Bat Troll","A Troll which can fly.");
        cow.initstats(7,3,0,1,1,"Cow","Moo");
        vampirebat.initstats(8,125,50,15,10,"Vampire Bat","A bat that feasts on rotting flesh");
        flyingcat.initstats(9,200,30,20,20,"Flying cat","A cat with buttered toast attached to it's back");
    };

```

---

### Post by TheBuzzSaw on 2009-06-23
> **ash.rossy said:**
> Thanks, having things explained in clearer terms makes it a lot easier for me!
I often wondered why the examples never had the complete method inside the class...

So my next question:

I want a pretty easy way to add new "monsters" to this game. It used to be:

```

    monster slug,snail,snaketroll,wormdragon,zombie,hlbt,cow,vampirebat,flyingcat;
    void initmonsters() // Could do with finding a way to make this into an easy database. Write a program to create new monsters in spare time?
    {
        slug.initstats(1,50,0,3,2,"Slug","An evil, smelly, slug");
        snail.initstats(2,60,10,3,4,"Snail","A garden variety snail. Cute.");
        snaketroll.initstats(3,65,35,5,4,"Snake Troll","A Troll with scaley skin");
        wormdragon.initstats(4,80,45,6,7,"Worm Dragon","A Segmented Dragon");
        zombie.initstats(5,100,0,7,5,"Zombie","I shall call it, Phil.");
        hlbt.initstats(6,85,45,9,6,"Hairy Legged Bat Troll","A Troll which can fly.");
        cow.initstats(7,3,0,1,1,"Cow","Moo");
        vampirebat.initstats(8,125,50,15,10,"Vampire Bat","A bat that feasts on rotting flesh");
        flyingcat.initstats(9,200,30,20,20,"Flying cat","A cat with buttered toast attached to it's back");
    };

```
My recommendation (if you plan on adding many more of these kinds of creatures) would be to read the data in from a file. That way, your generic "engine" could just load up a huge list of creatures that you can easily edit later on. You could store them into a dynamic array and use them at will.

---

### Post by ash.rossy on 2009-06-23
I thought that myself, just had hell with file I/O in a previous program, gotta confront my fear though :P

So problem solved!!

Thanks for the help!!

---

### Post by TheBuzzSaw on 2009-06-23
> **ash.rossy said:**
> I thought that myself, just had hell with file I/O in a previous program, gotta confront my fear though :P

So problem solved!!

Thanks for the help!!
Outta curiosity, what difficulties did you have in the past? I remember struggling with file I/O, but then it all clicked once I learned about <fstream>. It's actually not too bad.

If you wanna chat over a messenger, lemme know!

---

### Post by ash.rossy on 2009-06-23
A messenger would be good, I'll PM my MSN messenger email to you. 

Difficulties I had. Well, I guess it's time for another code sample :P

It was a guess the number game with ordered high scores (read from a scores.his file)

Here's the code in it's entirety

```

#include <iostream>
#include <fstream>
#include <string>
#include <stdlib.h>
#include <time.h>
using namespace std;

bool correct = false;
int times_tried;

void check(int random_num, int input)
{
    if (input > 100) // if input is incorrect (Ie: over highest number)
    {
        cout << "You entered an incorrect number \nTry again:\n";
    }
    else
    {
        if (random_num == input) //Checks if the answer is correct
        {
            times_tried++;
            cout << "Well done \n You did that in " << times_tried << " tries!\n\n";
            correct = true;        
        }
        else
        {
            if (random_num < input) //If the answer is too high
            {
                cout << "Too high. \nGuess again: \n";
                times_tried++;
            }
            else //If the answer is too low
            {
                cout << "Too low. \nGuess again: \n";
                times_tried++;
            }
        }
    }
}

void highscore_update() // This opens a scores.his plaintext file and stores the highscores in a new line
{
    string namingway;
    cout << "Please input your name:\n";
    cin >> namingway; // FF homage here <<
    cout << "\n\n\n";
    string line;
    ofstream high_scores;
    high_scores.open("scores.his",ios_base::app);
    high_scores << namingway << ":    " << times_tried << "\n";
    high_scores.close();
}

int stringtointarray(string str[], int times)
{
    int integ[11];
    int i;
    for (i=0;i<=10;i++)
    {
        integ[i] = atoi(str[i].c_str());
    }
    return integ[times];
}

void highscore_check() // Not currently working ???
{
    auto string tempstr[11];
    auto int tempint[11];
    int i;
    ifstream scores;
    scores.open("scores.his");
    for (i=0;i<=10;i++){getline(scores,tempstr[i],'\n');tempint[i] = stringtointarray(tempstr,i);}
    scores.close();
    if (tempint[9] < times_tried){highscore_update();}
    else {cout << "Sorry, you didn't get into the high scores...\n\n";}
}    
void highscore_view()
{
    string line;
    ifstream high_scores ("scores.his");
    while (! high_scores.eof())
    {
        getline (high_scores, line);
        cout << line << "\n";
    }
        
}

void bubble_sort(int array[],string strarray[]) // Good enough sorting algorithm for this exercise
{
     int i, j, flag = 1;    // set flag to 1 to begin initial pass
     int temp;             // holding variable
     string strtemp;
     int arrayLength = 11; 
     for(i = 1; (i <= arrayLength) && flag; i++)
     {
          flag = 0;
          for (j=0; j < (arrayLength -1); j++)
         {
               if (array[j+1] < array[j])      // descending order simply changes to >
              { 
                    temp = array[j];             // swap elements
                    array[j] = array[j+1];
                    array[j+1] = temp;
                    strtemp = strarray[j];
                    strarray[j] = strarray[j+1];
                    strarray[j+1] = strtemp;
                    flag = 1;               // indicates that a swap occurred.
               }
          }
     }
}

void outputnewscores(string outputstr[],int outputarr[])
{
    auto int i;
    ofstream scores;
    scores.open ("scores.his");
    for (i=0;i<10;i++)
    {
        scores << outputstr[i] << ": " << outputarr[i] << "\n";
    }
    scores.close();
}

int highscore_order()
{
    string stringscore[11];
    string names[11];
    int score[11];
    int i;
    ifstream scores;
    scores.open("Scores.his");
    for (i=0;i<11;i++)
    {
        getline(scores,names[i],':');
        getline(scores,stringscore[i],'\n');
        //cout << names[i] << "\n"; // Debug code
    }
    for (i=0;i<=10;i++){score[i] = stringtointarray(stringscore,i);}
    scores.close();
    bubble_sort(score,names);
    outputnewscores(names,score);
    return 0;
}

int main()
{
    string choice;
    int z;
    string opt;
    srand(time(0)); // Creates a random number seed based on the time
    int n = rand()%101; // As far as i'm aware, it never will be 101
    cout << "Guess the number between 1 and 100 \n";
    //cout << n << "\n"; // Test code
    while (correct != true)
    {
        cin >> z;
        check(n,z);
    }
    highscore_check();
    highscore_order();
    cout << "Would you like to see the highscores?(y/n)\n";
    cin >> opt;
    cout << "\n\n\n\n\n\n\n"; //Hacked up way of clearing the screen
    if (opt == "y"){highscore_view();}
    else{if (opt == "Y"){highscore_view();}}
    cout << "\n\n\n";
    return 0;
}


```


The main problems I had were getting it to read the data from scores.his properly. I then read about getline() and how to change the character it terminates from. That's in the for statement in highscore_order()

The funny thing was I wrote a nearly 90 line function to do the same thing (sigh)... It wasn't until I started using getline in that function, did i realise i made it defunct!

---

### Post by Mirge on 2009-06-23
Interesting thread... following this one.

---

### Post by ash.rossy on 2009-06-23
In what way interesting? To me this seems like a simple question with a simple answer...

---

### Post by Mirge on 2009-06-23
> **ash.rossy said:**
> In what way interesting? To me this seems like a simple question with a simple answer...

I like the OP's game :). And the OOP explanations. It's just nice to see a non "student grading" example.

---

### Post by ash.rossy on 2009-06-23
I'm the OP XD

Do you want me to post the old game? It's a horror in programming to be honest but has some pretty decent things (and it's playable!)

---

### Post by Mirge on 2009-06-23
> **ash.rossy said:**
> I'm the OP XD

Do you want me to post the old game? It's a horror in programming to be honest but has some pretty decent things (and it's playable!)

Yeah that'd be killer, I'd like to take a look at it. I might try writing a console game too just for kicks.

---

### Post by ash.rossy on 2009-06-23
Here it is:

Living_Things.h:

```

#include <iostream>

using namespace std;

class living_thing // Applies to anything in a battle
{
    protected:
    signed int current_health,max_health,current_mana,max_mana,level,id,attack,defence;
    string name;
    public:
        string statsout() // Returns all the stats initalised in living_thing
        {
            char chlevel[3],chhealth[8],chmana[8];
            sprintf(chlevel,"%d",level);
            sprintf(chhealth,"%d",current_health);
            sprintf(chmana,"%d",current_mana);
            string strlevel(chlevel),strhealth(chhealth),strmana(chmana),stats;
            stats = "Name: "+name+"\nLevel: "+strlevel+"\nHealth: "+strhealth+"\nMana: "+strmana+"\n";
            return stats;
        };
        void setstats(int i, int health, int mana,int atk,int def, string n) // Set the stats of a living_thing
        {
            id = i;
            current_health = health;
            max_health = health;
            current_mana = mana;
            max_mana = mana;
            attack = atk;
            defence = def;
            name = n;
            level = 1;
        }
        void modhealth(int points) // Used in battles + potions
        {
            current_health -= points;
            if (current_health < 0){current_health = 0;}
        };
        string printname()
        {
            return name;
        };
        int attackstat()
        {
            return attack;
        };
        int defencestat()
        {
            return defence;
        };
        int printcurrenthealth()
        {
            return current_health;
        }
};
class character: public living_thing // Characters are yourself and npc's
{
    private:
        signed int gold;
    public:
        void initstats(int i, int health, int mana, int atk, int def, string n)
        {
            setstats(i,health,mana,atk,def,n);
            gold = 0;
        };
        string printstats()
        {
            char chgold[15];
            string stats = statsout();
            sprintf(chgold,"%d",gold);
            string strgold(chgold);
            stats += "Gold: "+strgold+"\n";
            return stats;
        };
        void lvlup()
        {
            int randn;
            randn = rand() % 10 + defence;
            max_health += randn;
            current_health = max_health;
            randn = rand() % 5 + defence;
            max_mana += randn;
            current_mana += max_mana;
            randn = rand() % 11;
            attack += randn;
            randn = rand() % 9;
            defence += randn;
            level++;
            cout << "Level up!\nName: " << name << "\nHealth: " << max_health << "\nMana: " << max_mana << "\nAttack: " << attack << "\nDefence: " << defence << "\nLevel: " << level << "\n";        
        }
};    
class monster: public living_thing // Monsters are things you battle against
{
    private:
        string description;
    public:
        void initstats(int i,int health,int mana,int atk, int def, string n,string d)
        {
            setstats(i,health,mana,atk,def,n);
            description = d;
        };
        string printstats()
        {
            string stats = statsout();
            return stats += "Description: "+description+"\n";
        }
};

class monsters
{
    public:
    monster slug,snail,snaketroll,wormdragon,zombie,hlbt,cow,vampirebat,flyingcat;
    void initmonsters() // Could do with finding a way to make this into an easy database. Write a program to create new monsters in spare time?
    {
        slug.initstats(1,50,0,3,2,"Slug","An evil, smelly, slug");
        snail.initstats(2,60,10,3,4,"Snail","A garden variety snail. Cute.");
        snaketroll.initstats(3,65,35,5,4,"Snake Troll","A Troll with scaley skin");
        wormdragon.initstats(4,80,45,6,7,"Worm Dragon","A Segmented Dragon");
        zombie.initstats(5,100,0,7,5,"Zombie","I shall call it, Phil.");
        hlbt.initstats(6,85,45,9,6,"Hairy Legged Bat Troll","A Troll which can fly.");
        cow.initstats(7,3,0,1,1,"Cow","Moo");
        vampirebat.initstats(8,125,50,15,10,"Vampire Bat","A bat that feasts on rotting flesh");
        flyingcat.initstats(9,200,30,20,20,"Flying cat","A cat with buttered toast attached to it's back");
    };
};

```

Main.cpp
```

#include <iostream>
#include <stdlib.h>
#include <sys/time.h>
#include "LivingThings.h"

using namespace std;

void gameover()
{
    cout << "You lose!\n";
}

string clearscreen()
{
    return "\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n";
}
void battle(monster enemy,character player)
{
    struct timeval time;
    gettimeofday(&time,NULL);
    srand((time.tv_sec * 100) + (time.tv_usec / 100)); // Random seed
    int randnumatk,randnumdef,hitval,tempdef,runchance,posneg;
    char choice = '0';
    bool battle_finished = false;
    cout << "Entered battle with a " << enemy.printname() << "\n";
    while (battle_finished == false)
    {
        bool valid_choice = false;
        while (valid_choice == false) // You attack
        {
            cout << "\n(A)ttack,(D)efend or (R)un?\n";
            cin >> choice;
            tempdef = 0;
            if (choice == 'a' or choice == 'A') // Attack
            {

                posneg = rand() % 6; // This will generate a random number between 0 and 5, will solve the problem of always positive.
                randnumatk = rand() % (player.attackstat() * 2)+posneg;
                randnumdef = rand() % (enemy.defencestat() * 2);
                hitval = randnumatk - randnumdef;
                if (hitval < 0){hitval = 0;}
                enemy.modhealth(hitval);
                if (enemy.printcurrenthealth() == 0)
                {
                    cout << "You won!\n";
                    battle_finished = true;
                }
                else
                {
                    cout << "You attacked the " << enemy.printname() << " for " << hitval << " damage. Leaving it with " << enemy.printcurrenthealth() << " Health remaining\n";
                }
                valid_choice = true;
            }
            if (choice == 'd' or choice == 'D') // Defend
            {
                tempdef = rand() % (player.printcurrenthealth() / (player.defencestat()*4));
                cout << "your defence went up by " << tempdef << " Giving you " << (player.defencestat()+tempdef) << "\n";
                valid_choice = true;
            }
            if (choice == 'r' or choice == 'R') // Run
            {
                runchance = rand() % 7;
                if (runchance == 3){cout << "You ran away!\n";battle_finished = true;}
                else {cout << "You didn't escape!\n";}
                valid_choice = true;
            }
            if (valid_choice == false){cout << "Please input a, d or r.\n";} // Input error
        }
        if (battle_finished == false) // Enemy attacks
        {
            posneg = rand() % 6; // This will generate a random number between 0 and 5, will solve the problem of always positive.
            randnumatk = rand() % (enemy.attackstat() * 2)+posneg;
            randnumdef = rand() % (player.defencestat() * 2 + tempdef);
            hitval = randnumatk - randnumdef;
            if (hitval < 0){hitval = 0;}
            player.modhealth(hitval);
            if (player.printcurrenthealth() == 0)
            {
            gameover();
            battle_finished = true;
            valid_choice = true;
        }
            else
            {
            cout << "The " << enemy.printname() << " hit you for " << hitval << " damage. Leaving you with " << player.printcurrenthealth() << " Health remaining\n";
            }
        }
    }
}

int main()
{
    string playername;
    monsters enemies;
    character player;
    enemies.initmonsters();
    cout << "\n\n               Welcome to THE GAME!\nNow what is your name?\n";
    cin >> playername;
    player.initstats(1,100,10,4,2,playername);
    cout << clearscreen() << player.printstats() << "\n\n\n\n" << "One day, " << playername << " was walking among the fields.\n";
    battle(enemies.slug, player);
    cout << clearscreen();
    cout << "After defeating the mighty slug, you rested.\n\n\n\nYou came back to find it had gained a spikey shell!!\n";
    battle(enemies.snail,player);
    cout << clearscreen();
    player.lvlup();
    cout << "You leveled up. You had never felt this powerful. Until a hideous troll loomed infront of you.\n\nYou nearly wet yourself.\n";
    battle(enemies.snaketroll,player);
    cout << clearscreen();
    cout << "Thanks for playing the game!";
    return 0;
}

```

Have any problems let me know.
Feedback appreciated.

Want to contribute? Maybe we could get something going? (This is out to anyone)

Main.cpp + Living_Things.h should be in the same dir.

---

### Post by TheBuzzSaw on 2009-06-23
I won! :D

I'll just make a couple comments.

First, I noticed you included <iostream> but still used functions like sprintf. If you are going to include <iostream> learn to use all the various stream functions. There should be replacements for just about everything like printf, scanf, etc.

Second, in terms of the game, it was well made, but I saw no real incentive to ever defend. I know it's a simple game, but try to be innovative and come up with a reason to defend! Maybe certain monsters have certain phases where they cannot take damage...? :)

---

### Post by ash.rossy on 2009-06-23
Thanks! What's the replacement for sprintf()? My new Outputstats() method is just a massive cout, but I'm only using that for debug purposes. 

I realise there was no incentive to defend (although I did decide to defend when your health is low) , but I'm in the middle of redesigning formula's for the new game. For example, there's no use for mana in that game, I stupidly gave each monster an ID (hoping to make a random battle generator out of them) until i realised that there's no way to get that ID without referencing the monster! (d'oh!)

Just finished the modhealth+modmana functions, they make sure (via if statement) that the health never drops below 0 (in reality it does, but the if statement corrects it).

---

### Post by lisati on 2009-06-23
> **ash.rossy said:**
> Ok, I get that public variables are bad practice (same as globals in non-oo programming?)
My experiences is mainly non-oo and would suspect that you're on the right track. Both public/global and local/private have their place; one of the things to keep in mind is reducing the risk of unintended side-effects.

---

### Post by Mirge on 2009-06-23
> **thebuzzsaw said:**
> i won! :d

lmao!

---

### Post by Can+~ on 2009-06-23
> **ash.rossy said:**
> A messenger would be good, I'll PM my MSN messenger email to you. 

Difficulties I had. Well, I guess it's time for another code sample :P

It was a guess the number game with ordered high scores (read from a scores.his file)

Here's the code in it's entirety

The funny thing was I wrote a nearly 90 line function to do the same thing (sigh)... It wasn't until I started using getline in that function, did i realise i made it defunct!

You could use a binary file to store the monster information, it's more practical when there will be multiple units as binary files are more compact and allow random access (if coded properly).

But more for the practical reasons, I was thinking as it making it part of your practice, so you can learn how to work with binary files.

As for the OP, the whole idea of "not having public variables" is to:

1. Be able to inherit or modify it properly in the future.
2. Avoid having your variables changed from outside without a check.

But I wouldn't demonize the public attribute, as they surely have their reason to exist.

*edit: Fun fact, I just remembered in python you could do:

[PHP]class LivingThing(object):
	def __init__(self, hp, mana=0):
		self.myhp = hp
		self.mymana = mana
	
	def get_hp(self):
		return self.myhp
	
	def set_hp(self, hp):
		self.myhp = hp
	
	hp = property(fget=get_hp, fset=set_hp, doc="Change HP")

if __name__ == "__main__":
	creature = LivingThing(100, 20)
	
	print creature.hp
	creature.hp = 50
	print creature.hp
[/PHP]

So attributes are being treated with their get and set functions indirectly (with function pointers). Is there any equivalent to this in C++? (not flaming really, I just want to know)

(edit: whoops, forgot the (object) inheritance there)

---

### Post by ash.rossy on 2009-06-23
I'm not sure, both Python and C++ have pointers, but im sure it destroys the point of something having private values (ability to know where your variables are being changes)

---

### Post by Habbit on 2009-06-23
Strictly speaking, you _can_ emulate the value-checking effect of properties in C++ through proxy objects, as in this crude example: (I'm sure a guru could rewrite it so that the compiler will optimize it away)```
template<typename T, typename prop_c, T (*prop_c::getter)(), void (*prop_c::setter)(const T&)>
class member_instance_property
{
public:
    typedef property<T, prop_c, getter, setter> property_t;
    property(T& parent) : obj(parent) {}
    
    operator T() {
        return obj.*getter();
    }
    
    property_t& operator=(const T& value) {
        obj.*setter(value);
        return *this;
    }
    
private:
    property_t& operator=(const property_t&);
    T& obj;
}

class earth_mountain {
private:
    void set_height(double meters) {
        if (meters < 0.0 || meters > 9000.0)
            throw std::out_of_range("Not on Earth!");
        height_v = meters;
    }
    double get_height() { return height_v; }

    double height_v;
public:
    member_instance_property<double, earth_mountain, get_height, set_height> height;
    
    earth_mountain() : height_v(0.0), height(this) {}
}

int main(int argc, char** argv) {
    earth_mountain olympus_mons;
    olympus_mons.height = 25000.0; // Will throw an exception
    cout << olympus_mons.height << endl;
}
```Please note that I'm writing this off the top of my head. Thinking that it might compile amounts to a pipe dream.

---

### Post by dwhitney67 on 2009-06-23
> **Habbit said:**
> ...
Please note that I'm writing this off the top of my head. Thinking that it might compile amounts to a pipe dream.

Here's your code, this time with the compilation errors fixed.
```

#include <iostream>
#include <stdexcept>

template<typename T, typename prop_c, T (prop_c::*getter)(), void (prop_c::*setter)(const T&)>
class member_instance_property
{
public:
    member_instance_property(prop_c& parent) : obj(parent) {}
    
    operator T() {
        return (obj.*getter)();
    }
    
    member_instance_property& operator=(const T& value) {
        (obj.*setter)(value);
        return *this;
    }
    
private:
    member_instance_property& operator=(const member_instance_property&);
    prop_c& obj;
};

class earth_mountain {
private:
    void set_height(const double& meters) {
        if (meters < 0.0 || meters > 9000.0)
            throw std::out_of_range("Not on Earth!");
        height_v = meters;
    }
    double get_height() { return height_v; }

    double height_v;
public:
    member_instance_property<double, earth_mountain, &earth_mountain::get_height, &earth_mountain::set_height> height;
    
    earth_mountain() : height_v(0.0), height(*this) {}
};

int main(int argc, char** argv) {
    earth_mountain olympus_mons;
    olympus_mons.height = 25000.0; // Will throw an exception
    std::cout << olympus_mons.height << std::endl;
}

```

---

