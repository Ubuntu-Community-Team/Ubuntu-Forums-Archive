---
title: "Running my own developed Java application"
date: 2006-04-20
forum: Programming Talk
---

### Post by Ron W on 2006-04-20
I've been developing a Java application using Eclipse. I'm now wanting to use this application outside of Eclipse and am unable to find out how to do it. Double clicking on the .class file that contains the 'main' function just gives a message saying that the .class file cannot be seen.

Can anyone advise me on how to run a Java application?

Thanks

Ron

---

### Post by kaamos on 2006-04-20
A good example why learning Java should be started with nano or emacs or vi... and not with eclipse. :)

Open a terminal, navigate (use the command "cd") to the directory where the .class file is locate. Assuming the name of your class is Example you would then type "java Example".

---

### Post by DeadEyes on 2006-04-20
If your using version 5 you might have to use a class path
try:
java -cp . Myapp

---

### Post by mostwanted on 2006-04-21
[QUOTE=Ron W]I've been developing a Java application using Eclipse. I'm now wanting to use this application outside of Eclipse and am unable to find out how to do it. Double clicking on the .class file that contains the 'main' function just gives a message saying that the .class file cannot be seen.

Can anyone advise me on how to run a Java application?

Thanks

Ron[/QUOTE]

Either associate .class files with java (right click, properties, open with) or make a launcher or shell script that opens your app with java.

---

