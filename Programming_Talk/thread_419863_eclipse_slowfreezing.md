---
title: "eclipse slow/freezing"
date: 2007-04-23
forum: Programming Talk
---

### Post by scotty2hott2k on 2007-04-23
hi, using eclipse in feisty (using it to program c++), it seems to randomly freeze up for short periods of time, i look in top or via system monitor and java spikes to 80-90% of cpu usage, is there a 'fix' for this or am i doing something wrong?

---

### Post by hod139 on 2007-04-23
Make sure you are using Sun's java, not GNU's.  There are plenty of threads available for installing Sun's java, some using the repositories others not.  I have an older thread for dapper that I think should still basically work: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)
You might have to update version numbers for feisty.  I should probably update that howto anyways.

---

### Post by scotty2hott2k on 2007-04-23
thanks, followed your guide, at the top of my config files was:

/usr/lib/jvm/java-gcj

which assume is the wrong one, so i made sun's top.

---

### Post by phossal on 2007-04-23
Are you ever going to upgrade your tutorial to reflect that SUN's Java is now 1 version and 1 update greater? JDK 5.0 with eclipse, instead of JDK 6u1?  Why?

---

### Post by hod139 on 2007-04-23
I upgraded my tutorial to now use java 6.

---

### Post by scotty2hott2k on 2007-04-24
right, sorry to say its still not fixed, java still spikes to 80% or so every so often and eclipse freezes/stops responding so i have to leave ot for 2 minutes (if not  more) til it recovers and is usable again.

---

### Post by hod139 on 2007-04-25
Have you done all the steps in my howto?  If you start eclipse from the terminal, it prints out which jvm it selected to run, make sure you see java-6-sun

---

### Post by scotty2hott2k on 2007-04-25
it appears that its the code complete assistant that is causing it to freeze/slow. it tends to run fine until i do class object then . then it spends ages searching for what members that class has. (ive got about 30 different source files in the project)

---

### Post by scotty2hott2k on 2007-04-25
right, just ran it from console like you said, appears you are right. i get:

searching for compatible vm...
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/jvm/java-gcj...found
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension

which would indicate (?) that its not using sun's java?

---

### Post by hod139 on 2007-04-25
> **scotty2hott2k said:**
> right, just ran it from console like you said, appears you are right. i get:

searching for compatible vm...
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/jvm/java-gcj...found

You are still using Gnu's java.  Make sure you do all the steps in my tutorial:
1) update java-alternatives
2) Edit the jvm configuration file
3) Edit eclipse's java_home file
Then it should use Sun's java.

> 
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension

This is interesting, have you done this?

---

### Post by scotty2hott2k on 2007-04-25
ok, its now much quicker though sitll pretty damn slow, like 6+ seconds for the popup for code assist to popup.

---

### Post by scotty2hott2k on 2007-04-25
just did the last bit it said on the console startup with setting permissions as root, made no difference, still takes on average 6seconds for it to popup, (ive got 768mb of ram, 2.4gig p4).

---

### Post by scotty2hott2k on 2007-04-25
just installed and using codeblocks now, much quicker than eclipse. i like the eclipse environment, but if its not working properly :(

---

### Post by Serguei_89 on 2007-04-27
In my case, this exact same slowness problem happens only when I use Eclipse installed via automatix or adept(don't remember which I used). If I use Eclipse downloaded and extracted from the Eclipse website, everything works smooth.

---

### Post by bedo on 2007-06-05
here's what fixed the problem for me

I made sure gcj is my java virtual machine

then installed "eclipse-gcj" package instead of plain "eclipse"


"sudo apt-get install eclipse-gcj"

to change the jvm follow the following steps (as per the tuturial) but instead switch to gcj

You are still using Gnu's java. Make sure you do all the steps in my tutorial:
1) update java-alternatives
2) Edit the jvm configuration file
3) Edit eclipse's java_home file

---

### Post by asymmetric on 2007-06-13
hi!

i extracted and compiled the JDK, so i didn't use the deb packages.. 

i tried to follow the tutorial, changing the config files accordingly

the jdk is in my home, so i added /home/lrnz/jdk1.6.0_01/ instead of /usr/lib/jvm/java-6-sun, because i don't have that directory..

but when i start eclipse via console, it still says it's using gcj, plus now it gives me that strange error about typing commands as root!

is there a way to completely uninstall gcj? is it safe?
or, alternatively, how could i completely remove the compiled java and install a clean deb over it?

thanks!
asy

---

### Post by asymmetric on 2007-06-23
anyone?

---

### Post by asymmetric on 2007-06-24
i solved by adding a symlink in /usr/lib/jvm called java-sun pointing to my java bin

thanks for the help ^^

---

