---
title: "[SOLVED] Oracle Java 1.7 install"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by guy.dillen on 2014-01-04
Standard install of Ubuntu 12.04 LTS Desktop installs OpenJDK1.07. I want Oracle JDK 1.7, so I installed it the following way:

[COLOR=#000000][FONT=Arial][FONT=Arial]1) Download the JDK 7 from: 
[http://www.oracle.com/technetwork/java/javase/downloads/jdk7u9-downloads-1859576.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7u9-downloads-1859576.html)[/FONT][FONT=Arial]2) You will download the tar.gz file. Extract it to your preferred location then run this:[/FONT][FONT=Arial]– Create a new folder:[/FONT][COLOR=#110000][FONT=Arial][COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**mkdir**[/COLOR] [COLOR=#660033]-p[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]lib[COLOR=#000000]**/**[/COLOR]jvm[COLOR=#000000]**/**[/COLOR]jdk1.7.0

[/FONT][/COLOR]
[FONT=Arial]– Move the content of JDK to your new location[/FONT][COLOR=#110000][FONT=Arial][COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**mv**[/COLOR] [COLOR=#000000]**<**[/COLOR]EXTRACTED_FOLDER[COLOR=#000000]**>/***[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]lib[COLOR=#000000]**/**[/COLOR]jvm[COLOR=#000000]**/**[/COLOR]jdk1.7.0[COLOR=#000000]**/**[/COLOR]

[/FONT][/COLOR]
[FONT=Arial]– Then Run the following lines one at a time[/FONT][COLOR=#110000][FONT=Arial][COLOR=#C20CB9]**sudo**[/COLOR] update-alternatives [COLOR=#660033]--install[/COLOR] [COLOR=#FF0000]"/usr/bin/java"[/COLOR] [COLOR=#FF0000]"java"[/COLOR] [COLOR=#FF0000]"/usr/lib/jvm/jdk1.7.0/bin/java"[/COLOR] [COLOR=#000000]1[/COLOR]
 
[COLOR=#C20CB9]**sudo**[/COLOR] update-alternatives [COLOR=#660033]--install[/COLOR] [COLOR=#FF0000]"/usr/bin/javac"[/COLOR] [COLOR=#FF0000]"javac"[/COLOR] [COLOR=#FF0000]"/usr/lib/jvm/jdk1.7.0/bin/javac"[/COLOR] [COLOR=#000000]1[/COLOR] 
 
[COLOR=#C20CB9]**sudo**[/COLOR] update-alternatives [COLOR=#660033]--install[/COLOR] [COLOR=#FF0000]"/usr/bin/javaws"[/COLOR] [COLOR=#FF0000]"javaws"[/COLOR] [COLOR=#FF0000]"/usr/lib/jvm/jdk1.7.0/bin/javaws"[/COLOR] [COLOR=#000000]1[/COLOR]

[/FONT][/COLOR]
[FONT=Arial]
This seems to work perfectly. When doing a java -version it gives me the last installed version 1.7.0_45.

But my question is: should I uninstall the OpenJDK1.7 (or leave it on my machine)?

Thanks.

[/FONT]
[/FONT][/COLOR]

---

### Post by QIII on 2014-01-04
Hello!

You can leave it.  They can coexist happlily.  The one you select as your alternative is the one that will be used.

Just so you are aware, you will have to watch for updates having done it the way you did.   And you pounded out a few more keystrokes than you needed to.

Please have a look at the link in my signature under "Command Line methods" and click on "Using webupd8.org's strikingly simple method" for a much easier way to install -- and it will automatically give you updates to Oracle Java 7 when you do your normal updates.

Cheers!

---

### Post by guy.dillen on 2014-01-04
Many thanks.

---

