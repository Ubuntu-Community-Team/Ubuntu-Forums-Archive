---
title: "Problem with running junit"
date: 2012-11-10
forum: Programming Talk
---

### Post by karnpreet on 2012-11-10
Hello,

I made two classes on my school computers named SortArray.java and SortArrayTest,java (being the test file) and it was compiling and working fine on their system, but when I try to compile and do the test on my computer at home it doesn't seem to work. I have Ubuntu 12.10 and have junit all installed. I do the following:-

> kevin@ubuntu:~/JavaG/Wk4/Ex2$ javac SortArray.java
kevin@ubuntu:~/JavaG/Wk4/Ex2$ javac -cp /usr/share/java/junit4.jar SortArrayTest.java
SortArrayTest.java:8: error: cannot find symbol
SortArray test;
^
  symbol:   class SortArray
  location: class SortArrayTest
SortArrayTest.java:11: error: cannot find symbol
test = new SortArray();
           ^
  symbol:   class SortArray
  location: class SortArrayTest
2 errors
kevin@ubuntu:~/JavaG/Wk4/Ex2$ ^C
kevin@ubuntu:~/JavaG/Wk4/Ex2$ 

Can anyone help me?

---

### Post by ofnuts on 2012-11-10
You explicitly set a class path but it doesn't contain the directory for SortArray.class. Try:
```

javac -cp /usr/share/java/junit4.jar:. SortArrayTest.java

```(I.e., add the current directory to the class path)

---

### Post by r-senior on 2012-11-10
Try adding the current directory to the classpath:

```
javac -cp .:/usr/share/java/junit4.jar SortArrayTest.java
```

---

### Post by karnpreet on 2012-11-10
It seems to work but everytime I put

> java org.junit.runner.JUnitCore SortArrayTest.java

it just doesn't seem to work as it comes out with the error :- 

> Error: Could not find or load main class org.junit.runner.JUnitCore

---

### Post by karnpreet on 2012-11-10
This is what happens:-

> kevin@ubuntu:~/JavaG/Wk4/Ex2$ javac SortArray.java
kevin@ubuntu:~/JavaG/Wk4/Ex2$ javac -cp .:/usr/share/java/junit4.jar SortArrayTest.java
kevin@ubuntu:~/JavaG/Wk4/Ex2$ java org.junit.runner.JUnitCore SortArrayTest.javaError: Could not find or load main class org.junit.runner.JUnitCore


---

### Post by r-senior on 2012-11-10
Don't you need to specify the classpath again?

```
java -cp .:/usr/share/java/junit4.jar org.junit.runner.JUnitCore SortArrayTest
```

---

### Post by karnpreet on 2012-11-10
You are literally a life saver, thank you so much!

---

