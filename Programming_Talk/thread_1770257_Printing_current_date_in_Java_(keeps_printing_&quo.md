---
title: "Printing current date in Java (keeps printing &quot;YES&quot;?)"
date: 2011-05-29
forum: Programming Talk
---

### Post by akand074 on 2011-05-29
Hey,

I'm trying to print just the current date in Java. I googled how to do it and come up with a few ways including:

```
Date currentDate = GregorianCalendar.getInstance().getTime();
DateFormat df = DateFormat.getDateInstance();
String dateString = df.format(currentDate);
System.out.println(dateString);
```and 

```
Date d = new Date();
System.out.println("today = " + d);
```and a couple other similar ones that I found online. With java.util.* and java.text* all imported and every single time it just prints:

```
YES
```Does anyone know why this is? Or what the proper way to do it is?

Thanks a lot!

---

### Post by Petrolea on 2011-05-29
> **akand074 said:**
> Hey,

I'm trying to print just the current date in Java. I googled how to do it and come up with a few ways including:

```
Date currentDate = GregorianCalendar.getInstance().getTime();
DateFormat df = DateFormat.getDateInstance();
String dateString = df.format(currentDate);
System.out.println(dateString);
```and 

```
Date d = new Date();
System.out.println("today = " + d);
```and a couple other similar ones that I found online. With java.util.* and java.text* all imported and every single time it just prints:

```
YES
```Does anyone know why this is? Or what the proper way to do it is?

Thanks a lot!

Try this:
[http://www.rgagnon.com/javadetails/java-0106.html](http://www.rgagnon.com/javadetails/java-0106.html)

---

### Post by akand074 on 2011-05-29
> **Petrolea said:**
> Try this:
[http://www.rgagnon.com/javadetails/java-0106.html](http://www.rgagnon.com/javadetails/java-0106.html)

That was actually the first one I tried. I mean, seems like it should work. I'm thinking it may not be a problem directly with the code:S

---

### Post by Zugzwang on 2011-05-29
It might sound a little bit silly, but since the code
```

Date d = new Date();
System.out.println("today = " + d);

```
can never result in printing "YES" (either the output starts with 'today = ...' or an exception is thrown), my guess is that you are actually executing some other code. So if you are using an IDE, double-check that you are executing the code you want to. 

Other than that, consider making some executable java class that makes your problem self-contained, i.e. store the following into "/tmp/Problem.java":
```

import java.util.*;

class Problem {

    static public void main(String[] args) {
        Date d = new Date();
        System.out.println("today = " + d);
    }
}

```
Then, go to the directory "/tmp/" and try out your program:
```

me@my-computer:/tmp$ javac Problem.java 
me@my-computer:/tmp$ java Problem
today = Sun May 29 20:26:37 CEST 2011

```
See if the problem still exists.

---

### Post by akand074 on 2011-05-29
> **Zugzwang said:**
> It might sound a little bit silly, but since the code
```

Date d = new Date();
System.out.println("today = " + d);

```can never result in printing "YES" (either the output starts with 'today = ...' or an exception is thrown), my guess is that you are actually executing some other code. So if you are using an IDE, double-check that you are executing the code you want to. 

Other than that, consider making some executable java class that makes your problem self-contained, i.e. store the following into "/tmp/Problem.java":
```

import java.util.*;

class Problem {

    static public void main(String[] args) {
        Date d = new Date();
        System.out.println("today = " + d);
    }
}

```Then, go to the directory "/tmp/" and try out your program:
```

me@my-computer:/tmp$ javac Problem.java 
me@my-computer:/tmp$ java Problem
today = Sun May 29 20:26:37 CEST 2011

```See if the problem still exists.

Hey yeah I thought it might have something to do with the IDE. I just ran it through the terminal and the output was exactly what it should have been! :S I don't know why it doesn't work through NetBeans. Perhaps I'll try that code through the actual project and see if it works.

---

### Post by Petrolea on 2011-05-29
> **akand074 said:**
> Hey yeah I thought it might have something to do with the IDE. I just ran it through the terminal and the output was exactly what it should have been! :S I don't know why it doesn't work through NetBeans. Perhaps I'll try that code through the actual project and see if it works.
 
You can also post the code here (if it isn't a secret :D) and we will analyse it for you :) (if it isn't related to IDE of course).

---

### Post by akand074 on 2011-05-29
> **Petrolea said:**
> You can also post the code here (if it isn't a secret :D) and we will analyse it for you :) (if it isn't related to IDE of course).

Well the code is actually exactly as I put it in the OP. I just created a new project and a new main class put that code in main and ran the single file. Anyways I'll just check if it works in my main project once I get to that point.

---

### Post by Petrolea on 2011-05-29
> **akand074 said:**
> Well the code is actually exactly as I put it in the OP. I just created a new project and a new main class put that code in main and ran the single file. Anyways I'll just check if it works in my main project once I get to that point.

Oh, ok, I thought it was just a part of a code. If you think you've solved your problem you can mark it as [SOLVED], if you got any more questions, make sure to ask :)

---

### Post by Zugzwang on 2011-05-29
@OP: Since you are using Netbeans, I can make an informed guess on what is wrong: perhaps you have chosen the wrong main class. In a project that has multiple classes with a main function, you have to tell the IDE which one is the one that you want to use when hitting "run". If I recall correctly (on an older version of Netbeans) you can right-click in the project explorer onto the class you want to be the main class to be executed and select that option from the context menu.

---

### Post by stchman on 2011-05-29
This will print out the date with time and year.

[PHP]
import java.util.*;

class GetDate {
    public static void main( String[] args ) {
        
        Calendar date = Calendar.getInstance();
        System.out.println( date.getTime() );
        
    }
}
[/PHP]

---

### Post by akand074 on 2011-05-30
Okay so there is definitely a problem that's happening for me in Netbeans! I'm actually so frustrated, for about 5 hours+ I've been getting a NullPointerException over and over again at the same place. The line it told me where the NullPointerException was always the same! Even when I moved code around and there was no code on that actual line. I looked everywhere and I was positive there is nowhere that I'm pointing toward a null reference. I made a copy of my entire project and just opened them all up in Dr.Java. Compiled and ran and it ran perfectly. This is messed up, such a waste of time! I might wipe netbeans config files and everything and reinstall it and see if it starts working fine, otherwise might use my Eclipse setup in the mean time.

EDIT: Marking this thread as solved, whole program running perfectly including the date as I wanted. Turns out NetBeans was the culprit indeed, I'll have to look more into the problem later.

---

### Post by stchman on 2011-06-01
> **akand074 said:**
> Okay so there is definitely a problem that's happening for me in Netbeans! I'm actually so frustrated, for about 5 hours+ I've been getting a NullPointerException over and over again at the same place. The line it told me where the NullPointerException was always the same! Even when I moved code around and there was no code on that actual line. I looked everywhere and I was positive there is nowhere that I'm pointing toward a null reference. I made a copy of my entire project and just opened them all up in Dr.Java. Compiled and ran and it ran perfectly. This is messed up, such a waste of time! I might wipe netbeans config files and everything and reinstall it and see if it starts working fine, otherwise might use my Eclipse setup in the mean time.

EDIT: Marking this thread as solved, whole program running perfectly including the date as I wanted. Turns out NetBeans was the culprit indeed, I'll have to look more into the problem later.

I just ran this is Netbeans and got the proper output.

[PHP]
package gettime;

import java.util.*;

/**
 *
 *
 */
public class GetTime {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
               
        GetTime m = new GetTime();
        
        m.returnTime();
    }
    
    public void returnTime() {
        Calendar date = Calendar.getInstance();

        String dateString = date.getTime().toString();
        
        System.out.println( dateString );
    }
}
[/PHP]This is the output I got:

```

Wed Jun 01 12:01:28 CDT 2011

```All appears to work well.

---

### Post by KdotJ on 2011-06-01
Did you have other projects open in Netbeans? When you create a new project but do not select "set as main project", when you click the *run* button, it will run the main class from one of the other projects open in Netbeans, not the newly created one.

---

### Post by stchman on 2011-06-02
You need to set the project you are working on as the main project.

---

