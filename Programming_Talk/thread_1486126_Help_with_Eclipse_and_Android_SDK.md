---
title: "Help with Eclipse and Android SDK"
date: 2010-05-17
forum: Programming Talk
---

### Post by lfitz on 2010-05-17
[SIZE=2]Hi, I installed the Android SDK and ADT Plugin for Eclipse.  But I have two problems: when I create a project I get an error message with no text, just an 'OK' button.  Also, the build target selection list doesn't display properly, I can access it by tabbing through all the elements then using the arrow keys to select say Android 2.1 and spacebar to activate the checkbox.  

Any ideas on how I could fix this?
[/SIZE]

---

### Post by soltanis on 2010-05-17
Make sure you have a proper JDK installed (OpenJDK), not the GNU Compiler for Java (gcj) which I think is the Eclipse default. When I installed the Android SDK I got weird behavior like that too until I realized my environment was configured to use GNU Classpath. Make sure you also have that compiler configured for use in Eclipse.

---

### Post by lfitz on 2010-05-17
> **soltanis said:**
> Make sure you have a proper JDK installed (OpenJDK), not the GNU Compiler for Java (gcj) which I think is the Eclipse default. When I installed the Android SDK I got weird behavior like that too until I realized my environment was configured to use GNU Classpath. Make sure you also have that compiler configured for use in Eclipse.

Can you explain how to do this?

I am still new to Eclipse.  

I downloaded JDK bin and installed it.  But I'm not sure how to change it in Eclipse.

Thank you!

---

