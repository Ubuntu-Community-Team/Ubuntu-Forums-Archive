---
title: "UpperCase problem"
date: 2008-08-03
forum: Programming Talk
---

### Post by logieen on 2008-08-03
[SIZE="2"]Hello everyone ..... 

 I am new in java i start learn it from 3 weeks ago so i don't know much abut java .
i want to write a program that ask the user to enter his/her name and the program will print the first name as it is and the last name will be in UpperCase .

the code it print this error " <identifier> expected  "in this line  prevCh='.';  

[/SIZE]

```
import javax.swing.*;
public class PrintUser
  {

    public static void main(String[]args)
    {
        String names=JOptionPane.showInputDialog(null,"Enter your Name :");
        System.out.println(names);
        UserName r=new UserName();
      JOptionPane.showMessageDialog(null,names);
     System.out.println();
    }
    
}

class UserName
{

   char ch;
   char prevCh;
   	String names;  
          int i;        
       prevCh='.';
          void r(String[]args);
  {
  
          for (i=0;i<names.length();i++ ) 
          	{
             ch = names.charAt(i);
             if ( Character.isLetter(ch)  &&  ! Character.isLetter(prevCh) )
                System.out.print( Character.toUpperCase(ch) );
             else
                System.out.print(ch);
             prevCh = ch;  
           }
         
       }
        
        
}
```

---

### Post by drubin on 2008-08-03
Take a look at the  void r(String[]args) line i corrected and hopfully explained.

**EDIT:** Next time try and format your code a little, If you are using a IDE to format your code and it ends up messed up try and work out what you changed to get it not to recognize it. 

> **logieen said:**
> 

[PHP]import javax.swing.*;
public class PrintUser
  {

    public static void main(String[]args)
    {
        String names=JOptionPane.showInputDialog(null,"Enter your Name :");
        System.out.println(names);
        UserName r=new UserName();
      JOptionPane.showMessageDialog(null,names);
     System.out.println();
    }
    
}

class UserName
{

   char ch;
   char prevCh;
   	String names;  
          int i;        
       prevCh='.';
          void r(String[]args);  //-<Take a LOOK you have ended the method with a semi colon, It should not be there. 
  {
  
          for (i=0;i<names.length();i++ ) 
          	{
             ch = names.charAt(i);
             if ( Character.isLetter(ch)  &&  ! Character.isLetter(prevCh) )
                System.out.print( Character.toUpperCase(ch) );
             else
                System.out.print(ch);
             prevCh = ch;  
           }
         
       }
        
        
}[/PHP]

Also next time try and use [NOPARSE][PHP]PUT code between php it has highlighting :)[/PHP][/NOPARSE]

---

### Post by logieen on 2008-08-03
ok i do as you said but it still show me the same error .

---

### Post by pmasiar on 2008-08-03
1) Start with simpler problems - plain commandline I/O

2) Start with simpler language - Python is more beginner-friendly (see sticky with poll). See wiki in my sig for links, including training tasks

---

### Post by logieen on 2008-08-03
there is no error now but it didn't convert the string to uppercase  can anybody tell me pleas what the problem

[PHP]import javax.swing.*;
public class PrintUsers
  {

    public static void main(String[]args)
    {
        String names=JOptionPane.showInputDialog(null,"Enter your Name :");
        System.out.println(names);
      JOptionPane.showMessageDialog(null,names);
      UserName r=new UserName();
     System.out.println();
    }
    
}

class UserName
{
           static void r(String str)  
  {
  char ch;
   char prevCh;
         
          int i;        
       prevCh='.';
          for (i=0;i<str.length();i++ ) 
              {
             ch = str.charAt(i);
             if ( Character.isLetter(ch)  &&  ! Character.isLetter(prevCh) )
                System.out.print( Character.toUpperCase(ch) );
             else
                System.out.print(ch);
             prevCh = ch;  
           }
         
       }
        
        
}  [/PHP]

---

### Post by descendency on 2008-08-03
What you need is in the Java Documentation.

[http://java.sun.com/j2se/1.3/docs/api/java/lang/String.html](http://java.sun.com/j2se/1.3/docs/api/java/lang/String.html)

On that page, you will find what you want. (If you know what you are doing, you'll see it. If not, maybe not.)

You're problem is two fold. You don't know how to manipulate strings in Java and you don't know how strings work in Java. 

My advise is to get a Java book or read a good tutorial on Java (there is one available from Sun - the makers of Java).

[http://java.sun.com/docs/books/tutorial/](http://java.sun.com/docs/books/tutorial/)

Oh, and your current code is WAY too complex for such a simple problem. (that's a hint)

edit: If this is your first time programming, I advise you pick an easier language. Java is a pain to learn for newer programmers, especially without any OOP experience (Your problem is OOP related). C++ would be easier, not that I am advocating that for newbies either. Python seems to be popular here, so I suggest that.

---

### Post by ghostdog74 on 2008-08-04
> **pmasiar said:**
> 
2) Start with simpler language - Python is more beginner-friendly (see sticky with poll). See wiki in my sig for links, including training tasks
Although its really none of my business to interfere, I would still suggest you don't start it. OP has a Java problem. If you really want to help him, pls solve his Java problem first. If its really unsolvable, which i doubt, then your solution might work.

---

### Post by drubin on 2008-08-04
> **descendency said:**
> 
[http://java.sun.com/j2se/1.3/docs/api/java/lang/String.html](http://java.sun.com/j2se/1.3/docs/api/java/lang/String.html)

Those are outdated. Please take a look at the latest ones.
[http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/) 

> **ghostdog74 said:**
> Although its really none of my business to interfere, I would still suggest you don't start it. OP has a Java problem. If you really want to help him, pls solve his Java problem first. If its really unsolvable, which i doubt, then your solution might work.

I agree. There is nothing wrong with Java. He the OP did not ask how this can be done in C or C++ or Python, they were just asking to be pointed in the right direction.

**EDIT:** Although your second point is very worth while!

---

### Post by drubin on 2008-08-04
> **logieen said:**
> 
[PHP]
    public static void main(String[]args)
    {
        String names=JOptionPane.showInputDialog(null,"Enter your Name :");
        System.out.println(names);
      JOptionPane.showMessageDialog(null,names);
      UserName r=new UserName();
     System.out.println();
    }
    
}[/PHP]

If you go through a program flow of your small applications you will see this.

1) Create Input Dialog, to read string back
2) Set names equal to the inputted value.
3) Print out the names.
3) Create a new Username
4) Print out a blank new line.

No where in your code are you ever making reference to static void r(String str); That is your method that converts the String.


I would also recommend changing the method (r)'s name to something more readable and making it return the String value of the output. This way you have more control of what you would like to do with the Uppered Case String.

Hope this helps you.

---

### Post by Reiger on 2008-08-04
From your code it's obvious you've been doing everything manually. That's where your problem is, as this makes it much harder to see "who you're gonna call" in the midst of trees that obfuscate the overview of the complete forest.

Hint: the better alternative is to be as lazy as possible:

1) Writing takes time & effort. So do it only if you really must; and even then do it only once.
2) So, first check your current object if it can do the trick you want.
3) If not check if there exist a library. Since we're lazy; we'll go to the Internet & use a search engine to find out (say Google).
4) If there really isn't anything that does our job for us; then sadly we will have to write it manually. But remember: once and only once!

This line of reasoning leads to checking the String class for available methods. Hint: that class contains case conversion methods.

---

### Post by drubin on 2008-08-04
> **Reiger said:**
> 
**Hint: the better alternative is to be as lazy as possible:**

Please do not tell people to be lazy!! Ever!

The only way to learn and truly be a good programmer is to have the ability to write every thing from scratch. The fact that mots of us **choose** not to is a matter of available time.

But the fact renames that these are fundamental things that need to be learnt. 

At the OP keep on learning and keep on asking questions where ever you feel you do not understand!

---

### Post by Reiger on 2008-08-04
Eh? :) To be able to write something out from scratch doesn't neccesarily make for good code; however to be lazy, as I meant it, means to write [a lot of] stuff once and only once. That principle is one of the key points in understanding what is good code, and what is not.

The example the OP posted, in all fairness; is characterisitc of bad code. The point is he is doing it all from scratch, whereas with Java (and programming languages in general) you must learn to reuse what you already have got: hence; review the capabilities of your object, review your installed/standard libraries. Only if you can't find what you need there do you start writing it out yourself.

To learn a programming language is to learn its mechanics and an understanding of where you can find what tools (in general). In casu: to learn that the String object contains methods "toUpperCase()" and "toLowerCase()".

---

### Post by drubin on 2008-08-04
> **Reiger said:**
> Eh? :) To be able to write something out from scratch doesn't neccesarily make for good code; however to be lazy, as I meant it, means to write [a lot of] stuff once and only once. That principle is one of the key points in understanding what is good code, and what is not.
Yes the idea is to get to that stage by hard work and learning, NOT to just teleport there.

> **Reiger said:**
> 
The example the OP posted, in all fairness; is characterisitc of bad code. The point is he is doing it all from scratch, whereas with Java (and programming languages in general) you must learn to reuse what you already have got: hence; review the capabilities of your object, review your installed/standard libraries. Only if you can't find what you need there do you start writing it out yourself.

I am sure the OP knew his code was not going to be sold to a multi billion dollar company  as the code to complete the world... blah blah.

That is why he was asking for help on the forums trying to improve him self. There is NOTHING wrong with trying to improve what you know. To think that you can not learn form any one is a disgrace, Every day i learn things form every one that i encounter.

> **Reiger said:**
> 
To learn a programming language is to learn its mechanics and an understanding of where you can find what tools (in general). In casu: to learn that the String object contains methods "toUpperCase()" and "toLowerCase()".

Ok now I am going to criticize your code and explain why even your solution is not correct.

toUpperCase only converts "lazy" to "LAZY" it does not like the OP's original code  "i am a good programmer and would like to learn things" to "I am A Good Programmer And Would Like To Learn Things"

If you are going to be smart about things, and try and correct people please try at least to be correct... 

Also please read this before for posting here again. 
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

**EDIT:** Actually the code was intended to capitalize I think sentences either way, the OP did not ask for help with his algorithm he was just asking for points about the programming lang and how to get about things.

---

