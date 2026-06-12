---
title: "[C++] Game development help"
date: 2009-04-06
forum: Programming Talk
---

### Post by Nexusx6 on 2009-04-06
Hello Prog Talk!

I'm currently writting a text based adventure game and I've hit a wall. The game is pretty far along, the player can move around rooms and exam stuff in the room but its not at all advanced: there are no different weapons, armors, or items you can pick up and use -- and this is where I now want to take it. I was using a struct to define the players attributes like health and such, but I wanted to re-write it as a class and I did so.

I figured the next logical would be to write the ability to equip armor and weapons that the player can get throughout the dungeon and here is where I've been stuck for a long time. I know these parts should be also classes but I'm really lost on how I need to go about doing this. If it was just straight number addition to damage (weapons) or reduction (armor) I think I could go about doing that pretty well, but what I really want is for the armor/weapon pieces to have special effects, like a weapon that can attack twice, or a shield that has a chance to negate all damage.

I've googled for a good long while, but as popular as the subject of game programming is, I can't find a good example or tutorial that goes about doing this. My question then, is if someone can show me how so that I can do the rest, or point me to a tutorial. I appreciate the help; I'll post my hero class for critique and an idea of whats happen in my code.

```
#include <iostream>
#include <ctime>

using namespace std;

class Characters
{
    string name;
    int health_max;
    int health;
    int strength;
    int damage;
    int exp;
    int level;
    int curr_room;
    void setHealthMax() { health_max = 130+(20*level); }
    void setStrength()  { strength = 20+(level*5); }
    void changeHealth(int change) { health += change; }
public:
    Characters(int, int, int);
    int attackDamage();
    void takeDamage(int damage);
    void gainExp(int exp);
    void showStats();
};
Characters::Characters(int init_health=150, int init_exp=0, int init_curr_room=1)
{
    health      = init_health;
    curr_room   = init_curr_room;
    level       = 1;
    exp         = 0;
    gainExp(init_exp);
    setHealthMax();
    setStrength();
}
void Characters::gainExp(int add_exp)
{
    exp += add_exp;
    int level_ups[6] = {0, 100, 250, 450, 550, 700};
    for (int i=1;exp >= level_ups[i];i++)
    {
        if (level<i)
        {
            level = i;
            setHealthMax();
            setStrength();
            cout <<" _   ___ _ _ ___ _     ___ ____ _ \n"
                   "| |_|  _| | |  _| |_  | | | __ \\ |\n"
                   "|   |  _| | |  _|   | | | |  __/_|\n"
                   "|___|___|\\_/|___|___| |___|_|  |_|\n\n";
        }
    }
}
void Characters::takeDamage(int damage)
{
    changeHealth(-1*damage);
}
int Characters::attackDamage()
{
    return (rand() % (strength+10) + (strength-10));
}
void Characters::showStats()
{
    cout << " =================\n";
    cout << "|| HEALTH: " << health << "/" << health_max << endl;
    cout << "|| STR:    " << strength << endl;
    cout << "|| LEVEL:  " << level << endl;
    cout << "|| EXP:    " << exp << endl;
    cout << " =================\n";
}
```

---

### Post by Sinkingships7 on 2009-04-07
Couldn't you use the rand() function to determine chances of shields negating damage and whatnot? Maybe have the chances fade away as the shield loses its durability, if you're wanting to incorporate such a feature.

---

### Post by shadylookin on 2009-04-07
I would create interfaces for weapon and shield and then implement them with specific Weapon and Shield classes

for instance 

interface weapon{
    attack();
} 

class UltimateWeapon implements weapon{
    attack(){
        doDamage();
        if(randomNumber){
            doDamage();//attack twice
        }
    }
}


class normalwepaon impelments weapon{
    attack(){
        dodamage();//unspecial weapon does normal damage
    }
}

I'm not real familiar with C++ syntax, but I'm sure there's a way to do this.

---

### Post by GF_Sobriquet on 2009-04-07
> **Sinkingships7 said:**
> Couldn't you use the rand() function to determine chances of shields negating damage and whatnot? Maybe have the chances fade away as the shield loses its durability, if you're wanting to incorporate such a feature.

I think this is how I would do it. Set up the events in a battle (or on each move, whatever) as if they were simply random events. Then you can weight the probabilities based on modifiers from various items, etc. If you want something to always attack twice, just round up the "attack twice" rand() to 1. Another option is to skip calls to certain rand() events all together if the player has (or doesn't have) a certain item.

Good luck, sounds like a fun project!

---

### Post by Nexusx6 on 2009-04-07
> **Sinkingships7 said:**
> Couldn't you use the rand() function to determine chances of shields negating damage and whatnot? Maybe have the chances fade away as the shield loses its durability, if you're wanting to incorporate such a feature.

Oh defiantly, that's how I would code that part of the armor, but what has me perplexed is how I can elegantly code these effects into the attack sequence. I know that I could use a bunch of if statements to check if the hero has the item and is equipped, and if they do then run these functions -- but that's very non modular and messy.

```
for instance

interface weapon{
attack();
} 
```

Putting the attack method in the weapon as opposed to in the Characters class is a good idea actually and give me an idea on how to go about the rest of this since by putting the equipped weapon in a vector and just calling attack() from the vector. Still open for any suggestion though.

---

### Post by tneva82 on 2009-04-07
Howabout visitor template? Have class weapon from which different weapons are derived. When somebody is attacked call weapons attack() method giving target as parameter. Weapon then does it's thing using target's interface to accomplish effect(reduce HP etc). This way you can add weapons easily by creating new classes for them and put code to create them when you get them. Just make sure target has flexible enough interface to do what you need to do.

That's how I approached similar problem long time ago when I needed to create whole bunch of different types of weapons that behaved differently(based on tabletop ruleset so hadn't much of a chance to alter those).

Edit: Shadylooking seems to have already pretty much suggested this :D

---

### Post by shadylookin on 2009-04-07
> **Nexusx6 said:**
> 
```
for instance

interface weapon{
attack();
} 
```

Putting the attack method in the weapon as opposed to in the Characters class is a good idea actually and give me an idea on how to go about the rest of this since by putting the equipped weapon in a vector and just calling attack() from the vector. Still open for any suggestion though.

I would just make it so that the character has a weapon attribute and when it wants to attack it uses it. Once again apologies for my lack of proper c++ syntax

[PHP]
class character{
        Weapon weapon;
}

character A;
A.weapon = UltimateWeapon;

A.weapon.attack();

[/PHP]

I just feel that whenever possible you should use object oriented principles.

The same could be done with armor and shields

You can create shield and armor interfaces and implement them

interface shield{
block();
}

class awesomeshield impelements shield{
block(){
aborbdamage();
if(randomNumber){
absorbmoredamage();//chance to absorb more damage
}
}
}

---

### Post by Nexusx6 on 2009-04-07
> 
[PHP]class character{
        Weapon weapon;
}

character A;
A.weapon = UltimateWeapon;

A.weapon.attack(); [/PHP]
I just feel that whenever possible you should use object oriented principles.

I whole heartedly agree and Your example is exactly what I was looking! C++ doesn't have interface like java or C#, but I did a lot of reading on it and ways to implement interface like objects in C++. This is the resulting code:

I added this into the characters class. It's public now to make it easier to test but I plan on making it private later:
```

public:
    Characters(int, int, int);
    Weapons * weapon;
    void equipWeapon(Weapons*);
void Characters::equipWeapon(Weapons * item)
{
    weapon = item;
}

```
And this is what Weapons and the DoubleStrikeSword classes look like:
```
class Weapons
{
public:
    virtual void attack() = 0;
};
class DoubleStrikeBlade: public Weapons
{
public:
    virtual void attack() { cout << "Damage done!" << endl; }
};


```
And finally, the main code and the output:
```
int main()
{
    srand(time(0));

    Characters hero(130);
    DoubleStrikeBlade twoxsword;
    Weapons * dbl_strike_sword = &two_x_sword;

    hero.equipWeapon(dbl_strike_sword);
    hero.weapon->attack();

//OUTPUT
Damage done!

```

Is this kind of what you were talking about? I would initialize the instances of each weapon in main, and any time the player switched weapons all I would have to do is call equipWeapon(whatever). The initialization is a little wierd, but the rest is simple. Thanks a ton for the help and advice.
Also, I'm still open to any other suggestions.

[EDIT]: Double Strike Blade is just an example name, I didn't intend for it to actually attack twice yet, I was just tossing up an example.

---

### Post by soltanis on 2009-04-07
I skimmed your message, so if I misunderstand I apologize.

It looks like you might be looking for (among other things) a way to write a modular/easily maintained system for having inventory items do special effects (like add +5 HP for wearing armor, for example).

Now pardon my C++, but I think using an interface, you can specify a certain set of methods (such as onEquip, onDeEquip, onAttack, onHit) that are fired when a certain event takes place (then simply write those methods into your code, so when your player is hit, call onHit for all equipped items, or when you attack, call onAttack for all items, and so on).

Then all you have to do is have all your equipment items conform to this interface.

(Using a base class might be smarter, actually, and have all equipped items inherit from that class).

---

### Post by Nexusx6 on 2009-04-07
> **soltanis said:**
> I skimmed your message, so if I misunderstand I apologize.

It looks like you might be looking for (among other things) a way to write a modular/easily maintained system for having inventory items do special effects (like add +5 HP for wearing armor, for example).

Now pardon my C++, but I think using an interface, you can specify a certain set of methods (such as onEquip, onDeEquip, onAttack, onHit) that are fired when a certain event takes place (then simply write those methods into your code, so when your player is hit, call onHit for all equipped items, or when you attack, call onAttack for all items, and so on).

Then all you have to do is have all your equipment items conform to this interface.

(Using a base class might be smarter, actually, and have all equipped items inherit from that class).

Exactly right :D The problem unfortunately is two-fold: C++ doesn't have interfaces, and I am newish to classes and OOP. 

I've found a few sites that explain how to emulate interfaces in C++, but as this isn't a native thing, finding the documentation/tutorials on this is hard and a bit over my head. My lack of experience in OOP is making this a slow uphill job, but I think I'm making head way. Could you perhaps check the code above and see if I'm on the right track?

---

