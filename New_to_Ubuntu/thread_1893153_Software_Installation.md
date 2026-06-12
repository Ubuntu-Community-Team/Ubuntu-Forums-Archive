---
title: "Software Installation"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by THD_Kl0ud on 2011-12-09
Hello,

New to Ubuntu.

Trying to install Java JDK and Netbeans.

Have managed to download alien and install Java JDK and Netbeans.  If I go into my Unbuntu Software Center it shows Netbeans is installed, but I cannot figure out how to get an icon for it.

Any help would be much appreciated.

Keep reading something about setting it into the environment variable, but not sure what that means. :confused:

Thanks
THD_Kl0ud

---

### Post by oldos2er on 2011-12-09
Not sure what 'alien' has to do with Java, but maybe these links can help:

[http://pasindudps.blogspot.com/2011/10/installing-netbeans-ide-in-ubuntu-1110.html](http://pasindudps.blogspot.com/2011/10/installing-netbeans-ide-in-ubuntu-1110.html)

[http://askubuntu.com/questions/82949/netbeans-7-0-1-installed-but-wont-run](http://askubuntu.com/questions/82949/netbeans-7-0-1-installed-but-wont-run)

---

### Post by seawolf167 on 2011-12-09
There is a how-to for NetBeans with information about Java located here
[https://help.ubuntu.com/community/Netbeans](https://help.ubuntu.com/community/Netbeans)
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by THD_Kl0ud on 2011-12-09
I used alien to convert the .rpm file I got from oracle.  Thank you for the links. Very useful.

---

### Post by F.G. on 2011-12-09
hey,
so i'm pretty sure that netbeans and the jdk are available from the repositories (you don't have to do anything with .rpm files).

if you go to: 
System > Admonistration > Synaptic Package Manager
and click and install etc. you should be good to go, i think netbeans appears as an icon under: 
Applications > Programming
if you can't get an icon you can always make a launcher by right clicking on the panel an going to 'Add Launcher'.

---

### Post by THD_Kl0ud on 2011-12-09
That seems to be where I got lost.  I installed jdk and netbeans using the Ubuntu Software Center.  It says both are installed, but I can't find them anywhere.  And if I search for "Installed" apps with the Software Center JDK shows up, but I can't find Netbeans.

Ended up going to Netbeans.com and downloading a .sh from there then just executing it in terminal.

Thanks for all the help!

---

### Post by F.G. on 2011-12-09
hey, have you just tried typing 'netbeans' into the terminal?

---

### Post by oldos2er on 2011-12-09
> **THD_Kl0ud said:**
> I used alien to convert the .rpm file I got from oracle.  Thank you for the links. Very useful.

Simpler to download the *deb file, alien doesn't work 100% of the time. Use the Webupd8 PPA, [http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

