---
title: "Whats my Classpath?"
date: 2006-02-18
forum: Programming Talk
---

### Post by Schneehenry on 2006-02-18
Hello,
I'm trying to compile some Javasources, but when I type
**jikes Source.java**
I get the following message:

Found 1 system error:

*** Semantic Error: You need to modify your classpath, sourcepath, bootclasspath, and/or extdirs setup. Jikes could not find package "java.lang" in:
                .


Ok, I know, I got to set my Classpath, but how could I find out were my Classes are?
Greets,
Simon

---

### Post by knalle on 2006-02-18
export CLASSPATH=/path/to/your/classes:/path/to/some/lib.jar

---

### Post by Schneehenry on 2006-03-12
ok, thx, but how could I find out the path?

---

### Post by kumoshk on 2009-06-06
Yes, I would also like to know the same thing.

I installed jikes, and I know you're supposed to edit ~/.bashrc and add your classpath and such there. However, I don't know what directories my java libraries and such are in. Tell me for gcj, open-jdk or whatever. I could try Sun's version, and that would be easy (since you just extract it in its own directory, and, of course, the files would be in it somewhere), but I'd rather not right now. Does java.lang even exist outside of Sun's implementation?

Why isn't this fixed by default? The problem still exists in Jaunty. I guess it's probably because there are so many kinds of Java in Linux and they don't want to be biased, and they don't want to make something that automatically detects an installed java.

---

### Post by raisen on 2009-08-31
Anyone would mind to share a solution for this issue? I'm having the same problem.

---

