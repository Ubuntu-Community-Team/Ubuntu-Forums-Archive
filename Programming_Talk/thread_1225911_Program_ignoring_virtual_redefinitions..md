---
title: "Program ignoring virtual redefinitions."
date: 2009-07-29
forum: Programming Talk
---

### Post by pepperphd on 2009-07-29
Hi I was hoping someone could help me figure out why my program is calling blank virtuals instead of the most recently defined one.

Here are the classes that are having this problem.  

```

class Enemy : public Env_var
{    
    protected:

        int max_health;    
        int current_health;
        int facing;
        int velocity_modifier;
        int x_vel;
        int y_vel;
        SDL_Rect hit_box;

    public:

        Enemy(int w, int h) : Env_var(w, h)
        {
            hit_box.w = w;
            hit_box.h = h;
        }

        void take_damage(int damage_taken) { current_health -= damage_taken; }
        void generic_gravitation(SDL_Rect target);

        void show()
        {
            apply_surface(hit_box.x, hit_box.y, sprite, screen, NULL);
        }

        virtual void action() const {}

        virtual void move() const {}

        virtual void handler() const {}
};

class Spike_block : public Enemy
{
        int axis;

    public:

        Spike_block(int a, int x, int y, int w = 36, int h = 36) : Enemy(w, h)
        {
            axis = a;
            hit_box.x = x;
            hit_box.y = y;
            sprite = spike_block_i;
            velocity_modifier = 10;
        }

        void action();
        void move();
        void handler()
        {
            move();
            show();
            action();
        }
};
```

Enemies are stored in <vector>s in another class called room, which has a member function that is supposed to call the handler() for each Enemy in the vector.  

```

void Room::handle_room_elements()
{
    register unsigned int i;

    for(i = 0; i < layout.size(); i++)
        layout[i].show();

    for(i = 0; i < env_var_list.size(); i++)
        env_var_list[i].handler();

    for(i = 0; i < enemy_list.size(); i++)
        enemy_list[i].handler();
}

```

But instead of calling the handler() for a Spike_block in the enemy_list vector, it calls the "virtual void handler() const {}" version.  Moving all of Spike_blocks member functions to Enemy's definition is counterproductive.  Why would this happen? If you need more code I'll be glad to hand it over.

---

### Post by Sockerdrickan on 2009-07-29
You are not using polymorphism

---

### Post by pepperphd on 2009-07-29
> **Tux0r said:**
> You are not using polymorphism

Explain?  If you're referring to the empty functions in spike_block, they are defined in another file.
```

void Spike_block::action()
{
    if(check_collision(hit_box, player.get_coll_box()))
        player.take_damage(1, DEFAULT);

    if(player.get_current_room()->static_obstruction_collision_check(hit_box))
        velocity_modifier = -velocity_modifier;
}

void Spike_block::move()
{
    if(axis == Y)
        y_vel = velocity_modifier;
    else    x_vel = velocity_modifier;

    if(axis == Y)
        hit_box.y += y_vel;
    else    hit_box.x += x_vel;
}

```

---

### Post by Sockerdrickan on 2009-07-29
[http://en.wikipedia.org/wiki/Polymorphism_in_object-oriented_programming#C.2B.2B](http://en.wikipedia.org/wiki/Polymorphism_in_object-oriented_programming#C.2B.2B)

---

### Post by pepperphd on 2009-07-29
Okay. I still have no idea if you're trying to make a point or not. Thanks for trying though.

---

### Post by Sockerdrickan on 2009-07-29
[http://lmgtfy.com/?q=polymorphism](http://lmgtfy.com/?q=polymorphism)

---

### Post by pepperphd on 2009-07-29
Posting here for help is a last resort.  I have googled, several times for several different terms.  I am not new to polymorphism, I have written similar functions in the past.  If you know what the problem is, please point it out because my program is stuck on it.  I have been looking for at least an hour, trying different things and reading, and haven't been able to produce a solution.

---

### Post by Sockerdrickan on 2009-07-29
I gave you the answer 15 minutes ago. You are not using polymorphism. It's as simple as that. Check the first link I gave you for an example on how to do it.

---

### Post by pepperphd on 2009-07-29
Can you actually point to what I'm doing wrong or are you just messing with me?

---

### Post by Sockerdrickan on 2009-07-29
> **pepperphd said:**
> Still nothing.  Care to spoil it yet?
I have no idea what you are talking about. The link to wikipedia shows you how to use your **Enemy **(not **Animal**) correctly. There's nothing more to it.

---

### Post by pepperphd on 2009-07-29
Are you telling me that I can't make a vector of Enemy and expect it to use the virtuals in Enemies derivatives?  Because I'm putting derivatives of Enemy in the vector.

---

### Post by Sockerdrickan on 2009-07-29
This is my last answer to you here. Check the friggin link for code example on how to do it, you are on the right way, just read the example. Please. Do it.

---

### Post by Drone022 on 2009-07-29
Do the methods in the subclass also need the virtual keyword?

---

### Post by Sockerdrickan on 2009-07-29
> **Drone022 said:**
> Do the methods in the subclass also need the virtual keyword?
No you don't explicitly have to.

---

### Post by Drone022 on 2009-07-29
enemy_list[i]->handler();?

---

### Post by Sockerdrickan on 2009-07-29
> **Drone022 said:**
> enemy_list[i]->handler();?
Yes, thus requiring pointers.

---

### Post by nvteighen on 2009-07-29
> **Tux0r said:**
> Yes, thus requiring pointers.
Ok, can you now tell me what the hell has that issue to do with polymorphism? Polymorphism is just multiple dispatching in a certain class-tree... The need for pointers or not will depend on how the hell the thing is stored!

```

#include <iostream>
#include <string>

class Something
{
public:
    std::string *blah;

    Something(const char *);
    ~Something();

    virtual void say();
};

class DerivedSomething : public Something
{
public:
    DerivedSomething(const char *str) : Something(str) {}

    void say();
};

Something::Something(const char *str)
{
    blah = new std::string(str);
}

Something::~Something()
{
    delete blah;
}

void Something::say()
{
    std::cout << "Something!" << std::endl;
}

void DerivedSomething::say()
{
    std::cout << *blah << std::endl;
}

int main()
{
    Something *ST1 = new Something("Hello!");
    DerivedSomething *DST1 = new DerivedSomething("Hi!");

    ST1->say();
    DST1->say();

    delete ST1;
    delete DST1;

    Something ST2 = Something("Bye!");
    DerivedSomething DST2 = DerivedSomething(":)");

    ST2.say();
    DST2.say();

    return 0;
}

```

---

### Post by Sockerdrickan on 2009-07-29
> **nvteighen said:**
> Ok, can you now tell me what the hell has that issue to do with polymorphism? Polymorphism is just multiple dispatching in a certain class-tree... The need for pointers or not will depend on how the hell the thing is stored!

```

#include <iostream>
#include <string>

class Something
{
public:
    std::string *blah;

    Something(const char *);
    ~Something();

    virtual void say();
};

class DerivedSomething : public Something
{
public:
    DerivedSomething(const char *str) : Something(str) {}

    void say();
};

Something::Something(const char *str)
{
    blah = new std::string(str);
}

Something::~Something()
{
    delete blah;
}

void Something::say()
{
    std::cout << "Something!" << std::endl;
}

void DerivedSomething::say()
{
    std::cout << *blah << std::endl;
}

int main()
{
    Something *ST1 = new Something("Hello!");
    DerivedSomething *DST1 = new DerivedSomething("Hi!");

    ST1->say();
    DST1->say();

    delete ST1;
    delete DST1;

    Something ST2 = Something("Bye!");
    DerivedSomething DST2 = DerivedSomething(":)");

    ST2.say();
    DST2.say();

    return 0;
}

```
If you are going to use polymorphism with objects in a std::vector (like OP), you better use pointer to base class. ;)

Which in turn is the definitive answer to OP's problem too.

**Edit**: What you did in your code was member function overriding, not polymorphism really so I don't see how that relates to this thread in particular. :P

---

### Post by scourge on 2009-07-29
The problem is that your action(), move(), and handler() methods are const in the base class, but non-const in the derived class. So you haven't really reimplemented anything.

---

### Post by nvteighen on 2009-07-29
> **Tux0r said:**
> 
**Edit**: What you did in your code was member function overriding. I don't see how that relates to this thread in particular. :P

Er... what I did is my very first C++ program :p

Ok, I know what polymorphism is from other OOP languages (Python, Objective-C and Common Lisp... haven't understood polymorphism in Perl yet). Polymorphism is about letting different classes to respond to the same "message" (in Smalltalk/Objective-C lingo) in a different way... I think that's what I did in my C++ snippet; ok, I didn't leave Something::say() defined blank but... isn't it the same?

Of course, the generic multiple dispatch in Common Lisp is really much better :)

---

### Post by Sockerdrickan on 2009-07-29
> **scourge said:**
> The problem is that your action(), move(), and handler() methods are const in the base class, but non-const in the derived class. So you haven't really reimplemented anything.Good spot :)

---

### Post by Sockerdrickan on 2009-07-29
> **nvteighen said:**
> Er... what I did is my very first C++ program :p

Ok, I know what polymorphism is from other OOP languages (Python, Objective-C and Common Lisp... haven't understood polymorphism in Perl yet). Polymorphism is about letting different classes to respond to the same "message" (in Smalltalk/Objective-C lingo) in a different way... I think that's what I did in my C++ snippet; ok, I didn't leave Something::say() defined blank but... isn't it the same?

Of course, the generic multiple dispatch in Common Lisp is really much better :)
```
#include <iostream>
#include <string>

class Something
{
public:
    std::string *blah;

    Something(const char *);
    ~Something();

    virtual void say();
};

class DerivedSomething : public Something
{
public:
    DerivedSomething(const char *str) : Something(str) {}

    void say();
};

Something::Something(const char *str)
{
    blah = new std::string(str);
}

Something::~Something()
{
    delete blah;
}

void Something::say()
{
    std::cout << "Something!" << std::endl;
}

void DerivedSomething::say()
{
    std::cout << *blah << std::endl;
}

int main()
{
    Something *some_things[3]={new Something("Hello!"),new DerivedSomething("Hi!"),new Something(":)")};

    for(int i(0); i<3; ++i) {
        some_things[i]->say();
        delete some_things[i];
    }
}
```

It's all about using a base pointer with type dependant implementations :D

---

### Post by dribeas on 2009-07-29
In C++ it is important to know how you are trying to store the objects. Unlike Java/C# etc, C++ has copy semantics by default. That means that if you try to insert into a vector of Base objects a Derived object you will be creating new Base objects that copy the common part of the Derived object. That is called slicing. A std::vector<Base> only holds Base objects, never Derived objects.

This could be part of the problem (I don't see your definition of the storage type). If it is so, the simple solution is storing pointers (I would recommend std::tr1::shared_ptr / boost::shared_ptr as it will release resources when the vector is destroyed).

Another thing is that the signature in the Base and Derived classes of the polymorphic methods must coincide in all but the possible co-variant return type. That is, the signature must exactly match (all argument types and const-ness of arguments and method) with the only exception that in the Derived signature you can return an object of a class that derives from that returned in the Base class method.

```

class BReturn {};
class DReturn : public BReturn {};

class Base
{
public:
   virtual BReturn* function( const BReturn&, BReturn, int ) const; 
};
class Derived
{
public:
   virtual BReturn* function( const BReturn&, BReturn, int ) const; // ok
// virtual DReturn* function( const BReturn&, BReturn, int ) const; // also ok: covariant return
// virtual int function( const BReturn&, BReturn, int ) const; // error not a covariant return --compilation error
// virtual BReturn* function( const DReturn&, BReturn, int ) const; // overload, not override the first argument type does not coincide
// virtual BReturn* function( const BReturn&, BReturn, double ) const; // overload, even if int can be converted to double they are not the same function
// virtual BReturn* function( const BReturn&, BReturn, int ); // overload, const-ness of the method changes
};

```

---

### Post by nvteighen on 2009-07-29
> **Tux0r said:**
> ```
#include <iostream>
#include <string>

class Something
{
public:
    std::string *blah;

    Something(const char *);
    ~Something();

    virtual void say();
};

class DerivedSomething : public Something
{
public:
    DerivedSomething(const char *str) : Something(str) {}

    void say();
};

Something::Something(const char *str)
{
    blah = new std::string(str);
}

Something::~Something()
{
    delete blah;
}

void Something::say()
{
    std::cout << "Something!" << std::endl;
}

void DerivedSomething::say()
{
    std::cout << *blah << std::endl;
}

int main()
{
    Something *some_things[3]={new Something("Hello!"),new DerivedSomething("Hi!"),new Something(":)")};

    for(int i(0); i<3; ++i) {
        some_things[i]->say();
        delete some_things[i];
    }
}
```

It's all about using a base pointer with type dependant implementations :D

Got the idea ;)

---

### Post by dribeas on 2009-07-29
> **Tux0r said:**
> It's all about using a base pointer with type dependant implementations :D

Or references, both of which allow for polymorphic behavior:

```

void f( Base & b )
{
   b.function(); // will call Derived.function() if function is virtual and it is called with a derived object
}

```

---

### Post by Sockerdrickan on 2009-07-29
> **dribeas said:**
> Or references, both of which allow for polymorphic behavior:

```

void f( Base & b )
{
   b.function(); // will call Derived.function() if function is virtual and it is called with a derived object
}

```
Well obviously since references are similar to constant pointers :D

---

### Post by soltanis on 2009-07-29
I believe this thread is reason enough never to use C++.

---

### Post by Sockerdrickan on 2009-07-30
> **soltanis said:**
> I believe this thread is reason enough never to use C++.
I believe your ignorance to the beauty of C++ polymorphism must be defeated! :D

---

### Post by pepperphd on 2009-07-30
Thank you dribeas, that answer was better than I could have asked for.

---

### Post by nvteighen on 2009-07-30
> **Tux0r said:**
> I believe your ignorance to the beauty of C++ polymorphism must be defeated! :D
If this is beautiful, Common Lisp's CLOS's (and TinyCLOS/SOS's... which are CLOS for Scheme) multiple dispatching based on generic procedures is divine :)

---

### Post by Sockerdrickan on 2009-07-30
> **nvteighen said:**
> If this is beautiful, Common Lisp's CLOS's (and TinyCLOS/SOS's... which are CLOS for Scheme) multiple dispatching based on generic procedures is divine :)
*"Not all martyrs see divinity"  *:D

---

