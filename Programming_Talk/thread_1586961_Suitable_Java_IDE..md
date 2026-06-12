---
title: "Suitable Java IDE."
date: 2010-10-02
forum: Programming Talk
---

### Post by cgroza on 2010-10-02
Hello, I have a question for you.
Do you know any lightweight easy to use IDE? I tried Eclipse and Geany. Eclipse looks bloated on my screen resolution and Geany has a bug. Thank you.

---

### Post by GregBrannon on 2010-10-02
Everything that can be said about this topic has been said in the Programming Talk area.  That doesn't mean it won't be repeated here, but you may want to review what has already been said.

---

### Post by Frank_Schley on 2010-10-02
You could try Netbeans or for something fun and lightweight try BlueJ.

---

### Post by cgroza on 2010-10-02
> **Frank_Schley said:**
> You could try Netbeans or for something fun and lightweight try BlueJ.
Thanks, i will give it a try. I am still open for suggestions.

---

### Post by lykeion on 2010-10-03
My fav IDE for Java is [IntelliJ IDEA]("http://www.jetbrains.com/idea/"). The community edition is free and open source.

---

### Post by KdotJ on 2010-10-03
Gedit with a few plugins, nice and lightweight :) though if you want debugging etc, maybe not...

---

### Post by r-senior on 2010-10-03
> **KdotJ said:**
> Gedit with a few plugins, nice and lightweight :) though if you want debugging etc, maybe not...
A text editor with Maven for dependency and project management isn't a bad choice but the other big advantage of the Java-aware IDEs is code completion, code generation (esp. brain-dead tasks like getters and setters, equals & hashcode), refactoring and integration with app servers (if you are doing web stuff).

I use Eclipse quite a bit but I find Netbeans quickest to get up and running on a new machine because it comes pretty much set-up with compatible plugins (Maven, SCM, JUnit). Some people will tell you it's slow but in these days of 2G+ memory it's not really an issue.

Any of Eclipse, IntelliJ, or Netbeans does a good job really. I'd strongly recommend investing time with Maven because it can save a huge amount of frustration grubbing around for JAR files when your projects become more complex. It will also generate JavaDoc and run unit tests as part of your build. Using Maven means the choice of IDE is less important because the build is externalised - I exchange Maven projects between Eclipse and Netbeans quite freely and it's easy to build from the command line or use a continuous integration tool like Hudson.

How much you get into these extras depends on the scale of what you are developing and how much you have in the way of inter-dependent projects.

---

### Post by WitchCraft on 2010-10-03
You could use Eclipse.

However, I recommend Intellij IDEA. Runs on Linux.

---

### Post by mainerror on 2010-10-03
Have you ever tried to deactivate/close the unneeded parts of Eclipse? You can also just minimize most of the views.

---

### Post by cgroza on 2010-10-03
Yes I tried but still the start up time is enormous. Thank you for your suggestions.

---

