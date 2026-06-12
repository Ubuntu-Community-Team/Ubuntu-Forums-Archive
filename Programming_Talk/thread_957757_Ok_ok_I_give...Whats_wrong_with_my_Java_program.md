---
title: "Ok ok I give...Whats wrong with my Java program??"
date: 2008-10-24
forum: Programming Talk
---

### Post by brian77095 on 2008-10-24
This is for a java programing class and I cant get it to compile.  The program is suppose to convert all letters in a string to uppercase letters in GUI.  I have ..



import java.util.*;
import java.io.*;
import javax.swing.JOptionPane;


public class A3g
{
 
     public static void main(String[] args)

     {

	String lettersAllCaps;

	lettersAllCaps =
	     JOptionPane.showInputDialog("Enter the letters: ");

	JOptionPane.showMessageDialog(null,lettersAllCaps.toUpperCase(),"The Letters in all Caps:");

System.exit(0);






     }

}



When I try to compile I get...

A3g.java:23: cannot find symbol
symbol  : method showMessageDialog(<nulltype>,java.lang.String,java.lang.String)
location: class javax.swing.JOptionPane
	JOptionPane.showMessageDialog(null,lettersAllCaps.toUpperCase(),"The Letters in all Caps:");
	           ^
1 error


Thanks for any advice, help, links....

Thanks!!!

---

### Post by phowells on 2008-10-24
What version of Java are you compiling with?  As far as I can see there is no showMessageDialog method in JOptionPane that takes an object and two Strings.

Your options are...

showMessageDialog(Component parentComponent, Object message) 
showMessageDialog(Component parentComponent, Object message, String title, int messageType)
showMessageDialog(Component parentComponent, Object message, String title, int messageType, Icon icon)

---

### Post by mike_g on 2008-10-24
You would need to create an instance of JOptionPane first. Something like:
```

JOptionPane theOptionPane = new JOptionPane();

```
Then call the methods from your object:
```

theOptionPane.showInputDialog("Enter the letters: ");
theOptionPane.showMessageDialog(null,lettersAllCaps. toUpperCase(),"The Letters in all Caps:");
```
Not sure if there are any other errors as I havent tested the code, but it should at least set you in the right direction.

---

### Post by aaargh486 on 2008-10-24
> **mike_g said:**
> You would need to create an instance of JOptionPane first. Something like:
```

JOptionPane theOptionPane = new JOptionPane();

```


That's not true. The showDialog, etc... methods of JOptionPane are static methods so you don't have to initialize an object.

The problem here is probably the JRE you are running. The default GNU JRE is very limited. It hasn't even got support for Scanner so I doubt Swing is already implemented. I use the [OpenJDK]("apt:openjdk-6-jre"). It's the Sun reference implementation but with open source code.

Happy Hacking.

---

### Post by shadylookin on 2008-10-24
[PHP]
import java.util.*;
import java.io.*;
import javax.swing.JOptionPane;


public class test
{

public static void main(String[] args)

{

String lettersAllCaps;

lettersAllCaps =
JOptionPane.showInputDialog("Enter the letters: ");

JOptionPane.showMessageDialog(null, "The Letters in all Caps: " + lettersAllCaps.toUpperCase());

System.exit(0);






}

}
[/PHP]

I think this is what you want. Just use the null, string option and make that one big string instead of trying to break it up.

---

### Post by drubin on 2008-10-25
> **aaargh486 said:**
> That's not true. The showDialog, etc... methods of JOptionPane are static methods so you don't have to initialize an object.

The problem here is probably the JRE you are running. The default GNU JRE is very limited. It hasn't even got support for Scanner so I doubt Swing is already implemented. I use the [OpenJDK]("apt:openjdk-6-jre"). It's the Sun reference implementation but with open source code.

Happy Hacking.
Yes all those methods are Static 
> The keyword static in front of a method indicates a static method, which associated only with the class and not with any specific instance of that class. Only static methods can be invoked without a reference to an object. Static methods cannot access any method variables that are not static.
[http://en.wikipedia.org/wiki/Java_programming_language](http://en.wikipedia.org/wiki/Java_programming_language) 

I would much rather use suns jdk. see sig. 

> **shadylookin said:**
> [PHP]
import java.util.*;
import java.io.*;
import javax.swing.JOptionPane;
........
[/PHP]

I think this is what you want. Just use the null, string option and make that one big string instead of trying to break it up.

What was the point of giving the complete solution to this problem? Now the OP is just going to copy it verbatim... Learning experience =0

---

### Post by shadylookin on 2008-10-25
> **drubin said:**
> Yes all those methods are Static 

[http://en.wikipedia.org/wiki/Java_programming_language](http://en.wikipedia.org/wiki/Java_programming_language) 

I would much rather use suns jdk. see sig. 



What was the point of giving the complete solution to this problem? Now the OP is just going to copy it verbatim... Learning experience =0

all he had to do was take out a comma and add a plus sign.

---

### Post by drubin on 2008-10-25
> **shadylookin said:**
> all he had to do was take out a comma and add a plus sign.

And the learning process for the OP was   ctrl+c, ctrl+v. Not having to read any of the explanations. I am not saying this is what he did but for next time.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.
[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

