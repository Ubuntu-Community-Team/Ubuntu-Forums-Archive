---
title: "Controlling Objects in Java?"
date: 2009-06-25
forum: Programming Talk
---

### Post by insilicium on 2009-06-25
Hello,

I am not new to programming, but most of my experience is limited to scientific computing (fortran and matlab).  I recently decided to try my hand at object-oriented programming in Java.  I ran into a bit of a problem when I wanted to create multiple instances of a class, and have them all perform a task based on their respective variables.  I wrote a short program that demonstrates my problem:

[PHP]public class MultipleInstanceTest {
  public static void main(String[] args) {
    new SaySomething("hi");
    new SaySomething();
    
    SaySomething.writeMessage();
  }
}

class SaySomething {
  static String message;
  
  public SaySomething() {
    message = "hello";
  }
  
  public SaySomething(String s) {
    message = s;
  }
  
  public static void writeMessage(){
    System.out.println(message);
  }
}[/PHP]

I had to make writeMessage and message both static in order to get it to compile.  But ideally, this program would output "hi" and then "hello" - two responses because there have been two objects created.  I realize that this might not be possible this way.  If it isn't, then what should I do?

---

### Post by credobyte on 2009-06-25
[DELETED]
[COLOR=Silver]P.S. - how to delete useless posts ?[/COLOR]

---

### Post by ddrichardson on 2009-06-25
You seem to have mixed up instance and class functions.  You created two objects but didn't assign them to a variable.
```
messageOne = new SaySomething("Hi");
messageTwo = new SaySomething();
```
Also, the second class hasn't been declared public.

---

### Post by estyles on 2009-06-25
"SaySomething" is the name of your class.  When you type "SaySomething.writeMessage()", you are attempting to call the method without an instance of the class (the way the last java book I read would refer to it would be that you have the blueprints for a house and are trying to turn on the water without actually building the house).  That's why it demands that the method be static.  However, making it static doesn't do what you want it to do.

The line that says "new SaySomething("hi");" is the first problem in your main() method.  That simply creates a new object and then throws it away. 

You want it to read like this: "SaySomething s1 = new SaySomething("hi");"  Then the next line should be "SaySomething s2 = new SaySomething();".  Then below that, you would call s1.writeMessage(); s2.writeMessage();

Also, get rid of static on writeMessage() - you don't want that there.

---

### Post by estyles on 2009-06-25
> **ddrichardson said:**
> You seem to have mixed up instance and class functions.  You created two objects but didn't assign them to a variable.
```
messageOne = new SaySomething("Hi");
messageTwo = new SaySomething();
```
Also, the second class hasn't been declared public.


Declaring the second class public would cause a problem.  You cannot declare two public classes in the same .java file, unless one of them is an inner class.  So, don't do that.

---

### Post by ddrichardson on 2009-06-25
> **estyles said:**
> "SaySomething" is the name of your class.  When you type "SaySomething.writeMessage()", you are attempting to call the method without an instance of the class (the way the last java book I read would refer to it would be that you have the blueprints for a house and are trying to turn on the water without actually building the house).  That's why it demands that the method be static.  However, making it static doesn't do what you want it to do.
Just to build on that, you can have methods that are called directly on the class (class methods) which are used a lot in Java to do things, such as convert types and so on.  Here though the problem is that you haven't assigned the objects to a variable name - its the variable name that the instance method is called on:
```
messageOne.writeMessage();
```Is called on the object referenced by messageOne
```
SaySomething.writeMessage();
```Is called as a message on the object type which in your case is accessing the single method:```
[COLOR=#000000][COLOR=#007700]public [/COLOR][COLOR=#0000bb]SaySomething[/COLOR][COLOR=#007700]() { 
    [/COLOR][COLOR=#0000bb]message [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#dd0000]"hello"[/COLOR][COLOR=#007700]; 
}[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700][COLOR=Black]Where message is being assigned a value - if you don't make that variable static it doesn't exist and cannot be set, hence the compile error[COLOR=#007700].[/COLOR][/COLOR]
 [/COLOR][/COLOR]

---

### Post by ddrichardson on 2009-06-25
> **estyles said:**
> Declaring the second class public would cause a problem.  You cannot declare two public classes in the same .java file, unless one of them is an inner class.  So, don't do that.
Oh sorry I didn't realize that it was the same file, my bad.

---

### Post by froggyswamp on 2009-06-25
```

public class Main {

    public static void main(String[] args) {
        SaySomething s1 = new SaySomething("hi");
        SaySomething s2 = new SaySomething();

        s1.writeMessage();
        s2.writeMessage();
    }
}

class SaySomething {

    String message;

    public SaySomething() {
        message = "hello";
    }

    public SaySomething(String s) {
        message = s;
    }

    public void writeMessage() {
        System.out.println(message);
    }
}

```Or, with static method:
```

public class Main {

    public static void main(String[] args) {
        SaySomething s1 = new SaySomething("hi");
        SaySomething s2 = new SaySomething();

        SaySomething.writeMessage(s1);
        SaySomething.writeMessage(s2);
    }
}

class SaySomething {

    String message;

    public SaySomething() {
        message = "hello";
    }

    public SaySomething(String s) {
        message = s;
    }

    public static void writeMessage(SaySomething s) {
        System.out.println(s.message);
    }
}

```

---

### Post by insilicium on 2009-06-25
wow - thanks everyone for your kind responses.  I understand that a simple way to solve this problem in the case of only 2 instances is to just assign names to each of the instances and then call writeMessage individually from each of them.  The problem that I am trying to address is in the case where you don't actually know how many SaySomething objects there will be.  That might look something like this:

Have an actionlistener that will let the user create a new SaySomething class each time they press, say, enter, and have it hold some message.  Then, have the program print out the messages from each instance of the class.  In this case, it would be impractical (impossible?) to name each of these variables separately and then to call writeMessage individually.

Is there a simple way to do this with classes, like with a class method?  What I'd like is to have some function that would tell every instance to run writeMessage and print out its own message.

Also, I know that in this particular case I'd be better off just having something like an array to hold the messages.  However, as I mentioned earlier, I'm only using this program as a way to illustrate my problem.

---

### Post by estyles on 2009-06-25
You would need to create an array of SaySomething objects for that.  I have to admit, I've been doing a lot of vb.net programming lately, and haven't done much real coding in java in like 10 years.  So, I'm not sure what API classes are available.

Ideally, for your case, I think you want a Queue.  Each time a new message is generated, you would create a new SaySomething object and add it to the Queue.  Each time you want to print out a message, you would Pop() an object out of the Queue, doing something like 
```
SaySomething s = (SaySomething)SomethingQueue.Pop();
s.writeMessage();
```

You'd have to check the API docs to see if there's an appropriate Queue object.

You could also do it as an array, either fixed-size or dynamically sized.  You would then have to keep a separate integer that stores the number of messages in the array.  When you add to the array, you would do something like
```
SomethingArray[numMessages++] = new SaySomething(message);
``` to add to the array, making sure you're within the array's declared size.  Then when you want to print the messages, somethign like:
```
for(int i = 0; i < numMessages; i++)
      SomethingArray[i].writeMessage();
numMessages = 0;
```

Edit: Sorry, just noticed that you did mention an array to hold the objects.  There's no way around having some sort of data structure to keep a reference to the objects.  There's no framework means of calling a method on every object of class foo that has been created.  And in fact there could be no such method, because of garbage collection - every so often, the garbage collector goes through and frees up memory that is assigned to an object which is no longer referenced.  So if you want your objects to not get tossed, you *have* to keep a reference to them.

---

### Post by insilicium on 2009-06-25
ah, that makes sense now.  If I don't have a reference to the object, it will get deleted by the automatic garbage collector.  I should make an array of objects, and loop through that array each time I want to print the output.  Thanks very much!

---

### Post by ddrichardson on 2009-06-25
> **insilicium said:**
> ah, that makes sense now.  If I don't have a reference to the object, it will get deleted by the automatic garbage collector.  I should make an array of objects, and loop through that array each time I want to print the output.  Thanks very much!
You might want to look into Java Collections framework if you're using collections of objects, its more flexible especially if you're working with strings.  The String class is immutable which might cause you a few issues down the road.

[http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)
[http://java.sun.com/docs/books/tutorial/collections/index.html](http://java.sun.com/docs/books/tutorial/collections/index.html)

---

