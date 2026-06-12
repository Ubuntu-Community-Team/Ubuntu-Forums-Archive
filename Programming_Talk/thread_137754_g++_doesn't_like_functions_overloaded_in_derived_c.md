---
title: "g++ doesn't like functions overloaded in derived classes"
date: 2006-02-28
forum: Programming Talk
---

### Post by norfenstein on 2006-02-28
Can someone possibly tell me if the following is portable C++ and if so, why g++ refuses to compile it (complaining that Base::method() is inaccessible in this context)? It compiles fine with [Comeau](http://www.comeaucomputing.com/tryitout/).
```
#include <iostream>
using namespace std;

class Base {
	public: void method() {
		cout << "Base::method" << endl;
	}
};

class Derived: public Base {
	using Base::method;
	public: void method(int) {
		cout << "Derived::method" << endl;
	}
};

int main() {
	Derived derived;

	derived.method(2);
	derived.method();

	return 0;
}
```
For some reason this code will compile and work correctly with g++ if "Derived" is changed to a struct. I'm at a loss personally, so any insight would be very appreciated. :-k

---

### Post by jerome bettis on 2006-02-28
.

---

### Post by jerome bettis on 2006-02-28
ok i was way off earlier lol ..  just when you think you know c++

all you have to do is move the using Base::method(); after the public: and it will work .. also you need to name the int parameter

---

### Post by norfenstein on 2006-02-28
Ah, wonderful, thank you very much :).

The unnamed parameter thing is weird, I never would have thought it was acceptable syntax until I saw it in some examples when I was researching this problem. Here I just used it to marginally simplify the code snippet but it occurs to me that it might actually be useful for what I was playing around with, which is basically using function overloading in lieu of a large switch/if-else-if statement with run-time type identification (which I don't even know how to do in C++). I should probably just look up the proper way of implementing the observer pattern in C++ though.

---

### Post by thumper on 2006-02-28
Look at the boost slots and signals library.

Despite the signal in the name, it is a implementation of the observer pattern.

---

### Post by hod139 on 2006-02-28
First, your base class is **not **overloading the parents function (this is really a method, but I will call the methods functions since you named your methods "method"). The parents function "method(void)" is not equal to the extended class' function "method(int)", since the parameters are not equal. This is why a Derived object cannot access the member function in Base. The keyword using should be reserved for namespaces, not classes, especially if you have the classes in separate files. That said, here are two ways to write your code without the "using" keyword (critiques welcome).

In the code below, *base is of type Base and has the limitation that it cannot refer to the members of Derived that Derived hasn't inherited from Base. Therefore, to call the method(void) function, we have to use the derived object.

```

[COLOR=#008000]#include <iostream>
[/COLOR]**class** Base {
   **public**: 
      [COLOR=#800000]void[/COLOR] method() {
          std::cout << [COLOR=#dd0000]"Base::method"[/COLOR] << std::endl;
      }
};
[B]
class[/B] Derived: **public** Base {
   **public**:
      [COLOR=#800000]void[/COLOR] method([COLOR=#800000]int[/COLOR]) {
         std::cout << [COLOR=#dd0000]"Derived::method"[/COLOR] << std::endl;
      }
};

[COLOR=#800000]int[/COLOR] main() {
   Derived derived;
   Base * base = &derived;

   derived.method([COLOR=#0000ff]2[/COLOR]);
   base->method();

   **return** [COLOR=#0000ff]0[/COLOR];
}

``` 
If we wanted to use method(int) with the pointer to Base, it must also be declared in the Base class. To do this, use virtual members
```
[COLOR=#008000]#include <iostream>
[/COLOR]**class** Base {
    **public**: 
       [COLOR=#800000]void[/COLOR] method(void) {
          std::cout << [COLOR=#dd0000]"Base::method"[/COLOR] << std::endl;
       }
        **virtual** [COLOR=#800000]void[/COLOR] method([COLOR=#800000]int[/COLOR]) = [COLOR=#0000ff]0[/COLOR];
};
 [B]
class[/B] Derived: **public** Base {
   **public**:
      [COLOR=#800000]void[/COLOR] method([COLOR=#800000]int[/COLOR]) {
         std::cout << [COLOR=#dd0000]"Derived::method"[/COLOR] << std::endl;
      }
};

[COLOR=#800000]int[/COLOR] main() {
   Base * derived = new Derived();

   derived->method([COLOR=#0000ff]2[/COLOR]);
   derived->method();

   delete derived;

   **return** [COLOR=#0000ff]0[/COLOR];
} 
```

---

### Post by jerome bettis on 2006-03-01
in your main method you make the distinction between Base and Derived.  that completely defeats the purpose of inheritance.  if i want to delcare a base, i'll do just that and use the base methods as i see fit.  but i'd rather declare a derived and have it behave like a base or derived when appropriate.


i.e. i don't want to declare a base ever, just a bunch of derived and not be concerned with what they are or what methods i'm really calling.  that's the whole point of inheritance, why even use it if you're going to make that distinction in your head when you type it?

---

### Post by LordHunter317 on 2006-03-01
> **hod139]First, your base class is **not **overloading the parents function (this is really a method, but I will call the methods functions since you named your methods "method"). The parents function "method(void)" is not equal to the extended class' function "method(int)", since the parameters are not equal. This is why a Derived object cannot access the member function in Base.[/quote]No, the two functions are completely different, so it can be accessed.  The issue is one of scoping.

By declaring a group of methods with the same name in the child class, he obscures the methods with the same names in the parent.  The method arguments are ignored in this process.

He can include the parent functions via the using directive.  

This is perfectly valid and logical: we may be extending an interface without overriding an implementation.

Consider:```

#include <string>
struct A {
    void load(std::string &) said:**
> The keyword using should be reserved for namespaces, not classes, especially if you have the classes in separate files.Nope, it's a perfectly cromulent use in thise case.

> That said, here are two ways to write your code without the "using" keyword (critiques welcome).Both ways are broken.  The violate the rule about "easy to use, hard to break."  The former requires the user to go through twisted semantics; the latter is completely brittle.

---

### Post by hod139 on 2006-03-01
Well, learned something new today about the "using declaration" and class members. I had always (incorrectly) assumed the "using" keyword was only for importing namespaces into the current scope. This definitely simplifies the more difficult polymorphic solution I had.

[quote=LordHunter317]
the latter is completely brittle
[/quote] 
What do you mean by "brittle"? All I did was make the base class abstract, and use traditional polymorphism. I could have not made it abstract, and done something like
```

  #include <iostream>
class Base {
    public: 
       void method(void) {
          std::cout << "Base::method(void)" << std::endl;
       }
       virtual void method(int){
          std::cout << "Base::method(int)" << std::endl;
       }
};
 
class Derived: public Base {
   public:
      void method(int) {
         std::cout << "Derived::method(int)" << std::endl;
      }
};

int main() {
   Base * derived = new Derived();

   derived->method(2);
   derived->method();

   delete derived;

   return 0;
} 

```
which is standard polymorphism using virtual members.  Is this less or more brittle?

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=hod139]What do you mean by "brittle"? All I did was make the base class abstract, and use traditional polymorphism.[/quote]It's because now, all variations of method() have to be defined in the base.

This isn't only brittle, it may be impossible.  More importantly, not all descendent classes may support such functionality (e.g., not all may support deserialization from a file), in which case it becomes not only brittle, but incorrect.

> which is standard polymorphism using virtual members.  Is this less or more brittle?For the specific situation purposed, it's still as brittle.

The whole point is that 'method(int)' may not be a property of all child classes of Base, hence, it shouldn't be there.  Working around the name obscuring by adding method(int) to Base is brittle and potentially incorrect.  That's why 'using' can be used to "reimport" Base::method() into a derived class.

---

### Post by hod139 on 2006-03-01
[quote=LordHunter317]
That's why 'using' can be used to "reimport" Base::method() into a derived class.[/quote] 
Now that I'm on the path to enlightenment, what else besides class members can 'using' "reimport" into a derived class? 

Also, what role does class protection play?  In this example I get an error
```

class Base{
   private: void load(float);
   public: void load(int);
};

class D : Base {
    using Base::load; // compilation error since Base::load(float) is private
    void load(void);
};

int main() {}
 
``` 
when I would have expected the[FONT=monospace] load(int) method to become available.
[/FONT]

---

### Post by jerome bettis on 2006-03-01
> **hod139]Now that I'm on the path to enlightenment, what else besides class members can 'using' "reimport" into a derived class? 

Also, what role does class protection play?  In this example I get an error
```

class Base{
   private: void load(float) said:**
>  load(int) method to become available.
[/FONT]

^ wow that's a very good question.  as soon as you put the () in the using stmt it's a syntax error.  i'd like to get stroustrup in here and see if he can answer that one, stuff like this is why c++ needs to go away.  what a mess, you should be able to do that.

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=hod139]Now that I'm on the path to enlightenment, what else besides class members can 'using' "reimport" into a derived class? 

Also, what role does class protection play?[/quote]You can only import a method group you can competely access.  This means that importing load, like in your example, is impossible.  It's an all or nothing thing.

However, if you made load(float) protected or public, it would work.

[quote=jerome bettis]i'd like to get stroustrup in here and see if he can answer that one, stuff like this is why c++ needs to go away.[/quote]Not especially.  It's better than Java, which doesn't provide a solution to this problem.  It isn't as ideal as C#, though.

>  what a mess, you should be able to do that.As a rule, you don't implement this pattern often anyway, so it's not a real issue.

---

### Post by hod139 on 2006-03-01
[quote=LordHunter317]It's better than Java, which doesn't provide a solution to this problem. [/quote] 
What do you mean, I thought Java handles this fine? If the object of the derived class cannot find the method in that class, it searches the parent. Java also has the "super" keyword to access the parents methods directly.

Here is some example Java code and output
```

class Base{
   protected void method() {
    System.out.println("Base::method");
   }
}

class Derived extends Base {
   public void method(int i){
    System.out.println("Derived::method");
   }

   public void method2(){
    super.method();
    System.out.println("Derived::method2");
   }

   public static void main(String[] args){
    Derived derived = new Derived();

        derived.method(2);
    System.out.println();
    derived.method();
    System.out.println();
        derived.method2();
   }
}

``` 

And the output:
```

Derived::method

Base::method

Base::method
Derived::method2

``` 
**Edit:** Just after posting this code, I think I understood what you meant. If I change the Base method to be private, then I still can't access it from the Derived class. Since I can't delete posts, I'll just leave it up.

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=hod139]What do you mean, I thought Java handles this fine?[/quote]Actually, I was mistaken.  It does appear to handle this correctly.

Your sample code is incorrect, because Java methods are virtual by default.  The example is not comparable unless the parent methods are 'final'.

You're confusing overloading across hierarchies with function polymorphism.  With the former, I'm defining a whole new function with the same name.  With the latter, I'm giving a new implementation (method body) to an existing function.

---

### Post by hod139 on 2006-03-01
[quote=LordHunter317]
Your sample code is incorrect, because Java methods are virtual by default.  The example is not comparable unless the parent methods are 'final'.

You're confusing overloading across hierarchies with function polymorphism.  With the former, I'm defining a whole new function with the same name.  With the latter, I'm giving a new implementation (method body) to an existing function.[/quote] 

I didn't think my example (even without the "final" keyword) was using function polymorphism.  The parameter type for Base::method() does not match the parameter type for Derived::method(int i), hence i'm not overriding the parent's method() when I write method(int) in the child class.  When an object of type Derived calls method(), it is actually calling Base::method(), not Derived::method(), since it does not exist in Derived. Therefore, this example is connoting what you called "overloading across hierarchies" and is comparible to the C++ code.  Or am I really missing something?

---

### Post by LordHunter317 on 2006-03-01
No, you're right.  My mind is clearly lost, my apologies.

---

