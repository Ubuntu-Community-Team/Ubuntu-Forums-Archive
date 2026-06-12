---
title: "Eclipse Java debug variables view not working"
date: 2008-05-13
forum: Programming Talk
---

### Post by Kilarin on 2008-05-13
I'm using Ubuntu 8.04 and I've got Eclipse Version: 3.3.1.1 Build id: M20071023-1652 installed.

I'm just learning Eclipse, so I may be doing something stupid here.  When I'm tracing through a Java program, the variables window is not actually displaying strings, but displaying the variable ID number.  Note the following example:
[[IMG]http://img108.imageshack.us/img108/5301/thetest2ke0.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img108.imageshack.us/img108/5301/thetest2ke0.b6819b6b37.jpg[/IMG]](http://g.imageshack.us/g.php?h=108&i=thetest2ke0.jpg)

As you can see, even though the println shows that all of the variables are set correctly, the "variables" tab shows only the ID numbers for the String and the StringBuffer.

Have I got something set up wrong, or is this a problem with Eclipse 3.3 in Ubuntu?

Thanks!

---

### Post by Quikee on 2008-05-14
> **Kilarin said:**
> I'm using Ubuntu 8.04 and I've got Eclipse Version: 3.3.1.1 Build id: M20071023-1652 installed.

I'm just learning Eclipse, so I may be doing something stupid here.  When I'm tracing through a Java program, the variables window is not actually displaying strings, but displaying the variable ID number.  Note the following example:
[[IMG]http://img108.imageshack.us/img108/5301/thetest2ke0.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img108.imageshack.us/img108/5301/thetest2ke0.b6819b6b37.jpg[/IMG]](http://g.imageshack.us/g.php?h=108&i=thetest2ke0.jpg)

As you can see, even though the println shows that all of the variables are set correctly, the "variables" tab shows only the ID numbers for the String and the StringBuffer.

Have I got something set up wrong, or is this a problem with Eclipse 3.3 in Ubuntu?

Thanks!

As far as I can see you are using GCJ for the JVM which might be the cause of the problem. I would rather recommend you use either sun-java5(6) or openjdk6.

---

### Post by Kilarin on 2008-05-14
> you are using GCJ for the JVM which might be the cause of the problem. I would rather recommend you use either sun-java5(6) or openjdk6.
That makes sense, thank you for the advice.  I have the sun Java 6 Runtime environment installed.  I just had to figure out how to point to it inside eclipse.

For anyone else with the same problem, here is how I switched it.
In the standard Applications - Add/Remove menu Java 6 Runtime environment was checked as installed, but that won't tell me WHERE it is installed.  So I went to System/Administration/Synaptic Package Manager.  And from there I searched on Java and then scrolled down to the Java 6 entry.  It showed that Sun Java 6 was installed on my machine at:
/usr/lib/jvm/java-6-sun-1.6.0.06

So back to Eclipse. In the Java view, I selected my project then File/Properties/Java Build Path/Libraries
There the gcj library was checked.  I want to add Sun Java 6 so:
I selected ADD LIBRARY/JRE SYSTEM LIBRARY/INSTALLED JRE's/ADD
Then I pasted /usr/lib/jvm/java-6-sun-1.6.0.06 into the JRE NAME field and FINISH

And that took care of the problem!  Now when I'm debugging, strings display properly.  StringBuffers still show as just an ID :(, but thats not the end of the world.

Thank you VERY much for the help!

---

### Post by Quikee on 2008-05-14
The problem with StringBuilder is that it is not treated specially as a String but as yet another Object. You can change that with detail formatters to some extend.

Go to Window >> preferences.. >> Java >> Debug >> Detail Formatters
Set "Show wariable details (toString() value)" to "As the label for variables with detail formatters".
Now go and debug some code with StringBuilder, right click the StringBuilder variable and click "New Detail Formatter..", in the code snippet area add "this.toString();" or just "this".

You can do this for any other type (Calendar or Date for example) and you can format it (for the debugger) as you wish.

---

### Post by Kilarin on 2008-05-14
> The problem with StringBuilder is that it is not treated specially as a String but as yet another Object. You can change that with detail formatters to some extend
thank you!  thank you very much!  that works great!

---

