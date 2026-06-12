---
title: "C++ inheritance question"
date: 2011-06-14
forum: Programming Talk
---

### Post by erotavlas on 2011-06-14
Hi,

I have a question about C++ inheritance. I have a base class with a protected method and a derived class (public inheritance) that uses that method. But the compiler gives an error "method is protected".
What could be the problem? I can solve it by making the method public, but I don't want do it.
Thank you

---

### Post by dwhitney67 on 2011-06-14
That's hard to believe.  Are you sure that you implemented the code as you described?

Something like this should be legal:
```

class A
{
public:
   A() {}

protected:
   void doSomething() {}
};

class B : public A
{
public:
   B()
   {
      doSomething();
   }
};

int main()
{
   B b;
}

```

---

### Post by PaulM1985 on 2011-06-14
Have you any example code?

You could have a function in your derived class (which has a different name) with a public interface which calls the function in your base class.

It's a little difficult to make a suggestion based on those details.

Paul

EDIT: posted just after (without seeing) dwhitney's comment.  I was assuming the OP meant that they where calling the function on the derived object, something like:

```

class A
{
public:
   A() {}

protected:
   void doSomething() {}
};

class B : public A
{
public:
   B()
   {
      doSomething();
   }
};

int main()
{
   B b;
   b.doSomething();
}

```

---

### Post by erotavlas on 2011-06-14
Hi, 

thank you for your fast answers. My code is very long...here there is a simplified version where the problem is still present.

```

class A { public:    A() {}  protected:    void doSomething_base() {} };  class B : public A { public:    B()    {    }

void doSomething_derived();

private:
vector<A*> myVector;
}; 
void B::doSomething_derived()
{
this->doSomething_base();
} 

```

The problem is inside the function doSomething_derived().
Is it legal?

Thank you

---

### Post by SledgeHammer_999 on 2011-06-14
> **erotavlas said:**
> Hi, 

thank you for your fast answers. My code is very long...here there is a simplified version where the problem is still present.

```

class A { public:    A() {}  protected:    void doSomething_base() {} };  class B : public A { public:    B()    {    }

void doSomething_derived();

private:
vector<A*> myVector;
}; 
void B::doSomething_derived()
{
this->doSomething_base();
} 

```

The problem is inside the function doSomething_derived().
Is it legal?

Thank you


Strange this code(after the deletion of the vector) builds fine on mingw32(gcc 4.5.2)...

```
class A 
{ 	
	public:
	A() {}
	
	protected:
	 void doSomething_base() {} 
};  

class B : public A 
{ 
	public: B()  {}

	void doSomething_derived();
	
}; 

void B::doSomething_derived()
{
this->doSomething_base();
}

int main(int argc, char *argv[])
{
	B b;
	b.doSomething_derived();
	return 0;
}
```

---

### Post by erotavlas on 2011-06-14
> **PaulM1985 said:**
> Have you any example code?

You could have a function in your derived class (which has a different name) with a public interface which calls the function in your base class.

It's a little difficult to make a suggestion based on those details.

Paul

EDIT: posted just after (without seeing) dwhitney's comment.  I was assuming the OP meant that they where calling the function on the derived object, something like:

```

class A
{
public:
   A() {}

protected:
   void doSomething() {}
};

class B : public A
{
public:
   B()
   {
      doSomething();
   }
};

int main()
{
   B b;
   b.doSomething();
}

```

I have tried to compile from command line this code and I get the same error ‘void A::doSomething()’ is protected. Very strange...

---

### Post by PaulM1985 on 2011-06-14
My post was a guess at what you where trying to do.

After sledgehammer's post it looks like you posted your cut down example incorrectly since sledgehammer can build it ok.

---

### Post by dwhitney67 on 2011-06-14
> **erotavlas said:**
> I have tried to compile from command line this code and I get the same error ‘void A::doSomething()’ is protected. Very strange...

Which compiler are you using?

---

### Post by erotavlas on 2011-06-14
> **dwhitney67 said:**
> Which compiler are you using?

g++ (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2

---

### Post by dwhitney67 on 2011-06-14
You are running a later version of the compiler than I have on my system.  Are you running Ubuntu 11.04?  Was GCC installed via the Synaptic Package Manager, or did you perform a manual install?

Personally, I have not yet upgraded to 11.04.  I prefer to let others sort out the issues a new release may have, then upgrade 3-4 months later once all the kinks are ironed out.

---

### Post by erotavlas on 2011-06-14
> **dwhitney67 said:**
> You are running a later version of the compiler than I have on my system.  Are you running Ubuntu 11.04?  Was GCC installed via the Synaptic Package Manager, or did you perform a manual install?

Personally, I have not yet upgraded to 11.04.  I prefer to let others sort out the issues a new release may have, then upgrade 3-4 months later once all the kinks are ironed out.

Yes I'm on Ubuntu 11.04 64 bit. I have installed g++ from repository with apt-get install g++.

---

### Post by erotavlas on 2011-06-14
> **PaulM1985 said:**
> My post was a guess at what you where trying to do.

After sledgehammer's post it looks like you posted your cut down example incorrectly since sledgehammer can build it ok.

Here is my complete code with the error...

```
 
#include <iostream>
#include <vector> 

class A 
{ 
public:    
A() {}  
protected:
  
virtual void doSomething_base() {} 
};  


class B : public A 
{ 
public:    
B()    {}

void doSomething_derived();

protected:

A* Get(int i) const
{
return this->myVector[i];
}

private:
std::vector<A*> myVector;
}; 

void B::doSomething_derived()
{
for(int i = 0; i < myVector.size(); ++i)
   this->Get(i)->doSomething_base();
}

int main(int argc, char *argv[])
{
    B b;
    b.doSomething_derived();
    return 0;
}

```

---

### Post by SledgeHammer_999 on 2011-06-14
Error from mingw32(gcc 4.5.2)
> main.cpp: In member function 'void B::doSomething_derived()':
main.cpp:10:14: error: 'virtual void A::doSomething_base()' is protected
main.cpp:35:35: error: within this context

If I understand your code correctly:
this->Get(i) returns a pointer to an instance of class A (A*). Then you use that pointer to execute a protected method of the object DIRECTLY. I don't think that this is legal.

Sidenote: You don't need to use "this" in "this->Get(i)"

EDIT: One solution is to declare class B as a "friend" of class A. [http://www.cplusplus.com/doc/tutorial/inheritance/](http://www.cplusplus.com/doc/tutorial/inheritance/)

---

### Post by erotavlas on 2011-06-14
> **SledgeHammer_999 said:**
> Error from mingw32(gcc 4.5.2)


If I understand your code correctly:
this->Get(i) returns a pointer to an instance of class A (A*). Then you use that pointer to execute a protected method of the object DIRECTLY. I don't think that this is legal.

So the only solution is to make the method public?

> 
Sidenote: You don't need to use "this" in "this->Get(i)"
Ok, It's true. But it still works.

---

### Post by dwhitney67 on 2011-06-14
> **erotavlas said:**
> So the only solution is to make the method public?


Sorry for this, but the question must be asked... why are you making B a subclass of A?  Is there really an "is-a" relationship between B and A?

Anyhow, the easiest solution for now is to make A::doSomething_base() a public method.

---

### Post by SledgeHammer_999 on 2011-06-14
Or a "friend". See my edit on my previous post.

---

### Post by erotavlas on 2011-06-14
> **dwhitney67 said:**
> Sorry for this, but the question must be asked... why are you making B a subclass of A?  Is there really an "is-a" relationship between B and A?

Anyhow, the easiest solution for now is to make A::doSomething_base() a public method.

The answer to the question is not simple. The class A is a sort of interface for other classes: B is one specialization of A that contains a vector of A. There is also C that is another specialization of B. By the polymorphism, the class B will contain a vector of elements of C class.
Ok, thank you.

---

### Post by JupiterV2 on 2011-06-14
dwhitney67 +1

---

### Post by erotavlas on 2011-06-14
> **SledgeHammer_999 said:**
> Or a "friend". See my edit on my previous post.

But a virtual function cannot be a friend. So the only solution is to make the method public.

---

### Post by SledgeHammer_999 on 2011-06-14
OK. I didn't know that.

But my question is: What are you trying to achieve by having a vector of the base class and calling a method on it? Maybe somebody here can suggest a different solution/approach to your problem.

---

### Post by nvteighen on 2011-06-14
I agree: the design is awful.

But FYI, this is why I think your compile doesn't compile:

1) By making doSomething_base a virtual method, one has to take the parent's and the child's version as different objects. The right method is chosen according to the object's actual class and not to its declared type, i.e. it's like it checked what constructor was used to create the object (very informal explanation), regardless of the type of pointer you're using to access that instance.

2) 'protected' just declares a private method as inheritable, but it keeps it private in both parent and child. What this means is that B will have access to its own doSomething_base but not to A's.

3) In Get(), you return an A*. This means that without further information at compile-time, C++ assumes that what you get are A objects... although some of those A objects could be B objects actually... So, it assumes that you want to access A's version of doSomething_base, which you can't because you're at B. Therefore, it fails to compile.

Using dynamic_cast<B *>(this->Get())->doSomething_base() in doSomething_derived allows your code to be compiled perfectly. But surely will crash as soon as you try to cast an A object into a B object (it'll only work to cast back a B object that has been previously casted to A).

What are you exactly trying to do?

---

