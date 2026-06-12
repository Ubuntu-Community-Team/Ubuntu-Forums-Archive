---
title: "Forward declaration of a class member"
date: 2011-09-06
forum: Programming Talk
---

### Post by erotavlas on 2011-09-06
Hi,

I have a question about a forward declaration. I have two classes A and B. The A class need to include the definition of the class B (classB.h) i.e. I can't use a forward declaration. While in the class B file I use a forward declaration for the class A to prevent a circular inclusion. I need to use the declaration of a public member of class A (A::PublicMember) but the compiler says that the member is not defined. How can overcome this problem?

Thank you

---

### Post by PaulM1985 on 2011-09-06
So, if I understand correctly, you have two classes which each must know (have a reference) to each other.  Lets assume you have a Teacher and Student class.  Each Teacher teaches some Students and each Student knows who its Teacher is.

You could have classes like this:

Teacher.h
```

#include "Student.h"  // <- Include the Student class here
class Teacher
{
 public:
   Teacher();
   ~Teacher();

private:
  std::vector<Student> m_Students;
};

```

Student.h
```

class Teacher; // <- Forward declare teacher
class Student
{
public:
  Student (Teacher *pTeacher);
  ~Student();
private
  Teacher *m_pTeacher;
};

```

Teacher.cpp
```

#include "Teacher.h" // <- Only need to include Teacher.h because this includes Student.h

// Implementation

```

Student.cpp
```

#include "Teacher.h" // <- This includes Student

// Implementation

```

Since Student needs to reference Teacher and Teacher needs to reference Student, one of the references in one of the definitions needs to be a pointer.  This is because in your class definition it needs to work out how much memory should be allocated for your class.

If you have:
```

class A
{
private:
  B m_b;
};

class B
{
private:
  A m_a;
};

```

and consider the case of class B in terms of the amount of memory required, B needs enough memory to accomodate class A which needs enough memory to accomodate class B, which needs enough memory to accomodate class A etc etc etc...

Hopefully this is clear.

Paul

---

### Post by erotavlas on 2011-09-06
Hi,

Thank for your fast answer. I'm not explained correctly. This is my case:

Teacher.h

```

#include "Student.h"  // <- Include the Student class here

 class Teacher {  
public:   
typedef std::vector<std::string> M_Students;   

 Teacher();   
 ~Teacher();

Function(const Student::Data& data)
{
// do something
}
  private:  
 M_Students m_Students;
 };

```

and Student.h

```

class Teacher; // <- Forward declare teacher

 class Student { 

public: 
typedef std::map<std::string, int> Data;

  Student ();   
~Student();

Function(const M_Students& m_students)
{
}

private:
Data data;

 };

```So the compiler can find all it need to compile the class Teacher, but it can't find M_Students declaration when it compiles the class Student. How can I solve it?

Thank you

---

### Post by PaulM1985 on 2011-09-06
Put the typedef for M_Student in student.h.

Paul

---

### Post by karlson on 2011-09-06
> **erotavlas said:**
> Hi,

Thank for your fast answer. I'm not explained correctly. This is my case:

Teacher.h

```

#include "Student.h"  // <- Include the Student class here

 class Teacher {  
public:   
typedef std::vector<std::string> M_Students;   

 Teacher();   
 ~Teacher();

Function(const Student::Data& data)
{
// do something
}
  private:  
 M_Students m_Students;
 };

```

and Student.h

```

class Teacher; // <- Forward declare teacher

 class Student { 

public: 
typedef std::map<std::string, int> Data;

  Student ();   
~Student();

Function(const M_Students& m_students)
{
}

private:
Data data;

 };

```So the compiler can find all it need to compile the class Teacher, but it can't find M_Students declaration when it compiles the class Student. How can I solve it?

Thank you

```

typedef std::vector<std::string> M_Students;

class Teacher
{
   // declaration
};

class Student
{
  //  declaration
};

```

Why make it more complicated?

---

### Post by erotavlas on 2011-09-06
The name M_Student is misleading. I have two typedef one per class and I need to use it from the other class.
The only way is to put the typedef out of the class?

---

### Post by PaulM1985 on 2011-09-06
A potential solution:

Data.h
```

typedef std::vector<std::string> M_Students;   
typedef std::map<std::string, int> Data;

```

Teacher.h
```

#include "Data.h"
 class Teacher {  
public:   

 Teacher();   
 ~Teacher();

Function(const Data& data)
{
// do something
}
  private:  
 M_Students m_Students;
 };

```

Student.h
```

#include "Data.h"
class Student { 

public: 

  Student ();   
~Student();

Function(const M_Students& m_students)
{
}

private:
Data data;

 };

```

However, your program structure seems odd.  Why should a function in the Teacher class take information which is belonging to a Student.  Shouldn't a Student be passed into the "Function" in the Teacher class?  Similarly, why should member data of a Teacher be passed into "Function" on the Student class?  Shouldn't a Teacher be passed in in this case?

Look up Laws of Demeter: [http://en.wikipedia.org/wiki/Law_of_Demeter](http://en.wikipedia.org/wiki/Law_of_Demeter)

Paul

---

### Post by erotavlas on 2011-09-07
Hi,

Let me to explain my case. I have three class: one class A owns a map of the class C, the class C contains a pointer to the last class B. First I need to construct the class A and class C and after I need to construct the class B. To construct the class B I need some informations of the elements contained in the class A (C). After I have to link the class C pointer to the correspondent element in the class B.

This is the A class
```

class A {
public:

typedef std::map<std:string, C> MyMap;
class A();
~class A();

LinkFunction(const B::ElementMap elementMap) {

}

private:
MyMap myMap;
};

```The B class
```

class B {
public:

typedef std::map<std:string, class C> ElementMap;
class B(const A::MyMap myMap); // it use myMap to build the elementMap
~class B();

private:
ElementMap elementMap;
};

```and the C class contained in the myMap of the class A. It contains a pointer to the class B.
```

class C {
public:

class C();
~class C();

private:
B* b;
};

```
How can I solve it?

---

### Post by dwhitney67 on 2011-09-07
> **erotavlas said:**
> 
How can I solve it?

Are you asking advice how to fix an error generated by the compiler, or are you asking for advice on how to design your classes?

If it is a compiler error, then don't you think it would be wiser to a) post your complete code, and b) post the actual error that is generated.

If you are seeking advice on a better design, then it would be better if you described the *problem* you are trying to solve... not describe how you *want* it solved.  As far as I can tell (and this was mentioned previously), you are headed towards designing a new strand of spaghetti.

---

### Post by nvteighen on 2011-09-07
My eyes!!!

Ok, "A, B, C" sounds fine when Sheila E. plays *Glamorous Life* live (no, do not mention Rihanna's cover)... But when it comes to classes, letters are the most uninformative names for classes, specially when no implementation tells us what the whole thing is actually designed for.

The easiest thing to do would be to create a single header that forward-declared all three classes.

I agree with dwhitney67 and along with him, I ask you to tell us what problem are you trying to solve.

---

### Post by karlson on 2011-09-07
> **erotavlas said:**
> Hi,

Let me to explain my case. I have three class: one class A owns a map of the class C, the class C contains a pointer to the last class B. First I need to construct the class A and class C and after I need to construct the class B. To construct the class B I need some informations of the elements contained in the class A (C). After I have to link the class C pointer to the correspondent element in the class B.

This is the A class
```

class A {
public:

typedef std::map<std:string, C> MyMap;
class A();
~class A();

LinkFunction(const B::ElementMap elementMap) {

}

private:
MyMap myMap;
};

```The B class
```

class B {
public:

typedef std::map<std:string, class C> ElementMap;
class B(const A::MyMap myMap); // it use myMap to build the elementMap
~class B();

private:
ElementMap elementMap;
};

```and the C class contained in the myMap of the class A. It contains a pointer to the class B.
```

class C {
public:

class C();
~class C();

private:
B* b;
};

```
How can I solve it?

@dwhitney67 & @nvteighen +1

I suggest you step back and redesign your solution and think about the objects you are trying to describe and types.

You have 2 types defined inside class A and class B that are the same, so define it outside the class there is nothing wrong with

typedef <something> my_type;
typedef my_type my_other_type;

If you are designing a Student->Teacher->class interaction then design something like: School has Classes, Classes have Teachers, Classes have Students, and if you need to have relationship of Teachers to Classes and Students to classes then School can contain maps of ones to the others.

In general I would suggest avoiding circular relationships of classes unless there is no other choice.

---

