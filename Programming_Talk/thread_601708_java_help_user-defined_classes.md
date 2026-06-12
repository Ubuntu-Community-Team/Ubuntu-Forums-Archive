---
title: "java help: user-defined classes"
date: 2007-11-03
forum: Programming Talk
---

### Post by dbbolton on 2007-11-03
luckily, i have realized that i hate programming so i'm not studying CS anymore after this semester. however, for now i still have a programming assignment to do.

i need some help with user defined classes.

i am given the class Person, and i have to do the following:

  	 	 	 	 	 	 	 	 	-Check whether a given last name 		is the same name as the last name of this person
-Check whether a given first name 		is the same name as the first name of this person
-Check whether a given middle name 		is the same name as the middle name of this person
	-Employ a method called [FONT=DejaVu Sans Mono, sans-serif][SIZE=2]equals[/SIZE][/FONT] 	that returns true if two objects contain the same first and last 	name
-Employ a method called  [FONT=DejaVu Sans Mono, sans-serif][SIZE=2]makeCopy[/SIZE][/FONT] 	that copies the instance variables of a [FONT=DejaVu Sans Mono, sans-serif][SIZE=2]Person[/SIZE][/FONT] 	object into another [FONT=DejaVu Sans Mono, sans-serif][SIZE=2]Person[/SIZE][/FONT] 	object
-Employ a method called [FONT=DejaVu Sans Mono, sans-serif][SIZE=2]getCopy[/SIZE][/FONT] 	that creates and returns the address of the object, which is a copy 	of another [FONT=DejaVu Sans Mono, sans-serif][SIZE=2]Person[/SIZE][/FONT] 	object.

there were other tasks that i already added as well, so this is what we have:

```

public class Person
{
    private String firstName; //store the first name
    private String middleName; //store the middle name 
    private String lastName;  //store the last name

    //default constructorwrw
    public Person()
    {
        firstName = "";
        middleName = "";
        lastName = "";
    }
    
    //copy constructor
    public Person(Person otherPerson)
    {
        firstName = otherPerson.firstName;
        middleName = otherPerson.middleName;
        lastName = otherPerson.lastName;
    }
    
    //create a person with a given first and last name
    public Person(String first, String last)
    {
        setName(first, last);
    }
    
    //create a person with a given first, middle, and last name
    public Person (String first, String middle, String last)
    {
        setName(first, middle, last);
    }
    
    //turn the full name into a string
    public String toString()
    {
        return (firstName + " " + middleName + " " + lastName);
    }
    
    //set the first name of a person
    public void setFirstName(String first)
    {
        firstName = first;
    }
    
    //set the middle name of a person
    public void setMiddleName(String middle)
    {
        middleName = middle;
    }
    
    //set the last name of a person
    public void setLastName(String last)
    {
        lastName = last;
    }
    
    //set both the first and last names of a person
    public void setName(String first, String last)
    {
        firstName = first;
        lastName = last;
    }
    
    //set the first, middle, and last names of a person
    public void setName(String first, String middle, String last)
    {
        firstName = first;
        middleName = middle;
        lastName = last;
    }
    
    //get the first name of a person
    public String getFirstName()
    {
        return firstName;
    }
    
    //return the middle name of a person
    public String getMiddleName()
    {
        return middleName;
    }
    
    //return the las name of a person
    public String getLastName()
    {
        return lastName;
    }
    
}

```

when i tried to create the "equals" method, i got a ton of errors. as for the copying tasks, i added the copy constructor but i'm not sure how to use it.

i don't want someone to simply do this for me, because i actually want to learn how to do it. so, some guidance to set me in the right direction would be greatly appreciated.

---

### Post by CptPicard on 2007-11-03
> **dbbolton said:**
> luckily, i have realized that i hate programming so i'm not studying CS anymore after this semester. however, for now i still have a programming assignment to do.

Oh! I hate programming too and I have my Master's! Programming is mostly Menial Labour, but as an undergrad you will have to learn it in order to use it as a tool later on when you must, but the most interesting CS stuff is perfectly doable with your mind, pencil and paper, unless you're into testing stuff with simulation. Even then, your code is allowed to be ugly, because it's an academic exercise... as long as it works :)

Trust me, the fun stuff is yet to come. Then again, if you're stuck already by this point...

First of all, get the equals method working, you're going to want it. I'd like to see your errors, but I suspect it is because equals has to be implemented to take Object. So inside the method, your first task is usually to check whether your parameter Object o is an "instanceof" Person (ok, your FIRST task REALLY is usually checking for reference equality). If it is, you can then start comparing field by field -- and because your fields are Strings, you'll be asking the String equals() method for String equality.

The copying methods are simple, you just instantiate a new Person and set the fields to match what you have in your original object, right?

---

### Post by dbbolton on 2007-11-03
I agree with you on that. I think certain parts of CS are interesting, like algorithm design. I just can't get past the programming, so I decided to be an English major :)

I think I figured part of it out. Here is what I tried as "equals" method:

```
public boolean equals(Person otherPerson)
    {
        return(firstName == otherPerson.firstName
               && lastName == otherPerson.lastName);
    }

```

Does that seem right?

---

### Post by CptPicard on 2007-11-03
Check this out for a fast Googled reference: [http://www.javapractices.com/Topic17.cjp](http://www.javapractices.com/Topic17.cjp)


No, it does not seem right, because you're making the fundamental reference comparison vs. equals-equality mistake. This is why the equals() method really exists... mind you, in your case, what you are doing might actually seem like working for a while, but only for as long as your entire system has a single instance of each literal string.

The point is that if you can actually have separate objects, say x and y, of String that all contain, say, "ABC". For them, the reference comparison x == y will actually return false, as they are separate objects in memory. However, x.equals(y) and y.equals(x) is supposed to return true, as they are the same string by their contents!

What you want to be returning for an equals value is thus a delegation to the String equals method:

```

return firstName.equals(otherPerson.firstName) && lastName.equals(otherPerson.lastName);

```

---

### Post by dbbolton on 2007-11-03
that's funny, because i copied that idea from an example in my textbook, which was an "equals" method for two members of a predefined "Clock" class:

```

public boolean equals(Clock otherClock)
    {
        return(hr == otherClock.hr
               && min == otherClock.min
               && sec == otherClock.sec);
    }

```

so, did the book just give a poor example? (i wouldn't be surprised. i've found errors in it before.)

---

### Post by CptPicard on 2007-11-03
The Clock's members probably aren't objects, but primitives such as int's. They can be compared directly like that. Objects can't, because the value of an "object variable" is actually a *reference*... essentially a memory address (a pointer, in C terms) that is used to access the object at that location.

An object is anything you initialize with a "new", in general... with String being a nasty little exception.... So... if you've got a 

```

String a = "Hello world!";  // could easily be written explicitly as new String("Hello world!");
String b = "Hello world!";

```

Then a == b will be false (they are two separate objects, references a and b point to separate memory locations) but a.equals(b) will be true (they are the same string by value) but

```

int x = 5;
int y = 5;

x == y  // This is true!

String c = a;

c == a  // this is true, as c now "points to" the same object as a
c.equals(a); c.equals(b);  // these are, of course, true  as values are the same

```

---

### Post by dbbolton on 2007-11-03
ah! now that you mention it, i (vaguely) remember talking about it in class. so, now i understand why the first idea doesn't work.

another part of the assignment was to write a small program to test the class Person. here is what i wrote:

```

import java.util.*;

class TestPerson
{
    public static void main(String [] args)
    {
        Scanner in = new Scanner(System.in);
        
        Person person1 = new Person(Daniel, Barrett, Bolton);
        Person person2 = new Person();
        
        String first, middle, last;
        
        System.out.print("Person1: ");
        person1.printName();
        System.out.println();
        
        person2.setName(Wolfgang, Amadeus, Mozart);
        
        System.out.print("After setting the name, person2: ");
        person2.printName();
        System.out.println();
        
        if (person1.equals(person2))
        {
            System.out.println("The two persons are equal.");
        }
        else
            System.out.println("The two names are not equal.");
            
        System.out.println("Enter a first name.");
        first = in.next();
        
        System.out.println("Enter a middle name.");
        middle = in.next();
        
        System.out.println("Enter a last name.");
        last = in.next();
        
        person1.setName(first, middle, last);
        
        System.out.print("New name of person1: ");
        person1.printName();
        System.out.println();
        
        person2.makeCopy(person1);
        System.out.println("After copying person1 into person2," +
                           " person2: ");
        person2.printName();
        System.out.print("\n\n The program is finished.");
    }//end main
    
}//end class

```

when i tried to compile it (i'n using Geany) it said that virtually all of the variables can't be resolved. any idea why?

---

### Post by CptPicard on 2007-11-03
Wonder what you mean by "virtually all variables"; seeing the error dump might enlighten. It does sound like some sort of a classpath issue, but nothing in your code seems obviously wrong, really.

Btw, a good analogy with your W.A. Mozart "Person" and reference-comparing == and value-comparing equals() is that == compares for the *same person* (there are just distinctly separate individual people), while equals() tells whether some two people *have the same name* (you could conceivably have some other guy called W.A. Mozart).

---

### Post by dbbolton on 2007-11-03
i would have posted the errors, but for some reason geany only allows one to copy one line at a time-- you can't just highlight all of the output at once. you just have to right click on a line and click copy.

here is the output from the compiler:

[http://i103.photobucket.com/albums/m128/envyouraudience/err1.png](http://i103.photobucket.com/albums/m128/envyouraudience/err1.png)
[http://i103.photobucket.com/albums/m128/envyouraudience/err2.png](http://i103.photobucket.com/albums/m128/envyouraudience/err2.png)

---

### Post by CptPicard on 2007-11-03
I get the vague impression that Geany doesn't run javac with any kind of a classpath set. Can you compile anything from there? What about from command line... like "javac PersonTest.java", and then "java PersonTest"...

And which Java do you have? gcj or Sun? The gcj one is a PITA...

---

### Post by dbbolton on 2007-11-03
it's odd. on my other computer, i used geany to write a program that compiled without anys errors, and the .class worked fine. when i tried to compile it with geany on this computer, it gave a lot of errors. so i'll try compiling TestPerson on my other as soon as i get a chance.

i have Sun (i think i have both jre and jdk 6).

---

### Post by Ramses de Norre on 2007-11-04
What's the output of **java -version**? It should be at least java 5 to use Scanner. Use  **sudo update-java-alternatives** with the **-l** and **-s** switches to change otherwise, read the man page for more info.

About your code, you might want to add tests for null-pointers in your setters and mind that person1.equals(person2) gives a NullPointerException if person1==null but not if person2==null while person1!=null, so mind the sequence. You should also use your getters instead of calling fields explicitly, instead of **person.firstName** you should invoke **person.getFirstName()**. This makes your code adaptable, if you'd ever change something about the implementation of the firstName field, you'd just need to change the getter and the setter and all other methods can be left unchanged.

This is what I'd use as equals() method, just for reference, I've written it fast so minor bugs are possible.
```

/**
 * Equals method, tests on first and last name only.
 */
@Override
public boolean equals(Object otherPerson)
{
    if(otherPerson!=null && 
        otherPerson.getClass().equals(this.getClass()))
    {
        return (getFirstName().equals(((Person)otherPerson).getFirstName())
            && getLastName().equals(((Person)otherPerson).getLastName()));
    }
    return false;
}

```

---

### Post by dbbolton on 2007-11-04
'java -version' gives:

```

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```

yet i have the package 'sun-java6-jre' installed...

---

### Post by CptPicard on 2007-11-04
It's the "jdk" one you want as you're trying to compile...

---

### Post by dbbolton on 2007-11-04
> **CptPicard said:**
> It's the "jdk" one you want as you're trying to compile...
yes; i also have 'sun-java6-jdk' installed.

---

### Post by CptPicard on 2007-11-04
You actually need just either, not both :)

---

### Post by Ramses de Norre on 2007-11-04
What's the output of **echo $CLASSPATH**? It should point to your java installation lib directories, I get this here: (java installed in /opt/)
```
pts/1 $ echo $CLASSPATH
:/opt/java/lib:/opt/java/jre/lib
```

You can set it correctly otherwise in your ~/.bashrc (by exporting CLASSPATH directly or by specifying JAVA_HOME).

---

### Post by dbbolton on 2007-11-04
there was no output (other than a blank line)

```

daniel@slimline:~$ echo $CLASSPATH

daniel@slimline:~$ echo $CLASSPATH

```

---

### Post by Ramses de Norre on 2007-11-04
Set it to the correct value by exporting it in your ~/.bashrc then. You need to specify the lib directories as in my example but you have to search where ubuntu installs java.

---

### Post by CptPicard on 2007-11-04
That may help but with newer Javas that is no longer really neccessary. For example my $CLASSPATH is not set, and Java works fine.

---

### Post by jespdj on 2007-11-05
> **Ramses de Norre said:**
> What's the output of **echo $CLASSPATH**? It should point to your java installation lib directories, I get this here: (java installed in /opt/)
```
pts/1 $ echo $CLASSPATH
:/opt/java/lib:/opt/java/jre/lib
```

You can set it correctly otherwise in your ~/.bashrc (by exporting CLASSPATH directly or by specifying JAVA_HOME).
No, this is wrong. You do **not** need the lib directories in your CLASSPATH. You do not need to set a CLASSPATH at all. If you leave the CLASSPATH unset, Java will look for class files in the current directory. It knows how to find the JRE's classes automatically; these never have to be included in the CLASSPATH.

---

### Post by geirha on 2007-11-05
This is a typical gotcha. Ubuntu ships by default with gcj, a gnu-alternative to java, it's probably still using this, even though you have sun's java installed. Run ```
update-java-alternatives --list
``` to see what java packages are installed, and set the sun-java to be the one to use. I have java 1.5.0 so I would do: ```
sudo update-java-alternatives --set java-1.5.0-sun
``` to achieve this.

---

