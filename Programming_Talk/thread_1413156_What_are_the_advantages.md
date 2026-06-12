---
title: "What are the advantages?"
date: 2010-02-22
forum: Programming Talk
---

### Post by Culver on 2010-02-22
What are the advantages of multiple inheritence?

---

### Post by s.fox on 2010-02-22
Hello,

Advantages of multiple inheritances: 

Multiple inheritance allows a class to inherit the functionality of  more than one base class thus allowing for modelling of complex  relationships 

You categorize classes in many ways. Multiple inheritance is a way of  showing our natural tendency to organize the world. During analysis,  for example, we use multiple inheritance to capture the way users  classify objects. 

 By having multiple super-classes, your subclass has more  opportunities to reuse the inherited attributes and operations of the  super-classes. 

Sourced from [here]("http://wiki.answers.com/Q/What_are_the_advantages_of_single_inheritance_over_multiple_inheritance")


-Silver Fox

---

### Post by NovaAesa on 2010-02-22
Class Person
Class Student extends Person.
Class Employee extends Employee.

Class EmployedStudent extends Person and Employee.
This sort of thing can be difficult if you don't have multiple inheritance (although it could be done with adjectival types).

Of course, if you bring repeated inheritance into the mix, you can have something like a DoublelyEmployedStudent (has two jobs and is studying).

---

### Post by CptPicard on 2010-02-22
Don't help him with his homework; it's obvious that all his posts are just homework questions brazenly posted onto the forum. Discussing inheritance is one thing, just a complete "do it for me" is another.

---

### Post by Elfy on 2010-02-22
Closed - homework is not asking others to do the work.

---

