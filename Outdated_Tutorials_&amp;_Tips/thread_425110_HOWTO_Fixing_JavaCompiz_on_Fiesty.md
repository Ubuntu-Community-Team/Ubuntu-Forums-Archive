---
title: "HOWTO: Fixing Java/Compiz on Fiesty"
date: 2007-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by kevykev on 2007-04-27
Unfortunately sun's java from the ubuntu repository (java6u1) and compiz still dont play well in feisty, i.e - desktop effects break some java applications. The reparenting window manager bug thingy is still there, and breaks all java apps that use swing. The problem seems to be resolved in java6u2 tho, here's how to upgrade:

I used the jdk cause i need to do development, but you can probably adapt this for just the jre too.

[LIST=1]
[*]**Download JDK 6u2**
You can download it from the development site here:  [http://www.java.net/download/jdk6/6u2/promoted/b02/binaries/jdk-6u2-ea-bin-b02-linux-i586-12_apr_2007.bin]("http://www.java.net/download/jdk6/6u2/promoted/b02/binaries/jdk-6u2-ea-bin-b02-linux-i586-12_apr_2007.bin")
Just save it to your desktop


[*]**Install the JDK**
I installed it to the /opt dir to keep it separate from apt packages. If you'd like to put it somewhere else just change opt to wherever you want to install it. Open a terminal and input the following

Copy installer to opt:
```
sudo mv ~/Desktop/jdk-6u2-ea-bin-b02-linux-i586-12_apr_2007.bin /opt
```

Move to the opt dir:
```
cd /opt
```

Make installer executable:
```
sudo chmod +x jdk-6u2-ea-bin-b02-linux-i586-12_apr_2007.bin 
```

Run the installer:
```
sudo ./jdk-6u2-ea-bin-b02-linux-i586-12_apr_2007.bin 
```

Remove the installer:
```
sudo rm jdk-6u2-ea-bin-b02-linux-i586-12_apr_2007.bin 
```


[*]**Update environment variables:**
You need to edit /etc/environment to let the system know where you installed java.

From a terminal:
```
gksu gedit /etc/environment
```

Add the following lines:
```
JAVA_HOME="/opt/jdk1.6.0_02"
CLASSPATH=".:/opt/jdk1.6.0_02/jre/lib/rt.jar"
```

And prepend the java bin folders to the start of the path so it looks something like this:
```
PATH="/opt/jdk1.6.0_02/bin:/opt/jdk1.6.0_02/jre/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```


[*]**Fix shortcuts**

If, like me, you had jdk6u1 installed already, the "Sun Java 6 Console" shortcut in the "System Tools" menu will point to the old jdk6u1 version. This can be fixed by right clicking on the "Applications" menu, and selecting "Edit Menus". Then locate "Sun Java 6 Console", right click, and select "Properties". Change the Command field to just "jconsole". and click close.

[/LIST]

You need to restart your computer for it to pick up the changed environment variables (is it possible for the system to reload this file without restarting?)

You should be able to run java swing apps, like netbeans and IntelliJ IDEA, fine again now :-)

This was tested on Ubuntu 7.04 32bit

---

### Post by MeanderingCode on 2007-10-18
First off, a thousand thanks to you.  The one liner in other threads:
```
export AWT_TOOLKIT=MToolkit
```
did not work for me.  This did.

NOTE OF POSSIBLE IMPORTANCE!!: I had to uninstall (via uninstall.sh as root in netbeans directory) and reinstall in order for this to work.  Upon installation, Netbeans asked which jvm to use...it kept using that, regardless of my environment variables.  There may be a text file to edit somewhere to point it in the right direction, but un/reinstalling was painless and did it for me.

Question:
About those changes to /etc/environment...That scares me.  Is there any more mainline approach that would fall into the stream of no-dicking-around upon an upgrade?  Replacing symlinks in /usr/bin or something?  I followed your recommendation and it's working, but (relatively new to linux, but familiar enough to know i don't want to bomb my environments file and wary of adding more directories to PATH than i have to) i'd rather find another solution to integrating this java into my system.

Any ideas?

Thanks.

---

### Post by aztechclan on 2008-01-02
awesome tip kev!  This got me going in gusty.  Actually, Gusty includes sun-java6-* packages so you can install the latest with synaptic now.

sudo apt-get remove sun-java5-bin sun-java5-jre sun-java5-jdk
sudo apt-get install sun-java6-jdk sun-java6-jre sun-java6-bin

then uninstall netbeans and reinstall.  Yay it works with compiz effects!  

-Jeremy

---

