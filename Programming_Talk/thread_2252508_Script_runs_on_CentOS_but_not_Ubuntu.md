---
title: "Script runs on CentOS but not Ubuntu"
date: 2014-11-12
forum: Programming Talk
---

### Post by bewareofthephog on 2014-11-12
Is there any reason why a script would run on CentOS and not Ubuntu?  The script I'm trying to execute can't be posted (I can however post the relevant bits, see below) but the line in question is referencing a packaged JVM.  I'm running Ubuntu 12.04 (No I can't upgrade).

The first problem was I needed to change #!/bin/sh to #!/bin/bash

Now I get the following error:
```
/home/user/installfolder/Ant/bin/ant: 1: exec: /home/user/installfolder/jre/bin/java: not found
```

I've verified that everything is sitting in the correct locations (as seen above)

The section of script producing this error is the following:

```
JAVA_HOME='pwd'/installfolder/jre; export JAVA_HOME
ANT_HOME='pwd'/installfolder/Ant; export ANT_HOME

${ANT_HOME}/bin/ant -f installfolder/AntInstall.xml -quiet -k -propertyfile install.properties -logger org.apache.tools.ant.Logger -lib installfolder/lib $@
```

This all works fine on CentOS 7 but not on Ubuntu 12.04.  The bash version is slightly different between the two but I don't see anything that stands out as that being the problem.

---

### Post by ofnuts on 2014-11-12
Have you got exec permission on /home/user/installfolder/Ant/bin/ant?

---

### Post by spjackson on 2014-11-12
What do you get from the following commands?
```

uname -a
file /home/user/installfolder/jre/bin/java
ldd /home/user/installfolder/jre/bin/java

```

---

