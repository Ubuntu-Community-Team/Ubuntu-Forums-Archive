---
title: "[SOLVED] Java Packages"
date: 2008-08-13
forum: Programming Talk
---

### Post by Java Geek on 2008-08-13
Hello everyone. I have recently tried to run a pre-made Java package called com.webs.masterprogrammer.calc and it is not compiling.

This is a java swing program. The caller file (Calculator.java) is trying to call SimpleCalculator.java, but i get this error:

 Calculator.java:1: package com.webs.masterprogrammer does not exist
import com.webs.masterprogrammer.calc;
                           ^
Calculator.java:5: cannot find symbol
symbol  : class SimpleCalculator
location: class Calculator
		SimpleCalculator simple = new SimpleCalculator();
		^
Calculator.java:5: cannot find symbol
symbol  : class SimpleCalculator
location: class Calculator
		SimpleCalculator simple = new SimpleCalculator();


I have the proper folders set up and the .class files in the right places, but The caller file will not compile because it cannot "find" the package files. I think i have to set the classpath or something to make it compile.

---

