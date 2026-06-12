---
title: "Installing BlueJ and Jdk"
date: 2009-02-05
forum: Programming Talk
---

### Post by coachabower on 2009-02-05
Hi, I'm trying to install BlueJ so I can do all of my programming in Linux instead of c++ in Linux and Java in Windows. 

So far I've used sudo apt-get install openjdk-6-jre-headless
to get my jdk installed, but I'm stumped on installing BlueJ.  The installation instructions on their website says to use the command path/to/jdk/bin/java -java bluej-250.jar
My path to jdk seems to be etc/java-6-openjdk  I could be wrong if theres another folder somewhere else, but in this folder there is no bin path.  So I get a /bin/java not found error, if I leave out the path/to/jdk part it says -java command not recognized.

It doesn't have to be BlueJ if anyone has another suggestion, thats just what I've used so far.  Any help would be great.

---

### Post by jespdj on 2009-02-05
Just try this:
```
java -jar bluej-250.jar
```

---

### Post by Austin32 on 2009-03-16
Can anyone help me, I am also trying to install bluej but my when I follow the bluej installation instructions I get

Unable to access jarfile bluej-250.jar

the file is installed right on my desktop so I believe my path is correct?

---

### Post by Sub101 on 2009-03-16
```
cd Desktop
java -jar bluej-250.jar
```

That should be all you need?

---

### Post by Austin32 on 2009-03-16
tried that is still says unable to access jarfile

this was the code I entered 

austin32@austin32-desktop:~/desktop$ java -jar bluej-250.jar

---

### Post by jespdj on 2009-03-17
Can you see that the file is there? If you type this:
```
ls -l
```
then what is the output?

---

### Post by Austin32 on 2009-03-17
when I type: ls -l it tells me total 0

and when I type: ls -l bluej-250.jar it says

 cannot access bluej-250.jar: no such file or directory

the file downloaded to my desktop I can see it

---

### Post by jespdj on 2009-03-17
Well, if ls doesn't show you the file, then you are not in the right directory.

Note that what you see on your desktop is in a folder named "**D**esktop" in your home directory - not "**d**esktop". File and folder names are case sensitive in Ubuntu.

Looking at your command:
```
austin32@austin32-desktop:~/desktop$ java -jar bluej-250.jar
```
It looks like you are in a folder named "desktop" instead of "Desktop".

---

### Post by Austin32 on 2009-03-17
Ok, thanks for the help, I have not had ubuntu very long, only a couple weeks and I had no previous linux experience so I am pretty new to it.

---

### Post by jespdj on 2009-03-17
So, is it working now?

---

### Post by Austin32 on 2009-03-17
No i just got home to try it, when I open the console it looks like this:

austin32@austin32-desktop:~$ 

when I enter : java -jar bluej-250.jar 

I get : unable to access jarfile bluej-250.jar

---

### Post by jespdj on 2009-03-18
You need to be in the correct directory. Maybe you should Google for a tutorial on how to use basic terminal commands. Ok, I'll try to explain it in small steps...

1. Open a terminal by selecting Applications / Accessories / Terminal. You'll see the terminal window with the prompt:
```
austin32@austin32-desktop:~$
```

2. Navigate to the Desktop folder with the "cd" command by typing in the following:
```
cd Desktop
```
Note that it is important that you type this in exactly. Do not type "desktop" with a lower-case "d" - folder names are case-sensitive in Ubuntu.

3. The prompt should now look like this:
```
austin32@austin32-desktop:~/Desktop$
```

4. Type in the following command to see the files in the Desktop folder:
```
ls -l
```
You should see the file bluej-250.jar in the list. If you don't see it, then you are not in the right directory, or you don't have the file for some reason.

5. If you do see it, type the following command to run the program:
```
java -jar bluej-250.jar
```

Try these tutorials for using the terminal:
[http://www.brighthub.com/computing/linux/articles/7116.aspx](http://www.brighthub.com/computing/linux/articles/7116.aspx)
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by Austin32 on 2009-03-18
Ok I followed the direction to the letter and when I used ls -l I did see the file however when I used java -jar bluej-250.jar I get:

invalid or corrupt jarfile bluej-250.jar

I will delete these and download them again from the java.sun website and try again

Thanks again for the assistance

---

### Post by nefffffffffff on 2009-05-07
I have a similar problem.  When I follow these steps, I get the following:

> Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
    at java.lang.Runtime.load0(Runtime.java:787)
    at java.lang.System.load(System.java:1022)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
    at java.awt.Component.<clinit>(Component.java:568)
Could not find the main class: Installer. Program will exit.What is wrong here? And I know it is not a typo problem -- I have checked and re-checked -- as well as re-downloading the file in case there was some sort of file corruption. Help?

---

### Post by jespdj on 2009-05-08
nefffffffffff, try installing Sun Java instead of OpenJDK Java (which you are using now):
```
sudo apt-get install sun-java6-jdk
sudo update-java-alternatives -s java-6-sun
```

---

### Post by nefffffffffff on 2009-05-08
Excellent, it worked.

Thanks a lot.

---

