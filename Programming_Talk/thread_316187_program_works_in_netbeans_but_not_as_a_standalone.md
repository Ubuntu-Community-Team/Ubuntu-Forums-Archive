---
title: "program works in netbeans but not as a standalone"
date: 2006-12-10
forum: Programming Talk
---

### Post by sailingboarder on 2006-12-10
i have made a program in java using the netbeans ide and the netbeans platform
the program works fine when i run it from inside the ide, but when i try 2 run it as a standalone application, it won't work
i've tried all different ways(including a zip and javaws distrubution), both on my ubuntu system and i've taken it over to my brother's xp box, but nothing seems to work

i think part of my problem on ubuntu is, while i do have the newest jre installed, the command ```
java --version
``` returns ```
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

how do i tell the computer to use jre1.5.0?

so this is a two part question, i guess
first, how do i get the program from netbeans with the platform to run on its own, preferribly on a windows box, since this is what i will eventually need it 2 run on, and secondly, how do i get rid of the old jre on ubuntu?

---

### Post by Ramses de Norre on 2006-12-10
```
sudo update-java-alternatives -s java-1.5.0-sun
```
Then cd to the dir with your java files and run ```
javac *.java
java MainClass
```

You need to add any external classes with the cp (classpath) option like this (mind the ":."!): ```
javac -cp /path_to_classes:. *.java
java -cp /payh_to_classes:. MainClass
```

And don't append the class extension when using java.

Print any errors that occur.

On windows you should be able to use the same commands, and when you pass the class file through you wont have use javac again.

---

### Post by DaveBorealis on 2006-12-10
> **Ramses de Norre said:**
> You need to add any external classes with the cp (classpath) option like this (mind the ":."!): ```
javac -cp /path_to_classes:. *.java
java -cp /payh_to_classes:. MainClass
```

And don't append the class extension when using java.


Yep, when I run java app's I use the following:
```
/usr/bin/java -cp ~/projects MyApp &
```

Note that the class path is to the _directory_ containing the class file with main(). I.e., there's no '/' between the containing directory and the application.  The '&' is optional...only used to return the prompt and run the app in the background.

---

### Post by sailingboarder on 2006-12-10
when i ran update-java-alternatives i got the error  ```
sudo update-java-alternatives -s java-1.6.0-sun
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.5.0-sun

``` (i realized i am using the 1.6.0-rc version of java
i tried reinstalling java into the /usr/lib/jvm folder, but got the same error
so then i tried using the name of the folder and got the following:
```
/usr/lib/jvm$ sudo update-java-alternatives -s jdk1.6.0
update-java-alternatives: file does not exist: /usr/lib/jvm/.jdk1.6.0.jinfo
```
any ideas on how to make this work?

im going 2 try the program on the xp box right now, and c if i can find the problem there, and i'll post here if i need help with that

thankyou Ramses de Norre and DaveBorealis for your help

---

### Post by Ragazzo on 2006-12-10
Try 

```

sudo update-alternatives --config java

```

---

### Post by sailingboarder on 2006-12-10
```
sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:
```
neither one of those is the updated version from sun

i am able to locate 4 or 5 other locations of the java program, but noe of them are on this list...why is that?

---

### Post by sailingboarder on 2006-12-10
i think i fixed my own problem...well, one of them

i found this how-to: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")
i found the packate in Applications -> Add/Remove, and installed it
i then used Ragazzo's suggestion to change the default version of java
now that i have java working on ubuntu, i can now tackle the larger problems (those actually related 2 my program)

thankyou everyone for your help, i truely appreciate it

---

### Post by Ramses de Norre on 2006-12-11
> **Ragazzo said:**
> Try 

```

sudo update-alternatives --config java

```

You alse need to to this for javac etc then.. update-java-alternatives is designed to to this for all java related apps.

---

### Post by Ragazzo on 2006-12-11
> **Ramses de Norre said:**
> You alse need to to this for javac etc then.. update-java-alternatives is designed to to this for all java related apps.

Thanks for the info. I've never had multiple JDK's installed so I've always updated just the java command.

---

