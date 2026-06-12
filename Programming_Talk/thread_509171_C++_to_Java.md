---
title: "C++ to Java"
date: 2007-07-25
forum: Programming Talk
---

### Post by Cyberslam on 2007-07-25
Hi all, 

I have made a small simple program in C++ using Turbo C but now i want to convert it into Java. Is there anyone here who is willing to help me in this ? 

Here is the source code of my program:

```

#include <iostream.h>
#include <conio.h>
void main()
{
clrscr();
  long phone[50];
  int count=0;
  char *name[100];
  long price[50];
  char *color[100];
  char *camera[100];
  char c1='y'; 
  int num=0;
while (c1=='y')
{
  clrscr();
  cout<<"Enter your choice"<<endl;
  cout<<"1.store information"<<endl;
  cout<<"2.output information"<<endl;
  cout<<"3.search for phone by phone number"<<endl;
  cout<<"4.average price of phones"<<endl;
  cout<<"5.total price of the phones entered"<<endl;
  cout<<"Enter no for operation"<<endl;
    cin>>num;
 if (num==1)
   {
     clrscr();
     char c='a';
       while (c=='a')
       {
       count++;
       int i=count;
       {
         cout<<"enter phone number"<<endl;
         cin>>phone[i];
   	 cout<<"enter phone name"<<endl;
   	 cin>>name[i];
   	 cout<<"enter price"<<endl;
     	 cin>>price[i];
   	 cout<<"enter color"<<endl;
   	 cin>>color[i];
   	 cout<<"camera option"<<endl;
   	 cin>>camera[i];
        }
   clrscr();
   cout<<"Press 'a' to continue adding phone info"<<endl;
   cin>>c;
   }

}
   if (num==2)
    {
     clrscr();
      for (int k=1;k<=count;k++)
       {
          cout<<"              phone  "<<k<<"  details "<<endl;
          cout<<"phone no: "<<phone[k]<<endl;
    	  cout<<"phone name: "<<name[k]<<endl;
    	  cout<<"phone price: "<<price[k]<<endl;
    	  cout<<"phone color: "<<color[k]<<endl;
    	  cout<<"camera present: "<<camera[k]<<endl;
       }
   getche();
}
	if (num==3)
   {
     int search=0;
     int l=1;
     char found;
     clrscr();
     cout<<"Search no of phone"<<endl;
     cin>>search;
      while (search!=phone[l])
       {
	l++;
	}
  if (search==phone[l])
  {
   cout<<"Phone no " <<l<<"  details"<<endl;
   cout<<"Phone no : "<<phone[l]<<endl;
   cout<<"Phone name : "<<name[l]<<endl;
   cout<<"Phone price : "<<price[l]<<endl;
   cout<<"Phone color : "<<color[l]<<endl;
   cout<<"Camera option : " <<camera[l];
  }
    getch();
  }
   if (num==4)
   {
     cout<<"yes\n";
     float avg=0;
     float avv=0;
     int z=0;
     for(z=1;z<=count;z++)
    {
     avg=price[z];
     avv=avv+avg;
    }
   cout<<"The Average price of the phones is :  "<<avv/2;
 getch();
}
  if(num==5)
   {
    int add=0;
    int y=0;
     for (y=1;y<=count;y++)
      {
       add=add+price[y];
     }
   cout<<"The Total amount of phone prices : ";
   cout<<add;
   getche();
    }
clrscr();
cout<<"Press 'y' to go to menu "<<endl;
cin>>c1;
}
clrscr();
cout<<"bye bye press any key to exit";
getche();
}

```

Thanks

---

### Post by LaRoza on 2007-07-25
How much Java do you know? It seems like a simple task, but I am at school and will not be able to rewritte it in Java.

Much of the code will be the same, but I do not know the clrscr() equivilent.

I don't know how much you know, but you declared main() to be void, it should be int. main() will return an int no matter how you declare it.

---

### Post by samjh on 2007-07-25
It's pretty straight-forward.

The problem is, Cyberslam is not using ISO-standard C++.  Turbo C's dialect of C++ is not standards-compliant, so the code is... crap.

The only thing that Java doesn't have a direct equivalent is clrscr().


Cyberslam,

Try doing a straight translation using this cheat sheet:
[http://www.digilife.be/quickreferences/QRC/JAVA%20Programming%20Guide%20-%20Quick%20Reference.pdf](http://www.digilife.be/quickreferences/QRC/JAVA%20Programming%20Guide%20-%20Quick%20Reference.pdf)

You will need some basic Java knowledge, which is easy enough to get.  Go through these tutorials in given order:
Getting Started: [http://java.sun.com/docs/books/tutorial/getStarted/index.html](http://java.sun.com/docs/books/tutorial/getStarted/index.html)
Basics: [http://java.sun.com/docs/books/tutorial/java/nutsandbolts/index.html](http://java.sun.com/docs/books/tutorial/java/nutsandbolts/index.html)
Strings: [http://java.sun.com/docs/books/tutorial/java/data/strings.html](http://java.sun.com/docs/books/tutorial/java/data/strings.html)
I/O from the Command Line: [http://java.sun.com/docs/books/tutorial/essential/io/cl.html](http://java.sun.com/docs/books/tutorial/essential/io/cl.html)

---

### Post by Cyberslam on 2007-07-25
LaRoza, i don't know a thing about JAVA so please help me out on this. The code i posted above is in C++ .


samjh, that cheating guide is no use to me if i don't know a thing about JAVA. 

Thanks

---

### Post by LaRoza on 2007-07-25
> **Cyberslam said:**
> LaRoza, i don't know a thing about JAVA so please help me out on this. The code i posted above is in C++ .


samjh, that cheating guide is no use to me if i don't know a thing about JAVA. 

Thanks

OK, most of the code will be similar, the syntax, and data types are very similar. Instead of a main(), Java must have a class with a main method, like so:

```

//IF YOU FIND A WAY TO CLEAR SCREEN, USE THE FIND AND REPLACE ON "//CLEAR_SCREEN"
//FOR INPUT, WHICH IS A PAIN, USE FIND AND REPLACE ON "//INPUT"
//FOR THE //GET_KEY_STROKE, USE FIND AND REPLACE ON "//GET_KEY_STROKE"

//THIS WILL NOT COMPILE UNTIL THE PROPER METHODS HAVE REPLACED THE ABOVER COMMENTS

class Phone
{
 public static void main(String args[])
 {
  //CLEAR_SCREEN
    long phone[50];
    int count=0;
    String name;
    long price[50];
    String color;
    String camera;
    char c1='y'; 
    int num=0;
  while (c1=='y')
  {
    //CLEAR_SCREEN
    System.out.println("Enter your choice");
    System.out.println("1.store information");
    System.out.println("2.output information");
    System.out.println("3.search for phone by phone number");
    System.out.println("4.average price of phones");
    System.out.println("5.total price of the phones entered");
    System.out.println("Enter no for operation");
      //INPUTnum;
   if (num==1)
     {
       //CLEAR_SCREEN
       char c='a';
         while (c=='a')
         {
         count++;
         int i=count;
         {
           System.out.println("enter phone number");
           //INPUTphone[i];
     	 System.out.println("enter phone name");
     	 //INPUTname[i];
     	 System.out.println("enter price");
       	 //INPUTprice[i];
     	 System.out.println("enter color");
     	 //INPUTcolor[i];
     	 System.out.println("camera option");
     	 //INPUTcamera[i];
          }
     //CLEAR_SCREEN
     System.out.println("Press 'a' to continue adding phone info");
     //INPUTc;
     }
  
  }
     if (num==2)
      {
       //CLEAR_SCREEN
        for (int k=1;k<=count;k++)
         {
            System.out.println("              phone  " + k + "  details ");
            System.out.println("phone no: " + phone[k]);
      	  System.out.println("phone name: " + name[k]);
      	  System.out.println("phone price: " + price[k]);
      	  System.out.println("phone color: " + color[k]);
      	  System.out.println("camera present: " + camera[k]);
         }
     //GET_KEY_STROKE
  }
  	if (num==3)
     {
       int search=0;
       int l=1;
       char found;
       //CLEAR_SCREEN
       System.out.println("Search no of phone");
       //INPUTsearch;
        while (search!=phone[l])
         {
  	l++;
  	}
    if (search==phone[l])
    {
     System.out.println("Phone no " + l + "  details");
     System.out.println("Phone no : " + phone[l]);
     System.out.println("Phone name : " + name[l]);
     System.out.println("Phone price : " + price[l]);
     System.out.println("Phone color : " + color[l]);
     System.out.println("Camera option : " + camera[l]);
    }
      //GET_KEY_STROKE
    }
     if (num==4)
     {
       System.out.println("yes\n");
       float avg=0;
       float avv=0;
       int z=0;
       for(z=1;z<=count;z++)
      {
       avg=price[z];
       avv=avv+avg;
      }
     System.out.println("The Average price of the phones is :  " + avv/2);
   //GET_KEY_STROKE
  }
    if(num==5)
     {
      int add=0;
      int y=0;
       for (y=1;y<=count;y++)
        {
         add=add+price[y];
       }
     System.out.println("The Total amount of phone prices : ");
     System.out.println(add);
     //GET_KEY_STROKE
      }
  //CLEAR_SCREEN
  System.out.println("Press 'y' to go to menu ");
  //INPUTc1;
  }
  //CLEAR_SCREEN
  System.out.println("bye bye press any key to exit");
  //GET_KEY_STROKE
 }
}
```
Since you seem to have no functions, you will put the code in main(String).

I/O is different, and I am not skilled in Java, but I will do my best. I am in school and cannot compile or run, so whatever I give will be yours to debug :D.

I know the code is C++, but it is not standard.

****************************************************************

I redid some of the code, but am unable to complete it, the input functions are not being used, you or someone else will have to do that. The file should be named "Phone.java", unless you want to change the class name, I didn't know what the file was called, nor the purpose of the program.

The rest of it should be easy, unless you are comparing strings, I didn't check. You will have to alter that also. As == will only see if it is the same string, not equivalent.

---

### Post by LaRoza on 2007-07-25
Why do you want to translate this to Java if you already have it in C++?

---

### Post by rjfioravanti on 2007-07-25
> **LaRoza said:**
> Why do you want to translate this to Java if you already have it in C++?

my guess is homework assignment needed to be in java and he found this program on a site somewhere in Turbo C

I never even heard of turbo C

---

### Post by samjh on 2007-07-25
> **LaRoza said:**
> //IF YOU FIND A WAY TO CLEAR SCREEN, USE THE FIND AND REPLACE ON "//CLEAR_SCREEN"
//FOR INPUT, WHICH IS A PAIN, USE FIND AND REPLACE ON "//INPUT"
//FOR THE //GET_KEY_STROKE, USE FIND AND REPLACE ON "//GET_KEY_STROKE"

Nice effort, LaRoza.

For getting input, put this as one of the import lines:
```
import java.io.Console;
```
... then create an instance of it at the beginning of the program...
```
Console c = System.console();
```
... then to obtain an input from console, and store the result in a String variable...
```
thisisastring = c.readLine();
```
... if the variable is not a String, then you need to cast the input to the required type; for example, if the variable you want to store the input into is an integer...
```
thisisaninteger = Integer.parseInt(c.readLine());
```

---

### Post by Cyberslam on 2007-07-26
LaRoza  , thanks alot for your great effort. I dont't know whether it works or not because i can't compile it in Turbo C++ as i don't have the Java compiler for it. Do you know any other program in which i can use this java code ? 

rjfioravanti, you are somewhat right. It was indeed as assignment for Java but i didn't get this code from any website, I coded it myself.

---

### Post by rjfioravanti on 2007-07-26
Sorry for the mean assumption!

Has your teacher provided help with a java environment? Why are you attached to using Turbo C++? What I recommend is getting the sun-java6-jdk package. Then you will have javac and java

To compile, all you have to do is 

javac Phone.java

to run..

java Phone

If you want to go all out you can get eclipse, which is a very nice java IDE, but it may be overkill for your purposes

---

### Post by Cyberslam on 2007-07-27
Any easier IDEs like Turbo C++ for java ? 

Abou the teacher help, i am only left with this programming course for my 2nd year but the problem is that the college where i am studying isn't providing this course for this term. If i don't take the course now i will wasting my 3-4 months just for one course which i am not willing to do. The worst part is that the instructor of this course is on a vacation.

This course consists of one java and some C++ assignments. I know the C++ coding but i have no clue of java.

Hope that clears up everything.

---

### Post by LaRoza on 2007-07-27
If you are used to C++, Java will be easy (to learn).

The main differences are:
0. Java has garbage collection
1. Java is Object Obsessed
2. Java gives you less control, no pointers and references.
3. Java passed variables by value, and objects by reference
4. Java runs on any computer will the jre, so you don't have to worry about the OS
5. Java implements Objects slightly differently, although the concepts are the same
6. Generics are like Templates, but not exactly the same

One interesting aspect is that the main class, the one that contains main(String args[]), has to be the exact same name as the file, minus the extension, .java. When you compile, you get a file with the same name, but with the .class extension. When you run that, don't type the extension.

So, here is how you would compile and run the above program, which I called Phone.java.

```

$ javac Phone.java
$ java Phone

```

---

### Post by Cyberslam on 2007-07-28
**samjh,** can you please explain a bit more ? What do you mean by import lines ? can you please explain as an example using any variable in the code ? 

Thanks

---

### Post by Cyberslam on 2007-07-28
LaRoza , i haven't compiled yet as i still haven't got that three missing commands in your program.

---

### Post by samjh on 2007-07-28
> **Cyberslam said:**
> **samjh,** can you please explain a bit more ? What do you mean by import lines ? can you please explain as an example using any variable in the code ? 

Thanks

No problem. :)  I've been trying to give hints, rather than straight cut-and-paste answers,

Imports are like includes in C++.

So in C++, you have:```
include <iostream>
```
Whereas in Java, you have:```
import java.io.Console
```(Note that <iostream> and java.io.Console are not equivalent to each other.  I'm just using them as examples.)

To use various functionality from the java.io.Console library, you need to create an instance of the object Console.  In the code below, I have instantiated it to an objected named c.  Here is a bare-bones example using Console:
```
import java.io.Console;

public class ConsoleDemo {
    public static void main(String[] args) {
        Console c = System.console();
    }
}
```I'll explain each line.

import java.io.Console;
This line imports the java.io.Console library into this code, so that you can use its methods, variables, etc.

public class ConsoleDemo
This line specifies that the code within the curly braces { } define a class named ConsoleDemo.  The source file for this program will be ConsoleDemo.java.  After compiling, the resulting file will be ConsoleDemo.class.  You can run it by typing this command in terminal: java ConsoleDemo

public static void main(String[] args)
This line defines the main method of the ConsoleDemo class. This is the Java equivalent of C++'s int main ( int argc, char *argv[] ).  Don't worry about public and static.  Void means the method returns no value.  String[] args contains command-line parameters in an array of Strings.

Console c = System.console();
Console is an object that represents the system console for the Java Virtual Machine.
c is the name of the object that will be created.  It is of type Console.
System.console() will assign c to the Console object for the Java Virtual Machine.  The System.console() method returns the Console object so that it can be assigned to c.

So there you go.  That little program will instantiate a console.

Now to expand further:
```
import java.io.Console;

public class ConsoleDemo {
    public static void main(String[] args) {
        Console c = System.console();
        String thisisastring;
        thisisastring = c.readLine();
    }
}
```This little program expands on the example I gave earlier in the post.  There are two new lines:
String thisisastring;
and
thisisastring = c.readLine();

String thisisastring;
Self-explanatory, since you already know C++.  This creates a variable named thisisastring, which is of type String.  In Java, strings are actually objects, not character arrays.  So this is similar to using C++ own string class.

thisisastring = c.readline();
This line is similar to the following C++ code: cin >> thisisastring;
readLine() is a method (a "member function" in C++) of the Console class, used for reading a line from standard input.  You have probably guessed that the result is returned to the String variable, thisisastring.

The example program above is limited, since readLine() returns a String, the variable to which it returns the result must be of String type.  If not, it will throw an exception at you.

To get readLine() to put stuff into variables of other types, you need to cast them.  For your purposes, I'm going to get a little messy and use a shortcut.  Every primitive type in Java has an object "wrapper" class associated with it.  For example, int (obviously integers) have the Integer class as its object wrapper.  These wrapper objects have a wide variety of methods that allow you to manipulate data types.

In the following example, we will read input using readLine() into an integer variable.  Let's use some code from you own program.  We will declare an integer variable called num, and read the user's choice into it:
```
import java.io.Console;

public class ConsoleDemo {
    public static void main(String[] args) {

        int num = 0;
        char c1 = 'y';

        Console c = System.console();

        while (c1 == 'y') {

            System.out.println("Enter your choice");
            System.out.println("1.store information");
            System.out.println("2.output information");
            System.out.println("3.search for phone by phone number");
            System.out.println("4.average price of phones");
            System.out.println("5.total price of the phones entered");
            System.out.println("Enter no for operation");

            num = Integer.parseInt(c.readLine());

        }
    }
}
```(This is an infinite loop, since c1 is always 'y'.  To end the program, just type in a non-number, and it will end itself with a jumble of error messages.)

int num = 0;
This creates a variable num, of int type, and initialises its value to 0.

char c1 = 'y';
Likewise with num, this is a variable called c1, of char type, initialised to the value of 'y'.  In Java, like C and C++, characters are enclosed in single quotes.

while (c1 == 'y')
Exactly the same syntax as C++ for a while-loop.

System.out.println("...");
This is the Java cousin of C++'s cout << "Hello there!" << endl;  The println will automatically attach an end-of-line.  Otherwise, use print, if you don't want an end-of-line.

The next line gets more interesting.  Java is very pedantic about types.  It is a strongly-typed language, and doesn't like methods or anything of one particular type, messing with another entity of a different type.  So casting needs to be used liberally in most Java applications.

num = Integer.parseInt(c.readLine());
Remember I said earlier that the primitive type int has the Integer class as its object wrapper?  Well, we're using the parseInt() method within the Integer class to convert the String returned by readLine(), into an int.  You might have figured it out already: just put c.readLine() inside the brackets of Integer.parseInt().

Viola!  Now you can read stuff from standard input straight into an int type variable.

To deal with c1 to end your program, you might be better off just making c1 a String.  It will save you the pain of trying to convert a String to a char.

I hope that was all useful to you. :)

---

### Post by Cyberslam on 2007-07-28
Thanks a lot - thats in detail as it can get ;) 

Now from what i gather from your post, equivalent of "cin" command ( C++) in Java is 

thisisastring = c.readLine(); ( where thisisstring being the variable name of string). Isn't it ? If its integer, it will be "integername"=c.readline(); (integername will be the integer variable name). ??? 


Now whereever LAroza has put "//input" in his source code, i have to replace it with the following: 

Lets take an example of this part from Laroza code:

```
System.out.println("5.total price of the phones entered");
    System.out.println("Enter no for operation");
      //INPUTnum;

```

i have to replace "//Inputnum" with the following:

```
System.out.println("5.total price of the phones entered");
    System.out.println("Enter no for operation");
num=c.readline();
```

Am i right ? 


Btw, any luck with the clear screen and get stroke commands ? I don't see the use of "get key stroke" here ?

---

### Post by Cyberslam on 2007-07-28
Btw, this is the code i compiled: 

```
class Phone
{
 public static void main(String args[])
 {
  //CLEAR_SCREEN
    long phone[50];
    int count=0;
    String name;
    long price[50];
    String color;
    String camera;
    char c1='y'; 
    int num=0;
  while (c1=='y')
  {
    //CLEAR_SCREEN
    System.out.println("Enter your choice");
    System.out.println("1.store information");
    System.out.println("2.output information");
    System.out.println("3.search for phone by phone number");
    System.out.println("4.average price of phones");
    System.out.println("5.total price of the phones entered");
    System.out.println("Enter no for operation");
      num=c.readline();
   if (num==1)
     {
       //CLEAR_SCREEN
       char c='a';
         while (c=='a')
         {
         count++;
         int i=count;
         {
           System.out.println("enter phone number");
           Phone=c.readline()[i];
     	 System.out.println("enter phone name");
     	 name=c.readline()[i];
     	 System.out.println("enter price");
       	 price=c.readline()[i];
     	 System.out.println("enter color");
     	 color=c.readline()[i];
     	 System.out.println("camera option");
     	 camera=c.readline()[i];
          }
     //CLEAR_SCREEN
     System.out.println("Press 'a' to continue adding phone info");
     c=c.readline();
     }
  
  }
     if (num==2)
      {
       //CLEAR_SCREEN
        for (int k=1;k<=count;k++)
         {
            System.out.println("              phone  " + k + "  details ");
            System.out.println("phone no: " + phone[k]);
      	  System.out.println("phone name: " + name[k]);
      	  System.out.println("phone price: " + price[k]);
      	  System.out.println("phone color: " + color[k]);
      	  System.out.println("camera present: " + camera[k]);
         }
     //GET_KEY_STROKE
  }
  	if (num==3)
     {
       int search=0;
       int l=1;
       char found;
       //CLEAR_SCREEN
       System.out.println("Search no of phone");
       search=c.readline();
        while (search!=phone[l])
         {
  	l++;
  	}
    if (search==phone[l])
    {
     System.out.println("Phone no " + l + "  details");
     System.out.println("Phone no : " + phone[l]);
     System.out.println("Phone name : " + name[l]);
     System.out.println("Phone price : " + price[l]);
     System.out.println("Phone color : " + color[l]);
     System.out.println("Camera option : " + camera[l]);
    }
      //GET_KEY_STROKE
    }
     if (num==4)
     {
       System.out.println("yes\n");
       float avg=0;
       float avv=0;
       int z=0;
       for(z=1;z<=count;z++)
      {
       avg=price[z];
       avv=avv+avg;
      }
     System.out.println("The Average price of the phones is :  " + avv/2);
   //GET_KEY_STROKE
  }
    if(num==5)
     {
      int add=0;
      int y=0;
       for (y=1;y<=count;y++)
        {
         add=add+price[y];
       }
     System.out.println("The Total amount of phone prices : ");
     System.out.println(add);
     //GET_KEY_STROKE
      }
  //CLEAR_SCREEN
  System.out.println("Press 'y' to go to menu ");
  //INPUTc1;
  }
  //CLEAR_SCREEN
  System.out.println("bye bye press any key to exit");
  //GET_KEY_STROKE
 }
}

```

But i am getting this error message: 

```

Compiling 1 source file to C:\Documents and Settings\Home\Phone\build\classes

C:\Documents and Settings\Home\Phone\src\phone\Main.java:21: ']' expected

    long phone[50];

C:\Documents and Settings\Home\Phone\src\phone\Main.java:24: ']' expected

    long price[50];

2 errors

BUILD FAILED (total time: 0 seconds)


```

I am using Netbeans IDE 5.0 to compile this.

---

### Post by samjh on 2007-07-28
Your syntax is wrong.

In Java, arrays are declared like this:
```
long[] phone;
```

If you want to allocated a defined number of elements for an array, it is like this (a long-type array named phone with 50 elements):
```
phone = new long[50];
```

Be careful about using readLine() to store stuff into an integer variable.  You need to cast it, otherwise you will get an error.  Use something like this, where num is an int variable:
```
num = Integer.parseInt(c.readLine());
```

To be able to use readLine(), you need to put this line at the top of your code:
```
import java.io.Console;
```
That's like doing #include <iostream> in C++.

---

### Post by bbzbryce on 2007-07-28
> **LaRoza said:**
> If you are used to C++, Java will be easy (to learn).

The main differences are:
0. Java has garbage collection
1. Java is Object Obsessed
2. Java gives you less control, no pointers and references.
3. Java passed variables by value, and objects by reference
4. Java runs on any computer will the jre, so you don't have to worry about the OS
5. Java implements Objects slightly differently, although the concepts are the same
6. Generics are like Templates, but not exactly the same

One interesting aspect is that the main class, the one that contains main(String args[]), has to be the exact same name as the file, minus the extension, .java. When you compile, you get a file with the same name, but with the .class extension. When you run that, don't type the extension.

So, here is how you would compile and run the above program, which I called Phone.java.

```

$ javac Phone.java
$ java Phone

```

7. Java uses jagged arrays.

---

### Post by Cyberslam on 2007-07-29
I changed the syntax now. Here is the syntax:

```
import java.io.Console;

class Phone
{
    public static void main(String args[])
 {
  //CLEAR_SCREEN
    phone = new long[50];
    int count=0;
    String name;
    price = new long[50];
    String color;
    String camera;
    char c1='y'; 
    int num=0;
  while (c1=='y')
  {
    System.out.println("Enter your choice");
    System.out.println("1.store information");
    System.out.println("2.output information");
    System.out.println("3.search for phone by phone number");
    System.out.println("4.average price of phones");
    System.out.println("5.total price of the phones entered");
    System.out.println("Enter no for operation");
    num = Integer.parseInt(c.readLine());
    
    if (num==1)
            
     {
       char c='a';
         while (c=='a')
         {
         count++;
         int i=count;
         {
           System.out.println("enter phone number");
           phone = c.readLine()[i];
     	 System.out.println("enter phone name");
           name = c.readline()[i];
     	 System.out.println("enter price");
           price = c.readline()[i];
     	 System.out.println("enter color");
           color = c.readline()[i];
     	 System.out.println("camera option");
           camera = c.readline()[i];
          }
       
         System.out.println("Press 'a' to continue adding phone info");
       
     c = c.readline();
     }
  
  }
     if (num==2)
      {

        for (int k=1;k<=count;k++)
         {
            System.out.println("              phone  " + k + "  details ");
            System.out.println("phone no: " + phone[k]);
      	  System.out.println("phone name: " + name[k]);
      	  System.out.println("phone price: " + price[k]);
      	  System.out.println("phone color: " + color[k]);
      	  System.out.println("camera present: " + camera[k]);
         }

  }
  	if (num==3)
     {
       int search=0;
       int l=1;
       char found;

       System.out.println("Search no of phone");
        search = c.readline();
        while (search!=phone[l])
         {
  	l++;
  	}
    if (search==phone[l])
    {
     System.out.println("Phone no " + l + "  details");
     System.out.println("Phone no : " + phone[l]);
     System.out.println("Phone name : " + name[l]);
     System.out.println("Phone price : " + price[l]);
     System.out.println("Phone color : " + color[l]);
     System.out.println("Camera option : " + camera[l]);
    }

    }
     if (num==4)
     {
       System.out.println("yes\n");
       float avg=0;
       float avv=0;
       int z=0;
       for(z=1;z<=count;z++)
      {
       avg=price[z];
       avv=avv+avg;
      }
     System.out.println("The Average price of the phones is :  " + avv/2);

  }
    if(num==5)
     {
      int add=0;
      int y=0;
       for (y=1;y<=count;y++)
        {
         add=add+price[y];
       }
     System.out.println("The Total amount of phone prices : ");
     System.out.println(add);

      }

  System.out.println("Press 'y' to go to menu ");
    c1 = c.readline();
  }

  System.out.println("bye bye press any key to exit");

 }
}
```

But i am still getting the errors: 

```
C:\Documents and Settings\.....\Desktop\MyLib\src\Phone.java:3: cannot resolve symbol

symbol  : class Console 

location: package io

import java.io.Console;

C:\Documents and Settings\.....\Desktop\MyLib\src\Phone.java:10: cannot resolve symbol

symbol  : variable phone 

location: class Phone

    phone = new long[50];

C:\Documents and Settings\.....\Desktop\MyLib\src\Phone.java:13: cannot resolve symbol

symbol  : variable price 

location: class Phone

    price = new long[50];

C:\Documents and Settings\.....\Desktop\MyLib\src\Phone.java:27: cannot resolve symbol

symbol  : variable c 

location: class Phone

    num = Integer.parseInt(c.readLine());

.
.
.
.
.
.


```


What am i doing wrong now ? 


Thanks

---

### Post by gekkio on 2007-07-29
The first error means that javac cannot find the java.io.Console class. Are you using Java 1.6? It was added in 1.6 so you won't be able to compile your code with earlier JDKs. To see which version you are using, try running
```
java -version
javac -version
```

The next two errors occur because you replaced declarations with assignments.
This is a declaration (you are telling javac that the variable phone is of type long array)
```
long[] phone;
```
and this is an assignment (you are assigning a new long array of length 50 to variable phone)
```
phone = new long[50];
```
You could combine them to get
```
long[] phone = new long[50];
```
which is probably what you want here.

The last error occurs because you didn't declare the variable c. Just add
```
Console c = System.console();
```
before the first while-loop. Note that this won't compile unless you are using Java 1.6, so you'll need to fix error number one first.

---

### Post by samjh on 2007-07-29
I've just fixed up your code.

Here it is.  It should compile with no errors if you're using Java 1.6.  I've made quite a number of changes, such as using String instead of char for c1 and c2 to make life easier.  I've added type casting, fixed up array declarations (my previous explanation was incomplete, sorry), coding style, and added more robust checking for c1 and c2 values.  This is by no means a good program, but it should suffice to give you a start:
```
import java.io.Console;

class Phone {
	public static void main(String[] args) {
		Console c = System.console();
		long[] phone = new long[50];
		int count = 0;
		String[] name = new String[50];
		long[] price = new long[50];
		String[] color = new String[50];
		String[] camera = new String[50];
		String c1 = "y";
		int num = 0;
		while (c1.equalsIgnoreCase("y")) {
			System.out.println("Enter your choice");
			System.out.println("1.store information");
			System.out.println("2.output information");
			System.out.println("3.search for phone by phone number");
			System.out.println("4.average price of phones");
			System.out.println("5.total price of the phones entered");
			System.out.println("Enter no for operation");
			num = Integer.parseInt(c.readLine());
			if (num == 1) {
				String c2 = "a";
				while (c2.equalsIgnoreCase("a")) {
					count++;
					int i=count;
					System.out.println("enter phone number");
					phone[i] = Long.parseLong(c.readLine());
					System.out.println("enter phone name");
					name[i] = c.readLine();
					System.out.println("enter price");
					price[i] = Long.parseLong(c.readLine());
					System.out.println("enter color");
					color[i] = c.readLine();
					System.out.println("camera option");
					camera[i] = c.readLine();
					System.out.println("Press 'a' to continue adding phone info");
					c2 = c.readLine();
				}
			}
			if (num == 2)
				{
				for (int k=1;k<=count;k++) {
					System.out.println("              phone  " + k + "  details ");
					System.out.println("phone no: " + Long.toString(phone[k]));
					System.out.println("phone name: " + name[k]);
					System.out.println("phone price: " + Long.toString(price[k]));
					System.out.println("phone color: " + color[k]);
					System.out.println("camera present: " + camera[k]);
				}
			}
			if (num == 3) {
				int search=0;
				int l = 1;
				char found;
				System.out.println("Search no of phone");
				search = Integer.parseInt(c.readLine());
				while (search!=phone[l]) {
					l++;
				}
				if (search==phone[l]){
					System.out.println("Phone no " + l + "  details");
					System.out.println("Phone no : " + Long.toString(phone[l]));
					System.out.println("Phone name : " + name[l]);
					System.out.println("Phone price : " + Long.toString(price[l]));
					System.out.println("Phone color : " + color[l]);
					System.out.println("Camera option : " + camera[l]);
				}
			}
			if (num == 4) {
				System.out.println("yes\n");
				float avg = 0;
				float avv = 0;
				int z = 0;
				for(z = 1; z <= count; z++) {
					avg=price[z];
					avv=avv+avg;
				}
				System.out.println("The Average price of the phones is :  " + avv/2);
			}
			if(num == 5) {
				long add = 0;
				int y = 0;
				for (y = 1; y <= count; y++) {
					add = add + price[y];
				}
				System.out.println("The Total amount of phone prices : ");
				System.out.println(add);
			}
			System.out.println("Press 'y' to go to menu ");
			c1 = c.readLine();
		}
		System.out.println("bye bye press any key to exit");
	}
}
```

Here's a sample output when I run it:```
Enter your choice
1.store information
2.output information
3.search for phone by phone number
4.average price of phones
5.total price of the phones entered
Enter no for operation
1
enter phone number
123456
enter phone name
ph1
enter price
10
enter color
blue
camera option
y
Press 'a' to continue adding phone info
a
enter phone number
987654
enter phone name
ph2
enter price
20
enter color
red
camera option
n
Press 'a' to continue adding phone info
n
Press 'y' to go to menu 
y
Enter your choice
1.store information
2.output information
3.search for phone by phone number
4.average price of phones
5.total price of the phones entered
Enter no for operation
2
              phone  1  details 
phone no: 123456
phone name: ph1
phone price: 10
phone color: blue
camera present: y
              phone  2  details 
phone no: 987654
phone name: ph2
phone price: 20
phone color: red
camera present: n
Press 'y' to go to menu 
y
Enter your choice
1.store information
2.output information
3.search for phone by phone number
4.average price of phones
5.total price of the phones entered
Enter no for operation
3
Search no of phone
123456
Phone no 1  details
Phone no : 123456
Phone name : ph1
Phone price : 10
Phone color : blue
Camera option : y
Press 'y' to go to menu 
y
Enter your choice
1.store information
2.output information
3.search for phone by phone number
4.average price of phones
5.total price of the phones entered
Enter no for operation
4
yes

The Average price of the phones is :  15.0
Press 'y' to go to menu 
y
Enter your choice
1.store information
2.output information
3.search for phone by phone number
4.average price of phones
5.total price of the phones entered
Enter no for operation
5
The Total amount of phone prices : 
30
Press 'y' to go to menu 
y
Enter your choice
1.store information
2.output information
3.search for phone by phone number
4.average price of phones
5.total price of the phones entered
Enter no for operation
```

Hope that helps.

---

### Post by Cyberslam on 2007-07-29
I do have the Version 1.6. 

samjh, i tried compiling exactly the same code of your but i am still getting the errors

```
C:\Documents and Settings\....\Desktop\MyLib\src\Phone.java:3: cannot resolve symbol

symbol  : class Console 

location: package io

import java.io.Console;

C:\Documents and Settings\.....\Desktop\MyLib\src\Phone.java:7: cannot resolve symbol

symbol  : class Console 

location: class Phone

                Console c = System.console();

C:\Documents and Settings\......\Desktop\MyLib\src\Phone.java:7: cannot resolve symbol

symbol  : method console ()

location: class java.lang.System

                Console c = System.console();

```



Which program did use ? Or are using command prompt to do this ? 

i am using netbeans IDE 5.0. 

Thanks

---

### Post by samjh on 2007-07-29
Well I'm using the terminal (command prompt).

Open up terminal, navigate to the directory where the source file is, and do:
```
javac Phone.java
```

It *should* be fine.  I have sun-java6-jdk installed, and it compiles perfectly.

---

### Post by Cyberslam on 2007-07-29
When i type 

javac Phone.java in command prompt i get the error: 

javac is not recognized as an internal or external command.

---

### Post by samjh on 2007-07-29
That means you don't have the JDK (Java Development Kit) installed.  You need it to compile Java source code.

Do you have Fiesty Fawn (Ubuntu 7.04)?  If so, open up your terminal, and type this:
```
sudo apt-get install sun-java6-jdk
```
That will install the JDK for Java 1.6.

Then try compiling again.

---

### Post by Cyberslam on 2007-07-29
Actually i am using Windows XP. 

??

---

### Post by samjh on 2007-07-29
[SIZE="7"]![/SIZE]

Gosh, I was wondering!

First of all, you should have JDK 1.6 installed.  If in doubt, go to [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) and download JDK 6 Update 2, download the installer, and install it.

Take note of WHERE your JDK is installed.  It should be something like C:\Program Files\Java\jdk-1.6.0_02

Right-click on your My Computer icon on the desktop, select the Advanced tab, and click on the button labelled Environment (or Environment Variables).  A new window should pop up, and in the top-half of the window is a field labelled PATH.  Add the path where your JDK is installed and append \bin at the end of it.  So if your JDK is installed in C:\Program Files\Java\jdk-1.6.0_02, then you should add C:\Program Files\Java\jdk-1.6.0_02\bin to your PATH.

After all that, you should be able to run javac from your command prompt.

---

### Post by Cyberslam on 2007-07-29
There is no field named PATH at the location you mentioned. 

But i got it working using Netbeans and it compiles without any errors. 

Thanks a lot to you and to everyone who contributed in this thread. I really appreciate it and i have learned quite a few things about JAVA from this.

---

