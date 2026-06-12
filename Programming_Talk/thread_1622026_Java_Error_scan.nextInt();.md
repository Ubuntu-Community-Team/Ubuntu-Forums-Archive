---
title: "Java Error: scan.nextInt();"
date: 2010-11-15
forum: Programming Talk
---

### Post by SBLMsurfer on 2010-11-15
So I'm writing a program for class that is supposed to ask the user an infinite amount of times for an integer, until the user types -999, which will end the program.  Then the program computes the average of the inputs and displays it on the screen.

Here is my code:
```
import sdsu.io.*;
public class HW6
{
public static void main(String args[])
{
        int item;
        int total = 0;
        int numberofitems = 0;
        int average = 0;

        System.out.println("Input next data item: ");
        item = scan.nextInt();

        while (item != -999)
        {
                total = (total + item);
                numberofitems +=
                average = total/numberofitems;
                item = scan.nextInt();
        }
        System.out.println("The average of your data values is: " + average);

}
}

```

but I get the following errors when I javac it:
```
HW6.java:12: cannot find symbol
symbol  : variable scan
location: class HW6
	item = scan.nextInt();
	       ^
HW6.java:19: cannot find symbol
symbol  : variable scan
location: class HW6
		item = scan.nextInt();
		       ^
2 errors

```

And I've searched and searched the internet trying to look for a similar problem on threads but can't seem to find anyone who knows.  Help?

---

### Post by Some Penguin on 2010-11-15
You didn't declare any variables named 'scan', let alone initialize them.

---

### Post by PaulM1985 on 2010-11-15
```

        while (item != -999)
        {
                total = (total + item);
                numberofitems +=
                average = total/numberofitems;
                item = scan.nextInt();
        }

```

Once you have fixed your first problem, highlighted by Some Penguin, I would also have a look at this loop, particularly at the numberofitems line.

Paul

---

