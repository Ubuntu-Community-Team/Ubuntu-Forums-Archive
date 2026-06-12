---
title: "what does bash mean"
date: 2014-02-04
forum: New to Ubuntu
---

### Post by newblank25 on 2014-02-04
I tried to use the terminal to get a program I downloade to work. I thought that if I TYPED java-jar/home/directoryname/java-jar programname & then terminal said bash. what did I do wrong?

---

### Post by grahammechanical on 2014-02-04
I do not know what you did wrong but BASH = Bourne Again SHell. It is a replacement for the Bourne Shell. In other words it is a command line interpreter = the terminal and the commands that run or execute in the terminal. The commands can also be written in text files called scripts.

[http://en.wikipedia.org/wiki/Bash_(Unix_shell)](http://en.wikipedia.org/wiki/Bash_(Unix_shell))

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

My guess is that you were running a script that ended without doing much.

Regards.

---

### Post by Iowan on 2014-02-04
It might be a bit easier (for some of us dense folks) if you could copy/paste a sample of what you're typing and seeing for results.

---

### Post by Bashing-om on 2014-02-04
newblank25; Hi !

See all the aboves: Me too slow (??).

A path - to the file to be executed - is required. In your example:
"/home/newblank25/directoryname/programname"
Where "programname" is located in the subdirectory "directoryname" in another subdirectory "newblank25" that may be 1 of several directories located under the top directory "home" that is under the topmost of all files "/".
For example:
```

sysop@1310mini:~$ ls -la /home/sysop/Downloads/shutdown.man.txt
-rw-rw-r-- 1 sysop sysop 3194 Jul 28  2013 /home/sysop/Downloads/shutdown.man.txt
sysop@1310mini:~$

```
where "shutdown.man.txt" might be an executable file.

Else: as I can be real dense-> copy and paste back to us what you are actually doing.

[INDENT]Ain't it great
[INDENT]free education !
[/INDENT][/INDENT]

---

### Post by nothingspecial on 2014-02-04
bash will tell you if you did it wrong but it won't tell you if you did it right (unless you tell it to do so)

So if you literally type ```
java-jar/home/directoryname/java-jar programname
```

Then bash will say ```
bash: java-jar/home/directoryname/java-jar: No such file or directory

```

Which is like saying "This is bash speaking: I can't find what you are asking for"

---

### Post by deadflowr on 2014-02-04
Did it say 
bash: java-jar/home/directoryname/java-jar: No such file or directory
?

Is java-jar a program?
Maybe needs a space.
Two seconds search shows a proper command for java -jar
[http://askubuntu.com/questions/101746/how-can-i-execute-a-jar-file-from-the-terminal](http://askubuntu.com/questions/101746/how-can-i-execute-a-jar-file-from-the-terminal)

---

### Post by newblank25 on 2014-02-04
$ java-jar/home/michael/game/fibs/JavaFIBS2001/JavaFIBS-1.0.12_java16.jar
bash: java-jar/home/michael/game/fibs/JavaFIBS2001/JavaFIBS-1.0.12_java16.jar: No such file or directory
this is what i tried?

---

### Post by ubudog on 2014-02-04
> **newblank25 said:**
> $ java-jar/home/michael/game/fibs/JavaFIBS2001/JavaFIBS-1.0.12_java16.jar
bash: java-jar/home/michael/game/fibs/JavaFIBS2001/JavaFIBS-1.0.12_java16.jar: No such file or directory
this is what i tried?

Hi,

I believe the command you are looking for is:
```
java -jar /home/michael/game/fibs/JavaFIBS2001/JavaFIBS-1.0.12_java16.jar
```

"-jar" is a paramater of the java command, used to specify that you wish to run a jar file.

---

### Post by newblank25 on 2014-02-04
i cut & pasted it & this happened. michael@michael-ubuntu:~$ java -jar /home/michael/game/fibs/JavaFIBS2001/JavaFIBS-1.0.12_java16.jarError: Unable to access jarfile /home/michael/game/fibs/JavaFIBS2001/JavaFIBS-1.0.12_java16.jar

---

### Post by ubudog on 2014-02-04
Do you know where your .jar is that you want to run?

---

### Post by Habitual on 2014-02-05
terminal> 
```
find /home/michael -name JavaFIBS-1.0.12_java16.jar
```

---

