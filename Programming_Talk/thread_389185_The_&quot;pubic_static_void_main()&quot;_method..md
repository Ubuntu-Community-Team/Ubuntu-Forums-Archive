---
title: "The &quot;pubic static void main()&quot; method."
date: 2007-03-20
forum: Programming Talk
---

### Post by Rizado on 2007-03-20
So I've made a small java app which draws some circles on a canvas. I can specify how many circles to be drawn through the constructor like this ```
public circles(int numberOfCircles)
```Everything works great but now I'd like the app to take a command line argument like 5 and pass on 5 to the constructor.

java -jar myClass -5 or 5 or whatever I find fits. It's just I have no idea how to do this.
I've read [this](http://scv.bu.edu/Doc/Java/tutorial/java/nutsandbolts/main.html) and [this](http://scv.bu.edu/Doc/Java/tutorial/java/cmdLineArgs/cmdLineArgs.html) but I honestly don't understand what they are doing? I really could need an example.

---

### Post by kaamos on 2007-03-20
```

    public static void main(String[] args){
        int numberOfCircles = 1;
        if(args.length>0)
            numberOfCircles = Integer.parseInt(args[0]);

        new Circles(numberOfCircles);
    }

```


Args is an array of strings that contains the arguments given to the program.

So with "java Myclass one two three":
args = { "one", "two", "three" };

---

### Post by Tomosaur on 2007-03-20
Java programs must ALWAYS be run via the class name which has the main method. The arguments to the main method are the command line arguments. If you only have one class - the Circles class, then change your existing constructor into the main method. Here's a short example:

```

class Circles{
  public static void main(String[] args){
    if(args.length != 1){  //If there are no command line arguments, or too many arguments
      System.out.println("Usage: java Circles <number>.");
      System.exit(0); //Exit the program
    }
    else{
      //method to parse the character in args[0] into an integer, then to draw the circles
    }
  }
}

```

It's important to remember that command line arguments are passed as strings. If you want to parse the command line argument into an integer, you need to use:
```

try{
  int myInt = Integer.parseInt(myString);
}
catch(NumberFormatException nfe){
  System.out.println("Couldn't convert command line arguments into an integer!);
}

```

The Try/Catch code is there because the conversion of the string into an integer might fail. Without the try/catch, your program would simply crash. This could happen if the user tries to run your program like this, for example:
```

java Circles five

```

instead of
```

java Circles 5

```

Because Java doesn't know how to turn 'five' into 5, but knows how to turn the CHARACTER '5' into the number 5.

Once your code is correct, you compile it like this:
```

javac Circles.java

```

and run it like this:
```

java Circles <number>

```

where number is the number of circles you wish to draw. Remember you DON'T use:
```

java Circles.class <number>

```
because this confuses the Java program, and causes an error. You must leave off the .class extension.

If you have any more problems, just ask here, we'll be glad to help :)

---

### Post by Rizado on 2007-03-20
Thanks guys :) I got it working pretty well. 
The method looks like this now:
```
public static void main(String args[])
    {
        int numberOfBalls = 5;
        if(args.length == 1)
        {
            try
            {
                numberOfBalls = Integer.parseInt(args[0]);
            }
            catch(NumberFormatException nfe)
            {
                System.out.println("Couldn't convert command line arguments into an integer. (Argument really integer?)");
                System.out.println("Usage: DoLikeThisBlahBlah <number>.");
                System.exit(0);
            }
        }
        else if(args.length>1)
        {
            System.out.println("Usage: DoLikeThisBlahBlah <number>.");
            System.exit(0);
        }
        new Circles(numberOfBalls);
    }
```There's a few things I'd like to know however. If i use a negative number I get this little error message: ```
Exception in thread "main" java.lang.NegativeArraySizeException
        at Circles.<init>(Circles.java:23)
        at Circles.main(Circles.java:64)
```Not so surprisingly I can't create negative 4 balls. I guess I should be able to check for this in one of thoose try/catch statements but can I have one of thoose catching two errors? ( catch(NumberFormatException nfe, NegativeArraySizeException ???) )
Also I see that NumberFormatException is the error message you see when trying to run the app but what does nfe do?

EDIT: Okey I read [this](http://java.sun.com/docs/books/tutorial/essential/exceptions/catch.html) and it says, one or more catch blocks. So I just created another one```
            catch(NegativeArraySizeException nase)
            {
                System.out.println("Error");
                System.exit(0);
            }
```This however does not work... It compiles but the error message is still there.

EDIT: A coffee break was everything needed. it couldn't catch the error because it wasn't that try that was causing it. I made a new try where it tries to create the balls, if it's negative a message will print.

---

### Post by Tomosaur on 2007-03-20
> **Rizado said:**
> Thanks guys :) I got it working pretty well. 
The method looks like this now:
```
public static void main(String args[])
    {
        int numberOfBalls = 5;
        if(args.length == 1)
        {
            try
            {
                numberOfBalls = Integer.parseInt(args[0]);
            }
            catch(NumberFormatException nfe)
            {
                System.out.println("Couldn't convert command line arguments into an integer. (Argument really integer?)");
                System.out.println("Usage: DoLikeThisBlahBlah <number>.");
                System.exit(0);
            }
        }
        else if(args.length>1)
        {
            System.out.println("Usage: DoLikeThisBlahBlah <number>.");
            System.exit(0);
        }
        new Circles(numberOfBalls);
    }
```There's a few things I'd like to know however. If i use a negative number I get this little error message: ```
Exception in thread "main" java.lang.NegativeArraySizeException
        at Circles.<init>(Circles.java:23)
        at Circles.main(Circles.java:64)
```Not so surprisingly I can't create negative 4 balls. I guess I should be able to check for this in one of thoose try/catch statements but can I have one of thoose catching two errors? ( catch(NumberFormatException nfe, NegativeArraySizeException ???) )
Also I see that NumberFormatException is the error message you see when trying to run the app but what does nfe do?

EDIT: Okey I read [this](http://java.sun.com/docs/books/tutorial/essential/exceptions/catch.html) and it says, one or more catch blocks. So I just created another one```
            catch(NegativeArraySizeException nase)
            {
                System.out.println("Error");
                System.exit(0);
            }
```This however does not work... It compiles but the error message is still there.


You'll be aware by now that to create variables in Java you use the following syntax:
```

Type variable_name = <value> OR new Type() OR methodWithReturnValue();

```

So let's say I want an integer called 'clouds' with the value of 5. Java has a native integer type, so I just do the following:
```

int clouds = 5;

```

If I want to make a new instance of an object however (let's say 'SkyObject' to represent objects in the sky) I would use:
```

SkyObject clouds = new SkyObject();

```

In the same way, a NumberFormatException is an **object** and nfe is the name you give it. You could change nfe to anything you feel like, such as 'ohNoMyProgramMadeAnError':
```

try{
  int x = Integer.parseInt(mystring);
}
catch(NumberFormatException ohNoMyProgramMadeAnError){
  //stuff
}

```
NumberFormatException is just an object with a name.

As for the NegativeArraySizeException, it looks like that error is happening somewhere else in your code. You should read the Java API for a proper explanation of when this error could occur - but I think it happens when you try to create an array with a negative size, like this:
```

String[] myArray = new String[-5];

```

---

### Post by Rizado on 2007-03-20
Yeah, it was when I tried to create the circles that the error occured. (It can't create -5 balls :P) I made a new try/code when it was creating them and now everything works perfectly (Until I think of something new I want to add)

The try/catch statments were something new to me. It's very handy. Again thank you guys, I'll keep asking questions if I have any :)

---

### Post by Tomosaur on 2007-03-20
> **Rizado said:**
> Yeah, it was when I tried to create the circles that the error occured. (It can't create -5 balls :P) I made a new try/code when it was creating them and now everything works perfectly (Until I think of something new I want to add)

The try/catch statments were something new to me. It's very handy. Again thank you guys, I'll keep asking questions if I have any :)

No problem. If you want to get around the -5 balls error, you could just do a simple check after you've converted the string to an int, to make sure that the int is above 0. Alternatively, you could just  convert the negative int into a positive int.

---

