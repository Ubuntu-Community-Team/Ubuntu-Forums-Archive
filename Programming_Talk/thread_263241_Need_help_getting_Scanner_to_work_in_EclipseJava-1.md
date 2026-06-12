---
title: "Need help getting Scanner to work in Eclipse/Java-1.5-Sun"
date: 2006-09-22
forum: Programming Talk
---

### Post by ZephyrXero on 2006-09-22
I really need the ability to use the Scanner library in Eclipse. I've been trying to make it work for about a month now with no luck. It's how my Java teacher is making us handle input, so I can't use any other methods. Apparently Scanner was added with Java 1.5, yet Eclipse is built to work with Java 1.4 in Ubuntu. I've followed [this guide](http://ubuntuforums.org/showthread.php?t=201378) to fix that, but I still can't get it to recognize it. I've even tried it under both Dapper and Edgy too. I know Scanner works fine in Windows (what my teacher unfortunately uses), but I reeaaalllly, don't want to have to do it that way.

Any ideas? Please....
Thanks!

---

### Post by gmclachl on 2006-09-23
Did you change the java library in eclipse to point to 1.5?

 George

---

### Post by ZephyrXero on 2006-09-26
Yes

---

### Post by gmclachl on 2006-09-27
So if you open up the terminal and type java -version

 you should get output similar to 

 java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_08-b03, mixed mode)

George

---

### Post by DeadEyes on 2006-09-27
From the main menu go Project->Propeties
with the treeview on the left select Java Compiler
On the right is your Compiler compliance level set to 5.0?

---

### Post by ZephyrXero on 2006-10-22
To answer both of the questions above, yes....

I ended up just having to download the binary from the Eclipse site, and now it works fine. I've also found that it's much faster since it's compiled against the actual Sun JRE instead of GCJ ;)

---

