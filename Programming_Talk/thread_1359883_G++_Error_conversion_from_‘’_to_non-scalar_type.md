---
title: "G++ Error: conversion from ‘*’ to non-scalar type"
date: 2009-12-20
forum: Programming Talk
---

### Post by OVERPOWER8 on 2009-12-20
Hello.

I just trying to make an outer function to work with class methods, but i get this error.

functions:  *DoShowInfo*  and *DoChangeAge* do not work properly...  I Don't understand how to make that functions to work. 

Can someone help me?

That's the** class:**

```

class Employee
{
        private:
                int *age;
        public:
                Employee();             ~Employee();
                
                void SetAge(int NewAge) { *age = NewAge; }
                void GetAge() const     { return *age; }
}
 
Employee::Employee()            {       age = new int(27);      }
 
Employee::~Employee()           {       delete age;             }


```[CENTER][B]Functions:
[/B][/CENTER]

```

void DoShowInfo(Employee name)
{
        name.GetAge();
}
 
void DoChangeAge(Employee name, int NewAge)
{
        name.SetAge(NewAge)
}
 
int main()
{
        Employee* Alexander = new Employee();
        ...
        DoChangeAge(Alexander, NewAge);
        DoShowInfo(Alexander);
        ...
        delete Elexander; Alexander = 0;
        ...
}


```

---

### Post by scragar on 2009-12-20
Look over your lessons again on pointers.

For future reference * and & both mean one of two things depending on context:
```
int *age; /// create a pointer that expects ints
foo = *age; /// returns the value of the address stored at age, not the pointer

foo = age & 0x40; // return the age bitwise AND'd with the number 40 in hex.
age = &foo; // set the pointer age to the address of foo.

```

---

### Post by OVERPOWER8 on 2009-12-20
>> [COLOR=Black]**[scragar]("http://ubuntuforums.org/member.php?u=319899")**[/COLOR]


That doesn't fix the problem, I still get the same error.

here:

[I]DoChangeAge(Alexander, NewAge);
        DoShowInfo(Alexander);[/I]

Error: conversion from ‘*’ to non-scalar type

---

### Post by scragar on 2009-12-20
> **OVERPOWER8 said:**
> That doesn't fix the problem, I still get the same error.

Sorry, I hadn't noticed that you had the same sort of problem more than once, you are probably better off reading your chapters on pointers again and attempting to write the code again.
I gave you advice in my edit on what works where, I hope it's helpful.

---

### Post by dwhitney67 on 2009-12-20
Before jumping to a solution, I would like to know why the OP felt compelled to declare the member data 'age' as an int-pointer?

It seems normal that the class would be:
```

class Employee
{
public:
   Employee(int empAge);

   ~Employee();

   inline void setAge(int empAge) { age = empAge; }
   inline int  getAge() const     { return age; }

private:
   int age;
};

```
```

Employee::Employee(int empAge)
   : age(empAge)
{
}

Employee::~Employee()
{
   // nothing to do here.
}

```

---

### Post by OVERPOWER8 on 2009-12-20
>> **[dwhitney67]("http://ubuntuforums.org/member.php?u=322753")**
This is the task and I have almost done it.

---

### Post by OVERPOWER8 on 2009-12-20
**ATTENTION EVERYONE:**

That's how it should look like:

```

#include <iostream>
 
using namespace std;
 
class Employee
{
        private:
                int *age;
        public:                
                Employee()            {       age = new int(27);      } 
                ~Employee()           {       delete age;             }
        void SetAge(int NewAge) { *age = NewAge; }
        int GetAge()                { return *age; }
 
};
 
int DoShowInfo(Employee* name)
{
        return name->GetAge();
}
 
void DoChangeAge(Employee* name, int NewAge)
{
        name->SetAge(NewAge);
}
 
int main()
{
        int NewAge = 17;
        Employee* Alexander = new Employee();
        DoChangeAge(Alexander, NewAge);
        cout << (DoShowInfo(Alexander)) << endl;
        delete Alexander;
}

```

---

### Post by dwhitney67 on 2009-12-20
> **OVERPOWER8 said:**
> **ATTENTION EVERYONE:**

That's how it should look like:
...

I disagree; you do not need to allocate at every corner.  You must've have studied Java before attempting C++.

Why aren't these floating C-style functions not part of the Employee class??
```

int DoShowInfo(Employee* name)
{
        return name->GetAge();
}
 
void DoChangeAge(Employee* name, int NewAge)
{
        name->SetAge(NewAge);
}

```
If you start adopting good programming practices now, not only will they help you with C++, but with other languages too.

On a scale of 0-100%, I rank your code at 66%.

---

### Post by dwhitney67 on 2009-12-20
> **OVERPOWER8 said:**
> >> **[dwhitney67]("http://ubuntuforums.org/member.php?u=322753")**
This is the task and I have almost done it.

BS.  And just because something works, it doesn't mean it was done "right".

---

### Post by grayrainbow on 2009-12-20
> **dwhitney67 said:**
> I disagree; you do not need to allocate at every corner.  You must've have studied Java before attempting C++.

Why aren't these floating C-style functions not part of the Employee class??
```

int DoShowInfo(Employee* name)
{
        return name->GetAge();
}
 
void DoChangeAge(Employee* name, int NewAge)
{
        name->SetAge(NewAge);
}

```
If you start adopting good programming practices now, not only will they help you with C++, but with other languages too.

On a scale of 0-100%, I rank your code at 66%.
It doesn't make sense something call show info to be part of the class which info is supposed to show, don't you think? No matter that in this example that function doesn't do what it says to do :)

@OP, in general, don't pass user define types by value, unless you really want to make copies of them, in which case(in general again) better explicitly write copy constructor(no matter that in this particular example automatic copy constructor will do the work). And yea, don't pas pointers where objects are expected(you got that right) :)
P.S. It won't be bad to return 0 from main(or -42 if you want :D ) :)

---

### Post by dribeas on 2009-12-20
I disagree that this is the way it should be. Also, @dwhitney67 suggested removing the free functions. In some cases having free functions is a nice simple way of extending a class in the least coupling way (when those functions can be implemented only in terms of other already provided public methods), but in your case, Why bother defining a function that will just forward the operation into an exactly equivalent method.

```

class Employee
{
public:
   Employee() : age() {}
   void setAge( int new_age ) { age = new_age; }
   int getAge() const { return age; }
private:
   int age;
};
// in case you did really want to offer the free functions:
void doChangeAge( Employee& employee, int new_age ) {
   employee.setAge( new_age );
}
int doGetAge( Employee const & employee ) {
   return employee.getAge();
}
int main() {
   Employee alexander;
   alexander.setAge( 34 );
   //doChangeAge( alexander, 35 );
   std::cout << "Alexander's age is: " << alexander.getAge() << std::endl;
}

```

You should avoid pointers whenever possible, reduce their use to situations where dynamically allocated memory is required to control object lifetime or for optional parameters or attributes, or when some other situation requires you not to use the stack (huge objects could fill up your stack). Avoiding pointers will make your code simpler to read and understand as well as probably less error-prone.

* How do we convince people that in programming simplicity and clarity —in short: what mathematicians call "elegance"— are not a dispensable luxury, but a crucial matter that decides between success and failure?* — Edgster W. Dijkstra

---

### Post by unknownPoster on 2009-12-20
I'm still questioning the logic behind the integer pointer in the class...

I can't see how it is helpful in this situation at all.

---

