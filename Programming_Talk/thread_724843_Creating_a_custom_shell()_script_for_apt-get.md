---
title: "Creating a custom shell(?) script for apt-get"
date: 2008-03-15
forum: Programming Talk
---

### Post by Redlazer on 2008-03-15
I find myself reformatting relatively often, and would like to create a script that will automatically download my rather long list of preferred programs. I looked around google, and all i really got was this:
```

#!/bin/bash

apt-get -y install filelight

apt-get -y install unison-gtk

apt-get -y install sun-java6-jdk

apt-get -y install azureus

apt-get -y install pidgin

apt-get -y install pidgin-plugin-pack

apt-get -y install vlc

apt-get -y install wine

apt-get -y install mysql-admin

apt-get -y install mysql-server

apt-get -y install firefox
```

It runs, but i get the following output:

```
: not foundes.sh: 2:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package firefox

```

Presumably, im missing something here.

You know what would be REALLY cool, is if someone can help me create a java program that would do the same (being as i have a basic understanding of Java). However, i cant imagine that being particularily easy. 

That outlandish wish aside, can anyone help me get my simple script working?

I did double check that I have all the package names correct. I can run them separately from the command line.

Thanks for your help : )

-Fred

---

### Post by wdk on 2008-03-15
Try using dpkg as in this post:

[http://ubuntuforums.org/showthread.php?t=261366]("http://ubuntuforums.org/showthread.php?t=261366")

Once you have installed all your preferred packages, create the list. Then, next time you reinstall your system, all you have to do is copy the list back to your fresh install and reinstall the packages using dpkg, as explained in the link.

Hope this helps!

---

### Post by Redlazer on 2008-03-15
Excellent find, thanks : )

-Fred

---

