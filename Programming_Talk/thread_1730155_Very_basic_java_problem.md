---
title: "Very basic java problem"
date: 2011-04-15
forum: Programming Talk
---

### Post by antagonist388 on 2011-04-15
So here's my problem, I keep getting a

 java.lang.NoClassDefFoundError: javaapplication3/welcome
Caused by: java.lang.ClassNotFoundException: javaapplication3.welcome

error and I don't know why. Keep in mind I am VERY new to programming, i.e. I know python and have been studying java for about 2 days. This could be a VERY simple problem, so don't put anything past me :).

Thanks!

Here is a picture of the program itself if you believe that will help

[http://i119.photobucket.com/albums/o129/qckslvr688/ubuntupicture.png](http://i119.photobucket.com/albums/o129/qckslvr688/ubuntupicture.png)

Let me know if I should provide any additional information

Btw my intention with this program is to roll two die until I get a pair
[php]/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */
import java.util.Random;

/**
 *
 * @author Mark
 */
public class javaapplication3 {

    /**
     * @param args the command line arguments
     */
    public static void main (String[] args) {
        int numRolls=0;
        int dieRoll1=1;
        int dieRoll2=0;
        while (dieRoll1!=dieRoll2){
            dieRoll1=new Random().nextInt() + 1;
            dieRoll2=new Random().nextInt() + 1;
            numRolls++;
            System.out.print1n("You rolled a"+dieRoll1+"and a "+dieRoll2);
        }
        System.out.print1n("You rolled doubles")

 
    }

}
[/php]

---

### Post by cgroza on 2011-04-15
Do the files and the class have the same name?
Edit, your file needs to have the same name as the public class inside it. Yours is named welcome.java.

---

### Post by r-senior on 2011-04-16
> **antagonist388 said:**
> [php]
        System.out.print1n("You rolled doubles")
[/php]
Apart from the file naming issue, does this really say print1n, or is it println?

It needs to be println, think "print line".

---

### Post by GregBrannon on 2011-04-16
I assume since you've coded dice that you meant to use Java's Random() class to generate numbers 1 through 6.  I suggest modifying your approach to:

```
Random rnd = new Random();
. . .
die = rnd.nextInt( 6 ) + 1;
```

or consider using [Math.random()]("http://download.oracle.com/javase/6/docs/api/java/lang/Math.html#random%28%29") which is commonly used to generate random numbers within a specific range.

---

### Post by antagonist388 on 2011-04-16
> **cgroza said:**
> Do the files and the class have the same name?
Edit, your file needs to have the same name as the public class inside it. Yours is named welcome.java.
[http://i119.photobucket.com/albums/o129/qckslvr688/ubuntupicture-1.png](http://i119.photobucket.com/albums/o129/qckslvr688/ubuntupicture-1.png)
still not working.. what am i doing wrong?

---

### Post by rabbitdaone on 2011-04-16
> **antagonist388 said:**
> [http://i119.photobucket.com/albums/o129/qckslvr688/ubuntupicture-1.png](http://i119.photobucket.com/albums/o129/qckslvr688/ubuntupicture-1.png)
still not working.. what am i doing wrong?

NetBeans is giving an error saying that it cant find javaapplication3.java, and your package name is also JavaApplication3, so i beleive NetBeans is searching for a class named javaapplication3, yours is called welcome.

---

### Post by r-senior on 2011-04-16
You've done the right thing in renaming the .java file to match the class name, i.e. welcome, but Netbeans still thinks your main class is something else. Right click on the project and go to Properties, then look in the section that I think is called Run. The name of the main class needs to change to "welcome".

That should work, although it is usual practice to use upper case as the first letter of the class name, so Welcome would be better. I'd get it working first, then change the names - file to Welcome.java, class name to Welcome and Netbeans main class to Welcome.

---

