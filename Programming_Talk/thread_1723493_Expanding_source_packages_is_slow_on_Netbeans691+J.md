---
title: "Expanding source packages is slow on Netbeans691+JDK6_23-64bits+Ubuntu10.10-64bits"
date: 2011-04-07
forum: Programming Talk
---

### Post by Damien B. on 2011-04-07
Hi, 
 
I have a fast machine (sandybridge i7+SSD) and netbeans loads fast, builds fast etc... 
The project is a maven project but it's not big (50 files). 
But when I expand a source package, I have to wait 3 secs on average... 
I have a small graphic card (embedded Intel i915) but I dont think  that's the issue as the rest of the app is fine (opening/closing windows  etc...). 
I have tried expanding the memory limits, improve gc, etc... 
Here are my startup options (they dont make any difference with the default ones, good or bad): 
netbeans_default_options="-J-client -J-Xss48m -J-Xms128m  -J-XXPermSize=256m -J-XX:MaxPermSize=512m  -J-Dapple.laf.useScreenMenuBar=true  -J-Dapple.awt.graphics.UseQuartz=true -J-Dsun.java2d.noddraw=true  -J-XX:+UseConcMarkSweepGC -J-XX:+CMSClassUnloadingEnabled  -J-XX:+CMSPermGenSweepingEnabled" 
Any idea? 
Thanks, 
Damien

---

### Post by r-senior on 2011-04-07
When you say expand, do you mean clicking in the navigator in Netbeans to see the contents of a project?

Is the project under version control?

---

### Post by Damien B. on 2011-04-07
I mean I open a maven project, expand it, expand the sources folder, then expand any package in the sources, and I wait 2-3 seconds for each package. I also wait 1-2 seconds to close it...
The project is not under any source control.
The same setup is quick under an average windows machine (just saying that for info).
My plan is to try changing the laf to Metal (GTK is always a bit different), then running on a 32bit JDK, then installing 11.04RC1 and see if any of them make a difference, unless you or anybody else has a better idea?
Thanks,
Damien

---

### Post by Damien B. on 2011-04-08
Indeed the problem is related to the GTK LookAndFeel...
I switched to Metal by adding "--laf Metal" in the jdk options in ./etc/netbeans.conf and the problem is solved!

---

