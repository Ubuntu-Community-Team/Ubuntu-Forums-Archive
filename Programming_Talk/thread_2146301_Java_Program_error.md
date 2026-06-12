---
title: "Java Program error"
date: 2013-05-18
forum: Programming Talk
---

### Post by felixyulin on 2013-05-18
Hello, i'm new to Java.
I have encountered some errors when i tried to run this Java Program.. Did i do sth wrong in here?
Please help:(
```

import javax.swing.JOptionPane;


public class DebugTest
{


public static void main(String[] args)
{


int PIE = 3.14;
String radius = "";
double radius = 0.0;
double area = 0.0;
float circumference = 0.0;


radius = JOptionPane.showInputDialog("Enter the radius of 
a circle to calculate the area: ");
radius = Double.parseDouble(radius);


area = Math.pow(2, radius) * PI;

JOptionPane.showMessageDialog(null, "The area of the 
circle is: " + area);


circumference = Math.sqrt(area / PI) * PI * 2;
JOptionPane.showmessagedialog(null, "The circumference of 
the circle is: " + circumference);


System.out.println("*** End of Processing ***");
}
}

```

---

### Post by r-senior on 2013-05-18
Could you explain your errors more clearly please? For example, did you get errors when you compiled this program, or when you ran it?

Could you post error messages in either case?

When posting code, could you enclose it in [noparse]```
...
```[/noparse] tags so that it is easier to read and paste into a file for testing?

Things I can see immediately:

1. You have two variables called radius, of different types.
2. You are defining a constant called PIE to represent pi. You should use Math.PI, a static constant in the java.lang.Math class.
3. It is unusual to show a dialog without a parent window or other windows. Perhaps you should work on a command-line program to start with?
4. You can calculate circumference directly from the radius as pi * diameter. Diameter is radius * 2.
5. You are mixing float and double in the calculation of circumference. Why?
6. You are not following the case of methods, e.g. show[COLOR="#FF0000"]m[/COLOR]essage[COLOR="#FF0000"]d[/COLOR]ialog.
7. Do you need to use Math.pow to square a number?
8. It looks like homework. Maybe it's just learning, but it does look like homework.

---

### Post by Leuchten on 2013-05-18
You have two declarations of radius as different types in the same scope.

A declaration looks like this in java:

```

int radius;
```

Scopes are started and ended inside brackets in java:

```

class A {
  int radius;

  if(true) {
    String radius = "hello"; //Works because this is a new scope
  }

  char radius; //Error, radius has been declared twice in the same scope.
}
```

---

### Post by mickeelm on 2013-06-24
I don't know if you're still working on the program here, but I have two suggestions (I believe the actual errors in the code have been pointed out to a good extent already):

1. Start with an easier application (as r-senior suggested), command-line at first. I'm afraid there are no shortcuts here from my experience, learn the syntax and rules by following easier examples at first.
2. When you feel a bit more comfortable and have learned the basics (e.g. no duplicate variable names are allowed and other stuff that r-senior and Leuchten have clarified), use an IDE like Eclipse or equivalent. The IDE will tell you what you have done wrong. But, I really recommend to dig into some basics first.

Have fun and welcome to java :)

---

