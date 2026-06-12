---
title: "Javadoc missing from netbeans 6.9"
date: 2011-08-21
forum: Programming Talk
---

### Post by briigga on 2011-08-21
I downloaded netbeans 6.9 and have open jdk 6 and my javadoc wont work. When the javadoc window pops up when i am writing code it says javadoc not found.

Anyone experience/solve this.

---

### Post by briigga on 2011-08-21
Found a solution.


Go to Netbeans and click tools -> java platforms -> click the javadoc tab and go to add.

From there, navigate to the java jdk 6 directory.. mine is: usr/lib/jvm/java-6-openjdk

and add the entire doc folder. So after adding it you should see the following directory if yours is like mine:

usr/lib/jvm/java-6-openjdk/doc

Netbeans should now have the javadoc working.

Alternatively, if you do the not the doc folder and are missing those contents, you can find them on the oracle website under downloads and additional resources.

---

