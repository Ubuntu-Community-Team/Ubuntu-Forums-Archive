---
title: "Java error."
date: 2007-02-24
forum: Programming Talk
---

### Post by Darkness3477 on 2007-02-24
Hi, I just upgraded my Laptop with Ubuntu 6.06 (Not sure if I'm going to get 6.10) and have spent the last little while getting all my stuff together. I've got the build essentials and everything else. I have also downloaded and install Java JDK 6 with JRE, I've tested it out and it works in my browser (Loaded up a Java based game). I just tried to test it with a simple Hello World app that can be found on Sun Microsystem's tutorial list. And, well, it compiled nicely. I just tried to run it and I got this error.

```
maver@maver-laptop:~/java$ java HelloWorldApp
Exception in thread "main" java.lang.ClassFormatError: HelloWorldApp (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.7)
   at java.lang.ClassLoader.defineClass(libgcj.so.7)
   at java.security.SecureClassLoader.defineClass(libgcj.so.7)
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)

```

Well, now I'm a complete newb at Java and haven't used Ubuntu in awhile, so I'm not sure how to fix it. I've tried doing what it says here [http://java.sun.com/docs/books/tutorial/getStarted/problems/index.html](http://java.sun.com/docs/books/tutorial/getStarted/problems/index.html) but I'm still to see the 'Hello world! pop out at me. 

Now, perhaps I need to set my class path, or perhaps I didn't set up my JDK properly. But I would of thought that if that was the case it wouldn't of compiled into the .class file. 

Also, I'm just going to start learning Java, and I need a good Development environment. Just something with nice Syntex highlighting, intellisense (IF they have that on any....) and a debugger and a compiler that I can use with just a single button click. I know it's not hard to compile something from the terminal, but it's more effort than I could really be assed giving. Also, I'm used to using the Microsoft Visual Express range of products. Is there anything along those lines I can download? If you know of anything that seems to be close to what I want, please tell me.

---

### Post by hod139 on 2007-02-24
I'm not sure how you installed java.  Try running
```

update-java-alternatives -l

```

And if you see the version of java you installed select it by running (this is for selecting java 6 which I installed through the repos.  I'm not sure what name/version you downloaded.)
```

sudo update-java-alternatives -s java-6-sun

```

---

### Post by Darkness3477 on 2007-02-24
Hi, thanks for your very speedy responce. The method I used for installing the JRE and JDK can be found [here]("http://ubuntuforums.org/showthread.php?t=332674&highlight=jdk").

I tried running those two commands in the terminal and this is what I got. 
```

*@*-laptop:~$ update-java-alternatives -l
java-gcj 1041 /usr/lib/jvm/java-gcj
```

```
*@*-laptop:~$ sudo update-java-alternatives -s java-6-sun
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun

```

So I'm really at a lose as to why it won't work. 

P.S. I tried running it again, the same error popped up.

EDIT: EDITED first post.. Made a mistake in the spelling, but I still get an error coming up. Although it is a slightly different one... Whoops. I really should watch my typing.

---

### Post by hod139 on 2007-02-24
The reason the second command didn't work is because the first command didn't list 
java-6-sun.  It only lists java-gcj, which is why you are having trouble.

Are you sure you followed all of phossal's guide, in particular step 4 where you add java to the list of alternatives.  IF it still doesn't work, you should post your problems in that thread.

---

### Post by Darkness3477 on 2007-02-24
Oh dear, thank you so very much. I guess using Windows for the last six months has made me lazy. What I forgot to do was to switch the default Java over by using  sudo update-alternatives --config java. 

Well, thanks for helping me out. Perhaps I'll be able to firgure this sort of things out when I get used to using Ubuntu again.

Also, if you happen to look back here, could you suggest a nice IDE for me?

---

### Post by hod139 on 2007-02-24
For java, there is eclipse or netbeans.

---

### Post by phossal on 2007-02-24
> **hod139 said:**
> Are you sure you followed all of phossal's guide, in particular step 4 where you add java to the list of alternatives.  IF it still doesn't work, you should post your problems in that thread.

Good call, Hod. ;)

---

### Post by atomsfat on 2007-09-03
Thanks it works for me.

---

### Post by pmn.blazer on 2007-11-18
thank you very much 
It is solve my problem now
:P

---

### Post by geirha on 2007-11-18
It will use the java command that comes first in the path (which is sort of what update-java-alternatives fixes). If you specify the path to your own installation of java 6, it should work fine. 

I.e. if your java 6 jdk is installed in /opt/java6/, then ```
/opt/java6/bin/java HelloWorldApp
```

Same goes for javac and the other commands.

---

