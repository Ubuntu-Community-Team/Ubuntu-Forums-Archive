---
title: "Help with System.out.println in Java"
date: 2012-10-21
forum: Programming Talk
---

### Post by vikkyhacks on 2012-10-21
I am moving from C# to Java ... In C# I have can output any statement like 

```
Console.WriteLine("Hello mr {0}, u are {1}.",myName,myType)
```

which will output-> "Hello mr Vikky u are tall"

but in Java I am forced to write with my arguments in between the string as 

```
System.out.println("Hello my"+myName+"You are"+myType);
```

any way to do it like C#, It gets confusing to pass the arguments like in the end hw it is in C#

---

### Post by trent.josephsen on 2012-10-21
System.out.printf follows C semantics mostly. You do have to add the newline explicitly if you want it.

```
System.out.printf("Hello, %s. You are %s\n", myName, myType);
```

---

### Post by CoreyB. on 2012-10-21
In java's System.out.println(), your not passing arguments in the middle of the string.  You are concatenating a string with other strings/primitives forming one string, and that string is passed into System.out.println().

---

### Post by vikkyhacks on 2012-10-21
problem solved .... Thanks !!!

---

### Post by muteXe on 2012-10-21
[http://docs.oracle.com/javase/1.4.2/docs/api/java/text/MessageFormat.html](http://docs.oracle.com/javase/1.4.2/docs/api/java/text/MessageFormat.html)

---

