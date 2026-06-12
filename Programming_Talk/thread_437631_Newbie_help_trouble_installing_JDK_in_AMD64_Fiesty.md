---
title: "Newbie help: trouble installing JDK in AMD64 Fiesty"
date: 2007-05-09
forum: Programming Talk
---

### Post by pcpete on 2007-05-09
I have searched around the forum quite a bit and am still confused. I have loved Fiesty Fawn, and in an effort to use Linux more (and learn Java) I have been trying to install the Java SDK. 

I have used the Sun Microsystem's manual install, and extracted the .bin to my home Folder. Afterwards, I tried creating a symbolic link with the command:

sudo ln -s /home/pete/jdk1.5.0_11/bin/javac ./

To my effort, the javac is still not working when compiling my tutorial files into bytecode! Therefore, I consulted trying to find Java in a package... Well, my repos look good but I didn't find it. Soon, I found the story that Sun cannot offcially create the .Debs....  therefore, I followed this:

[http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package](http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package)

 STILL a problem! For some reason, issueing make-jpkg with fakeroot has the error "No Plugins found"

In the end I considered this.... but I just wanted to see what the community thought!
[http://ubuntuforums.org/showthread.php?t=332674&highlight=java+sdk](http://ubuntuforums.org/showthread.php?t=332674&highlight=java+sdk)

**I have Fiesty Fawn 64bit running on my computer but I don't want to mess up the 32bit plugins for Java I setup with firefox32.... Additionally, I am not understanding what this GNU Java is. What is the best way to create 32bit compatible Java apps and not mess up my system. I will be happy to provide configuration files/ specs! Additionally, I might need n00b help with PATH/Classpath. Thanks-- I don't want to develope in the M$ environment! **

---

### Post by pcpete on 2007-05-09
Anyone install an SDK recently? Anyway I can get it running, I'll do. I did want to build the .deb Java SDK package so it could be updated through synaptic, but I'm not afraid of a manual install. Thing is-- my Java Runtime Environment is working so smooth I don't exactly want to remove that. LMK, I'll be rechecking this forum! 

I just have to say you guys should check out the Amarok player--- soooo sweet I just downloaded all the cover art!

---

### Post by LaRoza on 2007-05-09
I installed it graphically in Synaptic recently and it worked fine.

---

### Post by pcpete on 2007-05-09
Good to know. I do see an option to install it in AutoMATIX.... but it is a 64bit AMD edition. And frankly, I don't want to run into any problems making apps that don't work on 32bit Windows/Mac machines. Would the 64bit extention make a difference? Also.. Anyone have a method that really wouldn't screw up my current JRE. I just don't really know where the runtime is stored in Ubuntu. 

Thanks for your help!

---

### Post by pcpete on 2007-05-09
**UPDATE!!!**

Okay.... heres an update! I found Java SDK 5.0 (1.50_11) in the Synaptic package manager and installed that. Now, my "javac" seems to work perfectly as a non-root... however when I try to run the program in the terminal with "java" I get an error. 

I am just trying to run a simple "Beginning Programming for Dummies" demo program called "Mortage.java" 
---------------------------------------------------------------
pete@allamerican:~/java$ javac Mortage.java
bash: ./Mortgage.class: Permission denied
pete@allamerican:~/java$ Mortgage.class 
bash: Mortgage.class: command not found
pete@allamerican:~/java$ java Mortgage
Exception in thread "main" java.lang.IllegalArgumentException: The currency code, $, is not supported.
   at java.util.Currency.getInstance(libgcj.so.70)
   at java.text.DecimalFormatSymbols.getCurrency(libgcj.so.70)
   at java.text.DecimalFormat.getCurrency(libgcj.so.70)
   at java.text.NumberFormat.getCurrencyInstance(libgcj.so.70)
   at java.text.NumberFormat.getCurrencyInstance(libgcj.so.70)
   at Mortgage.main(Mortgage.java:18)



^^HERE IS THE ERROR. I didn't bother with CLASSPATH/PATH. What do you'll think? 

Thanks again!

---

### Post by LaRoza on 2007-05-09
Could you show the code?

---

### Post by pcpete on 2007-05-09
Heres the code in the file Mortage.java I am just starting out in Java, so its all giberish to me. But here goes:

import java.io.*;
import java.text.NumberFormat;

public class Mortgage 
{

   public static void main(String args[]) throws IOException
   {

      BufferedReader keyboard =
         new BufferedReader(new InputStreamReader(System.in));
      double principal, rate, ratePercent;
      int years, n;
      final int paymentsPerYear = 12;
      final int timesPerYearCalculated = 12;
      double effectiveAnnualRate;
      double payment;
      NumberFormat currency = NumberFormat.getCurrencyInstance();

      System.out.println();
      System.out.print("How much are you borrowing?            ");
      principal = Double.parseDouble(keyboard.readLine());
      System.out.print("What's the interest rate?              ");
      ratePercent = Double.parseDouble(keyboard.readLine());
      rate = ratePercent/100.00;
      System.out.print("How many years are you taking to pay?  ");
      years = Integer.parseInt(keyboard.readLine());
      System.out.println("------------------------------");

      n = paymentsPerYear * years;
      effectiveAnnualRate = rate / paymentsPerYear;
      payment = principal*(effectiveAnnualRate / (1 - Math.pow(1 + effectiveAnnualRate, -n)));
      System.out.print("Your monthly payment is                ");
      System.out.println(currency.format(payment));
      System.out.println();
   }
}

(this is from a proven Dummies book so I am assuming the syntax is good!)

---

### Post by LaRoza on 2007-05-09
I noticed that you are in the "java" directory, leave that and go back to home.

Write a simpler program, the "hello world!" program:

```

class hw
{
    public static void main(String args[])
    {
        System.out.println("Hello world!");      
    }
}

```

Save it as hw.java, in your home directory, use this command: javac hw

then run it: java hw

Does it work?

By the way, books have errors in them, and you may not have what they are using, especially if you do not understand it.

---

### Post by pcpete on 2007-05-09
You are correct, the "Hello World" hw.java was compiled and run successfully in my home folder... 

I then tried moving Mortage.java to my home directory and when trying to compile (with javac) the error generated was:
-------------------------
pete@allamerican:~$ javac Mortage2.java 
Mortage2.java:4: class Mortgage is public, should be declared in a file named Mortgage.java
public class Mortgage 
       ^
1 error
-------------------------

Thanks for your persistant help, I am really encouraged to get this going. If I need to reinstall/remove anything I am certainly willing. Also bear in mind a 32bit package is totally cool (there are no real 64bit plugins yet for the browser!).

---

### Post by LaRoza on 2007-05-10
The name of the source files must be the same name as the class, case counts.

"Mortgage" is the name of your class, the file must be called "Mortgage.java".

When posting error messages, it is a good idea to tell the name of the file, and post the code.

I hope it works:)

---

### Post by jespdj on 2007-05-10
> **pcpete said:**
> Good to know. I do see an option to install it in AutoMATIX.... but it is a 64bit AMD edition. And frankly, I don't want to run into any problems making apps that don't work on 32bit Windows/Mac machines. Would the 64bit extention make a difference? Also.. Anyone have a method that really wouldn't screw up my current JRE. I just don't really know where the runtime is stored in Ubuntu. 

Thanks for your help!

For programming in Java it doesn't matter if you use the 64-bit or 32-bit version of Java. The Java bytecode that the compiler produces will be exactly the same. The only difference between the 64-bit and 32-bit version of the Java VM is in the implementation of the VM itself.

So you don't need to get the 32-bit version if you want to be sure that your Java program will run on 32-bit Windows or Mac.

If you have 64-bit Ubuntu, just use the 64-bit version of Java, unless you want / need the Java browser plug-in to run applets in your browser; the 64-bit version of Java unfortunately doesn't include the browser plug-in.

---

### Post by pcpete on 2007-05-10
thanks for your help guys--- consider this all solved up! Seems like everything is working. I love Ubuntu!

---

