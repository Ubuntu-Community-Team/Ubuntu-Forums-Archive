---
title: "Java Inheritance Confusion"
date: 2008-11-01
forum: Programming Talk
---

### Post by tdrusk on 2008-11-01
The inheritance goes like this.
```
public class Employee {
String name;
int id;
}
```
then
```
public class Doctor extends Employee {
    public String speciality, person, job;
    //Constructor with name, id, and speciality input
    public Doctor(String person, int number, String job){
        name = person;
        id = number;
        speciality = job;
    }
    private String getDoctorService(){
        return speciality;
    }     
    private String getDoctorName(){
        return name;
    }
    public void doctorService(){
        System.out.println(name+"is a "+job+" doctor");
    }    

    }
```
then 
```

public class Hospital extends Employee{

    public static void main (String args[]) {        
        Doctor doctor = new Doctor(Michael, 123,Heart);
    }
}

```

Now, all compile accept the last. I'm not exactly sure how to get it to use the Doctor class, along with some other classes in the same level of inheritance as the Doctor class.
Help please?

---

### Post by CptPicard on 2008-11-01
> **tdrusk said:**
> Now, all compile accept the last.

Now, if you showed us the compiler error I am sure we'd see that you're not importing Doctor from whatever package you put it into. :) What is your source code directory structure and package definitions? They are missing from code.

>  I'm not exactly sure how to get it to use the Doctor class, along with some other classes *in the same level of inheritance *as the Doctor class.

Hmm... I get the weird feeling you're confusing packages and inheritance...

---

### Post by tdrusk on 2008-11-01
> **CptPicard said:**
> Now, if you showed us the compiler error I am sure we'd see that you're not importing Doctor from whatever package you put it into. :) What is your source code directory structure and package definitions? They are missing from code.



Hmm... I get the weird feeling you're confusing packages and inheritance...
I might be. I'm not sure. 

Basically, I have the employee class. Under it is the Doctor class along with nurse, administrator, and receptionist. To test  the implementation I have to use the hospital class.

I just noticed the word "implementation". How would that come into play?

EDIT: just added a picture

---

### Post by CptPicard on 2008-11-01
Well, to be sure you could post the compiler error and your source tree structure... are all classes in the same directory? They should be, you're using the default package in all of them.

---

### Post by tdrusk on 2008-11-01
Excuse my ignorance, but I don't know what to do when you ask me to show you my source tree.

errors
```
/Doctor.java:5: interface expected here
public class Doctor implements Employee {
                               ^
Hospital.java:26: cannot find symbol
symbol  : variable Michael
location: class Hospital
        Doctor doctor = new Doctor(Michael, 123,Heart);
                                   ^
Hospital.java:26: cannot find symbol
symbol  : variable Heart
location: class Hospital
        Doctor doctor = new Doctor(Michael, 123,Heart);
                                                ^
./Doctor.java:9: cannot find symbol
symbol  : variable name
location: class Doctor
        name = person;
        ^
./Doctor.java:10: cannot find symbol
symbol  : variable id
location: class Doctor
        id = number;
        ^
./Doctor.java:17: cannot find symbol
symbol  : variable name
location: class Doctor
        return name;
               ^
./Doctor.java:20: cannot find symbol
symbol  : variable name
location: class Doctor
        System.out.println(name+"is a "+job+" doctor");
                           ^
7 errors

```

---

### Post by Delever on 2008-11-01
> **tdrusk said:**
> The inheritance goes like this.
```
public class Employee {
String name;
int id;
}
```
then
```
public class Doctor extends Employee {
    public String speciality, person, job;
    //Constructor with name, id, and speciality input
    public Doctor(String person, int number, String job){
        name = person;
        id = number;
        speciality = job;
    }
    private String getDoctorService(){
        return speciality;
    }     
    private String getDoctorName(){
        return name;
    }
    public void doctorService(){
        System.out.println(name+"is a "+job+" doctor");
    }    

    }
```
then 
```

public class Hospital extends Employee{

    public static void main (String args[]) {        
        Doctor doctor = new Doctor(Michael, 123,Heart);
    }
}

```

Now, all compile accept the last. I'm not exactly sure how to get it to use the Doctor class, along with some other classes in the same level of inheritance as the Doctor class.
Help please?

Idea with inheritance is this:

If you have group of of objects, which behave in same way, you can inherit them from same base object.

For example, i know i can get name of any employee. That employee class has a method to get name. So if I inherit doctor as employee, i don't need to write new method to get name.

Now I am going to change your code somewhat (and Hospital probably should not be based on employee):

```

public class Employee {
    protected String name; // protected fields are visible in inherited class
    protected int id;

    public Employee(int id, String name)
    {
        this.id = id; // "this" ensures you refer to class variable, and not method variable, so you can asign incoming "id" to private "id" in class
        this.name = name;
    }

    // now, its logical to write method to get name here, so any class which is going to inherit this one, will have this method (Doctor)
    public String GetName()
    {
        return this.name;
    }

    public int GetId()
    {
        return this.id;
    }
}

```

```
public class Doctor extends Employee {
    protected String speciality, job;

    //Constructor with name, id, and speciality input
    public Doctor(int id, String name, String job, String speciality){
        // now, we extended Employee here; so we can call
        // Employee constructor like this:
        super(id, name); // and pass id with name

        // job and speciality, however, are unique to this class,
        // so we asign them here
        this.job = job;
        this.speciality = speciality;
    }

    private String getDoctorService()
    {
        return this.speciality; // "this" is optional here
    }

    private String getDoctorJob()
    {
        return this.job;
    }
   
    // we no longer need to write method to get name; it exists in Employee
    /*private String getDoctorName(){ 
        return name;
    }*/

    // say more clearly what method does; this one prints object properties
    /*public void printDoctorService(){
        System.out.println(name+"is a "+job+" doctor");
    }    */

    // however, if I remember right, java has ToString() method for that:
    
    public String ToString()
    {
        return name + " is a " + job +" doctor";
    }
}

```

```

public class Hospital 
{
    public static void main (String args[]) {        
        Employee employee = new Doctor(123, "Michael", "MD", "Heart");
        System.out.println(employee.ToString());
    }
}

```

EDIT: i had no time to check if it compiles, but i fixed few mistakes for sure

EDIT2: changed fields from private to protected

EDIT3: get to know how inheritance works, but use it only when it is really necessary; it can get very confusing.

---

### Post by Tomosaur on 2008-11-01
> **tdrusk said:**
> The inheritance goes like this.
```
public class Employee {
String name;
int id;
}
```then
```
public class Doctor extends Employee {
    public String speciality, person, job;
    //Constructor with name, id, and speciality input
    public Doctor(String person, int number, String job){
        name = person;
        id = number;
        speciality = job;
    }
    private String getDoctorService(){
        return speciality;
    }     
    private String getDoctorName(){
        return name;
    }
    public void doctorService(){
        System.out.println(name+"is a "+job+" doctor");
    }    

    }
```then 
```

public class Hospital extends Employee{

    public static void main (String args[]) {        
        Doctor doctor = new Doctor(Michael, 123,Heart);
    }
}

```Now, all compile accept the last. I'm not exactly sure how to get it to use the Doctor class, along with some other classes in the same level of inheritance as the Doctor class.
Help please?

Ok, a few things:

It is probably bad form to make your main class anything other than basically a stub. Maybe it's just me - Java will certainly allow you to do it, but do you want your main class to be inheriting the fields and methods of the Employee class? A hospital is not an employee of itself, right?

Secondly: Although Java does implicitly call the super-constructor, you might want to explicitly call it yourself if you're just starting out with inheritance, to make life easier on yourself (The 'super constructor' is the constructor of the class you're inheriting from). It must always be the first call in the constructor of the inheriting class. To call the super constructor, you just use 'super();'. If your super-class has overloaded constructors, then you would just call it like this: 'super(a, b, c);'. Java only ever implicitly calls the empty constructor, however.

Now, to help you with your actual question, your 'Doctor' class constructor takes a string, an int, and a string:
```

  public Doctor(String person, int number, String job){...}

```You are instantiating the Doctor class like this (in your main class):
```

  public static void main (String args[]) {        
      Doctor doctor = new Doctor(Michael, 123,Heart);
  }

```Look carefully. How do you define strings in Java?

---

### Post by jespdj on 2008-11-01
First, you show us code where Doctor **extends** Employee. Then you show us your compiler error, which indicates that in your code you really wrote: Doctor **implements** Employee.

Post your actual code, otherwise it's going to be difficult to help you.

In Java, "implements" is for implementing interfaces, "extends" is for extending classes.

Furthermore, what's really strange in the design of your program is that class Hospital extends Employee. Inheritance (extending a class) implies that there is an "is a" relationship between the subclass and the superclass.

So if you write "Hospital extends Employee", what you're saying is that a Hospital **is an** Employee. That's kind of strange...

See [Interfaces and Inheritance](http://java.sun.com/docs/books/tutorial/java/IandI/index.html) in Sun's Java Tutorials to learn more about this.

---

### Post by pmasiar on 2008-11-01
> **tdrusk said:**
> 
```
public class Doctor extends Employee {
    public String speciality, person, job;
    //Constructor with name, id, and speciality input
    public Doctor(String person, int number, String job){
        name = person;
        id = number;
        speciality = job;
    }

```


It's painful to see code like this. If you can get to use keyword 'this', your code can be much cleaner:
```
public class Doctor extends Employee {
    public String speciality, person, job;
    //Constructor with name, id, and speciality input
    public Doctor(String name, int id, String speciality){
        this.name = name;
        this.id = id;
        this.speciality = speciality;
    }

```

So you don't have to invent so many names, and you see that you assign free variables (input parameters) to class attributes.

Also, your clas diagram is wrong: hospital cannot inherit from different types of emlpoyees, it just yses them. Fromt it's shape it is impossible (in Java), it's called 'diamond of death': no way to inherit from multiple classes.

---

### Post by tdrusk on 2008-11-02
Thanks guys. I am going to work with it later on today. I appreciate the guidance.

---

### Post by drubin on 2008-11-02
> **pmasiar said:**
> It's painful to see code like this. If you can get to use keyword 'this', your code can be much cleaner:
```
public class Doctor extends Employee {
    public String speciality, person, job;

```


I would also recommend not declaring all your vars on one line it is very hard to read. This is the preferred way of coding. you would also change the access with out having to move a lot of things around. 
```
public class Doctor extends Employee {
    public String speciality;
    public String person;
    public String job;

```

---

