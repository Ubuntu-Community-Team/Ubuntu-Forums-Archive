---
title: "Programming with Java, OpenJDK ?"
date: 2012-05-19
forum: Programming Talk
---

### Post by jaho22 on 2012-05-19
I need to know where i can read OpenJDK lisences, and everything i need to know before i can use OpenJDK with my Java project.

Or is it this simple that i just type 'sudo aptitude install openjdk-7-jdk', and then i can use it as i wish ?

---

### Post by GonchuB on 2012-05-19
Download it directly. You'll find the licenses and information once you downloaded it.

```
sudo apt-get install openjdk-7-jdk
```

---

### Post by jaho22 on 2012-05-19
> **GonchuB said:**
> Download it directly. You'll find the licenses and information once you downloaded it.

```
sudo apt-get install openjdk-7-jdk
```

Im a bit a noob with all this ubuntu and java, i do have years of experience, but seems that i havent learn that much, lol, could you please share a bit of information about the location where license and all other information i need to know when i use openjdk-7-jdk are.

i have use to use sun java jdk before this is my first try with openjdk.

---

### Post by GonchuB on 2012-05-19
[GNU]("http://en.wikipedia.org/wiki/GNU_General_Public_License") and [GPL Linking Exceptions]("http://en.wikipedia.org/wiki/GPL_linking_exception") are the licenses involved in openjdk

---

### Post by CptPicard on 2012-05-20
> **jaho22 said:**
> I need to know where i can read OpenJDK lisences, and everything i need to know before i can use OpenJDK with my Java project.

If you're simply compiling your own Java and running it on top of the JDK, then you don't need to care about the licenses. If you were altering the JDK itself, it would be a different situation.

---

### Post by jaho22 on 2012-05-20
I think that, I may later ask a small sum of money from my java work.

I go reading the GNU and GPL later, but really want to ask a short answer before reading them, so is it also ok to create commercical java work with copyrights  only to me, with ubuntu and openjdk.

I wont alter the jdk or do any jni, just basic java code.

---

### Post by CptPicard on 2012-05-20
> **jaho22 said:**
> 
I go reading the GNU and GPL later, but really want to ask a short answer before reading them, so is it also ok to create commercical java work with copyrights  only to me, with ubuntu and openjdk.

Yes. Where do the Ubuntu and OpenJDK copyrights come from? Do you plan to grant them specifically?

If compilers and standard libraries had "viral" licenses that actually restricted what you can do with software you write, we couldn't do much... you will want to be more careful with any additional libraries you may use.

---

