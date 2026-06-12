---
title: "Setting CLASSPATH and PATH"
date: 2011-01-23
forum: Programming Talk
---

### Post by yASHpRIT on 2011-01-23
i am totally new to Ubuntu as i have done with everything except setting CLASSPATH and PATH for java 6.
i googled this question but didn't get my work done. i don't want to do spam by asking repeating question i am really facing problem that's why i am asking this question 
can somebody tell me how to do this but in simple way as i even don't know which type of shell i am using 

when i type 
which java i got
```
 /usr/bin/java
```
what i want is that setting class path for my class which is in another drive not on where ubuntu is installed drive was created by windows and have formate NTFS 
total path to my folder where my source  file are stored is 
/media/ENG_SONG/Learning_Assignment/JAVA/src$
and my class file are stored in 
/media/ENG_SONG/Learning_Assignment/JAVA/class$
.java file can be complied and stored in class folder in windows by doing 

```
javac -d ..\class MyProgram.java
```
now how to attain this in Ubuntu 
so totally i am having these question can somebody explain me this and tell me how to do these thing 
PS i don want to use netbeans and eclipse or any IDE 
P.S. Sorry for bad English

---

### Post by Some Penguin on 2011-01-24
Same way you set up any other environment variables in Ubuntu.  Why should it be any different?

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

### Post by slavik on 2011-01-24
start learning about ant.

---

### Post by yASHpRIT on 2011-01-24
i got my path variable ready now i am only facing problem ib classpath

my current working directory is:
```
/media/ENG_SONG/Learning_Assignment/JAVA/src$
```
now i complied java program by this:
```
/media/ENG_SONG/Learning_Assignment/JAVA/src$ javac -d ../class Life.java

```
till now every thing works fine but as soon as i run my program from this directory 
```
/media/ENG_SONG/Learning_Assignment/JAVA/src$ java Life

```
i am getting NoClassDefFoundError
i have also tried to chnage my working directory then checked weather it working or not 
```
/media/ENG_SONG/Learning_Assignment/JAVA/class/codechef$ java Life

```
whereas codechef is package name defined in java file its creating package but running my program
i know this is related to CLASSPATH
can anybody tell me how to do this in exact way 
please guys help me out as i am running out of time

---

### Post by dileepm on 2011-01-27
in your '/etc/environment' file you can say

> CLASSPATH=/your_ntfs_path_classes:/your_any_other_jars:.

I hope this helps

---

