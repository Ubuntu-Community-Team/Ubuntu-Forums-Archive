---
title: "C++ why can't I pass a pointer into a function? why isn't this working"
date: 2008-04-04
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2008-04-04
This is just a simple RPG (not even) that I'm writing to help me learn C++.

Can anyone tell me why this won't work?

Thanks so much!

```
#include <iostream>

using namespace std;

class Entity
{
    private:
        int attackPower;
        int shield;
        string name;

    public:
        int health;
        //Contructors
        Entity();
        Entity(int h, int s, int a, string n)
        {
            health = h;
            shield = s;
            attackPower = a;
            name = n;
        };
        //Functions
        void Display()
        {
            cout << "Name: " << name << endl;
            cout << "Health: " << health << endl;
            cout << "Shield: " << shield << endl;
            cout << "Attack Power: " << attackPower << endl;
        };

        int Attack()
        {
            cout << name << " attacks for " << attackPower << " damage";
            return attackPower;
        };

        void takeDamage(int opponentAttackPower)
        {
            health = (health - (opponentAttackPower * (.3 * shield)));
        };

 };

void battle(Entity* player1, Entity* player2)
{
    while (player2.health > 0 || player1.health > 0)
    {
        player2.takeDamage(player1.Attack());
        player2.Display();

        if (player2.health > 0)
        {
            player1.takeDamage(player2.Attack());
            player1.Display();
        }
        else
        {
            break;
        }
    }
}

int main()
{
    Entity jake = Entity(10, 5, 2, "Jake");
    Entity *pJake = &jake;

    Entity john = Entity(10, 5, 2, "John");
    Entity *pJohn = &john;


    battle(&jake, &john);
}

```

---

### Post by mike_g on 2008-04-04
Your main problem seems to be that you are trying to access the class variables the wrong way inside your battle function. As the players are pointers you need to do somethinglike: [COLOR="DarkRed"]player->takedamage()[/COLOR] instead of[COLOR="DarkRed"]player.takedamage()[/COLOR] With those changes g++ will compile it for me for me, but still throws up a few extra wrnings you may want to fix.

---

### Post by Aztek on 2008-04-04
Mike is correct. When you access the member data items of a pointer, you must *dereference* the pointer first. There are 2 ways to do this in C++:

1) Direct member access operator on a pointer that is already dereferenced.
```
(*player1).takeDamage()
```

2) Indirect member access operator.
```
player1->takeDamage()
```

Method 2 is much cleaner and more widely used in my experience.

---

### Post by WW on 2008-04-04
Or...

You can use references (instead of pointers) as the arguments to battle():
```

[...snip...]

void battle(Entity& player1, Entity& player2)
{
    while (player2.health > 0 || player1.health > 0)
    {
        player2.takeDamage(player1.Attack());
        player2.Display();

        if (player2.health > 0)
        {
            player1.takeDamage(player2.Attack());
            player1.Display();
        }
        else
        {
            break;
        }
    }
}

int main()
{
    Entity jake = Entity(10, 5, 2, "Jake");
    Entity john = Entity(10, 5, 2, "John");

    battle(jake, john);
}

```

---

### Post by Aztek on 2008-04-04
> **WW said:**
> Or...

You can use references (instead of pointers) as the arguments to battle():
```

[...snip...]

void battle(Entity& player1, Entity& player2)
{
    while (player2.health > 0 || player1.health > 0)
    {
        player2.takeDamage(player1.Attack());
        player2.Display();

        if (player2.health > 0)
        {
            player1.takeDamage(player2.Attack());
            player1.Display();
        }
        else
        {
            break;
        }
    }
}

int main()
{
    Entity jake = Entity(10, 5, 2, "Jake");
    Entity john = Entity(10, 5, 2, "John");

    battle(jake, john);
}

```


I would also recommend using references instead.

---

### Post by oodlesOfmoodles on 2008-04-04
First: Thank you all for your quick responses!

Thanks mike_g and Aztek. I appreciate the clarification on the most commonly used way to access a pointer's member variables/functions.


And thank you WW (and Aztek) for the suggestion to use references.

Would you mind explaining why references are preferred over passing pointers?

Thanks!

---

### Post by dwhitney67 on 2008-04-04
You should also consider changing the following code:
```

[...snip...]
    Entity jake = Entity(10, 5, 2, "Jake");
    Entity john = Entity(10, 5, 2, "John");

```

to be:
```

    Entity jake(10, 5, 2, "Jake");
    Entity john(10,5, 2, "John");

```

This will save time in constructing the object, hence is more efficient.

---

### Post by oodlesOfmoodles on 2008-04-04
Thank for the help dwhitney!

What is the difference between:
```
Entity jake = new Entity(10, 5, 2, "Jake")
```
```
Entity jake(10, 5, 2, "Jake")
```
```
Entity jake = Entity(10, 5, 2)
```

What do they each do and which one's better?

Thanks again!

---

### Post by dwhitney67 on 2008-04-05
> **oodlesOfmoodles said:**
> Thank for the help dwhitney!

What is the difference between:
```
Entity jake = new Entity(10, 5, 2, "Jake")
```
```
Entity jake(10, 5, 2, "Jake")
```
```
Entity jake = Entity(10, 5, 2)
```

What do they each do and which one's better?

Thanks again!
The first won't compile... you are attempting to assign a pointer (returned by the new operation) to a non-pointer declaration.

The second example constructs an Entity object using a defined constructor (perhaps the default constructor?).

The third example constructs an Entity object using a defined constructor, and then calls the copy constructor.  If a copy constructor is not defined (by you), then the compiler will create one for you.  Before you get all excited about this, please bear in mind that the compiler-created copy-constructor will only be able to copy simple objects (int, float, double, string).  For more complex copying of class components, you should define the copy-constructor yourself.

A typical copy-constructor looks like:
[PHP]Entity::Entity( const Entity &ent )
{
  // copy elements here
  this->field = ent.field;
}[/PHP]

As for which of your examples is better, examples 2 and 3 each have their benefits/costs.  Obviously example 2 is more efficient than example 3.

---

### Post by aks44 on 2008-04-05
> **dwhitney67 said:**
> You should also consider changing the following code:
```

[...snip...]
    Entity jake = Entity(10, 5, 2, "Jake");
    Entity john = Entity(10, 5, 2, "John");

```

to be:
```

    Entity jake(10, 5, 2, "Jake");
    Entity john(10,5, 2, "John");

```

This will save time in constructing the object, hence is more efficient.

> **dwhitney67 said:**
> The third example constructs an Entity object using a defined constructor, and then calls the copy constructor.
[...]
Obviously example 2 is more efficient than example 3.


Wrong. The standard explicitly states that those two notations are strictly equivalent.

Since I can't be bothered to find the exact chapter and verse right now, here's an example that demonstrates this equivalence:

```
#include <iostream>

class Foo
{
private:
  int m_i;
public:
  Foo(int i)
    : m_i(i)
  {
    std::cout << "In Foo(int) constructor: i = " << m_i << std::endl;
  };
  Foo(const Foo& other)
    : m_i(other.m_i)
  {
    std::cout << "In Foo copy-constructor: i = " << m_i << std::endl;
  };
  Foo& operator =(const Foo& other)
  {
    m_i = other.m_i;
    std::cout << "In Foo assignment operator: i = " << m_i << std::endl;
    return *this;
  };
};


int main()
{
  Foo foo1 = Foo(3);
  Foo foo2(4);
  return 0;
}
```

```
$ g++ -o test test.cpp
$ ./test
In Foo(int) constructor: i = 3
In Foo(int) constructor: i = 4
```


Note that neither the copy constructor nor the assignment operator get called.

Both notations being equivalent, using either one just boils down to personal style preference.

As far as I'm concerned, I prefer using the first one [COLOR="DarkRed"]Foo x = Foo(...)[/COLOR] as IMHO it makes the code more visually explicit. YMMV of course, as this is purely a style matter.

---

### Post by oodlesOfmoodles on 2008-04-05
Thank for your reply aks44. This may seem like a newb question in the face of that explanation, but could you clarify as to what the : does in 
```
Foo(int i)
    : m_i(i)
```

---

### Post by dwhitney67 on 2008-04-05
Sorry, you're right.  My little testing last night was based on writing similar, but obviously not equivalent code.

I had done:
[PHP]Foo f1(1);
Foo f2 = f1;     // this calls the copy constructor[/PHP]
[PHP]
Foo f3 = Foo(3);    // this does NOT call the copy constructor; just the constructor[/PHP]

---

### Post by the_unforgiven on 2008-04-05
> **oodlesOfmoodles said:**
> Thank for your reply aks44. This may seem like a newb question in the face of that explanation, but could you clarify as to what the : does in 
```
Foo(int i)
    : m_i(i)
```
The **:** in the above statement says that the member initialization list follows - this is a standard practice in C++ to initialize all(?) the member variables through ctors (short for constructors :p)

---

### Post by aks44 on 2008-04-05
> **oodlesOfmoodles said:**
> could you clarify as to what the : does in 
```
Foo(int i)
    : m_i(i)
```

As the_unforgiven already pointed out, it's an *_initialization list_*.

The following code may help you understand *why* it is a best practise to use them in constructors:
```
#include <iostream>

class Foo
{
public:
  Foo() { std::cout << "Foo default constructor." << std::endl; };
  Foo(int) { std::cout << "Foo(int) constructor." << std::endl; };
  Foo(const Foo&) { std::cout << "Foo copy constructor." << std::endl; };
  Foo& operator =(const Foo&) { std::cout << "Foo assignment operator." << std::endl; return *this; };
};

class Inefficient
{
private:
  Foo m_foo;
public:
  Inefficient()
  {
    m_foo = Foo(42);
  };
};

class Efficient
{
private:
  Foo m_foo;
public:
  Efficient()
    : m_foo(42)
  {
  };
};

int main()
{
  std::cout << "Inefficient:" << std::endl;
  Inefficient inefficient;
  std::cout << "Efficient:" << std::endl;
  Efficient efficient;
  return 0;
}
```

yields:
```
Inefficient:
Foo default constructor.
Foo(int) constructor.
Foo assignment operator.
Efficient:
Foo(int) constructor.
```





> **dwhitney67 said:**
> Sorry, you're right.  My little testing last night was based on writing similar, but obviously not equivalent code.

I had done:
[PHP]Foo f1(1);
Foo f2 = f1;     // this calls the copy constructor[/PHP]

That code also shows something interesting: it's the *_copy-constructor_* that gets called, **not** *_default-constructor + assignment_*.


So, that code is equivalent to:
```
Foo f1(1);
Foo f2(f1);
```

:)

---

### Post by glok_twen on 2008-04-05
> **oodlesOfmoodles said:**
> First: Thank you all for your quick responses!

Thanks mike_g and Aztek. I appreciate the clarification on the most commonly used way to access a pointer's member variables/functions.


And thank you WW (and Aztek) for the suggestion to use references.

Would you mind explaining why references are preferred over passing pointers?

Thanks!

mostly simplicty of the code - don't need to create another variable. and , you still get the performance benefit of not having to create another copy of the the passed parameter if it it's passed by value.

---

