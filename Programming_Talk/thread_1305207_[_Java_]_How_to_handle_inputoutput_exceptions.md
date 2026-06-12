---
title: "[ Java ] How to handle input/output exceptions ?"
date: 2009-10-29
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-29
[LEFT]What's wrong with this code ? As far as I remember, I used it in the same way a few days ago and it worked just fine :neutral:


```
import java.io.*;

```[/LEFT]
```

  
public class Main {

    public static void main(String[] args) {

        try {
            File file = new File(args[0]);
        } catch (IOException e) {
            System.out.println("Something went totally wrong ..");
        }

    }

}

``````
[COLOR=Red]Uncompilable source code - exception java.io.IOException is never thrown in body of corresponding try statement at sample.Main.main(Main.java:14)[/COLOR]
```

---

### Post by PaulM1985 on 2009-10-29
The constructor for a File object does not need any try/catch statements because the constructor does not throw an exception.  However, if you were going to do anything with that File object, like create a new file, you would have to have try/catch around that.

So:

File aFile = new File(aPath);

is fine, but 

aFile.createNewFile();

would need to be inside try/catch statements catching an IOException.  Look at the API for the File class and click on the methods for information on exceptions they throw.

Hope this is of some help.

Paul

---

### Post by OpenGuard on 2009-10-29
```
public class Main {

    public static void main(String[] args) {

        File file = new File(args[0]);

        try {
            if (file.exists()) {
                System.out.println("File found!\n");
            } else {
                System.out.println("File NOT found!\n");
            }
        } catch (IOException e) {
            System.out.println("Sorry, I don't know whether the file exists or not!\n");
        }

    }

}
```Still the same issue ( *exception never thrown* .. ) :( Any ideas ?

---

### Post by PaulM1985 on 2009-10-29
The exists() method of File does not throw an exception, so you are trying to catch an IOException that is never thrown.

[http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)

Go on this link and click on the File link.  It should be in the panel to the bottom left. This will give the methods of the File class.  Click on the methods and it will say what exceptions they throw.  If it doesn't say that the method you require throws an IOException, you don't have to try and catch one.

Also, you shouldn't try to catch an Exception which is a subclass of RuntimeException.  You can find this out by clicking on the exceptions, if any, that the method throws.  At the top of the screen that appears it should show which class it inherits from.

Hope this makes it a bit clearer on finding out which exceptions you need to catch and how to find out what you need to catch.

Paul

---

### Post by OpenGuard on 2009-10-29
> **PaulM1985 said:**
> The exists() method of File does not throw an exception, so you are trying to catch an IOException that is never thrown.

[http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)

Go on this link and click on the File link.  It should be in the panel to the bottom left. This will give the methods of the File class.  Click on the methods and it will say what exceptions they throw.  If it doesn't say that the method you require throws an IOException, you don't have to try and catch one.

Also, you shouldn't try to catch an Exception which is a subclass of RuntimeException.  You can find this out by clicking on the exceptions, if any, that the method throws.  At the top of the screen that appears it should show which class it inherits from.

Hope this makes it a bit clearer on finding out which exceptions you need to catch and how to find out what you need to catch.

Paul

Ok, thank you - documentation link is now in my bookmark list :) A little bit further reading led me into the fact that file.exists() may throw a SecurityException, but, if I don't catch it ( I removed try/catch ), in what cases it might end up in an unexpected crash ?

---

### Post by PaulM1985 on 2009-10-30
> **OpenGuard said:**
> Ok, thank you - documentation link is now in my bookmark list :) A little bit further reading led me into the fact that file.exists() may throw a SecurityException, but, if I don't catch it ( I removed try/catch ), in what cases it might end up in an unexpected crash ?


If you click on the SecurityException link it will take you to the SecurityException page.  On this page you can see the class hierarchy resulting in SecurityException.  You can see that this inherits from RuntimeException.  In general should not try to catch exceptions which inherit from runtime exceptions, but write your program so that it doesn't throw any.

This link may help.

[http://journals.ecs.soton.ac.uk/java/tutorial/java/exceptions/runtime.html](http://journals.ecs.soton.ac.uk/java/tutorial/java/exceptions/runtime.html)

Paul

---

