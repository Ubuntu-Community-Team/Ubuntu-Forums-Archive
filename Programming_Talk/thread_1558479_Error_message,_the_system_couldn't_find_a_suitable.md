---
title: "Error message, the system couldn't find a suitable main method?"
date: 2010-08-22
forum: Programming Talk
---

### Post by Diaby does Gallas on 2010-08-22
I am trying to run this basic bit of code in JCreator which I have got from thenewboston:
 
import java.util.Scanner;
 
class Building a Basic Calculator 7 {
public static void main(String args[]){
Scanner anthony = new Scanner(System.in);
double fnum, snum, answer; //fnum mean first num, snum mean second num
System.out.println("Enter first num: ");
fnum = anthony.nextdouble();
System.out.println("Enter second num: ");
snum = anthony.nextDouble();
answer = fnum + snum;
System.out.println(answer);
}
}
 
 
I have done everything that was asked but when I compile the program I get an error saying that a '}' is required on linne 3, and if I try to run the program it just says that the system couldn't find a suitable main method, can you please tell me where I may be going wrong?

---

### Post by geirha on 2010-08-22
First off, please put code-tags around code so whitespace doesn't get squeezed.

The actual problem with that code is that you're trying to create a class name with spaces. That is not allowed. It must be one word.
```
class BasicCalculator7 {
  ...

```

---

### Post by Diaby does Gallas on 2010-08-22
> **geirha said:**
> First off, please put code-tags around code so whitespace doesn't get squeezed.
 
The actual problem with that code is that you're trying to create a class name with spaces. That is not allowed. It must be one word.
```
class BasicCalculator7 {
  ...

```
 
 
Okay will do and thanks!
 
Shabba!

---

### Post by geirha on 2010-08-22
Oh, and each java file, should have a public class with the same name as the java file. So you should add public in front of class and save that in a file called "BasicCalculator7.java"
```
import java.util.Scanner;

public class BasicCalculator7 {
    public static void main...

```

---

### Post by Diaby does Gallas on 2010-08-22
> **geirha said:**
> Oh, and each java file, should have a public class with the same name as the java file. So you should add public in front of class and save that in a file called "BasicCalculator7.java"
```
import java.util.Scanner;
 
public class BasicCalculator7 {
    public static void main...

```
 
 
Thanks very much got it working, the thing is though I have been getting that error message for ages and never knew what the problem was, and now I know so maximum respect!:guitar::KS

---

