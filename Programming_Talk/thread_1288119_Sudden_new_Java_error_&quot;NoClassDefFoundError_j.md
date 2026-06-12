---
title: "Sudden new Java error &quot;NoClassDefFoundError: java.util.Scanner&quot;"
date: 2009-10-11
forum: Programming Talk
---

### Post by Andante on 2009-10-11
Hi everyone,

Just now when trying to run one of my programs that ran fine several days ago, and still works fine on other computers, I get this error message:

Exception in thread "main" java.lang.NoClassDefFoundError: java.util.Scanner

I'm not really sure what the problem is. The only thing I can think I've done since it last worked was install Eclipse, which I've removed to no luck.

for java -version I have
java version "1.5.0"
gij (GNU libgcj) version 4.3.3

(I know I installed version 6 update 16, and the java site still tells me I have it -- is this the same thing? I can't tell)

for javac -version I have
Eclipse Java Compiler 0.894_R34x, 3.4.2 release, Copyright IBM Corp 2000, 2008. All rights reserved.

which is kind of worrying since I don't even have that anymore. Regardless, without recompiling the program it still didn't work so I don't think this is the issue, though I fear it may cause some later on.

Any ideas?

Thanks!

---

### Post by shadylookin on 2009-10-11
gcj is crap get the sun version of java. In the repos its something like sun-javajdk

then do this if you're using the eclipse ide

go into eclipse.
click window in the toolbar
under window click preferences
open up the java tag
click on compiler
make sure your compiler compliance level is 1.6

next click on Installed JREs
you should have something like java-6-sun-1.6.0.10 with a location of
/usr/lib/jvm/java-6-sun-1.6.0.10

---

### Post by Andante on 2009-10-11
Thanks so much! I was able to Google how to change to the Sun version in the terminal as well so everything is working perfectly.

---

### Post by shadylookin on 2009-10-11
No problem, it's a pretty common issue. I really wish they'd sticky the solution or even better dump gcj and replace it with openjdk as the default version of java.

---

