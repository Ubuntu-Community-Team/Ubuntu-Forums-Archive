---
title: "plz help me out with classpaths"
date: 2007-04-05
forum: Programming Talk
---

### Post by punkdanne on 2007-04-05
Im doing a schoolprojet in Java, making an mp3-player.
I want to use mp3spi from [http://www.javazoom.net/mp3spi/mp3spi.html](http://www.javazoom.net/mp3spi/mp3spi.html) to play mp3 files, and in the readme file it says:

- How to install MP3SPI ?
Before running MP3SPI you must set PATH and CLASSPATH for JAVA
and you must add jl1.0.jar, tritonus_share.jar and mp3spi1.9.4.jar to the CLASSPATH.

But i have never used classpaths before, and am not quite sure what they are reffering to. isn't it enough just to leave these jars in the same folder as the project?
thanks in advance for any help!

---

### Post by Tuna-Fish on 2007-04-05
Classpath is a list of the places java will look for code to use. If you'r classpath includes . (current directory), then you can just dump them in the same dir as your own program.

---

### Post by samjh on 2007-04-05
> **punkdanne said:**
> But i have never used classpaths before, and am not quite sure what they are reffering to. isn't it enough just to leave these jars in the same folder as the project?

For simple projects, yes.

But if you cannot execute your main .class file with java, then you will need to use the -cp parameter to specify the location of your class files.

For example, let's say you have your project's main class (let's call it MyProject.class) at /home/you/project directory, and there is a class you want to use located at /home/anotherdude/classes

In that case, you will need to run MyProject.class using this command:
```
java -cp /home/you/project:/home/anotherdude/classes MyProject
```
What that command does is tell the java virtual machine to look for classes to run at /home/you/project and /home/anotherdude/classes directories.  Notice that : symbol is used to separate the different directory paths.

If you are running the java command from the same directory that your class file is, then you can use ./ instead of the full directory name.

---

### Post by punkdanne on 2007-04-11
Thanks for the help =) its finally working now :D

---

