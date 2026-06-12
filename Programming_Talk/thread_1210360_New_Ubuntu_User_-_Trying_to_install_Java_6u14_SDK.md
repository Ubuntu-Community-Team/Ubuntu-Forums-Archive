---
title: "New Ubuntu User - Trying to install Java 6u14 SDK"
date: 2009-07-11
forum: Programming Talk
---

### Post by cwrighta70 on 2009-07-11
[FONT=Arial]Hello, All.  This is very new to me.  I've been developing on a Windows machine for quite some time and wanted a change.  I'm spending the weekend getting my machine set up for work again, but I'm having difficulty getting things installed properly.

I downloaded the Java 6u14 SDK bin and installed, but then realized that I did everything in the desktop.  Now, I'm trying to figure out how to get Java installed in the usr directory (which, I believe, is where it goes).  Unfortunately, there is no "java" directory in "usr", and using[/FONT] [FONT=Courier New]"mkdir java"[/FONT] [FONT=Arial]from the [/FONT]command line gives me [FONT=Courier New]"permission denied"[/FONT].

Any step-by-step help would be greatly appreciated.

Thanks!
Chris

---

### Post by prvteprts on 2009-07-11
Use sudo mkdir. Modifying anything outside of your home folder usually requires sudo. I think the recommended location would be usr/local then just copy the entire folder there, so usr/local/jdk1.6.0_14. That's exactly what I did. If you want to install Netbeans manually (not from add/remove or apt-get), it goes into the same /usr/local folder. Actually, the binary Netbeans installer does that for you automatically.

---

### Post by prvteprts on 2009-07-11
Oh yeah, duh. If you are going to copy the folder and not create, use cp -r.

```
sudo cp -r /home/username/Desktop/jdk1.6.0_14/ /usr/local/jdk1.6.0_14
```

Where username is your username or login name.

---

### Post by cwrighta70 on 2009-07-11
Thanks, prvteprts.  I was able to get the jdk into the correct directory.  Now on to the next question: When typing java -version in the command line, I get "command cannot be found".

Where and how do I set the path for java?

---

### Post by txcrackers on 2009-07-11
I would strongly suggest just installing Java from the repositories. That will take care of setting up paths, etc. and is quite a bit less painful.

---

### Post by froggyswamp on 2009-07-11
I'd suggest copying/extracting the JDK into your home dir, say into /home/yournick/apps/jdk6u14.
Next.
Now you need the "java" & "javac" executables from your new JDK to run by default, thus:
-create a dir "bin" in your home dir (thus "/home/yournick/bin" if it doesn't exist)
-create and put there 2 (soft) links called "java" & "javac" pointing correspondingly to
"path-to-new-jdk/bin/java" & "path-to-new-jdk/bin/javac".
(To create a soft link right-click the corresponding files from Nautilus, choose "Make link", put those links into the "/home/yournick/bin" dir and rename them to "java" & "javac" accordingly).

Changes will take effect after restart (or maybe after logout & login back).
Sounds little crazy but it works.

---

### Post by prvteprts on 2009-07-12
> **txcrackers said:**
> I would strongly suggest just installing Java from the repositories. That will take care of setting up paths, etc. and is quite a bit less painful.

You could do this, but I'm not sure if it's the most updated version. You must also be careful to install the correct "kind" of java you want, as there are a lot of them in the repositories.

For setting up the path, I found this: [http://ubuntuforums.org/archive/index.php/t-8523.html](http://ubuntuforums.org/archive/index.php/t-8523.html)

But froggyswamp's method is interesting. I did something like that before in Windows. You could try that out.

---

### Post by slavik on 2009-07-12
Up to date jaunty install with sun java 6.0 jdk install:

```

slavik@slavik-desktop:~$ uname -a
Linux slavik-desktop 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux
slavik@slavik-desktop:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
slavik@slavik-desktop:~$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)

```

use update-java-alternatives to switch default java version.

---

### Post by cwrighta70 on 2009-07-12
Okay, so I reinstalled Java into the /usr/local folder (instead of opening the .bin and installing in Desktop then moving to local).  Then I edited the bash.bashrc file to contain:

PATH=$PATH:/usr/local/jdk1.6.0_14/bin
export PATH

Unfortunately, I still receive the "bash: java: command not found" error when typing java -version in the command line.

What else could be wrong?

Thanks,
Chris

---

### Post by prvteprts on 2009-07-13
I think you have to restart for the change to take effect?

---

### Post by slavik on 2009-07-13
please see this: [http://ubuntuforums.org/showthread.php?t=1211628](http://ubuntuforums.org/showthread.php?t=1211628)

---

### Post by cwrighta70 on 2009-07-14
Haha, thanks slavik.

Yes, problem is solved now.  Thanks to all who helped!

---

