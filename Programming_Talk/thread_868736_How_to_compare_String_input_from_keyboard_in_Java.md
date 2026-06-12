---
title: "How to compare String input from keyboard in Java"
date: 2008-07-24
forum: Programming Talk
---

### Post by her_ron_potter on 2008-07-24
I want to write a Java program to do this excercise:
- Ask user to enter the **full names** of 3 members in user's family. And display the name of the family member who has the longest **first name** (note that the **longest first name**, not the longest total name).

I just completed to prompt the user to enter name, but I don't know how to spilit the first name of the full names and compare the first name input from keyboard. Plz help me.
This is my code:
[B]
import javax.swing.JOptionPane;
public class Name {
        public static void main(String[] args) {
        int []names = new int [10];
        int get;
         //Prompt user to enter the full names
         for (get=0; get<3; get++) {
         names[get] =   Integer.parseInt(JOptionPane.showInputDialog("Please enter" +
         "the full names of 3 of" + "your family members"));[/B]

Sorry for my bad English :(

---

### Post by dribeas on 2008-07-24
[QUOTE=her_ron_potter;5448054]
```

import javax.swing.JOptionPane;
public class Name {
   public static void main(String[] args) {
      String []names = new String[3];
      int get;
      //Prompt user to enter the full names
      for (get=0; get<3; get++) {
         names[get] = JOptionPane.showInputDialog("Please enter" +
            "the full names of 3 of" + "your family members").trim();
      }
      // *
   }
}

```

First things first... you are not trying to read the names but parsing integers. You should store whatever String the user enters (trim was added to remove leading and trailing whitespaces.

Then you have a couple of options to fill in * for each of the three Strings to obtain longest name length:
[LIST]
[*] Find index of first space .indexOf(' '), in all three stored Strings, highest means longer first name (assuming non-compound names)
[*] Call String.split("\s"), which will break the String in words  and obtain length() of the first returned element.
[*] Use StringTokenizer to break the string, obtain first substring (name) and obtain it's length()
[/LIST]

With the maximum you already know what to printout.

First option assumes that space character is used. StringTokenizer allows for space, tab, or newline.

---

### Post by her_ron_potter on 2008-07-24
Hi!
I used the String.split to obtain length of the first element. This is my code:

[B]import javax.swing.JOptionPane;
public class Try {
   public static void main(String[] args) {
      String []names = new String[3];
      int get;
      //Prompt user to enter the full names
      for (get=0; get<3; get++) {
         names[get] = JOptionPane.showInputDialog("Enter name:");
       }

      //Get the first name from a name string 
      String[] name1 = names[0].split(" ");
      String[] name2 = names[0].split(" ");
      String[] name3 = names[0].split(" ");

      // Get the lengths of strings using length() instance method
      int length1 = name1[0].length();
      int length2 = name2[0].length();  
      int length3 = name3[0].length();

      // Compare the lengths of the first names between 3 people
      if ((length1>length2) & (length1>length3)) {
          System.out.println(name1[0] + " has the longest first name");
      } else if ((length1<length2) & (length3<length2)) {
          System.out.println(name2[0] + " has the longest first name");
      } else {
          System.out.println(name3[0] + " has the longest first name");
      }                 
      
   }
}[/B]

But when I try to input 3 full names, the screen show only the name of the person 2 but the person 1 has the longest first name.
Can u show me the error? 
Thanks in advance

---

### Post by her_ron_potter on 2008-07-24
Hi!
I used the String.split to obtain length of the first element. This is my code:

[B]import javax.swing.JOptionPane;
public class Try {
   public static void main(String[] args) {
      String []names = new String[3];
      int get;
      //Prompt user to enter the full names
      for (get=0; get<3; get++) {
         names[get] = JOptionPane.showInputDialog("Enter name:");
       }

      //Get the first name from a name string 
      String[] name1 = names[0].split(" ");
      String[] name2 = names[0].split(" ");
      String[] name3 = names[0].split(" ");

      // Get the lengths of strings using length() instance method
      int length1 = name1[0].length();
      int length2 = name2[0].length();  
      int length3 = name3[0].length();

      // Compare the lengths of the first names between 3 people
      if ((length1>length2) & (length1>length3)) {
          System.out.println(name1[0] + " has the longest first name");
      } else if ((length1<length2) & (length3<length2)) {
          System.out.println(name2[0] + " has the longest first name");
      } else {
          System.out.println(name3[0] + " has the longest first name");
      }                 
      
   }
}[/B]

But when I try to input 3 full names, the screen show only the name of the person 2 but the person 1 has the longest first name.
Can u show me the error? 
Thanks in advance

---

### Post by mike_g on 2008-07-24
If its anything like javascript (which it probably is) then you should only need to call split() once and it will be assigned to an array of strings. 

Heres an example: [http://www.rgagnon.com/javadetails/java-0438.html](http://www.rgagnon.com/javadetails/java-0438.html)

---

### Post by ORiONx9 on 2008-07-25
&&

---

### Post by dribeas on 2008-07-25
Please, use [ CODE ] tags, as it makes code much more readable.

Whenever you run into a problem with your code doing something you don't expect, try adding traces/logs of what is going on, what variables are at each point in the code, etc.

You will probably have noticed that name1, name2 and name3 contain just the same value. Ah, and as someone pointed before, logic and is &&, not & (bitwise and).

> **her_ron_potter said:**
> ```
      //Get the first name from a name string 
      String[] name1 = names[0].split(" ");
      String[] name2 = names[0].split(" ");
      String[] name3 = names[0].split(" ");
```

---

### Post by her_ron_potter on 2008-07-25
thank to all, I finally finished this exercise. Sorry for my noob in Java. I'm beginner :)

---

