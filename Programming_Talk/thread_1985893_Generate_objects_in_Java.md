---
title: "Generate objects in Java"
date: 2012-05-23
forum: Programming Talk
---

### Post by Triblaze on 2012-05-23
I'm working on a little project that stores student information. For the sake of the simplicity of my explanation, let's say it's a telephone book. Each person is an object, with several properties, name, number, address, etc. I'm making a GUI that manages it, or at least adds entries. I know you generate a class with:
Person bob = new Person(arguments);

But if I want to give the program the ability to generate new entries, essentially an infinite amount, how would I do this? So that if [String name] is the name, I could initial the object with:

```
while(true) {
name=in.next();
if (button.isPressed()) {
Person [name] = new Person(arguments);
}
}
```"name" is a variable that could be set in the GUI, and then I could hit a button and it would create a new object, called [name], with the attributes I set. So I enter Alice and it generates the object Alice, and then Bob generates Bob, all the way to Zula and beyond. But from what I've tried and found, you have to have a set name for the instance of the class you make, you can't use a variable or have the program generate new ones while running. How would I accomplish this?

Or should I just make a ton of instances and have them filled in as needed, even though it's technically limited then?

---

### Post by Some Penguin on 2012-05-24
Require or generate a unique identifier, then use that to index in something like a HashMap.

---

### Post by Triblaze on 2012-05-24
> **Some Penguin said:**
> Require or generate a unique identifier, then use that to index in something like a HashMap.
New-ish to Java, can you put this in simpler terms? Or at least post an example code, doesn't have to be too complex, just a basic structure. I can probably pick up the concept from that.

---

### Post by ofnuts on 2012-05-24
> **Triblaze said:**
> I'm working on a little project that stores student information. For the sake of the simplicity of my explanation, let's say it's a telephone book. Each person is an object, with several properties, name, number, address, etc. I'm making a GUI that manages it, or at least adds entries. I know you generate a class with:
Person bob = new Person(arguments);

But if I want to give the program the ability to generate new entries, essentially an infinite amount, how would I do this? So that if [String name] is the name, I could initial the object with:

```
while(true) {
name=in.next();
if (button.isPressed()) {
Person [name] = new Person(arguments);
}
}
```"name" is a variable that could be set in the GUI, and then I could hit a button and it would create a new object, called [name], with the attributes I set. So I enter Alice and it generates the object Alice, and then Bob generates Bob, all the way to Zula and beyond. But from what I've tried and found, you have to have a set name for the instance of the class you make, you can't use a variable or have the program generate new ones while running. How would I accomplish this?

Or should I just make a ton of instances and have them filled in as needed, even though it's technically limited then?
```

List <Person> allPersons=new ArrayList();
while(true) {
   name=in.next();
   if (button.isPressed()) {
     Person person= new Person(arguments);
     allPersons.add(person);
   }
}

```
(Check the actual syntax)

---

### Post by Triblaze on 2012-05-24
> **ofnuts said:**
> ```

List <Person> allPersons=new ArrayList();
while(true) {
   name=in.next();
   if (button.isPressed()) {
     Person person= new Person(arguments);
     allPersons.add(person);
   }
}

```(Check the actual syntax)
Thanks, I managed to contact a friend who knows some and he suggested basically this. One thing I forgot to mention though is that there are multiple objects, Student is a subclass of Person, CollegeStudent is a subclass of Student, and Teacher is a subclass of Person. So how do I initialize the arraylist if there are multiple objects? Still use Person because it's the super? I'm not quite sure how to do the initialization, I just left it as:
ArrayList list = new ArrayList();
So it gives me a warning that ArrayList is not parametrized.

*I tried just using Person and it seems to work. Still managing out a few odd errors. Thanks for the help!

---

### Post by ofnuts on 2012-05-25
> **Triblaze said:**
> One thing I forgot to mention though is that there are multiple objects, Student is a subclass of Person, CollegeStudent is a subclass of Student, and Teacher is a subclass of Person. So how do I initialize the arraylist if there are multiple objects? Still use Person because it's the super? Exactly... you will have to downcast to Student/Teacher or whatever if you want to use attributes/methods specific to these classes.

---

