---
title: "SuperBeginner - Java"
date: 2010-03-05
forum: Programming Talk
---

### Post by hakermania on 2010-03-05
Hello.I haven't made my first java program yet, because I have no idea how to execute it.I have installed java runtime 6
and gcj
What do I need to do?
Plz give me an example of a java program and explain me a bit as well. Thank you!!!!:D

---

### Post by radeon21 on 2010-03-05
Your best bet is probably to check out this thread:

[http://ubuntuforums.org/showpost.php?p=1997993](http://ubuntuforums.org/showpost.php?p=1997993)

---

### Post by GregBrannon on 2010-03-05
For a Java textbook that you can download for free:

[http://math.hws.edu/javanotes/]("http://math.hws.edu/javanotes/")

---

### Post by hyperAura on 2010-03-06
hello there.. first program i write in every single language is hello world.. in java this is:

public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }//main
}//class Hello

this is the simplest program you can have but you have to understand some keywords such as:

public
static
void
main

i see the other guys have provided u some notes so it wont be hard.. if u need any more example programs i can provide u as long as it is for training purposes..

---

### Post by hyperAura on 2010-03-06
once u understand the main concepts u can seek help by having a look at the java api which provides u with loads of methods and classes according to what u want to do..

[http://java.sun.com/j2se/1.4.2/docs/api/](http://java.sun.com/j2se/1.4.2/docs/api/)

---

### Post by karthick ayyapillai on 2010-03-08
hi 
if you are using ubuntu then you will get a inbuilt JAVA version 6 in the kernel source you dont need to install anything all you need to do is open the terminal and type javac you will get a list of commands if you have java installed and then if you type java --version it will display the details of the installed version to you .
if you want to create a program follow this 
in terminal go to your desktop and then type mkdir java_tut
cd java_tut
fire the vim editor 
vim simple.java
you can start your program now 
press i before typing and then 
type the code
class simple{
public static void main(String[ ] args ){
System.out.println("hello ");
}
}
then press esc key type in wq! your file is saved now 
then in terminal type javac simple.java
your class file will be created now 
then finally type java simple 
you ll get the output as hello in terminal 
NOTE L if you want a GUI IDE try NETBEANS is a best one for JAVA and sun products.

---

