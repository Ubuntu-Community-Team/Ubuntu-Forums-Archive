---
title: "Problems in Java, Scanner. ubuntu 9,04"
date: 2010-01-14
forum: Programming Talk
---

### Post by Guitar-maniac on 2010-01-14
I'm using Eclipse for coding Java and i cannot get the Scanner working, eclipse says it cannot resolve it.

I searched the forums and found some help but it did not work. :(

heres the version of my Compiler/Java:
javac 1.6.0_16
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Server VM (build 14.2-b01, mixed mode)

i also used "sudo update-alternatives --config java" and chose: "/usr/lib/jvm/java-6-sun/jre/bin/java" option as suggested. but it still don't work, not from eclipse or when trying to compile from console.

---

### Post by nmccrina on 2010-01-14
Could you post your code? Are you importing java.util.Scanner?

---

### Post by Guitar-maniac on 2010-01-14
import java.util.Scanner;

public class test 
{
 public static void main(String[] args) 
{

    int luku;
    Scanner scan = new Scanner(System.in);

    System.out.println("Anna luku: ");
    luku = scan.nextInt();
    System.out.println("\n"+luku);
    }
} 

I am just learning to code in Java, so there may be a possibility that i have written something wrong..?

---

### Post by nmccrina on 2010-01-14
What you have there works for me, in Eclipse and manually on the terminal. Weird.

---

### Post by Zugzwang on 2010-01-14
At some point, I've read in this forum that Eclipse has its own dialog for choosing the JVM used and is unaffected by this "sudo update-alternatives --config java" thing. Also don't forget "sudo update-alternatives --config javac".

---

### Post by nmccrina on 2010-01-14
> **Zugzwang said:**
> At some point, I've read in this forum that Eclipse has its own dialog for choosing the JVM used and is unaffected by this "sudo update-alternatives --config java" thing. Also don't forget "sudo update-alternatives --config javac".

I have never done any of this. I just installed the sun-java6-jdk and eclipse packages, and everything "just worked". If the OP removed eclipse and java and then reinstalled them (to clear these java-alternatives settings), would that fix the problem?

---

### Post by Zugzwang on 2010-01-14
> **nmccrina said:**
> I have never done any of this. I just installed the sun-java6-jdk and eclipse packages, and everything "just worked". If the OP removed eclipse and java and then reinstalled them (to clear these java-alternatives settings), would that fix the problem?

The possibility I've mentioned is just a possibility. However, the difference between your computer and the OP's one might be that you don't have GCJ installed whereas the OP has. In this case, eclipse could have chosen a different JVM as the default one.

---

### Post by nmccrina on 2010-01-14
> **Zugzwang said:**
> The possibility I've mentioned is just a possibility. However, the difference between your computer and the OP's one might be that you don't have GCJ installed whereas the OP has. In this case, eclipse could have chosen a different JVM as the default one.

Either way, I guess the best thing to do would be to go into Eclipse, go to Window->Preferences and under "Installed JRE's" make sure that what's there matches up with what you know or think you know is on your computer. :)

---

### Post by Guitar-maniac on 2010-01-15
> **nmccrina said:**
> Either way, I guess the best thing to do would be to go into Eclipse, go to Window->Preferences and under "Installed JRE's" make sure that what's there matches up with what you know or think you know is on your computer. :)
 
 
Ok, i'll try that one out :) two weeks to Java Exam so i really shuold have to get it working so i can practice at home. thanks for the replies.

---

### Post by Guitar-maniac on 2010-01-15
I checked the windows => preferences => installed JRE's, there was java-1.5.0-gcj-4.3-1.5.0.0.

Can/should i somehow update it? since console shows my java/javac is 1.6.0.

---

