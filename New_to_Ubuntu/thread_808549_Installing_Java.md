---
title: "Installing Java?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by dalezjc on 2008-05-26
Okay, I downloaded Java version jre-6u6-linux-i586.binto my desktop, but I haven't a clue how to install. 

Suggestions are appreciated.

dale

---

### Post by macaholic on 2008-05-26
Why don'y youn install it from the Ubuntu Repository? Search for "Java" in synaptic Package Manager, and you'll get a bunch of install options, free and proprietary.

---

### Post by Sinkingships7 on 2008-05-26
Run this command in the terminal and you're good to go. You can get rid of that package you downloaded.
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by inportb on 2008-05-26
Indeed, prefer the Debian/Ubuntu way.

If you *really* want to install from the bin file, just make it executable and run it as you would a shell script.

---

### Post by dalezjc on 2008-05-26
> **Sinkingships7 said:**
> Run this command in the terminal and you're good to go. You can get rid of that package you downloaded.
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

Perfect instructions!  Thanks for the help.

Dale

---

### Post by dalezjc on 2008-05-26
When I verify the java version at Java.com, I get the following error:

Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.

Download Free Java for Linux

Version 6 Update 6 

Thanks,
Dale

---

### Post by Paqman on 2008-05-26
For the future, there's a package called ubuntu-restricted-extras. It'll set up Java, Flash, multimedia codecs and a whole lot more good stuff on your machine in one step. It's always one of the first things I install.

---

### Post by Sinkingships7 on 2008-05-26
> **dalezjc said:**
> When I verify the java version at Java.com, I get the following error:

Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.

Download Free Java for Linux

Version 6 Update 6 

Thanks,
Dale

Yeah. The repos aren't too good at keeping up with update software all the time, but you won't notice a difference in your java performance. Everything will work just fine.

---

