---
title: "Get jars properly in my Classpath"
date: 2008-01-29
forum: Programming Talk
---

### Post by Saithn on 2008-01-29
For compiling a simulator I have to set some jars in my classpath. However it doesn't seem to work. 

I'm using ubuntu 7.10 and compiling using java is no problem. However, the classes in the jars give erros (they can't be found, so classpath problem I suppose).

The four jars are located at:

/home/delodic/Study/mason/itext-1.2.jar
/home/delodic/Study/mason/jcommon-1.0.0.jar
/home/delodic/Study/masonjfreechart-1.0.1.jar
/home/delodic/Study/mason/jmf.jar


~/Study/mason$ sudo gedit /etc/environment

gives

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
CLASSPATH=":/home/delodic/Study/mason/itext-1.2.jar:/home/delodic/Study/mason/jcommon-1.0.0.jar:/home/delodic/Study/masonjfreechart-1.0.1.jar:/home/delodic/Study/mason/jmf.jar"
```

I extended the environment by adding the CLASSPATH="...." so maybe I have to add something more?

---

### Post by Saithn on 2008-01-29
I just found all packages in the synaptic. However, when compiling I still get errors. First errors that the packages don't exist, and later missing symbol messages. The pacakage erros:

```
sim/util/media/PDFEncoder.java:7: package com.lowagie.text.pdf does not exist
import com.lowagie.text.pdf.*; 
^
sim/util/media/chart/ChartGenerator.java:22: package org.jfree.data.xy does not exist
import org.jfree.data.xy.*;
^
sim/util/media/chart/ChartGenerator.java:23: package org.jfree.chart does not exist
import org.jfree.chart.*;
^
sim/util/media/chart/ChartGenerator.java:24: package org.jfree.chart.event does not exist
import org.jfree.chart.event.*;
^
sim/util/media/chart/ChartGenerator.java:25: package org.jfree.chart.plot does not exist
import org.jfree.chart.plot.*;
^
sim/util/media/chart/ChartGenerator.java:26: package org.jfree.data.general does not exist
import org.jfree.data.general.*;
^
sim/util/media/chart/ChartGenerator.java:27: package org.jfree.chart.renderer.xy does not exist
import org.jfree.chart.renderer.xy.*;
^
sim/util/media/chart/ChartGenerator.java:28: package org.jfree.data.general does not exist
import org.jfree.data.general.*;
^
sim/util/media/chart/ChartGenerator.java:31: package com.lowagie.text does not exist
import com.lowagie.text.*;
^
sim/util/media/chart/ChartGenerator.java:32: package com.lowagie.text.pdf does not exist
import com.lowagie.text.pdf.*;
```

And all jars are now installed using the synaptic

```
delodic@Delodic:~/Study/mason$ sudo apt-get install libjcommon-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]libjcommon-java is already the newest version.
libjcommon-java set to manual installed.[/B]
0 upgraded, 0 newly installed, 0 to remove and 129 not upgraded.

delodic@Delodic:~/Study/mason$ sudo apt-get install libjlayer-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**libjlayer-java is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 129 not upgraded.

delodic@Delodic:~/Study/mason$ sudo apt-get install libjfreechart-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**libjfreechart-java is already the newest version**.
0 upgraded, 0 newly installed, 0 to remove and 129 not upgraded.

delodic@Delodic:~/Study/mason$ sudo apt-get install libitext-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**libitext-java is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 129 not upgraded.
```

---

### Post by xlinuks on 2008-01-30
Try setting the classpath like this (putting the leading point):
```

CLASSPATH=".:/home/delodic/Study/mason/itext-1.2.jar:/home/...and so on"

```
If that doesn't help consider posting your source code including the packages, I will try to compile and see what's the matter (but don't promise anything).

---

### Post by Saithn on 2008-01-30
Thanks for your reply. To bad it didn't work. However, I've chosen different software now, so this is not a problem anymore :)

---

