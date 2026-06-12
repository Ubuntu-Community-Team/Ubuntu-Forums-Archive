---
title: "C++ Member variables changing on their own!"
date: 2007-12-22
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2007-12-22
Hey guys

Here's a weird one for you, I have a object that contains a vector list of pointers to objects of another class. within the other objects I have a vector list of pointers to yet another class of a different type.

My problem is that the last class seems to be having member variables that have changing values. 

I have made all member vars protected so that they can only be accessed outside the object using Get and Set member functions but they still continue to change with being made to by my code!!!!???!?!?!

They are all created on the heap with the first object being created as a new object assigned to a pointer to the new object which is also on the heap.

The members in question are all of type GLfloat if thats worth knowing. I also have checked and the Get / Set members are only used in the places that I want them and I know exactly what they are doing so it can be them.

Does anyone have a clue what could be happening?

here is some code to help:

```

class ObjectThree{
  public:
        // I use Get / Set members here to access the protected vars

  protected:
    GLfloat x,y,z;
};

class ObjectTwo{
  public:

  protected:
    vector <ObjectThree *> MyListOfObjectThrees;
};

class ObjectOne{
  public:

  protected:
    vector <ObjectTwo *> MyListOfObjectTwos;
};

``` 

I'm currently compiling with -ggdb -Wall -O0 so as to debug.

PLEASE HELP!

Mike

---

### Post by dwhitney67 on 2007-12-22
Please post a listing of the part of your application that is instantiating Object1, and performing memory allocations for Object2 and Object3.

Also, are you initializing x, y, and z in Object3's constructor?

---

### Post by Mickeysofine1972 on 2007-12-23
ok here's how ObjectOne gets created:
```

void InitObjectOne()
{
   ObjectOne *  MyGlobalObjectOnePtr = new ObjectOne;
}

ObjectOne::Add(ObjectTwo* a_ObjectTwo){
   
   MyListOfObjectTwos.push_back(a_ObjectTwo);
 
}

```

Later WHen its time to add objects to the list i do this:

```

...
   ObjectTwo * MyObjectTwo = new ObjectTwo;
   
   MyGlobalObjectOnePtr->Add( MyObjectTwo );
...

Also, the ObjectThree is made in the constructor of object two like so:

   ObjectTwo::ObjectTwo()
   {
       ObjectThree * MyObjectThree = new ObjectThree;
       MyListOfObjectThrees.push_back( MyObjectThree );
   }

```

Hope this helps

Mike

---

### Post by dwhitney67 on 2007-12-23
Do you have a method to add Object3 objects to the list contained within Object2?  I see that you add one object during the construction.  But it does not show me that x, y, and z are being initialized to any particular values (maybe they are zero?).

The other issue is the declaration for MyGlobalOneObjectPtr.  This is declared as a local variable within the C-style function InitObjectOne().  After you call this function, the pointer is no longer accessible because the variable that points to the allocated object is local to the function.

Something like this might be more in-line with what you are trying to accomplish:

```

// ...

int main()
{
  Object3 obj3_a = new Object3(  5, 10, 15 );
  Object3 obj3_b = new Object3( 30, 60, 90 );
  Object3 obj3_c = new Object3;          // all coordinates are defaulted to zeroes

  Object2 obj2_a = new Object2;
  obj2_a.add( obj3_a );

  Object2 obj2_b = new Object2;
  obj2_b.add( obj3_b );
  obj2_b.add( obj3_c );

  Object1 obj1;
  obj1.add( obj2_a );
  obj1.add( obj2_b );

  // ...
}
```

I'm still not sure what purpose your program will serve, hence I cannot comment on the design too much.  For your design, ensure that you implement a destructor that will delete all of the objects that have been allocated.  This is needed for the Object1 and Object2 classes.

P.S.  I know that you merely experimenting at this time, however you should consider coming up with more descriptive names for your classes and variables; names that provide context for the data that is stored/manipulated.

---

