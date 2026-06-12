---
title: "strange error using generics in java on ubuntu"
date: 2009-10-03
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2009-10-03
Hey All

I get a really strange error when I try to use generics in java on 9.04.  My code:
```

private ArrayList<myType> list = new ArrayList<myType>();

```
and the error:
```
Syntax error, parametrized types are only available if source level is 1.5
```
Do I need to update javac?

---

### Post by NovaAesa on 2009-10-03
Generics have only existed in Java since version 5.0 (which is the same version at 1.5, they did a weird version thing).

You can find out the versions of java you have by using the following code ```
update-java-alternatives -l
``` You will want to see ```
java-6-sun 63 /usr/lib/jvm/java-6-sun
``` there as one line. If it's not there, you need to install Sun's java (I have found it to be the best for coding, as it is both the dejour and defacto implementation). You can install it with ```
apt-get install sun-java6-jdk sun-java6-jre sun-java6-bin
``` Once that is installed (or if it was already installed) you need to switch the java and javac commands so they actually work with the correct compiler. This can be done with ```
update-java-alternatives -s java-6-sun
```

Hope this helps!

---

### Post by NovaAesa on 2009-10-04
By the way, are you trying to compile from the command line? or inside of an IDE? (this will make a difference as to what you have to do to fix the problem).

---

