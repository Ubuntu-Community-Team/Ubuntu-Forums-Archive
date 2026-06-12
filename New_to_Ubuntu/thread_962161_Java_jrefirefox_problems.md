---
title: "Java jre/firefox problems"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by sadpony on 2008-10-29
I am a complete beginner with Linux, having just installed Ubuntu less than a week ago. So far the only problem that I have found that I can't figure out how to fix is this: 

When I try to view java sites on Firefox I can't seem to get it to work. I have tried to install (and I think I have successfully) Java, but I still get messages saying that Java is not turned on. Any ideas on how to fix this? Am I missing something? 

Thanks in advance!

---

### Post by wolfen69 on 2008-10-29
in your browser, type about:config and see if javascript.enabled is set to true.

---

### Post by sadpony on 2008-10-29
> **wolfen69 said:**
> in your browser, type about:config and see if javascript.enabled is set to true.

I checked that, and it is set to true

---

### Post by Nepherte on 2008-10-29
What architecture are you using? 32bit or 64bit?

Javascript is something different than java. The browser takes care of javascript and a runtime environment takes care of java.

To install java and the browser plugin on 32bit:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

To install java and the browser plugin on 64bit:
```
sudo apt-get install openjdk-6-jre icedtea-gcjwebplugin
```

---

### Post by jespdj on 2008-10-29
Note that there are different implementations of Java available for Ubuntu. There's Sun Java, OpenJDK Java and GNU Java.

The best one to use is Sun Java (if you're using 32-bit Ubuntu). Install it with the instructions that Nepherte already mentioned:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
And then make sure that Sun Java 6 is the Java that's used on your machine:
```
sudo update-alternatives --config java
```
Select Sun Java 6 in the menu that this command presents you with.

---

### Post by sadpony on 2008-10-29
> **Nepherte said:**
> What architecture are you using? 32bit or 64bit?

Javascript is something different than java. The browser takes care of javascript and a runtime environment takes care of java.

To install java and the browser plugin on 32bit:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

To install java and the browser plugin on 64bit:
```
sudo apt-get install openjdk-6-jre icedtea-gcjwebplugin
```

I would assume that I am running 32-bit, but I am not 100% sure. Is there a way a can check that?

---

### Post by Sarmacid on 2008-10-29
```
uname -p
```Outputs the type of processor you're using. Should say something with 86 if it's 32. Sorry about the little amount of info but I can't access linux right now x_x

---

### Post by Nepherte on 2008-10-29
Type
```
uname -m
```
If it says "x86_64", you are running 64bit. If it says something else like i386, i686, i586 or x86 you are running 32bit.

---

### Post by sadpony on 2008-10-29
> **Nepherte said:**
> Type
```
uname -m
```
If it says "x86_64", you are running 64bit. If it says something else like i386, i686, i586 or x86 you are running 32bit.

awesome, I'm using 64bit and had installed the 32bit so I fixed it and it works like a charm. Thanks for the help!

---

