---
title: "class constructor chain problem, c++"
date: 2008-09-06
forum: Programming Talk
---

### Post by monkeyking on 2008-09-06
Hi, I've been programming a lot of c code,
and now I'm trying to set my mind into the c++ way of doing things.
so I'm trying to avoid pointers, and use refs instead.


I have 2 classes that I want to contain in another class.
But these 2 classes needs to have their constructor arguments.
And I'm havind problems fiddling it together.

But I can't instantiate the inner classes.


This is a code snippet that illustrates this problem.

I think the problem is in the constructor of my container class.

thanks in advance
```

#include <iostream>

class aClass{
 public:
  float f1;
  float f2;
  int *array;
  aClass(float var1, float var2){printf("norm class construct\n");f1=var1;f2=var2;}
};

template <typename T>
class aTemplate{
  float f1;
  float f2;
  T *array;
  aTemplate(float var1, float var2){printf("template class constructor\n");f1=var1;f2=var2;}
};



class aCollector{
  int a;
  int b;
  aCollector(int f, int g) {myTemplate(f,g);myobj(f,g);}
  aTemplate<int> myTemplate;
  aClass myobj;
};

int myFun(aStruct as){
  return 0;
}

int main(){
  aCollector acol(2,3);
  return 0;
}

```

---

### Post by Lux Perpetua on 2008-09-06
Use an initializer list. See below: ```
  aCollector(int f, int g) : myTemplate(f,g), myobj(f,g) { }
```

---

### Post by monkeyking on 2008-09-06
Thanks I did manage to get alot further now.
But I think I have a design problem.

I have my containerclass,
that should contain an instantiation of either aClass or aTemplete.
Not both of them.

I've tried changing the initilizer list to

```

class aCollector {
public:
  int a;
  int b;
  aCollector(int assd,int f, int g): (assd==0)?myTemplate(f,g):myobj(fg){}
  aTemplate<int> myTemplate;
  aClass myobj;
};

```

The compiler tells me, that I'm using a anachronistic class initializer...
Thats a new one :)


But it seems, that you're not allowed to have objects in another object, without actually instantiating it.
In a world of c, I would just have made a pointer, to my datastructs.
And then only allocing the one I needed.

thanks in advance

Am I missing some basic c++ idea.

---

### Post by dribeas on 2008-09-06
> **monkeyking said:**
> ```

class aCollector {
public:
  int a;
  int b;
  aCollector(int assd,int f, int g): (assd==0)?myTemplate(f,g):myobj(fg){}
  aTemplate<int> myTemplate;
  aClass myobj;
};

```

If you define your object as having both aTemplate<int> and aClass, you should initialize both. Initializer lists are not designed to have flow control (you implicit if in (x?y:z) ).

Then again, if you are sure you want to have either type and you don't want to go into initialization of both, you can always use a pointer (I would recommend a smart pointer):

```

class X
{
   std::auto_ptr<type1> x_;
   std::auto_ptr<type2> y_;
public:
   X(bool selector) : x_(0), y_(0) // initialize pointer to 0
   {
      if ( selector ) {
         x_.reset( new type1() ); // reset x_
      } else {
         y_.reset( new type2() );
      }
   }
};

```

Now, in most cases you'll want to redesign. It does not make sense to have either one or the other class initialized but not both. Then all your methods will have to deal with the two possibilities. If aClass and aTemplate<> do share an interface you can always use a template:

```

template <typename T>
class aCollector
{
   T data_;
   aCollector( int ***, int f, int g ) : data_( f, g ) {}
};

```

With some more insight I could even recommend template specializations (if *** is known at compile time) or some other techniques.

---

### Post by dribeas on 2008-09-06
> **monkeyking said:**
> ```

class aCollector {
public:
  int a;
  int b;
  aCollector(int assd,int f, int g): (assd==0)?myTemplate(f,g):myobj(fg){}
  aTemplate<int> myTemplate;
  aClass myobj;
};

```

If you define your object as having both aTemplate<int> and aClass, you should initialize both. Initializer lists are not designed to have flow control (you implicit if in (x?y:z) ).

Then again, if you are sure you want to have either type and you don't want to go into initialization of both, you can always use a pointer (I would recommend a smart pointer):

```

class X
{
   std::auto_ptr<type1> x_;
   std::auto_ptr<type2> y_;
public:
   X(bool selector) : x_(0), y_(0) // initialize pointer to 0
   {
      if ( selector ) {
         x_.reset( new type1() ); // reset x_
      } else {
         y_.reset( new type2() );
      }
   }
};

```

Now, in most cases you'll want to redesign. It does not make sense to have either one or the other class initialized but not both. Then all your methods will have to deal with the two possibilities. If aClass and aTemplate<> do share an interface you can always use a template:

```

template <typename T>
class aCollector
{
   T data_;
   aCollector( int assd, int f, int g ) : data_( f, g ) {}
};

```

With some more insight I could even recommend template specializations (if assd is known at compile time) or some other techniques.

---

### Post by monkeyking on 2008-09-06
thanks I thought it was possible to have this flow control in the initializer list.
But I'll go with the c style pointer.

---

