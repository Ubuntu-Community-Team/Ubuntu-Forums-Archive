---
title: "Netbeans not starting....help please"
date: 2010-01-03
forum: Programming Talk
---

### Post by D3mon_Spawn on 2010-01-03
I have recently just installed the netbeans IDE 6.7.1 from the Ubuntu Software Center and and can't seem to get it to start. I have a feeling this problem is happening because I previously had the 6.8 version, but instead of installing 6.8 from the software center, I did it through a regular installation file from the Netbeans website. By default it installed 6.8 to my home folder so when I decided I didnt want it, I just deleated the folder with all the program files. I understand that it wasn't the right way to remove it and I don't know why I did that. Anyway can anyone help me out.

---

### Post by Axos on 2010-01-03
Open a terminal window and run "netbeans". Use copy and paste to post any errors or exceptions which result.

---

### Post by D3mon_Spawn on 2010-01-04
just tried typing in "netbeans" and it still didn't work. This is what came up: 

john@Blue-Box:~$ netbeans
Cannot find java. Please use the --jdkhome switch.

^^^p.s. I defiantly have java installed

---

### Post by Axos on 2010-01-04
How did you install the JDK? Did you install it from the Ubuntu repository or download it from Sun's site? Did you install Sun's JDK or some other JDK (like OpenJDK)?

What you need to do is run netbeans from a terminal, telling it where the root of the JDK directory is. Where it is depends upon how you installed the JDK. For example, on my system, since I manually installed the Sun JDK and installed it in the home directory of a dedicated "java" user I created for the purpose, I would run netbeans like this:

netbeans --jdkhome /home/java/jdk1.6.0_17

Once you've figured out the correct directory, you can find and edit the file netbeans.conf and change the netbeans_jdkhome property to point to the JDK directory so you no longer have to use the --jdkhome option to run netbeans. Here's what that property looks like in my netbeans.conf file: 

# Default location of JDK, can be overridden by using --jdkhome <dir>:
netbeans_jdkhome="/home/java/jdk1.6.0_17"

---

### Post by D3mon_Spawn on 2010-01-05
I installed Sun JDK from package manager.

---

### Post by D3mon_Spawn on 2010-01-05
okay, i just got netbeans to work by using the method above but now when I try to modify my netbeans.conf file it says I can't save cuz i dont have permission. how can i override this?

---

### Post by Axos on 2010-01-05
Use sudo to run the editor. For example:

sudo gedit netbeans.conf

---

### Post by D3mon_Spawn on 2010-01-05
just to verify everything, I seem the have 3 netbeans.conf files:
1.) netbeans.conf in /ect
2.) netbeans.conf in /usr/share/netbeans/6.7.1/etc (i think this one is a link)
3.) netbeans.conf.orig in/usr/share/netbeans/6.7.1/etc

which one should I be modifying?

---

### Post by Axos on 2010-01-05
My guess would be either of the first two. If you edit the link, it edits the file the link points to. The .orig file is definitely not the one.

---

### Post by D3mon_Spawn on 2010-01-06
thaank you very much for all the help!!!

---

### Post by beaucoder on 2011-04-06
Hi Guys!!

Many thanks. This worked for me.

Ubuntu Lucid 10.04 Netbeans 6.9.1. Installed the latest version of Sun Java 1.6.0.24 and my NetBeans quit. 

Used the --jdkhome switch with directory = "/usr/lib/jvm/java-6-1.6.0.24" and -- Shazzam!!! NetBeans was off roaring back down the turnpike. So nice!!

Many thanks D3mon_Spawn.

Ken "Beaucoder" in Sugar Creek, Missouri. 

NetBeans, Ruby, Rails and MySQL flying high.

---

