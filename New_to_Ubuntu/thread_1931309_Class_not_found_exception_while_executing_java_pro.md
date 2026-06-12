---
title: "Class not found exception while executing java progs"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by ray93 on 2012-02-25
installed mysql and jdbc recently on my ubuntu 11.04
Referred to the forum to connect sql and java. 
i made the following changes to /etc/environment using ht evi editor in the terminal
 sudo vi /etc/environment
CLASSPATH=".:/usr/share/java/mysql.jar"

after logging out/in i typed in 
echo $CLASSPATH as per the directions and got this output

":/usr/share/java/mysql.jar"

now the problem is i am not able to execute any java program.
the compilation occurs,  .class file is present but whenever i run
javac A.java
java A in the terminal, a ClassNotFoundException occurs

code :
class A
 {
  public static void main(String args[])
    {
      System.out.println("ABC");
    }
 }
there had been no prior problems executing java progs...
Please Help :confused:

this

---

### Post by jacob.david on 2012-02-25
This is because the java interpreter is looking for A.class in the value of CLASSPATH. As it doesn't found a one you are getting this error. Try the following

java -cp <path containing A.class> A

You can also add is path to CLASSPATH ( or a simple . that will look under current directory)
Things could be slightly different when you start using packages.

---

