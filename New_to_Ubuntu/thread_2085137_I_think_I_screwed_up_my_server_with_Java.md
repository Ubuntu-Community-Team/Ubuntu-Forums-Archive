---
title: "I think I screwed up my server with Java"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by clskier on 2012-11-17
I'm guessing at the cause here.  Here's the story so far.  I have been setting up my HTPC using Ubuntu server and XBMC. Everything has been working great.  Slowly adding more services.  Have an FTP, torrent, SSH, Crashplan backup client, and Samba server all running great.  Yesterday I decided to try a subsonic server.  After following these directions:

[INDENT]First, install Java: sudo apt-get install openjdk-6-jre
Download the Subsonic .deb package and install it: sudo dpkg -i subsonic-x.x.deb[/INDENT]

I noticed a dramatic slowdown to the responsiveness of the system over SSH as well as a significantly higher CPU usage.  After playing around with subsonic on my phones and tablets I decided the service was not worth the drain on the system.  I attempted to uninstall using:

[INDENT]sudo apt-get remove openjdk-6-jre
sudo apt-get remove Subsonic[/INDENT]

However after a reboot I still see the same drain on the system, it looks like there are remnants of subsonic, and "top" is reporting a 15% CPU usage by Java when the server is sitting idle.

sudo update-alternatives –config java shows two versions of Java to choose from (6 and 7)

Everything still works, just seems like something is wrong.

---

### Post by Ms. Daisy on 2012-11-17
use dpkg to make sure you removed all the java and subsonic packages.
```
dpkg -l | grep jre*
``` 
You could also try the --purge switch with apt-get:
```
sudo apt-get remove --purge Subsonic
```

---

### Post by clskier on 2012-11-17
dpkg -l | grep jre*

ii  default-jre-headless                   1:1.6-43ubuntu2                          Standard Java or Java compatible Runtime (headless)
ii  icedtea-6-jre-cacao                    6b24-1.11.5-0ubuntu1~12.04.1             Alternative JVM for OpenJDK, using Cacao
ii  icedtea-6-jre-jamvm                    6b24-1.11.5-0ubuntu1~12.04.1             Alternative JVM for OpenJDK, using JamVM
ii  icedtea-7-jre-jamvm                    7u9-2.3.3-0ubuntu1~12.04.1               Alternative JVM for OpenJDK, using JamVM
ii  openjdk-6-jre-headless                 6b24-1.11.5-0ubuntu1~12.04.1             OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib                      6b24-1.11.5-0ubuntu1~12.04.1             OpenJDK Java runtime (architecture independent libraries)
ii  openjdk-7-jre                          7u9-2.3.3-0ubuntu1~12.04.1               OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-7-jre-headless                 7u9-2.3.3-0ubuntu1~12.04.1               OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-7-jre-lib                      7u9-2.3.3-0ubuntu1~12.04.1               OpenJDK Java runtime (architecture independent libraries)

---

### Post by Ms. Daisy on 2012-11-17
That output is telling you that you have not completely removed Java.  Run the same dpkg command with Subsonic to see what packages remain from that as well.

Then you can use ```
apt-get remove --purge <fill_in_package_name>
``` to remove the packages. Replace <fill_in_package_name> with each package name.

---

### Post by clskier on 2012-11-19
Thanks for the help.  Your followed the directions and removed all signs of Java on the system, yet I still had the lag in responsiveness.  I re-installed from a recovery point I had from a week ago and everything was great.  That recovery point was before I had set up Crashplan, so I re installed Crashplan and noticed the installation included Java.  After Crashplan was running, everything was still working perfectly.

My assumption is that somehow the two versions of Java conflicted with one another.  Not sure why I couldn't remove the conflict, but it's working fine now.

---

### Post by Ms. Daisy on 2012-11-19
Glad you got it sorted out.

---

