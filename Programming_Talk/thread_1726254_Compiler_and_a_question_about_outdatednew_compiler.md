---
title: "Compiler and a question about outdated/new compilers"
date: 2011-04-10
forum: Programming Talk
---

### Post by Airforcefalco on 2011-04-10
I'm learning how to program and I'm wanting the newest version of gcc and Java. Ubuntu has 4.4 installed and I want 4.5 (i believe those are the most current in the package manager. I'd like to learn how to compile the newest ones myself since i believe 4.6 is out and if anyone could help me with that I'd appreciate it). I know i can use the remove completely option but I believe it removes some documentation that I want to keep and I'm not sure if it removes anything else that is needed.

Also I am programming in Java and I'd like to use Sun's JDK and remove the one installed. If that isnt possible I want to know how I choose which one is the default one when I type "javac helloworld.java" (I tried to open the FAQ but it said the certificate was bad). This goes back to the previous issue of having two programs installed (the GCC) and wanting to use the most current one. If the one I don't want to use is removed, would that affect anything?

Thanks for the help!

---

### Post by Airforcefalco on 2011-04-10
Also I tried the 
```
sudo aptitude install sun-java6-jdk
``` as well as apt-get and it didnt work. Any help is greatly appreciated!

---

### Post by Airforcefalco on 2011-04-10
```
sudo update-java-alternatives --set java-6-sun
```
That didn't work as well.

---

### Post by NovaAesa on 2011-04-11
Regarding GCC, you are correct, version 4.6 is the latest version, while the version in the ubuntu repos is 4.4.5. Have a look here [http://gcc.gnu.org/gcc-4.5/changes.html](http://gcc.gnu.org/gcc-4.5/changes.html) and here [http://gcc.gnu.org/gcc-4.6/changes.html](http://gcc.gnu.org/gcc-4.6/changes.html) for the changes between versions - there's nothing especially fancy. IMO, if you want the latest and greatest packages "just because", Ubuntu probably isn't the distro you want, you might want to try a rolling release such as Arch Linux or Gentoo.


As for Java, what went wrong when you ran those commands? From memory, they should do it. Please post the output of java -version and javac -version

---

### Post by r-senior on 2011-04-11
> **Airforcefalco said:**
> ```
sudo update-java-alternatives --set java-6-sun
```
That didn't work as well.
Did you install Sun Java (from the repositories) before you did that? If you didn't, it has nothing to switch to. Essentially what that update alternatives program does is look for predictably installed options and switch symbolic links around.

If you want bleeding edge Java for development, you are probably better downloading the archives direct from Oracle, unpacking them under your home directory and setting JAVA_HOME and CLASSPATH accordingly.

---

