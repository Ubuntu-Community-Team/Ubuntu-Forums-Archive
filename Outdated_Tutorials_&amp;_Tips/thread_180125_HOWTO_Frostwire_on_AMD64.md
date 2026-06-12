---
title: "HOWTO: Frostwire on AMD64"
date: 2006-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Sevoma on 2006-05-21
First, enable extra repositories.
Open up a terminal and type:
```
sudo apt-get install sun-java5-bin
```

Now, download this to your desktop: [http://mirror1.peercommons.net/frostwire/4.10.9/FrostWire-4.10.9-1.i586.deb](http://mirror1.peercommons.net/frostwire/4.10.9/FrostWire-4.10.9-1.i586.deb)

Now open a terminal (or use the one you may have already open) and type:
```
cd Desktop
sudo dpkg -i --force-architecture FrostWire-4.10.9-1.i586.deb

```
If that was successful, type this:
```
sudo gedit /usr/lib/frostwire/runFrost.sh
```
When gedit opens up, remove _everything_ in it and put this in instead:
```
#!/bin/sh

cd "`dirname "$0"`"

export J2SE_PREEMPTCLOSE=1

/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/java -jar -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. -jar FrostWire.jar

```


Now you are finished :D
You can launch it by typing "frostwire" (without the CODEs) in the terminal or by going to Applications->Internet->FrostWire


I hope it works! I wrote this from memory.

---

### Post by ktulu1115 on 2006-05-21
Ran into some difficulties with this.  Java had to be installed via method in this thread - [http://ubuntuforums.org/showthread.php?t=179608&highlight=sun-java5-bin](http://ubuntuforums.org/showthread.php?t=179608&highlight=sun-java5-bin) (basically use Synaptic instead of apt-get - need to accept license).

However, after that, when I try to run Frostwire I get the following error - Unable to access jarfile .logging.impl.NoOpLog

---

### Post by Sevoma on 2006-05-21
[QUOTE=ktulu1115]
However, after that, when I try to run Frostwire I get the following error - Unable to access jarfile .logging.impl.NoOpLog[/QUOTE]

Now it should work. There was a space in the line. I changed the quotes to code and it has correct formatting now.

---

### Post by Strangerdave on 2006-05-28
Hey this worked great thanks!

-SD-

---

### Post by tha_rainman on 2006-05-28
Has anyone got this working with XGL/compiz? I had to log-into my gnome session to get it running. Just displays a blank screen otherwise.

---

