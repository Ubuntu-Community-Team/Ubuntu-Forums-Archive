---
title: "Launcher for .jar unresponsive"
date: 2017-10-25
forum: New to Ubuntu
---

### Post by kianb on 2017-10-25
Hello I am new to Ubuntu and Linux in general. 

So far so good except for one issue 

I'm trying to run this program [https://mediaserver.thinkorswim.com/installer/install.html](https://mediaserver.thinkorswim.com/installer/install.html)

I am able to install it and when it runs after install everything is fine so I know I'm able to use it. The problem is afterwards when I click the launcher nothing happens 

When I try and use java -jar launcher.jar 
I get this response 

java.lang.NullPointerException
	at java.util.Arrays.sort(Arrays.java:1438)
	at com.devexperts.jnlp.SuitLoader.loadSuit(SuitLoader.java:40)
	at com.devexperts.jnlp.Launcher.run(Launcher.java:22)
	at java.lang.Thread.run(Thread.java:748)

I have already checked off the executable box in properties. And I have tested this with Java 8 and 9

Any help would be appreciated, apologies in advance if my question format is off. This is literally the first time I'm asking anything

---

### Post by kernel-klink on 2017-10-28
I had a similar problem but the response was that the updater failed to launch. I did several things and I'm not sure which one fixed it.


1. I re-ran the java install per the commands at the TOS webpage you referenced.
2. I re-ran thinkorswim_installer.sh. I selected a new install in a new directory (my user directory), selected 1 user. 1st run failed.
3. I opened the properties of the 2 jars and the main application and selected java 8 as the default for all 3.
4. 2nd attempt to run worked.


I think these default selections were the problem. I saw some instructions on another TOS page that included a similar sequence whereby the option
 to execute at the end of the install is deselected, but the rest of their instructions looked like some Windows gibberish. 
I think the key is to get it installed, set the defaults and then run it.


The 1st successful run took a long time to update. Some of the setup came in from my existing Windows setup - grids, styles, studies and drawings. 
Workspaces did not, but I can live with that. We'll see how it executes trades next week.

---

