---
title: "[SOLVED] Scanner cannot be resolved to a type? Java problem in Eclipse"
date: 2008-11-19
forum: Programming Talk
---

### Post by SilverDragon on 2008-11-19
I looked at the FAQs and on there is this link on posting homework questions:

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

but on there it says > Just because posting homework assignments is against forum policy, you can ask questions that are related to homework. If you get stuck on certain aspects of the assignment(like compiling your code in Linux, or something not specific to the solution to the problem.  and I feel like my question would warrant that, because all the work I have to do is in a separate class.(Hopefully I'm keeping within the rules here)

My problem isn't with my code(well maybe it is but it's compiling fine), but with the Driver class the teacher provided.

I get a similar error to the one this person is having:

[http://www.tek-tips.com/viewthread.cfm?qid=1193576&page=1](http://www.tek-tips.com/viewthread.cfm?qid=1193576&page=1)

and my error is: 

> Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
	Scanner cannot be resolved to a type
	Scanner cannot be resolved to a type

   at ScrabbleDriver.main(ScrabbleDriver.java:8)

The class starts with ```
import java.util.*;
``` at the top and this worked on Dr. Java the compiler I used in Windows, but since I went back to 32 bit Ubuntu to get Java applets to work I decided to just wipe Windows and learn how to use Eclipse and use Ubuntu 100% of the time.

I ask a few of my friends who program in Eclipse but they're all on Windows and they told me it should work fine.

Am I missing something to use the Scanner class?

---

### Post by PaulM1985 on 2008-11-19
Have you tried checking the Java version you are running as mentioned in the link.  

Scanner only came out in Java 1.5, so maybe your Eclipse is running an earlier version.  If you have got a later version of Java, make sure that Eclipse is "looking" at that version.

Paul

---

### Post by drubin on 2008-11-19
please post the output of 
```
java --version
javac --version
```

Maybe you have the incorrect version of java. Check that you have at least 1.5 Possibly check my sig for installing java

---

### Post by SilverDragon on 2008-11-19
> please post the output of
Code:

java --version
javac --version



That didn't work but I ran it with one - instead.

```

java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)

javac -version
javac 1.6.0_0-internal

```

I think that's what you were asking for.

---

### Post by drubin on 2008-11-19
Sorry was a typo.. :)

I do not find the any other then sun java is just not worth it.   
Hint: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) <<But I don't think this is your issue 100%

Please post the accual code you are testing with and please use the code/php tags.

---

### Post by shadylookin on 2008-11-19
since it says you have 1.6 
go into eclipse. 
click window in the toolbar
under window click preferences
open up the java tag
click on compiler
make sure your compiler compliance level is 1.5 or 1.6

next click on Installed JREs
you should have something like java-6-sun-1.6.0.10 with a location of 
/usr/lib/jvm/java-6-sun-1.6.0.10

if not you need to make it so that it does

Give that a try and see what happens

---

### Post by drubin on 2008-11-19
/me forgot to read "Scanner cannot be resolved to a type? Java problem in **Eclipse**"

---

### Post by SilverDragon on 2008-11-19
@drubin

I tried going through the steps at the link for > Choosing the default Java to use but that didn't work.

Here is the code [php]import java.util.*;
import java.io.*;

public class ScrabbleDriver{
  public static void main(String args[]) 
  {
    try{
    Scanner s = new Scanner(System.in);
    System.out.println("enter file name, then word size");
    String f = s.next();
    int size = s.nextInt();
    Scrabble scrab = new Scrabble(f,size);
    scrab.readLines();
    scrab.reportWinner();
    }
    catch(Exception e)
    {System.out.println(e);}
  }
}[/php]

@shadylookin

Under compiler I can pick 1.3,1.4,5.0, or 6.0.

Under Installed JREs it says 

java-1.5.0-gcj-4.3-1.5.0.0 

and 

/usr/lib/jvm/java-1.5.0-gcj-4.3-1.5.0.0

I ran ```
 sudo update-java-alternatives -s java-6-sun 
```but ```
 java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)

```

I guess it doesn't change for some reason.

---

### Post by shadylookin on 2008-11-19
> **SilverDragon said:**
> @drubin

I tried going through the steps at the link for  but that didn't work.

Here is the code [php]import java.util.*;
import java.io.*;

public class ScrabbleDriver{
  public static void main(String args[]) 
  {
    try{
    Scanner s = new Scanner(System.in);
    System.out.println("enter file name, then word size");
    String f = s.next();
    int size = s.nextInt();
    Scrabble scrab = new Scrabble(f,size);
    scrab.readLines();
    scrab.reportWinner();
    }
    catch(Exception e)
    {System.out.println(e);}
  }
}[/php]

@shadylookin

Under compiler I can pick 1.3,1.4,5.0, or 6.0.

Under Installed JREs it says 

java-1.5.0-gcj-4.3-1.5.0.0 

and 

/usr/lib/jvm/java-1.5.0-gcj-4.3-1.5.0.0

I ran ```
 sudo update-java-alternatives -s java-6-sun 
```but ```
 java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)

```

I guess it doesn't change for some reason.

well we're getting somewhere. under compliance pick 6.0 I forgot java's screwed up naming system(1.6 is 6.0)

sudo update-alternatives --config java then select which one you want to use. 

Since you said you installed sun java

go into eclipse 
window
preferences 
java 
installed jres
now click add

select stanard vm if that pops up not sure if that will be in your version of eclipse

click browse
go to /usr/lib/jvm/The Appropriate One Probably java-6-sun-1.6.0.10 or similar/

Then just make sure you deselect the other JREs and only have this one selected

---

### Post by SilverDragon on 2008-11-19
@ shadylookin

Your solution seems to have worked :)

Thank you very much for your help.

@ drubin

Thanks for trying to help me solve my problem. I'm glad you realized the problem was in Eclipse haha :)

---

### Post by drubin on 2008-11-19
> **SilverDragon said:**
> 
@ drubin

Thanks for trying to help me solve my problem. I'm glad you realized the problem was in Eclipse haha :)

No worries I am actually have a rather off day. So I was pretty useless  :)

hint:
If you have a problem with eclispse/any ide try compiling via the command line to check if it is your IDE or java set up.

---

### Post by SilverDragon on 2008-11-19
That's a good tip.

I've heard to run code through the terminal you just do java (the java class) and javac (the java class).

Would you happen to know the difference?

Does java run it and javac compile it?

---

### Post by drubin on 2008-11-19
> **SilverDragon said:**
> That's a good tip.

I've heard to run code through the terminal you just do java (the java class) and javac (the java class).

Would you happen to know the difference?

Does java run it and javac compile it?

Spot on! 
javac Driver.java
java Driver

Note the no .class and the .java.

---

### Post by SilverDragon on 2008-11-19
Does that mean you run java Driver(which is the file with .class after it) just without the .class?

---

### Post by drubin on 2008-11-19
> **SilverDragon said:**
> Does that mean you run java Driver(which is the file with .class after it) just without the .class?

98% sure. give it a try and see :), been a while since I did  CLI compiling and running with out the packages being bundled in a .jar file and there being more then one. hehe

---

### Post by shadylookin on 2008-11-19
> **SilverDragon said:**
> @ shadylookin

Your solution seems to have worked :)

Thank you very much for your help.

@ drubin

Thanks for trying to help me solve my problem. I'm glad you realized the problem was in Eclipse haha :)

No problem I've ran into this issue in the past I can't wait till java is fully open sourced so Ubuntu can use it and avoid this hassle for new users

it's javac Whatever.java then java Whatever

Anyway happy coding:guitar:

---

### Post by jluda on 2009-05-07
Can someone help me i have the same problem but it is not working i must be doing something wrong. Tell me what i need to do for you to help me, please.

---

### Post by Neheb on 2009-05-07
what is your eclipse java version set to?

---

### Post by souridbit on 2009-09-11
This is an interesting discussion. thank you for sharing

---

### Post by cnateb on 2009-11-25
Was having the same problem.  Thanks to those who posted solutions.  resolved by changing java preferences in eclipse.

---

### Post by monikaraj on 2012-02-01
[B]hi i....

im having d same problem actually im doing d program in notepad and compiling it in command prompt(cmd) ....and im getting 2 runtime errors .....saying[/B]....one pointing d first S and second error pointing the 

cannot resolve type
symbol : class Scanner
location :class program name
Scanner sc=new Scanner(System.in);.one error pointing d first 'S'(Scanner) and second error pointing the 2nd S (Scanner(System.in);)

[B]
and i have imported util package also.dont know wt to do.....but still the result is same.[/B]**dont know wt to do**[B]..plz some one help me...

thnQ....
[/B]

---

### Post by Zugzwang on 2012-02-01
> **monikaraj said:**
> 
and i have imported util package also.dont know wt to do.....but still the result is same.[/B]**dont know wt to do**[B]..plz some one help me...


Please do three things:
[LIST]
[*] Open up a new thread (the admins don't like the resurrection of two-year old hreads), then post your *complete* code. 
[*] Check that you really imported "java.util.*" and not just "java.util".
[*] Explain how you are compiling your program and which Java version is used for compiling. Explain in your new thread how you found it out. Java version of < 1.5 do not have the Scanner class
[/LIST]

Make sure to mention all three steps (or their results) in your new post. Good luck! And please, use proper language. Non-native speakers often have a hard time to figure out what "wt" or "plz" means.

---

