---
title: "slow eclipse auto complete"
date: 2007-05-21
forum: Programming Talk
---

### Post by destructchaos on 2007-05-21
i recently installed eclipse on my shiny new feisty kubuntu laptop.  everything seems to work perfectly, except the auto complete box take close to twenty seconds to begin filtering results after it initially opens.  is there an easy way to fix this, or is there an easy way to disable it so it doesn't show up at all?

---

### Post by hod139 on 2007-05-21
My guess is that you are not using Sun's java.  See this thread for how to fix: [http://ubuntuforums.org/showthread.php?t=419863](http://ubuntuforums.org/showthread.php?t=419863)

---

### Post by azntfl on 2007-06-30
I have the exact same problem and I am pretty sure I am using SUN JAVA. Everything in Eclipse works except the auto-complete box.

---

### Post by hod139 on 2007-07-01
> **azntfl said:**
> I have the exact same problem and I am pretty sure I am using SUN JAVA. Everything in Eclipse works except the auto-complete box.
Did you follow my guide?  What is the output of 
```

java -version

```
and 
```

javac -version

```

---

### Post by azntfl on 2007-07-02
1.6.0 for both, where is this guide at?

---

### Post by hod139 on 2007-07-02
> **azntfl said:**
> 1.6.0 for both, where is this guide at?
I apologize, I mistakenly thought the link in my second post was the link to my howto.  My howto can be found here: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378).

---

### Post by azntfl on 2007-07-02
Thanks! your guide was exactly what I needed.

---

### Post by moz44 on 2009-11-21
Well, my eclipse Galileo 3.5 was not giving me the method list after I pressed [.] period because it was the Eclipse Galileo PHP bundle. After I downloaded the classical Eclipse 3.5 everything was solved. I hope it helps someone

---

### Post by cariboo on 2009-11-21
Another thread brought back fom the dead. Closed.

---

