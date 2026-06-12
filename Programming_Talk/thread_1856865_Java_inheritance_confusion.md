---
title: "Java inheritance confusion"
date: 2011-10-09
forum: Programming Talk
---

### Post by orrymr on 2011-10-09
So, I have the following code:
```

class Person{
    String name;

    Person(String name){
        this.name = name;
    }    
}

class Student extends Person{
    String studentNum;    
    
    Student(String name, String studentNum){
        super(name);    
        this.studentNum = studentNum;
    }
}

public class example2{
    public static void main(String[] args){
        Person bob = new Person ("Bob");
        Person tom = new Student ("Tom", "abc123");
        
        System.out.println(bob.name);//prints out bob's name
        System.out.println(tom.name);//prints out Tom's name
        System.out.println(tom.studentNum);//Will print an error
    }
}

```Now both bob and tom are persons, but I've instantiated tom using new student, so therefore he can have the studentNumber attribute, but when I print out his student number, as I expected, there is an error, because he is of type Person. If I want to access the subclass' methods/variable I have to perform a cast.

My question is, why is java like this? I've told it that tom is of type 'Person' yet I can use the Student type to finish off my declaration? If I go (tom instanceof Student) I get a result of true, yet I can't make tom behave like a student without an explicit cast.

---

### Post by cgroza on 2011-10-09
All statically typed OOP languages are like this. C++ is the same. It happens because this is how sub-type polymorphism  works.

You declared it as of type Person and you assigned a Student to it.
Since the reference is of type Person, and not Student, you can use only the Person's interface through it.

Hope this helped.

---

### Post by ofnuts on 2011-10-09
> **orrymr said:**
> So, I have the following code:
```

class Person{
    String name;

    Person(String name){
        this.name = name;
    }    
}

class Student extends Person{
    String studentNum;    
    
    Student(String name, String studentNum){
        super(name);    
        this.studentNum = studentNum;
    }
}



public class example2{
    public static void main(String[] args){
        Person bob = new Person ("Bob");
        Person tom = new Student ("Tom", "abc123");
        
        System.out.println(bob.name);//prints out bob's name
        System.out.println(tom.name);//prints out Tom's name
        System.out.println(tom.studentNum);//Will print an error
    }
}

```Now both bob and tom are persons, but I've instantiated tom using new student, so therefore he can have the studentNumber attribute, but when I print out his student number, as I expected, there is an error, because he is of type Person. If I want to access the subclass' methods/variable I have to perform a cast.

My question is, why is java like this? I've told it that tom is of type 'Person' yet I can use the Student type to finish off my declaration? If I go (tom instanceof Student) I get a result of true, yet I can't make tom behave like a student without an explicit cast.

Because for Java your variable "tom" holds a Person, not a Student. OK, in your code the contents are a Student, but you could be calling some method in some other class that returns a plain Person and there would be no way to tell at compile time what the contents of tom would be...  So, yes, instanceof and cast are the solution, but this is the symptom of bad design... You shouldn't be in a situation where the code that handles Persons must know if these Persons are Students or not. In good object design, the users of class instances shouldn't care about the actual content/type of the objects they handle, they just ask them to perform operations (methods) that said instances perform possibly in a class-dependent way (overloaded methods). For instance:

```

public class VirtualMethodDemo
{
    private static class Dog
    {
        Dog()
        {
            // Empty constructor
        }
        
        void bark()
        {
            System.out.println("Wah!");
        }
        
        void wagTailAndBark()
        {
            System.out.println("{wagging tail}");
            bark();
        }    
    }   
     
    private static class BigDog extends Dog
    {
        BigDog()
        {
            super();
        }
        
        void bark()
        {
                System.out.println("Woof!");
        }
    }
    
    public static void main(String[] args)
    {
        Dog dog;
        System.out.println("---------");
        dog=new Dog();
        System.out.println("Dealing with a "+dog.getClass().getName());
        dog.wagTailAndBark();
        System.out.println("---------");
        dog=new BigDog();
        System.out.println("Dealing with a "+dog.getClass().getName());
        dog.wagTailAndBark();
    }
}

```

PS: And you shouldn't have public attributes either.

---

### Post by orrymr on 2011-10-10
Yeah, it was just a toy example.
Maybe a benefit of this approach could be if you had several classes extending human, say student along with, chef and doctor. Now, if you wanted to you could create an array of variables declared as humans (but are assigned as either doctor, chef or student), and have easy access to these different humans in one array, by simply using instanceof and a cast?

---

### Post by ofnuts on 2011-10-10
> **orrymr said:**
> Yeah, it was just a toy example.
Maybe a benefit of this approach could be if you had several classes extending human, say student along with, chef and doctor. Now, if you wanted to you could create an array of variables declared as humans (but are assigned as either doctor, chef or student), and have easy access to these different humans in one array, by simply using instanceof and a cast?
Yes,  but in general, the whole idea of OO design is that the code handling the array shouldn't need to know the actual type of data it handles, beyond the "Person". Some other part of the application may add new types and as long as they are derived classes of Person the original code handling the array should run properly. Normally, class attributes are private, so the outer code cannot access them directly. The lonly thing this outer code can see and use is the public methods, and these can be overloaded by derived classes. In your toy exemple that would mean that class Person has a "print()" method that prints the name by default, and that class Student overloads it with its own print() method that also prints the student number. So the outer code calls print() on every array element and doesn't need to know more aboutt the array elements.

---

