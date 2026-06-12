---
title: "Little beginner Java help"
date: 2011-01-23
forum: Programming Talk
---

### Post by CaptainMark on 2011-01-23
Just working through a basic beginner program in java, just read about the exception handling syntax and cant figure out what i seem to be doing wrong, ive written this try/catch statement in ```

        try { //Try to capture data
            System.out.print("\nPlease enter you meal price: £");
            value = reader.readLine(); // Capture meal price
            mealPrice = Float.parseFloat(value); // Parse string to float
            System.out.print("\nPlease enter the amount you want to tip in %: ");
            value = reader.readLine(); // Capture Tip percentage
            tipPercent = Float.parseFloat(value); // Parse string to float
        } // End try
        catch (IOException ioe) { // Handle exceptions
            System.out.println("Input Output Error!");
        } // End catch
        
```But when i run the program and input some text instead of a number i dont get the message ive typed but a program error message```
mark@mark-desktop:~/Documents/programming/java/java_programming_for_absolute_beginners/chapter_2$ java userInput 
----------------------------------------------

    £££ Tip Calculator £££

Please enter you meal price: £example
Exception in thread "main" java.lang.NumberFormatException: For input string: "example"
    at sun.misc.FloatingDecimal.readJavaFormatString(FloatingDecimal.java:1242)
    at java.lang.Float.parseFloat(Float.java:439)
    at userInput.main(userInput.java:33)
```I dont understand why, ive copied the syntax as it should be from the book i have
It compiles and runs no problem, and just to be sure, i ran the version that came with the book and it does the same
Any suggestions?

---

### Post by johnl on 2011-01-23
Float.parseFloat throws a NumberFormatException.  You are only catching an IOException -- if a NumberFormatException occurs, it will not go into your catch() statement.

I believe you can do something like this:

```

        try { //Try to capture data
            System.out.print("\nPlease enter you meal price: £");
            value = reader.readLine(); // Capture meal price
            mealPrice = Float.parseFloat(value); // Parse string to float
            System.out.print("\nPlease enter the amount you want to tip in %: ");
            value = reader.readLine(); // Capture Tip percentage
            tipPercent = Float.parseFloat(value); // Parse string to float
        } // End try
        catch (IOException ioe) { // Handle exceptions
            System.out.println("Input Output Error!");
        } // End catch
        catch (NumberFormatException nex) {
            System.out.println(nex.getMessage());
        }

```

---

### Post by CaptainMark on 2011-01-24
Thanks, i half expected this could be a cause from my experience with python but you never expect a published book to give wrong instructions, 

In python i can get the exception handling syntax based on the error im given by a program crash, i can see where NumberFormatException comes from but how would i find out the ioe or the nex part when i come across handling other exception types

---

### Post by PaulM1985 on 2011-01-24
It is always useful to check the API.  It will give information on what kinds of exceptions functions will throw as well as a decent description of what the function will do.

[http://download.oracle.com/javase/1.5.0/docs/api/](http://download.oracle.com/javase/1.5.0/docs/api/)

And here is a link to the parse function that you were using:

[http://download.oracle.com/javase/1.5.0/docs/api/java/lang/Float.html#parseFloat(java.lang.String](http://download.oracle.com/javase/1.5.0/docs/api/java/lang/Float.html#parseFloat(java.lang.String))

If you look at the description for Double.valueOf(string) (give you an exercise to browse the API :-)), it provides a description on how to write code so that it will not throw a NumberFormatException.

EDIT: I was always advised to try and write defensive code so that I don't aim to catch RuntimeExceptions, which NumberFormatException derives from, and only catch the exceptions that the compiler forces you to catch.

Paul

---

### Post by fct on 2011-01-24
> **CaptainMark said:**
> Thanks, i half expected this could be a cause from my experience with python but you never expect a published book to give wrong instructions, 

In python i can get the exception handling syntax based on the error im given by a program crash, i can see where NumberFormatException comes from but how would i find out the ioe or the nex part when i come across handling other exception types

Critical exceptions like I/O ones are required to be caught by the java compiler.

NumberFormatException is not a critical one, so compilation didn't output an error.

Also, IDEs like Eclipse will point out the error or warning in the editor, before compiling.

If you want generic exception treatment in cases you can't know the exception beforehand, there's this possibility:

```

try{
...
}catch (Exception e){
    if (e instanceof NumberFormatException){
        ...
    }else if (e instanceof IOException){
        ...
    }else{
        System.err.println("Unhandled exception!");
        e.printStackTrace();
    }
}

```

---

### Post by CaptainMark on 2011-01-24
I see i didnt realise it wouldnt compile without the io exception catch, im assuming thats because the try contains a bufferedReader, so the book is not putting the io exception instead of number exception by mistake but probaly to keep the code short as possible

---

