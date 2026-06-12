---
title: "C++ static variable between multiple instances"
date: 2011-10-11
forum: Programming Talk
---

### Post by akvino on 2011-10-11
I tried researching this information but couldn't find an answer.

If you declare static member variable that is a pointer to the data structure (static pointer to the object, static pointer to the array, static pointer to the hash table, etc...), and the data structure is allocated dynamically (with the keyword 'new'), how is the access to the data structure managed between instances?

In code it would look something like this:

[PHP]
class A
{
   static B * p_toB;

};

class B
{
   int someArray[10000];

}

[/PHP]

---

### Post by PaulM1985 on 2011-10-11
You would access it using:

```

// You now have a local variable pointing to the static instance of B
B *p_toB = A::p_toB;  

// Used the pointer to call a function on the static object
p_toB->SomeFunction();

```

Alternatively you could just do:

```

A::p_toB->SomeFunction();

```

Paul

---

### Post by karlson on 2011-10-11
> **akvino said:**
> I tried researching this information but couldn't find an answer.

If you declare static member variable that is a pointer to the data structure (static pointer to the object, static pointer to the array, static pointer to the hash table, etc...), and the data structure is allocated dynamically (with the keyword 'new'), how is the access to the data structure managed between instances?

In code it would look something like this:

[PHP]
class A
{
   static B * p_toB;

};

class B
{
   int someArray[10000];

}

[/PHP]

Not sure I understand what you are trying to do?  If you are allocating and deleting an instance of B then you would need to assign
```

A::p_toB = <address of an instance of B>

```
and every time you want to change it you will need to reassign that.

I would look at the implementation of the Singleton pattern as an example.

---

### Post by akvino on 2011-10-11
So this is little confusing.


Assignment would be something like:
[PHP]

class A 
{ 
   static B * p_toB; 

}; 

class B 
{ 
   int someArray[10000]; 

}  

//initializing static variables
B A::p_toB = NULL;



//Then Assignment
A::A()
{
  if (p_toB == NULL)
  {
     p_toB = new B;
  }
 
}


[/PHP]

The question is:
If there are multiple instances of 'A', how do we manage access to p_toB->someArray, between the instances of 'A'. Static assures that we have only one pointer (Singleton data pattern). I am trying to find out if some sort of locking mechanism is needed (mutex), when accessing array?

---

### Post by karlson on 2011-10-11
> **akvino said:**
> 
```

//Then Assignment
A::A()
{
  if (p_toB == NULL)
  {
     p_toB = new B;
  }
  else
    return p_toB;
}

```


This is just wrong.

> 

The question is:
If there are multiple instances of 'A', how do we manage access to p_toB->someArray, between the instances of 'A'. Static assures that we have only one pointer (Singleton data pattern). I am trying to find out if some sort of locking mechanism is needed (mutex), when accessing array?

The pointer between instances of A will be identical, so if you are updating something in the instance of B you will need a lock.

I would suggest downloading source for this:
[http://www.cs.wustl.edu/~schmidt/ACE.html](http://www.cs.wustl.edu/~schmidt/ACE.html)

and looking into the implementation of the Singleton.

Not sure if there is one in boost as I haven't looked.

---

### Post by akvino on 2011-10-11
> **karlson said:**
> This is just wrong.



The pointer between instances of A will be identical, so if you are updating something in the instance of B you will need a lock.

I would suggest downloading source for this:
[http://www.cs.wustl.edu/~schmidt/ACE.html](http://www.cs.wustl.edu/~schmidt/ACE.html)

and looking into the implementation of the Singleton.

Not sure if there is one in boost as I haven't looked.

Fixed:
[PHP]
//Then Assignment
A::A()
{
  if (p_toB == NULL)
  {
     p_toB = new B;
  }
 
}  
[/PHP]


So I do need a lock.....

---

### Post by akvino on 2011-10-11
New update...

If the instances are running on the same thread then one will not need a lock, only if instances are running on different threads, then one has a problem...

---

### Post by karlson on 2011-10-11
> **akvino said:**
> Fixed:
[PHP]
//Then Assignment
A::A()
{
  if (p_toB == NULL)
  {
     p_toB = new B;
  }
 
}  
[/PHP]


So I do need a lock.....

More like:
```

A::A()
{
   if( NULL == p_toB )
   {
       Lock();
       if( NULL == p_toB )
       {
           p_toB = new B;
       }
       Unlock();
   }
}

```
That is if you are running in a multi-threaded environment.

---

