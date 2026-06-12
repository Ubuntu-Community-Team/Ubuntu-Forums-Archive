---
title: "Eclipse Question"
date: 2007-07-26
forum: Programming Talk
---

### Post by DBQ on 2007-07-26
Hey Everybody,
   I have an issue in Eclipse,  I just installed it, and tried to run a simple java program with swing, and string classes etc.  String, Swing, JavaFilter, everything is highlited in red.  Eclipse does not appear to see these classes.  Whats wrong?  What should I do to fix it. Thank you.

---

### Post by arist0tle on 2007-07-26
What error messages do you get? What exactly do you mean by "it doesnt see the classes"? If you are getting compiler errors about the classes themselves not being found from the compiler (this is what I am assuming), make sure you have the correct version of java installed. when you set up a configuration (the "Run as"), you have the option of what compiler to use. If you are using an older compiler, then its possible that those classes are not supported yet. go to the repositories and look for sun jdk's. i am using 6. install it. after it is installed it is usually installed in /usr/lib/jvm/java version/bin. i hope that this helps.

---

