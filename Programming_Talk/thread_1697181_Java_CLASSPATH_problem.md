---
title: "Java CLASSPATH problem"
date: 2011-02-28
forum: Programming Talk
---

### Post by avs3323 on 2011-02-28
Hi,  

I have some java files that I am trying to compile that uses Junit. 

I have the path to the junit.jar in my $CLASSPATH, but it does not seem to work in javac.  However, when I pass the classpath to javac it works fine.

For example:

javac *.java does not work

BUT

javac -classpath $CLASSPATH *.java DOES work

So my environment variable is set, but it seems that javac is not reading it

Can anyone help me?

---

