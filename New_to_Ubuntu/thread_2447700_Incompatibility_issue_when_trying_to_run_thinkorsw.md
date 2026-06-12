---
title: "Incompatibility issue when trying to run thinkorswim"
date: 2020-07-23
forum: New to Ubuntu
---

### Post by bkscroggs on 2020-07-23
Hello everyone! I'm having a compatibility issue when I'm trying to run the TD Ameritrade software thinkorswim. I get to the splash screen and it says "Oracle JRE 8 update 11 or later is required to run application."
It would be awesome if someone could help. I love Ubuntu and the community. I'm running Ubuntu 20.04 LTS

I'm running Ubuntu 20.04 LTS. I know I have Open JRE but I'm unable to install Oracle JRE 8 with the following code :

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer

---

### Post by CatKiller on 2020-07-23
That PPA doesn't have anything in any more. Oracle changed the licensing.

You can either use OpenJDK or get Oracle's Java from Oracle.

---

### Post by bkscroggs on 2020-07-23
I&#8217;ll have get it from their site then. Thanks!

---

### Post by bkscroggs on 2020-07-24
Do I need to uninstall OpenJDK first before I install Oracle's Java?

---

### Post by CatKiller on 2020-07-24
> **bkscroggs said:**
> Do I need to uninstall OpenJDK first before I install Oracle's Java?
Probably? 

I mean, in the GUI it's relatively straightforward to pick which Java you want to use for a particular invocation, and java is part of the alternates system so you can pick which gets called when you run "java," but there's not really a reason to have both unless you actually need to use both. 

My one machine that has Oracle's Java (for a particular Minecraft mod: the base game is fine with OpenJDK) got it from the PPA before the licence change, and my other machines are perfectly fine with OpenJDK, so I couldn't tell you anything about the new process, only that there is one.

---

### Post by bkscroggs on 2020-07-25
Thank you. So I can donwnload oracles latest Java JDK or do I need to install it&#8217;s older JRE?

---

### Post by bkscroggs on 2020-07-28
[SOLVED]  All I had to do was dl the Zulu java8 and manually switch it to that instead of openjre as my default java. Thanks everone!!!

---

