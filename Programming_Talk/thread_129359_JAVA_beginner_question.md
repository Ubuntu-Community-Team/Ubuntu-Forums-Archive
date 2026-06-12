---
title: "JAVA beginner question"
date: 2006-02-13
forum: Programming Talk
---

### Post by Griff on 2006-02-13
I have a class file that I need to put in the JAVA bin.  Is there a bin in particular that java uses exclusively?  I'm not sure where it needs to go.  I'm using arnieboys java from automatix if that matters.

---

### Post by LordHunter317 on 2006-02-13
Wait, I'm confused.  You want to reference the class from another class?  If so, you can add it to the classpath when you run Java.  It needs to be in the proper location relative to the other class though.  The best idea is to package everything into a single jar, so it's self-contained.

---

### Post by Griff on 2006-02-13
Hmm.  Not sure what you mean.  On my PC's windows partition I just put the .class file in the java\bin directory.  I tried finding this same 'bin' so to speak on the linux side (ended up trying /usr/lib/(SDK 1.5 somethin)/bin ,but doesn't seem to work.  I am not familiar with the term 'jar'.

---

### Post by juancnuno on 2006-02-13
Why do you want to do this?

---

### Post by Griff on 2006-02-14
Ok. Got it. I just had to put that .class file within the same directory as the .class i was working in.

PS: I wanted to do it because I needed to be able to use the file in an intro to java class.

---

### Post by kaamos on 2006-02-14
You can do the same with
```
javac -classpath ./:/path/to/directory Class.java
java  -classpath ./:/path/to/directory Class
```

---

