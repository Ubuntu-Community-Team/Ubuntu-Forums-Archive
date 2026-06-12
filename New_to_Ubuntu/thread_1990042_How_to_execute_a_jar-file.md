---
title: "How to execute a jar-file?"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by kramer65 on 2012-05-29
Hello there,


I want to install a downloaded jar-program. To do this, [the instructions]("http://individuals.interactivebrokers.com/en/control/systemstandalone.php?os=unix") tell me to download the program and then run the command:
```
jar xf unixmacosx.jar
```
When I run this though I get a message saying this:
> The program 'jar' can be found in the following packages:
 * default-jdk
 * fastjar
 * gcj-4.6-jdk
 * openjdk-6-jdk
 * gcj-4.5-jdk
 * openjdk-7-jdk
Try: sudo apt-get install <selected package>

Does anybody know what I need to do in order to execute the jar-file?

All tips are welcome!

---

### Post by ngubk on 2012-05-29
sudo apt-get install openjdk-7-jdk

java -jar filename.jar

---

### Post by kc1di on 2012-05-29
I'm assuming you have openjdk installed on your machine.
if not install either version 6 or 7  and you might as well install Icedtea plugin to match the version your choose. 

the syntax for executing a .jar file is as follows in a terminal

```
java -jar "filename.jar" 
``` without the quotes 
of course you have to be in the same director /file folder where the file is located.

you can install openjdk and icedtea by doing the following in a terminal also.
```
sudo apt-get install icedtea-7-plugin
```
That will plug all the others you need. 

Good Luck

---

### Post by kramer65 on 2012-05-29
How stupid of me. I recently reinstalled Ubuntu 12.04 and forgot to install the openjdk after that. Thanks for the tip!

One more question. I just installed Openjdk-6-jdk (since all other java-versions where also version 6). After that I tried the instruction provided with the download:
```
jar xf unixmacosx.jar
```
That worked like a charm, and I've got the program running now. I still wonder though. What is the differernce between '*jar xf filename.jar*' and the code you two suggested: '*java -jar filename.jar*'

Or are they the same?

---

### Post by kc1di on 2012-05-29
> **kramer65 said:**
> How stupid of me. I recently reinstalled Ubuntu 12.04 and forgot to install the openjdk after that. Thanks for the tip!

One more question. I just installed Openjdk-6-jdk (since all other java-versions where also version 6). After that I tried the instruction provided with the download:
```
jar xf unixmacosx.jar
```
That worked like a charm, and I've got the program running now. I still wonder though. What is the differernce between '*jar xf filename.jar*' and the code you two suggested: '*java -jar filename.jar*'

Or are they the same?
Glad you got it going. 
```
jar xf 
```
is the code to extract a compessed java/jar file so the file you had must have been compressed and only need to be extracted to work.

the command we gave was the actual execute command from a terminal

---

