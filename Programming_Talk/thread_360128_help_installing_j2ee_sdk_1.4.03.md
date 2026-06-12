---
title: "help: installing j2ee sdk 1.4.03"
date: 2007-02-12
forum: Programming Talk
---

### Post by onewaytrip on 2007-02-12
i downloaded the j2ee sdk 1.4.03 from sun and i ended up with a bin file. as you probably know i have no idea as what to do at this point. after some searching i found some info on how but in the process only lead to more confusion. so can someone help me out. also is the jre already installed on ubuntu (6.10) or must i installed that as well?

---

### Post by onewaytrip on 2007-02-12
can anyone help?

---

### Post by phossal on 2007-02-13
JDK 1.4 is a pretty simple installation. If you have the bin file on your desktop, *chmod* it so it's executable. (Again, keep it on your desktop by default).
```
sudo chmod +x *.bin
```
Then execute it: Replace filename with the name of the file
```
sudo sh *filename*.bin
```
It will run, make you agree to the license, and then extract a file to your desktop. Effectively that's the guts of installing it. There are a few steps of configuration depending on how integrated you want it, but none of it is absolutely necessary. Perhaps share what you intend to use it for, and how you want to access it, and I can make some recommendations.

---

### Post by onewaytrip on 2007-02-13
well i just want to set it up to i can compile and run java programs i write from the bash shell.  see i had it set up on my windows machine where i only had to type javac file.java to generate the class file then java file to execute the program. so i would like to have a similar setup.

---

### Post by phossal on 2007-02-13
The link to the SUN website is here:
[http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

You probably want to download: *j2sdk-1_4_2_13-linux-i586.bin*. Download it to your desktop. Right-click and change permission to *execute*. Right-click and "open", "run in terminal". Agree to the license terms. It will create a file called: *j2sdk1.4.2_13* either in your desktop or home directory (depending on how you launched the script). Rename that file: Java4 (for convenience). If that file *isn't* on your desktop, move it to your desktop.

Then do this:
```
cd ~/Desktop/Java4/bin
./java -version

```
The output should look something like this:
```
bash 3.1:**./java -version**
java version "1.4.2_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_13-b06)
Java HotSpot(TM) Client VM (build 1.4.2_13-b06, mixed mode)
bash 3.1:

```

I just did it myself, so I'm fairly sure it will work. The only thing I can't be sure of at the moment is whether or not you'll need a sym link to an older module. The earlier versions require it, and I've already created one, so I can't tell if JDK4 would ordinarily kick back any "error: cannot find <filename>.so " messages. If it does, the Java Tutorial in my sig contains a post on how to fix that.

---

### Post by onewaytrip on 2007-02-13
thanks, i cant believe there so many different ways of installing this thing, from what i described above which method would be best?

---

### Post by phossal on 2007-02-13
Direct, as I laid out. By *best*, I imply that it accomplishes your goals, and I've done it successfully. That means I can *help you do it.* :)

---

### Post by onewaytrip on 2007-02-13
alright i got everything ready and gonna try to installed. ill reply the result after im done.

---

### Post by onewaytrip on 2007-02-13
great i installed everything just like you said and got the exact same output as you. now my question is how do i compile and run my programs?

---

### Post by phossal on 2007-02-14
You cd into the folder, and then instead of running *./java* you run *./javac* and pass it whatever params and file paths you want.

---

### Post by onewaytrip on 2007-02-14
ok i wrote a simple "hello world" program and it compiles but when i try to run i get an error.

here the code:

public class test
{
      public static void main(String args [])
          {
                System.out.println("hello world");
          }
}

so then i cd to java folder, then i type:

 ./javac ~/Desktop/test.java

everything compiles and a class file is generated. now back in java folder i type:

 ./java ~/Desktop/test

then i get this error:

 Exception in thread "main" java.lang.NoClassDefFoundError: "/home/ricky/Desktop/test"

and thats where im stuck at the moment, any ideas as to what im doing wrong?

---

### Post by phossal on 2007-02-14
When you're compiling the way you are, you need to include the classpath on your executable.
```
~/Desktop/Java4/bin/javac *-classpath ~/Desktop/Java4/bin* ~/Desktop/test.java
```
Then:
```
~/Desktop/Java4/bin/java ~/Desktop/test
```
There are tricks to setting the classpath. For me, as an example, I set it in my .bashrc file. You can see examples in the tutorial included in my signature. I have 4 different JDK's, and I need to swap between them easily. 

Your *needs* will dictate how you configure your system.

---

### Post by ashishk03 on 2009-07-21
i m also having similar problem while installing jdk. i m using ubuntu 9.04!!
after executing the following command:
[B]sudo sh  java_ee_sdk-5_07-linux.bin
[/B]i get following error:
[B]jdk-507.bin: 1: Syntax error: "(" unexpected
.
.
.
[/B]plz help me out, i dnt understand whr problem lies? :(

thanks

---

