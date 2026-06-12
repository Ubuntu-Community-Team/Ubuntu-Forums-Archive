---
title: "Unable to launch JDK"
date: 2008-01-09
forum: Programming Talk
---

### Post by 3th0s on 2008-01-09
I was just blowing it. >.<

---

### Post by 3th0s on 2008-01-10
^^ 
sort of...
So i'm getting a lot of errors, i'm running jGRASP right now, because its what my class requires. When i try to run debug, it says that i am not even running JDK, but JRE instead, because i need to 'change my path'. 

Any ideas how to switch off of JRE onto JDK?

---

### Post by jespdj on 2008-01-10
```
sudo apt-get install sun-java6-jdk
```
I don't know what "jGRASP" is.

---

### Post by 3th0s on 2008-01-10
I think jGRASP is just another program that allows the development and compilation of code for any language. 
I couldn't figure out how to launch JDK, but I could get jGRASP going, but like I said, its running JRE instead of JDK, so im kind of lost.
Is there a way to launch JDK from the terminal?

---

### Post by TheOrangePeanut on 2008-01-11
This is only a half-assed answer, but it works.  I went through this same problem last semester and never found a GOOD way to get it to work, but I did find a way to get it to work well enough.  Also, this assumes you've installed the JDK through Synaptic.

Basically, what you need to do is set the PATH environment variable to look for java, javac, and jdb in the JDK instead of in /usr/bin, which contain symbolic links to those files.  First, you need to find where the JDK is installed.  Since I'm not very Linux savvy, I do it like this.  In the terminal, cd to /usr/bin.  Then, type file javac and it will tell you what it symbolically links to.  cd to that folder, and then do it again until it stops spitting symbolic links at you.  I just did that and apparently my jdk is installed at /usr/lib/jvm/java-6-sun/bin 

Now, what you need to do is add that directory to your PATH variable.  You do this by editing your ~/.bashrc file.  At the bottom of the file, you need to add the line export PATH=/usr/lib/jvm/java-6-sun/bin:$PATH.  Restart your computer and then open bash again.  Type echo $PATH.  It should look something like 
/usr/lib/jvm/java-6-sun/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

Now, you have to launch jGrasp from the terminal.  I don't know why, but you can't just launch it from the gui and it still be connected to the JDK (this is why I say this solution is only half-assed).  To do that, you need to launch from the jgrasp/bin folder.  I installed jGrasp to my opt folder, so when I launched it I had to launch it like this from the terminal:

/opt/jgrasp/bin/jgrasp

(jgrasp is a jar file if I remember correctly).  Now, it will launch and it is connected to the JDK.  You can close the terminal once it has launched.

I know my instructions probably aren't that good, but that's how I got it to work.  Hope it works for you.

edit:  Actually, I opened /usr/lib/jvm in Nautilus, and it turns out java-6-sun is a link to the real JDK (located in the same folder).  The real JDK on my machine is actually/usr/lib/jvm/java-6-sun-1.6.0.03 so if java-6-sun doesn't work you might want to look in Nautilus and see what it is linking to and export THAT in ~/.bashrc.  So, what I'm saying is, put this in ~/.bashrc and THEN launch jgrasp from the terminal

export PATH=/usr/lib/jvm/java-6-sun-1.6.0.03:$PATH

---

