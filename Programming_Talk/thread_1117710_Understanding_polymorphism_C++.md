---
title: "Understanding polymorphism C++"
date: 2009-04-06
forum: Programming Talk
---

### Post by Benzaa on 2009-04-06
Hi,

I was wondering if you could help me to understand some
things regarding polymorphism in C++.

Im trying to make a general container for a class. Something
like this:

```

class fruit {
  >> code here
}

class apple : public fruit {

}

class banana : public fruit {

}

```

What I want is a general container for the three of them. 
Something like:

```

class bagOfFruit {
  vector<fruit*> mfruit;

  >> code here
}

```

and then I can create different types of bags, something
like this

```

class bagOfApples : public bagOfFruit {
  >> code here
}

class bagOfBananas : public bagOfFruit {
  >> code here
}

```

My problem is the use of the command new for the creation of
the fruit objects.

In a bagOfApples, I would need to use
```

mfruit[0] = new Apple

```

and for bagOfBananas 
```

mfruit[0] = new banana

```

So far, my code works fine like this.

The problem comes when I copy a bagOfApples or bagOfBananas.
The funtion will call the copy constructor of bagOfFruit
wich will call the copy constructor of fruit. 

So, what the copy constructor is doing is:
for bagOfApples
```

mfruit[0] = new Fruit

```

for bagOfBananas
```

mfruit[0] = new Fruit

```

This is a problem because I want to create a Banana or an
Apple.

Any ideas to solve this problem??

---

### Post by dwhitney67 on 2009-04-06
I'm surprised that you were able to use the operator[] of a vector even though you did not indicate you had resized the vector.  Anyhow, maybe I'm wrong and thinking of some other issue.

Wrt your bagOfFruit copy constructor, it needs to make a deep-copy of the fruit items in the 'other' vector.  There are a few ways to do this, but the easiest is to use a virtual clone() method.  Define this method in Fruit as a pure-virtual, and implement it in each of your Fruit-subclasses.

Here's an example:
```

bagOfFruit(const bagOfFruit& other)
{
  for (std::vector<Fruit*>::const_iterator it = other.mfruit.begin(); it != other.mfruit.end(); ++it)
  {
    mfruit.push_back( (*it)->clone() );
  }
}

```

---

### Post by Benzaa on 2009-04-06
And what should you put in the clone method?

I'm thinking that it generates a fruit object and then it returns that object.

But by doing so I will be returning a Fruit object

```

class fruit {
  virtual fruit clone(void) = 0;
}

class banana : public fruit {
  virtual fruit clone(void);
}

fruit banana::clone(void) {
  banana NewBanana;

  return NewBanana;
}

```

Is that right?

Btw, I did resize the vector before using the operator[]

---

### Post by dwhitney67 on 2009-04-06
My apologies for not giving you the solution earlier, but this seemed like a class assignment from school.  But now that you have made an attempt, I am free to assist you a little more.

```

class fruit
{
  ...

  virtual fruit* clone() = 0;
};

class apple : public fruit
{
  ...

  fruit* clone();
};

...

fruit*
apple::clone()
{
  return new apple;
}

```

If your apple constructor takes any special parameters, obtain these values from the 'this' object in clone().

In the real-world, there is more than one type of apple.  Thus the apple-type could be one of these apple attributes.

---

### Post by Benzaa on 2009-04-06
dwhitney67, thanks for the help!!!

now I got it working.

Sorry if I gave you the impression that this is my assigment. 
At this moment Im learning c++ for a project (phd) that Im working on.

Btw, now I want to add operator() to the classes, but I get this error:

> 
In member function "apple& bagOfApple:: operator()(unsinged i).
error: conversion from "fruit" to non-scalar type "apple" requested


my function looks like this:

```

apple& bagOfApple::operator()(unsigned i) {
   return *mfruit(i);
}

```

Any idea??

---

### Post by dwhitney67 on 2009-04-06
The syntax is incorrect; what you want to implement is the operator[] method, not the operator().  The latter is used to define functor objects.

```

class bagOfFruit
{
  ...

  const fruit* operator[](const size_t i) const
  {
    return mfruit[i];
  }

  ...
};

```

---

### Post by Benzaa on 2009-04-06
mmm, I was using the () operator because im working with a matrix.

It is easier to access it by (row,col) than by a single [index]

Thanks for the help, know I got it working like I want it.

---

### Post by dwhitney67 on 2009-04-06
You lost me; this thread has introduced classes for 'fruit', 'apple', 'banana', and 'bagOfFruit'.  I do not see a definition for a matrix anywhere.

---

### Post by Benzaa on 2009-04-06
Sorry about that,

I am working with an object that behaves like a matrix. 

But my problem was the use of virtual constructors (clone function). 

I thought that I was going to easier to explain my problem with a simple class (like the fruit example) than using my original classes.

Your help has been great. I applied all the things that you told me. I've been learning c++ for just 3 months and there are some things that I can not fully understand until I see a good example.

---

### Post by dwhitney67 on 2009-04-06
> **Benzaa said:**
> ...
But my problem was the use of virtual constructors (clone function). 
...

Do not think of the clone() method as a virtual constructor.  Constructors cannot be virtual.  Think of clone() has a "helper" instantiator or something along those lines.

So what does your matrix look like?  Is it a two-dim array, or a 2-dim vector, or something else?

---

### Post by Benzaa on 2009-04-08
Hey, sorry for the laaaate reply,

I was away and didnt have time to check my inbox.

My matrix is a 1-dim vector. It is a vector that contains all the objects that I am working with. The only difference is the way to access the index.
I wrote a function that converts the ROW and COL into an INDEX for the vector. 

By doig so, I am using the () operator to access the elements of the vector

BagOfFruit Bag1;
Bag1(1,2).color();

That is the idea, very simple but it helps me for my program.

---

