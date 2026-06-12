---
title: "Java performance problem"
date: 2008-05-11
forum: Programming Talk
---

### Post by Maqz447 on 2008-05-11
Hello everyone. Might there be a Java guru here that can help me? I've written a graphical game based on "Life" in Java using Swing. I'm using Hardy. Unfortunately, the game has serious problems dealing with large board sizes - but only if I launch it from a terminal. When I launch it from Eclipse, it's quite speedy at all board sizes. With a 160x160 board it crawls to a halt when launched from the command line, while it has no problems with this size when launched from Eclipse. The puzzling thing is, best as I can tell I'm using the same JVM in both cases. "java -version" in the terminal produces: "1.6.0_06" and "Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)". What could possibly be wrong? I've uninstalled all the GNU and OpenJDK/IcedTea Java stuff. :confused:

---

### Post by rfreedman on 2008-05-11
It seems likely that your Eclipse environment is starting your application with more memory than the default that you get when you launch it at the command line with no memory options.

Take a look at [http://blog.codebeach.com/2008/02/determine-available-memory-in-java.html](http://blog.codebeach.com/2008/02/determine-available-memory-in-java.html)
to see how to add code to your application to determine the amount of available memory. You can also try out jconsole.

---

### Post by Maqz447 on 2008-05-12
Thanks for your suggestion, but that doesn't seem to be the problem. I tried to specify the initial heap size with the -Xms flag set to various amounts (up to 1 gig), and this did increase the memory usage of my program up to around 200 mb at most, however it still ran just as slowly. When launched from Eclipse, it uses 120 mb at most, and runs much, much faster. I'm really puzzled about this...

Edited to add that I use the same binaries in both cases.

---

### Post by NormR2 on 2008-05-12
Can you see the commandline that Eclipse uses to start the program?
Does it have better runtime libraries than Sun's jre?

---

### Post by Maqz447 on 2008-05-13
I don't know what runtime libraries that would be, the only libs I'm using is swing and awt which come with the JVM. I've verified that I don't have anything gcj-related installed. 
When the board is sufficiently small, say 40x40, there's no perceptible difference, but with large boards the difference is quite dramatic, lightning fast vs. almost total freeze, and it doesn't seem to be a memory issue. wtf?

---

### Post by NormR2 on 2008-05-13
Can you see the commandline that Eclipse uses to start the program?

---

### Post by Maqz447 on 2008-05-13
No, I haven't been able to find out what command Eclipse uses to start the program. That doesn't seem to be possible.

---

### Post by jamesstansell on 2008-05-13
> **Maqz447 said:**
> No, I haven't been able to find out what command Eclipse uses to start the program. That doesn't seem to be possible.

The Eclipse laucher has several options, including one that specifies the Java Runtime to use.  I believe it defaults to whatever the project is using, but it can be changed.  It can also be changed to specify an "execution environment" (or similar name) - the idea seems to be to target earlier versions of the JVM while actually running with a current version.

The ps command should most likely be able to see your running program.

The other commands to check out are jconsole (included with JDK) and visualvm (visualvm.dev.java.net) which should be able to tell you which JVM is being used and what the classpath is, and more.  As you may guess, visualvm is a little more advanced.

When I first heard your description my first guess was memory settings.  A second guess might be the difference between the -client and -server switches, but that seems even more far-fetched.

Regards,

-james.

---

### Post by Maqz447 on 2008-05-13
Thanks, I'll check them out.

---

### Post by Maqz447 on 2008-05-13
Ok, so I tried jconsole. Actual and maximal heap sizes were similar in both cases (up to ~50 mb out of 500 mb maximum), so that's not where the problem lies. Everything else seemed to be similar too, except for the extreme difference in speed of execution. When launched from Eclipse it used 2 more threads, but I doubt that's significant.

Eclipse uses the VM argument '-Djava.security.policy=java.policy.applet'.

Eclipse library path: 
'/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/server:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/../lib/i386:/usr/lib/xulrunner:/usr/java/packages/lib/i386:/lib:/usr/lib' 

The one I use from the terminal is identical except I don't have /usr/lib/xulrunner.

Boot class path is identical in both cases:
'/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/resources.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/rt.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/sunrsasign.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/jsse.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/jce.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/charsets.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/classes'.

Bizarre... :(

Edited to add: HotSpot server VM and tiered JIT compiler in both cases. Roughly similar amounts of time seemed to be spent JIT-compiling, and roughly similar numbers of garbage-collections occurred.

---

### Post by LaRoza on 2008-05-13
> **Maqz447 said:**
> When launched from Eclipse it used 2 more threads, but I doubt that's significant.

That seems very significant ;)

---

### Post by Maqz447 on 2008-05-13
Heh, I suddenly had an "Eureka" moment. When I launch a Java program I've written from the command line, I always use the -ea option (enable assertions). I use quite a lot of assertions, and this has never been a problem in terms of performance, in fact I've never even thought of it as anything that could impede performance. However, in the program in question (a version of "Game of Life"), with a board size of 160x160, i have 25,600 cell instances that I must iterate over for each generation. And the code that determines what happens with each and every one of those cells is riddled with assertions. Of course this slows it down tremendously.

Eclipse doesn't enable assertions by default, that's why it ran so much faster. Turns out that when I launch it from a terminal without the -ea option, it's equally fast.

Lesson learned! :)

---

### Post by Maqz447 on 2008-05-13
How do I mark it as solved?

---

### Post by LaRoza on 2008-05-13
> **Maqz447 said:**
> How do I mark it as solved?

Thread Tools on the top left of the thread.

---

