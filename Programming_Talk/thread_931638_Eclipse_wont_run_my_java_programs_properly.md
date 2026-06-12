---
title: "Eclipse wont run my java programs properly"
date: 2008-09-27
forum: Programming Talk
---

### Post by situz on 2008-09-27
Hey. I have an odd problem with Eclipse. I've followed a tutorial installing eclipse on Ubuntu I found on this forum. 

I don't have the same problem in windows, but i do have the same problem on 2 different computers running Ubuntu hardy. 

the problem is with input dialogs, or java scripts that opens a window in general.  for example:

javax.swing.JOptionPane.showInputDialog("");

the input dialog will come up, but it locks up, i cant close it, it just hangs, and wont disappear before i exit eclipse.

when i run eclipse from a terminal, it doesn't show any errors either, so i have no idea what causes this. 

any help would be much appreciated!
thanks in advance! :)

---

### Post by Reiger on 2008-09-27
Typical GNU Java bug, try (installing & using) the SUN version from the repos instead. Make sure to configure Eclipse properly with the Window > Preferences window.

---

### Post by situz on 2008-09-27
thanks for the reply! 
but, I'm a noob with eclipse, so would you please explain how to configure eclipse properly?

---

### Post by situz on 2008-09-28
nvm, I figured how to configure it myself :P

for those who wants to know how to configure eclipse to use the right sun java version, in eclipse, click window > preferences > java > installed JREs. click search, chose the folder /usr/ on your disk, let it search, and when done click java-6-sun. 

worked for me atleast :)

---

### Post by anlazarov on 2008-10-11
well, it didn't work for me! I made my java sun 6 be the default even before installin eclipse, and now eclipse shows this is what it's using, but still have the problem with the input JOptionPane. :S Any Other Ideas?

---

### Post by Reiger on 2008-10-11
You mean something like:
```
sudo update-alternatives --configure java
``` ??

Also check settings under: Java in: Window > Preferences. Make sure the right compiler is actually used by Eclipse.

---

### Post by SartoriusGenuflectus on 2008-11-29
Thank you. This post helped me.
I had a problem running java programs with Eclipse 3.2.2. The symptoms were that the program would run so far and then terminate.eg for the following java code in a public class that extends java.applet.Applet :
        Environment world = new Environment();
	Cell[] cells = new Cell[1000];
I could tell from messages generated using System.out.println that the Environment object was being instantiated but the Cell object was not ie I got these messages and nothing else in the Eclipse console window:
        Environment constructor entered
        Environment constructor completed
At first I thought it was something I had changed in my code that was causing the problem as the program had worked last time I used it a couple of months ago. However when I tried other java programs that I had not changed and had similar issues then I came looking on Ubuntu forums.
From this post I found (from Windows / Preferences / Java) that Eclipse was running Java-6-sun-1.6.0.0 but the compiler compliance version was set to 1.4. I changed this to version 6 and Hey Presto! my java programs are working again.
Thanks again for the help.

---

