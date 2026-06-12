---
title: "Synaptic Tomcat5.5 &amp; JDK 5.0 install"
date: 2007-02-16
forum: Programming Talk
---

### Post by Turner.kj on 2007-02-16
When I use Synaptic to install Tomcat and a JDK.  Where are these really being installed to, what directory?

---

### Post by hod139 on 2007-02-16
Not sure about tomcat, but sun-java5 goes to  /usr/lib/jvm/java-1.5.0-sun-1.5.0.xx (where xx is the version), it also creates a simlink to /usr/lib/jvm/java-1.5.0-sun.  It then uses /etc/alternatives/java* to decide which java* to use when you type the command (e.g. javac).  You can use update-java-alternatives to list (-l) and set (-s) the version of java to use from the many various possible installations.

---

### Post by lloyd mcclendon on 2007-02-16
tomcat is in /var/lib, what a stupid place.  they piss around with the config files and the init script is so over engineered the whole thing doesn't work correctly for most people.

for any piece of software written in java (& the sdk), it's really easier and better just to download it from the web, extract & install.  debian packages that try to do all kinds of stuff usually just make java software not work

---

### Post by hod139 on 2007-02-16
Hopefully configuration will get better with Sun open sourcing Java 6.

---

### Post by jejones3141 on 2007-04-21
BTW... one of the problems I had upgrading to Feisty had to do with tomcat 5.5. Turned out that the install never created a user "tomcat5.5", and when I tried to uninstall tomcat5.5, the uninstall tripped over that. I had to go to the command line to create the tomcat5.5 user, because of that "."; the GNOME GUI-based user/group management program won't let you override the regexp that refuses to create a username with a period in it.

---

### Post by luizfar on 2007-04-21
> **Turner.kj said:**
> When I use Synaptic to install Tomcat and a JDK.  Where are these really being installed to, what directory?

Once a package is installed, just right-click it in Synaptic, choose Properties and then the Installed Files tab.

---

