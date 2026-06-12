---
title: "C++ vs Java (Performance, Purely Object Oriented ...."
date: 2006-06-26
forum: Programming Talk
---

### Post by karthik085 on 2006-06-26
I recently came across this comment at Slashdot.org:
[http://ask.slashdot.org/comments.pl?sid=187162&cid=15442640]("http://ask.slashdot.org/comments.pl?sid=187162&cid=15442640")

Just wondering what the Ubuntu Community thinks about this...

---

### Post by LordHunter317 on 2006-06-26
The guy doesn't seem to know what he's talking about at all.

Java, especially Java 5, performs as well if not better than C++ for many cases.  Garbage collection for example, can yield huge benefits for some applications, like lots of server-side stuff where deferring memory allocation can be done for longish periods of time and it can be done independent of the rest of the system, at a lower priority.

Manual memory management isn't a reason to hate C++.  Java still requires manual resource managment, which is far more important. 

I don't know how he's defining "purity" but I'm sure it's wrong and it doesn't mean anything anyway.

He's totally wrong about robustness.  He needs to look the word up in a dictionary.  He also needs to read about virtual machines and how they function.

---

### Post by Daverz on 2006-06-26
I'm mainly a Python guy, so Java's performance seems quite good to me.  Even the much maligned Swing seemed to perform pretty well in my own tests as far as start time and responsiveness go.  If you need better performance, you'll know, otherwise there's a bit too much obsessing on this topic IMO.

However, I don't see purity of the object model as a selling point in a practical language (which is not to say I like C++; I don't have a use for it).

---

### Post by Stromham on 2006-06-26
i think either could be faster, its just easier to make java fast but the firs time you run the program its slow after that quick as a bug :D. c++ can be fast aswell but i think its harder to do, and requires more experience, maybe im wrong but thats the way i see it :P

---

### Post by mlind on 2006-06-26
Java vs. C++ performance tests are  [interesting reading]("http://kano.net/javabench/"), but should be taken less seriously too.

I used to mock 1.4 JVM for being slow and bloated, but I had to shut my face after trying 5.0 JVM  and especially the server VM.

---

