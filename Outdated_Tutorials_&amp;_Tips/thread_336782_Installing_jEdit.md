---
title: "Installing jEdit"
date: 2007-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by danrooke on 2007-01-12
Hi there,

I thought that I would share with you a method to install jEdit on Edgy Eft. I hope it helps someone!

[LIST=1]
[*]If you do not have a Java Runtime Environment installed, install package 'sun-java5-jre' and it's dependencies via Synaptic.
[*][Download]("http://jedit.org/index.php?page=download") jEdit's Java Based Installer
[*]Start installer by right clicking on the file and selecting 'Open with "Sun Java 5.0 runtime"' from the context menu.
[*]Follow install procedure taking note of where you install.
[*]jEdit should now be installed.
[*]Create a new launcher with the command ```
java -server -mx128m -classpath "/home/danr/jedit/4.3pre8/jedit.jar" org.gjt.sp.jedit.jEdit $@
``` adjusting the path as necessary.
[*]Select icon for launcher from '/home/danr/jedit/4.3pre8/doc/', adjust path again.
[*]Resize icon where necessary by right clicking and selecting 'Stretch icon' from context menu.
[/LIST]

---

### Post by Sef on 2007-01-12
Moving to HowTo forum.

---

