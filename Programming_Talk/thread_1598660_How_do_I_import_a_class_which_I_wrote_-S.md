---
title: "How do I import a class which *I* wrote? :-S"
date: 2010-10-16
forum: Programming Talk
---

### Post by youbuntu on 2010-10-16
Hi guys. Just beginning to learn Java. Wrote a .java file and compiled it into a .class file, which I saved to the Desktop. I then wrote another .java file, and tried to import the previous class (saved to the Desktop, remember) into it, in order to instantiate it and use its' methods.

For some reason it doesn't like the way I am doing this - I know you are supposed to import a class and NOT a class as a file... but how, please?

Treat me gently - I am a n00b!

Thank you :)

---

### Post by dwhitney67 on 2010-10-16
There's no need to import anything.  Just use the class, and make sure that CLASSPATH is defined for your environment.

In lieu of saving files to your desktop, consider placing them into a folder (directory) that is relative to your home directory.

In either case, the CLASSPATH can be defined either in a file like ~/.bashrc, or from the command line.  The former is easier to manage.

For example, within ~/.bashrc:
```

export CLASSPATH=~/Desktop:~/workspace/Special:./

```
Then "source ~/.bashrc" or open a new terminal.

---

### Post by youbuntu on 2010-10-16
> **dwhitney67 said:**
> There's no need to import anything.  Just use the class, and make sure that CLASSPATH is defined for your environment.

In lieu of saving files to your desktop, consider placing them into a folder (directory) that is relative to your home directory.

In either case, the CLASSPATH can be defined either in a file like ~/.bashrc, or from the command line.  The former is easier to manage.

For example, within ~/.bashrc:
```

export CLASSPATH=~/Desktop:~/workspace/Special:./

```Then "source ~/.bashrc" or open a new terminal.

????? :confused:

---

### Post by kbryk on 2010-10-17
```

public class Test{

    public static void main(String[] args)
    {
        JavaClass test = new JavaClass();
    
        test.saySomething();

    }

}

```

```

public class JavaClass{

    public void saySomething()
    {
        System.out.println("Test");
    }
}

```

Was this the route you were trying to go?

---

### Post by cinohpa on 2010-10-17
Um... where are you writing this code? Are you using any IDE or anything?

You shouldn't really need to touch .class files at all..... They have nothing to do with classes really.

You import a class at the (very) top of the .java file you want to use it in.

---

### Post by mickeelm on 2010-10-17
Yes, an important matter here is: How are you writing your code? Are you writing in a text editor or an IDE (Integrated Development Environment, a program for writing code)?

If you are writing your code in a text editor (which I personally believe is the best way to start, but consider going over to an IDE pretty soon after your first classes have been written), which it sounds like you are doing, it should be no problem doint what you are trying to do. Although you should save your .class-files in a folder ;)

Can you please post your code, and maybe we can give you better help?

---

### Post by dwhitney67 on 2010-10-17
Perhaps the OP was merely having trouble compiling, not with running the application such as I had originally thought.

As I stated earlier, the "import" statement is not required, unless you are importing a package.

To compile Java code that is in one directory, but depends upon other Java code that is residing elsewhere, use the *sourcepath* compiler option.

For example, suppose we have **~/Desktop/One.java**, and we compile this to derive **~/Desktop/One.class**.

Later, when want to use the One class in our other Java source file, say located at ~/Projects.  This is how to compile this file:
```

**javac -sourcepath=~/Desktop Other.java**

```
Now, when it comes to running the Other class object, the Class Path  will come into play.  You can either define the Class Path as an environment variable, or specify it on the command line itself.  Here are examples of each:
```

**java -classpath=~/Desktop:. Other**    # note the dot for cur dir

# or

**export CLASSPATH=~/Desktop:.**   # note the dot for cur dir
**java Other**

```
If you do not want to type the Class Path every time you run the program, then refer to my earlier post where I explain how to add it to one's ~/.bashrc file.

---

### Post by youbuntu on 2010-10-17
Thanks.  Will mull this over later :-)

---

### Post by youbuntu on 2010-10-17
> **kbryk said:**
> ```

public class Test{

    public static void main(String[] args)
    {
        JavaClass test = new JavaClass();
    
        test.saySomething();

    }

}

``````

public class JavaClass{

    public void saySomething()
    {
        System.out.println("Test");
    }
}

```Was this the route you were trying to go?

Yes it was/is.

---

### Post by kbryk on 2010-10-17
Place both .java files within the same folder, compiling the source that has the main method and run the one with the main method. But if you are using an IDE there should be nothing more than writing the code and running it.

I am/we? are assuming you can compile and run a "Hello world" program without errors in either CLI or an IDE.

Here is the command line output of what I described above in the first sentence.
```
user1@user1-computer:~/test1$ dir
JavaClass.java  Test.java

user1@user1-computer:~/test1$ javac Test.java

user1@user1-computer:~/test1$ dir
JavaClass.class    JavaClass.java  Test.class  Test.java

user1@user1-computer:~/test1$ java Test
Test

```Continued from my example above with the two source codes.

---

### Post by mickeelm on 2010-10-17
> **kbryk said:**
> 
I am/we? are assuming you can compile and run a "Hello world" program without errors in either CLI or an IDE.

Good point. Glossywhite, can you run a simple hello world? If you're unsure, create a file called HelloWorld.java, put this code into it:

```
public class HelloWorld {

   public static void main(String[] args) {
       System.out.println("Hello World!");
   }
}
```

compile it and run it, and it should print "Hello World!" in your terminal output.

You might be familiar with this already but we're just trying to help ;)

---

### Post by youbuntu on 2010-10-17
> **mickeelm said:**
> Good point. Glossywhite, can you run a simple hello world? If you're unsure, create a file called HelloWorld.java, put this code into it:

```
public class HelloWorld {

   public static void main(String[] args) {
       System.out.println("Hello World!");
   }
}
```compile it and run it, and it should print "Hello World!" in your terminal output.

You might be familiar with this already but we're just trying to help ;)

Easy. Did that ages ago :)

---

### Post by kbryk on 2010-10-17
You're making this tough. :P

If you REALLY wanted to use import I believe you would need to package your class file into a JAR and then import it, at least that's how I remember doing it.

Is there a reason why you want to import rather than make a call to the constructor or method from the other class?

---

### Post by mickeelm on 2010-10-18
glossywhite, I still believe it would be good if you pasted your code. You confirmed that Hello World worked fine, which means that your java environment should be set up OK - you can both compile and run. In my world, your code should be working then if you have coded it as kbryk's example.

So, there might be a hint in your code where we can see why your code is not working?

---

### Post by nvteighen on 2010-10-18
Ok, I don't have a clue about Java and could manage to access a class I created in another file basing myself on kbryk's posts and some general knowledge on programming environments. As I see, the problems arise when you try to use cross-package classes, not in-package ones... and Java considers the current directory as a package.

What's the issue, then?

---

### Post by mickeelm on 2010-10-18
Just paste the code here glossywhite and maybe we can see the issue :) You kinda have to now, I'm curious :)

---

