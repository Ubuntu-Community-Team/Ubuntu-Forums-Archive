---
title: "problems installing Specify in Ubuntu 12.04"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by fernandesornito on 2013-06-06
[COLOR=#000000][FONT=Lucida Grande]Dear all,

[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande][/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]I am trying to install the program "specify" [/FONT][/COLOR][http://specifysoftware.org/](http://specifysoftware.org/)[COLOR=#000000][FONT=Lucida Grande] in ubuntu 12.04. [/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande][/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]Using the terminal (./Specify_unix_EZDB_64.sh) I got this message:[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]"The version of the JVM must be at least 1.6 and at most 1.6.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/passarinho/.install4j"



It could be a problem with the Java but I have installed java 1.7.0. MySQL is also installed.
[COLOR=#051624][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#051624][FONT=Arial]I would be grateful if someone could give me some tips how to solve this problem. Specify is a very important program for my work. It is easy to install in windows but I am not using windows anymore.....[/FONT][/COLOR]
[/FONT][/COLOR]

Cheers

Alex

---

### Post by slickymaster on 2013-06-06
> **fernandesornito said:**
> [COLOR=#000000][FONT=Lucida Grande]Dear all,[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]I am trying to install the program "specify" [/FONT][/COLOR][http://specifysoftware.org/](http://specifysoftware.org/)[COLOR=#000000][FONT=Lucida Grande] in ubuntu 12.04. [/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]Using the terminal (./Specify_unix_EZDB_64.sh) I got this message:[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]"The version of the JVM must be at least 1.6 and at most 1.6.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/passarinho/.install4j"

It could be a problem with the Java but I have installed java 1.7.0. MySQL is also installed.[COLOR=#051624][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#051624][FONT=Arial]I would be grateful if someone could give me some tips how to solve this problem. Specify is a very important program for my work. It is easy to install in windows but I am not using windows anymore.....[/FONT][/COLOR][/FONT][/COLOR]

Cheers

Alex

It seems that Specify requires Java 6 and you have Java 7 installed. So either you downgrade your Java Virtual Machine to Java 6 or you install Java 6, still keeping Java 7 installed, but you'll have to point Specify to Java 6.

---

