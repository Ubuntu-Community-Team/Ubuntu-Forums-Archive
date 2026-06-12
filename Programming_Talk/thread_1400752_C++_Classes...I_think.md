---
title: "C++ Classes...I think"
date: 2010-02-07
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-07
Okay I looked at all the tutorials, few make sense and I think it's to do with classes. 

I want to create a class (i think) called Disposition

so essentially, characterName.disposition

so that I can use disposition for other characters as well yet still be unique. (I'm messing around with an RPG text based game if that's any help) (planning to add graphics later)

So any help would be appreciated.

---

### Post by Sinkingships7 on 2010-02-07
> **Ravenshade said:**
> Okay I looked at all the tutorials, few make sense and I think it's to do with classes. 

I want to create a class (i think) called Disposition

so essentially, characterName.disposition

so that I can use disposition for other characters as well yet still be unique. (I'm messing around with an RPG text based game if that's any help) (planning to add graphics later)

So any help would be appreciated.

Not entirely sure what you're getting at, but it sounds like you want a class to create characters from, like so:
```

// character.h

#ifndef CHARACTER_H
#define CHARACTER_H

class Character{
public:
    // Constructors and public data and methods go here.
    <return-type> disposition(<args>);
private:
    // Private data and methods go here.
};


#endif

```
```

// character.cpp
#include "character.h"

<return type> Character::disposition(<args>){
    // Whatever you're trying to do here.
}

```
```

//main.cpp

#include "character.h"

int main(void}{
    Character characterName;
    characterName.disposition(<args>);

    return 0;
}

```

---

### Post by Zorgoth on 2010-02-07
I do not think you are talking about a class but rather a member of a class.  A "class" called "character" would be, for example

class character
{
public:
...
return_type accessdisposition();
private:
...
other_class_name disposition;
};

and then you would say in your program:

...
character character1;
return_type disposition;
disposition = character1.accessdisposition();
...

Try rephrasing your question, it's hard for me to understand what you are asking; it is very unclear.

In particular it would help if you explained what exactly "disposition" is.

---

### Post by Ravenshade on 2010-02-07
disposition is just a name. 

It seems I have a lot to learn about classes, maybe I should go and look at the tutorials again. 

I wanted to create a system that would remember variables for the NPC's involved in my game. In this instance Disposition is how the NPC feels about that character. If that character feels good he might respond in a more helpful manner for instance. 

That's why I wanted to create a class of NPC's where information such as Disposition or Health are stored. With each member of that class having their own attributes of each of those.

---

### Post by Zorgoth on 2010-02-07
You might consider having an enum of potential dispositions (look it up, they're pretty simple); then you can just call them, for example, things like "favorable" or "hostile" or whatever other words you wanted; you might also consider and integer scale.  If you care about NPC reactions to more than one character you would probably want to create either a list or an array (a list is a kind of data structure if you don't know) of pairings of an NPC with a disposition inside each character's class.  Otherwise (that is if you only have one character to worry about) it should be a property of an NPC.

It is not good practice to directly access something like character.disposition from outside the class (or perhaps as I described it dispositions); you should make the list "dispositions" a private object which is accessed by public functions so that you can properly restrict what the program can do to it.

And as I said before "disposition" is not a class but most likely a private member of a class.  A class is something like "playerCharacter" or "NPC" or "int" or "string."  It has member objects which are normally declared under "private:" and member functions which may be "public:" or "private:."

---

### Post by Ferrat on 2010-02-07
Well guessing in the RPG that you want to have different classes, races etc? 

one way to do it is to first create a "char" class then in that class depending on external input have that class create own classes.

For ex. 

you got the "Class" classes "Warrior" and "Mage"

both these contain the function attack which takes the same params and gives a result how ever the internal workings differ, fopr ex. the Warrior needs to be close to his enemy for his attack to hit, while the Mage has a longer range and so on. 

Depending on what "class" you select your "char" class creates a object within itself based on that

so a Character that's a Warrior would initialize a Warrior object within itself as the "class" object, while a Mage would create a Mage object as "class", both having the function attack but using it differently. 

It depends on how you create the engine really, either you can have the engine handle disposition if it's just a matter of aggression and just have an simple INT or something comparing values within the engine but for more complex handling I would actually put every thing that has a interaction in classes and then incorporate them within a base-class allowing for a more dynamic build up of characters as you might want different reactions on the same things depending on other thing. 
This way for ex if you later on realize you want to add a certain disposition that acts totally different from the others or reacts in a new way compared to the earlier ones it would not be as much digging in the old code as just creating a new class based on the same basic template on what functions and params it takes. 

but that's just my taste :)

Edit:
This also makes each for.ex NPC objects act on their own and not as just a passive set of numbers interpreted by the engine

---

### Post by Ravenshade on 2010-02-08
ack. That's complicated. Do you mean a character.class or a class of type char (always getting confused with these things. 

At the moment I'm not dealing with distance ... way too complicated at the moment.

---

### Post by Ferrat on 2010-02-08
I mean character.class

it's not really that complicated, it's the same idea that you had more or less from start :) a class within another class :) it's like inheritance but backwards, I'll try to explain it more. 

First you have a base-class (a class in the programming sence), this class is called ENTITY

ENTITY in turns creates other classes (c++ classes) within itself for different things

In a RPG it's not uncommon for both Player Characters and NPCs to use some for of AI in battle, while they might react similar to some things other stuff you might want the NPCs to do differently, like NPC more hellbent on killing the player and the players helpers more concentrated at healing / saving their friends.

The Battle AI then needs to take certain actions depending on parameters, for ex. it's useless to heal someone if they aren't injured or attacking someone that's dead. 

While you probably want to use overloading you probably want a few standardized functions. (otherwise errors in the code will be hard to avoid, always try to standardize your code to make it easier to edit and less error prone when you are working with different objects that handle the same stuff) :)

So ENTITY needs to create a AI object within itself, but there are a two different types to choose from, NPC_AI, HENCHMAN_AI depending on the ENTITY type, so when you start creating the ENTITY object that in turn creates a AI object inside itself. 

But if the HENCHMAN for ex. is taken over by mind control or something you can just destroy the HENCHMAN_AI object and create a NPC_AI in it's place, when spell is countered of wares off you destroy the NPC_AI object and create a HENCHMAN_AI object again. 

you could just redirect but I gave this ex so that you might understand what I mean :) it's not really as hard as it sounds you just need to understand the structure of it

---

### Post by Ravenshade on 2010-02-09
Now I just need to figure out the syntax ^_^;

---

