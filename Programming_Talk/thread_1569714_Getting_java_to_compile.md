---
title: "Getting java to compile"
date: 2010-09-07
forum: Programming Talk
---

### Post by ptpare on 2010-09-07
I am trying to learn the JAVA programming language but I am finding it very difficult to get past first base.
The problem seems to be with the CLASSPATH setting.
I am running Linux Ubuntu Hardy Heron and I have included some of my terminal output below.
I have eventually managed to compile SIUnits, List.java, Text.java, Graph.java and Display. java from Judith Bishop's book, Java Gently for Engineers and Scientists, but I can not get TrainTravel.java or any of the other programes in Chapter 2 of the book to compile.

I received the following output:```

bad class file: /home/phillip/java/javagently/Text.class
class file contains wrong class: javagently.Text
Please remove or make sure it appears in the correct subdirectory of the classpath.
("The journey covers " + Text.format(totalDistance,5,2) + " km");
^
1 error
```

I have included My session history, the Text.java file and the TrainTravel.java file below
I was redirected to this forum after having initially posted in the Absolute Beginner forum.

Would Netbeans be an easier way to learn Java? I tried a Windows version of Netbeans but even there I had difficulties in getting everything to compile. 

Would Netbeans also be able to work with the OpenJDK or would I have to use the Sun JDK?

I did implement the following instructions:

Starting with java-common 0.23ubuntu1, the update-java-alternatives 
script can be used to set a bunch of jre/jdk alternatives: 

- Set all runtime tools to point to the openjdk-6 alternatives: 

  update-java-alternatives --jre --set java-6-openjdk 

- Set all runtime tools (headless only) to point to the openjdk-6 
  alternatives: 

  update-java-alternatives --jre-headless --set java-6-openjdk 

- Set all runtime and development tools to point to the openjdk-6 
  alternatives: 

  update-java-alternatives --set java-6-openjdk 

- Set all runtime and development tools to auto mode: 

  update-java-alternatives --auto


Any help will be appreciated.
Thank you.
Regards

Phillip


I found the JDK version that I am using as follows:

```
phillip@voogdy-study:~/java/myprograms/ch2$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1~8.04.3)
OpenJDK Client VM (build 16.0-b13, mixed mode, sharing)
phillip@voogdy-study:~/java/myprograms/ch2$
```

My session history:

```
phillip@voogdy-study:~$ echo $CLASSPATH

phillip@voogdy-study:~$ export CLASSPATH=~/java/:.
phillip@voogdy-study:~$ echo $CLASSPATH
/home/phillip/java/:.
phillip@voogdy-study:~$ javac Graph.java
javac: file not found: Graph.java
Usage: javac <options> <source files>
use -help for a list of possible options
phillip@voogdy-study:~$ cd java
phillip@voogdy-study:~/java$ cd javagently
phillip@voogdy-study:~/java/javagently$ ls
Display.java List.class List$Node.class Text.java
Graph.java List.java Text.class
phillip@voogdy-study:~/java/javagently$ javac Graph.java
phillip@voogdy-study:~/java/javagently$ export CLASSPATH=$CLASSPATH:~/java/javagently/
phillip@voogdy-study:~/java/javagently$
phillip@voogdy-study:~/java/javagently$ echo $CLASSPATH
/home/phillip/java/:.:/home/phillip/java/javagently/
phillip@voogdy-study:~/java/javagently$ ls
Display.java Graph.java List.java Text.java
phillip@voogdy-study:~/java/javagently$ cd ..
phillip@voogdy-study:~/java$ cd ..
phillip@voogdy-study:~$ javac text.java
javac: file not found: text.java
Usage: javac <options> <source files>
use -help for a list of possible options
phillip@voogdy-study:~$ echo $CLASSPATH
/home/phillip/java/:.:/home/phillip/java/javagently/
phillip@voogdy-study:~$ cd java
phillip@voogdy-study:~/java$ cd javagently
phillip@voogdy-study:~/java/javagently$ ls
Display.java Graph.java List.java Text.java
phillip@voogdy-study:~/java/javagently$ cd ..
phillip@voogdy-study:~/java$ cd ..
phillip@voogdy-study:~$ javac Text.java
javac: file not found: Text.java
Usage: javac <options> <source files>
use -help for a list of possible options
phillip@voogdy-study:~$ cd java
phillip@voogdy-study:~/java$ cd javagently
phillip@voogdy-study:~/java/javagently$ ls
Display.java Graph.java List.java Text.java
phillip@voogdy-study:~/java/javagently$ javac Text.java
phillip@voogdy-study:~/java/javagently$ javac List.java
phillip@voogdy-study:~/java/javagently$ javac Graph.java
phillip@voogdy-study:~/java/javagently$ javac Display.java
Note: Display.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
phillip@voogdy-study:~/java/javagently$ ls
Display$1.class Display$Watcher.class Graph.java List$Node.class
Display.class Graph$1.class Graph$Point.class Text.class
Display$Data.class Graph.class List.class Text.java
Display.java Graph$Dataset.class List.java
phillip@voogdy-study:~/java/javagently$ cd ..
phillip@voogdy-study:~/java$ cd myexamples
bash: cd: myexamples: No such file or directory
phillip@voogdy-study:~/java$ cd myprograms/
phillip@voogdy-study:~/java/myprograms$ ls
ch10 ch2 ch3 ch4 ch5 ch6 ch7 ch8 ch9
phillip@voogdy-study:~/java/myprograms$ cd ch2
phillip@voogdy-study:~/java/myprograms/ch2$ ls
DisplayWarning.java NewFleet.java SIUnits.class TrainTravel.java
LiquidFlow.java Resistance.java SIUnits.java TrigGraphs.java
phillip@voogdy-study:~/java/myprograms/ch2$ javac TrainTravel.java
TrainTravel.java:40: cannot access Text
bad class file: /home/phillip/java/javagently/Text.class
class file contains wrong class: javagently.Text
Please remove or make sure it appears in the correct subdirectory of the classpath.
("The journey covers " + Text.format(totalDistance,5,2) + " km");
^
1 error
phillip@voogdy-study:~/java/myprograms/ch2$ javac TrigGraphs.java
TrigGraphs.java:15: cannot access Graph
bad class file: /home/phillip/java/javagently/Graph.class
class file contains wrong class: javagently.Graph
Please remove or make sure it appears in the correct subdirectory of the classpath.
Graph g = new Graph("Sine and Cosine","x","y");
^
1 error
```

[php]package javagently;

import java.io.*;
import java.util.*;
import java.text.*;

This is the Text.java file:

public class Text {

  public Text () {};

  /* The All New Famous Text class     by J M Bishop  Aug 1996
   *            revised for Java 1.1 by Alwyn Moolman Aug 1997
   *            revised for efficiency by J M Bishop Dec 1997
   *            revised with renamed output methods
   *              by J M Bishop in July 1999
   * 
   * Provides simple input from the keyboard and files.
   * Now also has simple output formatting methods
   * and file opening facilities.
   *
   * public static void   prompt (String s)
   * public static int    readInt (BufferedReader in)
   * public static double readDouble (BufferedReader in)  
   * public static String readString (BufferedReader in)  
   * public static char   readChar (BufferedReader in) 
   * public static String writeInt (int number, int align)
   * public static String writeDouble 
                   (double number, int align, int frac)
   * public static BufferedReader open (InputStream in)
   * public static BufferedReader open (String filename)
   * public static PrintWriter create (String filename)
   */

  private static StringTokenizer T;
  private static String S;

  public static BufferedReader open (InputStream in)  {
    return new BufferedReader(new InputStreamReader(in));
  }

  public static BufferedReader open (String filename) 
	throws FileNotFoundException {
    return new BufferedReader (new FileReader (filename));
  }
  
  public static PrintWriter create 
	 (String filename) throws IOException {
    return new PrintWriter (new FileWriter (filename));
  }

  public static void prompt (String s) {
    System.out.print(s + " ");
    System.out.flush();
  }

  public static int readInt (BufferedReader in) throws IOException {
      if (T==null) refresh(in);
      while (true) {
        try {
          return Integer.parseInt(T.nextToken());
        }
        catch (NoSuchElementException e1) {
          refresh (in);
        }
        catch (NumberFormatException e2) {
          System.out.println("Error in number, try again.");
        }
      }
   }

 public static char readChar (BufferedReader in) throws IOException {
      if (T==null) refresh(in);
      while (true) {
        try {
          return T.nextToken().trim().charAt(0);
        }
        catch (NoSuchElementException e1) {
          refresh (in);
        }
      }
   }

 public static double readDouble (BufferedReader in) throws IOException {
      if (T==null) refresh(in);
      while (true) {
        try {
          String item = T.nextToken();
          return Double.valueOf(item.trim()).doubleValue();
        }
        catch (NoSuchElementException e1) {
          refresh (in);
        }
        catch (NumberFormatException e2) {
          System.out.println("Error in number, try again.");
        }
      }
   }

  public static String readString (BufferedReader in) throws IOException {
    if (T==null) refresh (in);
    while (true) {
      try {
        return T.nextToken();
      }
      catch (NoSuchElementException e1) {
        refresh (in);
      }
    }
  }

  private static void refresh (BufferedReader in) throws IOException {
    S = in.readLine ();
    if (S==null) throw new EOFException();
    T = new StringTokenizer (S);
  }

  //  Format methods
  //  --------------

  private static DecimalFormat N = new DecimalFormat();
  private static final String spaces = "                    ";
  
  public static String format(double number, int align, int frac) {
    N.setGroupingUsed(false);
	N.setMaximumFractionDigits(frac);
	N.setMinimumFractionDigits(frac);
	String num = N.format(number);
	if (num.length() < align)
	   num = spaces.substring(0,align-num.length()) + num;
    return num;
  }
  
  public static String format(int number, int align) {
    N.setGroupingUsed(false);
    N.setMaximumFractionDigits(0);
    String num = N.format(number);
    if (num.length() < align)
       num = spaces.substring(0,align-num.length()) + num;
    return num;
  }

  public static String writeDouble (double number, int align, int frac) {
    // Deprecated in July 1999 but retained for compatability
	return format (number, align, frac);
  }
  
  public static String writeInt (int number, int align) {
    // Deprecated in July 1999 but retained for compatability
  	return format (number, align);
  }
}
This is the TrainTravel.jar file:

import javagently.*;

class TrainTravel {

  /* The Train Travel Program           J M and N T Bishop
     ========================           1990, 1999
   *
   * Calculates the distance travelled under acceleration,
   * constant speed and deceleration.
   * Illustrates constants, variables, expressions and printing
   */

  static final double startAcceleration = 0.5;     //  m/s/s
  static final double deceleration = 1.0;     //  m/s/s
  static final double time1 = 2;              //  min
  static final double time2 = 3;              //  min
  static final double kilo = 1000;   
                         // metre to km conversion factor

  public static void main (String args []) {
    System.out.println("******* Train travel *******\n");
    System.out.println(startAcceleration + 
                       " m/s/s decreasing to 0 in " +
                       time1 + " mins,");
    System.out.println("constant speed for " + time2 + " mins,");
    System.out.println("and " + deceleration + "m/s/s to rest\n");
    
  // Perform the calculation in simple steps, saving
  // each partial result

    double secs1 = time1*60;    // time1 in secs
    double secs2 = time2*60;    // time2 in secs
    double velocity = 0.5 * startAcceleration * secs1;
    double distance1 = (startAcceleration * secs1 * secs1) / 3;
    double distance2 = velocity * secs2;
    double distance3 = velocity * velocity / (2 * deceleration);
    double totalDistance = (distance1 + distance2 + distance3) 
                           / kilo;
    System.out.println
           ("The journey covers " + Text.format(totalDistance,5,2) + " km");
  }
}[/php]

---

### Post by Joeb454 on 2010-09-07
Moved to **Programming Talk**

Also added [noparse][code] tags to the terminal output, and [php][/noparse] tags to the java code (for syntax highlighting).

---

### Post by dwhitney67 on 2010-09-07
It would seem the OP thinks that the CLASSPATH setting will allow him to compile his Java source code from any directory location he is at; this is not true.

The CLASSPATH is used by the JRE during runtime to locate compiled Java classes.

P.S.  I personally prefer to use Sun's JDK versus using the OpenJDK.  YMMV with the choice you choose.

---

### Post by VernonA on 2010-09-07
Both when you are compiling and when you are executing a Java program, the CLASSPATH variable tells the compiler/JVM where to find class files used by the class you typed. So when you enter, say, "java Graph", the JVM tries to execute Graph.class by looking for a file with this name in the current directory and in the dirs named in the class-path. You can actually supply the classpath as part of the command line, or for convenience you can put it in a system var called CLASSPATH as you are doing. If Graph uses the Text class, then the file Text.class also needs to exist in the class path you supplied. In the examples you give, this is often not true. Note that if Text.class is in the same dir as Graph.class, and you are in that directory too, you don't really need to supply a class-path at all. You only need to supply classpaths if you are using classes in a different directory from your current one.

One final point. The src files you give use a "package" declaration. This impacts the classpath, as it tells the compiler/JVM that classes are in subdirectories with the given package name. Whilst you are getting Java clear in your head you might want to comment out these lines, then add them back as you understand what is going on.

---

### Post by raffaele181188 on 2010-09-07
This error seems strange to me. Can you provide a tarball? Maybe uplodading it on mediafire.com or else..
Your CLASSPATH contains ~/java/, so the compiler should find javagently.Text
It seems there's something wrong with your class qualified name. Anyway I can't reproduce a similar behavior on my machine.
I also prefer Sun's JDK, and I think starting with an IDE would be a good idea because you can learn the Java language without these build/runtime complications, which are managed by the IDE for you. After the learning phase you can study the build/runtime process to deploy your application, but I have never thought it's better to start with a text editor

---

### Post by ptpare on 2010-09-07
@Joeb454, dwhitney67, VernonA, raffaele181188
Thank you all for your useful comments.
Which IDE would you recommend for a newcomer to JAVA - Eclipse or Netbeans, or something else? Would Netbeans work on Ubuntu?

---

### Post by raffaele181188 on 2010-09-07
Often Java IDEs are developed in Java, so they are available on all platforms ;)

Lots of people like Eclipse (for other languages too) but I think that recently Netbeans filled the gap. Also, Netbeans often implements most recent features, being the official Sun IDE. I feel NB interface better designed and, above all, it boasts Matisse which is the best GUI visual builder available for FREE (Eclipse has no a good free one).
Worth mentioning, Eclipse is far more used then NB, so you have more chances to get help

My suggestion is starting with NB
(Regarding NB, I remember that it looked very ugly on my Ubuntu box, so I used the Metal laf, available only in the Sun JDK! If you are interested, the switch is --laf javax.swing.plaf.metal.MetalLookAndFeel .. Here is the link [http://wiki.netbeans.org/FaqCustomLaf](http://wiki.netbeans.org/FaqCustomLaf))

Good luck

---

