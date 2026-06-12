---
title: "Java Question (Random Phone Number)"
date: 2008-06-30
forum: Programming Talk
---

### Post by tdrusk on 2008-06-30
I am having trouble with my java assignment.

> Write an application that creates and prints a random phone number of the form xxx-xxx-xxxx. Include
the dashed in the output. Do not let the first three digits contain an 8 or 9 (but don’t be more restrictive
than that).
And make sure that the second set of three digits is not greater than 742 (i.e. &#8804; 742). Hint: Think
through the easiest way to construct he phone number. Each digit does not have to be determined
separately.

This is what I have, but I keep getting errors on my if statements. What am I doing wrong?
```

import java.util.Random;

public class untitled {

    public static void main (String args[]) {        
        
        Random generator = new Random();
        int one = generator.nextInt(8);
        int two = generator.nextInt(8);
        int three = generator.nextInt(8);
        int fourthroughsix = generator.nextInt(743);
        
        if (fourthroughsix < 100 && >10)
         int fourthroughsix = ("0" + fourthroughsix);
        if (fourthroughsix =>9 && =<0)
         int fourthroughsix = ("00" + fourthroughsix);
         
         int seventhroughten = generator.nextInt(10000);
        if (seventhroughten =< 999 && => 100)
         int seventhroughten = ("0" + seventhroughten);
        if (seventhroughten =< 99 && => 10);
         int seventhroughten = ("00" + seventhroughten);
        if (seventhroughten =< 9 && => 0);
         int seventhroughten = ("000" + seventhroughten); 
        
        System.out.println("Your random phone number is" + one + two + three + "-" + fourthroughsix + "-" + seventhroughten);
         
        
        
    }
}

```

---

### Post by LaRoza on 2008-06-30
Give the errors...

---

### Post by tdrusk on 2008-06-30
Sorry
```
tyler@ubuntu:~/Java/Computer Science I$ javac '/home/tyler/Java/Computer Science I/HW3/random.java'
/home/tyler/Java/Computer Science I/HW3/random.java:34: illegal start of expression
        if (fourthroughsix < 100 && >10)
                                    ^
/home/tyler/Java/Computer Science I/HW3/random.java:35: '.class' expected
         int fourthroughsix = ("0" + fourthroughsix);
             ^
/home/tyler/Java/Computer Science I/HW3/random.java:35: not a statement
         int fourthroughsix = ("0" + fourthroughsix);
         ^
/home/tyler/Java/Computer Science I/HW3/random.java:35: illegal start of expression
         int fourthroughsix = ("0" + fourthroughsix);
                            ^
/home/tyler/Java/Computer Science I/HW3/random.java:35: ';' expected
         int fourthroughsix = ("0" + fourthroughsix);
                             ^
/home/tyler/Java/Computer Science I/HW3/random.java:35: not a statement
         int fourthroughsix = ("0" + fourthroughsix);
                                   ^
/home/tyler/Java/Computer Science I/HW3/random.java:35: ';' expected
         int fourthroughsix = ("0" + fourthroughsix);
                                                   ^
/home/tyler/Java/Computer Science I/HW3/random.java:36: illegal start of expression
        if (fourthroughsix =>9 && =<0)
                            ^
/home/tyler/Java/Computer Science I/HW3/random.java:36: illegal start of expression
        if (fourthroughsix =>9 && =<0)
                                  ^
/home/tyler/Java/Computer Science I/HW3/random.java:36: illegal start of type
        if (fourthroughsix =>9 && =<0)
                                    ^
/home/tyler/Java/Computer Science I/HW3/random.java:36: illegal start of expression
        if (fourthroughsix =>9 && =<0)
                                     ^
/home/tyler/Java/Computer Science I/HW3/random.java:36: ')' expected
        if (fourthroughsix =>9 && =<0)
                                      ^
/home/tyler/Java/Computer Science I/HW3/random.java:40: illegal start of type
        if (seventhroughten =< 999 && => 100)
                               ^
/home/tyler/Java/Computer Science I/HW3/random.java:40: illegal start of expression
        if (seventhroughten =< 999 && => 100)
                                   ^
/home/tyler/Java/Computer Science I/HW3/random.java:40: illegal start of expression
        if (seventhroughten =< 999 && => 100)
                                       ^
/home/tyler/Java/Computer Science I/HW3/random.java:41: '.class' expected
         int seventhroughten = ("0" + seventhroughten);
             ^
/home/tyler/Java/Computer Science I/HW3/random.java:41: not a statement
         int seventhroughten = ("0" + seventhroughten);
         ^
/home/tyler/Java/Computer Science I/HW3/random.java:41: illegal start of expression
         int seventhroughten = ("0" + seventhroughten);
                             ^
/home/tyler/Java/Computer Science I/HW3/random.java:41: ';' expected
         int seventhroughten = ("0" + seventhroughten);
                              ^
/home/tyler/Java/Computer Science I/HW3/random.java:41: not a statement
         int seventhroughten = ("0" + seventhroughten);
                                    ^
/home/tyler/Java/Computer Science I/HW3/random.java:41: ';' expected
         int seventhroughten = ("0" + seventhroughten);
                                                     ^
/home/tyler/Java/Computer Science I/HW3/random.java:42: illegal start of type
        if (seventhroughten =< 99 && => 10);
                               ^
/home/tyler/Java/Computer Science I/HW3/random.java:42: illegal start of expression
        if (seventhroughten =< 99 && => 10);
                                  ^
/home/tyler/Java/Computer Science I/HW3/random.java:42: illegal start of expression
        if (seventhroughten =< 99 && => 10);
                                      ^
/home/tyler/Java/Computer Science I/HW3/random.java:44: illegal start of type
        if (seventhroughten =< 9 && => 0);
                               ^
/home/tyler/Java/Computer Science I/HW3/random.java:44: illegal start of expression
        if (seventhroughten =< 9 && => 0);
                                 ^
/home/tyler/Java/Computer Science I/HW3/random.java:44: illegal start of expression
        if (seventhroughten =< 9 && => 0);
                                     ^
27 errors

```

---

### Post by CptPicard on 2008-06-30
The correct way to do it:

```

if (x > 3 && x < 10)
  ...

```

---

### Post by myrtle1908 on 2008-06-30
There were many problems with your code.  Have a look below for a working solution.

[PHP]
import java.util.Random;

public class untitled {

    public static void main (String args[]) {        
        
        Random rand = new Random();
        String one = Integer.toString(rand.nextInt(8));
        String two = Integer.toString(rand.nextInt(8));
        String three = Integer.toString(rand.nextInt(8));
        String fourThroughSix = leftPad(rand.nextInt(743), 3);
        String sevenThroughTen = leftPad(rand.nextInt(10000), 5);
        System.out.println("Your random phone number is: " + one + two + three + "-" + fourThroughSix + "-" + sevenThroughTen);
    }
    
    public static String leftPad(int n, int padding) {
    	return String.format("%0" + padding + "d", n);
    }
    
}
[/PHP]

---

### Post by tdrusk on 2008-06-30
Thanks guys. I see the mistakes I made. I appreciate it.

---

### Post by amrosamy79 on 2009-12-09
import java.util.*;
class Frm {
String fr (int a1,int b1,int c1)
{
//convert recived ints to string
String aj=new Integer (a1).toString().substring(0,3).replace("8",expt89()).replace("9",expt89()) ;
String bj=new Integer (b1).toString().substring(0,3) ;
String cj=new Integer (c1).toString().substring(0,4) ;
 
String last = "(" + aj + ") - " + bj + " - " + cj;
return last;
}
String expt89()// to return numbers from 0 to 7 to replace in frist int
{
Random rand = new Random();
String ex =new Integer (rand.nextInt()).toString();
return ex;
}
}
public class Phone
{
public static void main(String args[])
{
Random rand = new Random();
 
Frm ff=new Frm();
Scanner sc = new Scanner(System.in);
System.out.print("How Many Phone Number you want to generate ? ");
int n = sc.nextInt();
for (int x = 0 ; x < n ; x++)
{
String c = ff.fr(Math.abs(rand.nextInt()), Math.abs(rand.nextInt()), Math.abs(rand.nextInt())); //sending 3 positiv integers to fr method
System.out.println("Number " + (x+1) + " IS : " + c);
}
}
}
 
 
 
note : in this line " String ex =new Integer (rand.nextInt()).toString(); " but 8 between () "in rand.nextInt()"  because when i do that
String ex =new Integer (rand.nextInt(8)).toString();

---

### Post by lisati on 2009-12-09
amrosamy79: (1) please use [noparse]```
 at the start of your quoted code, and 
``` at the end[/noparse], it helps make it easier for us to read. (2) Do you have a question?

---

### Post by jespdj on 2009-12-09
@amrosamy79, welcome to the forums. Why are you responding to a topic that is almost 1.5 years old? The original poster is most likely not still waiting for an answer.

---

