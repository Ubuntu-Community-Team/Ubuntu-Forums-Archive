---
title: "Java Swing issues: randomly greyed out input and message dialogs"
date: 2008-04-29
forum: Programming Talk
---

### Post by jonathanmotes on 2008-04-29
Has anyone else had this problem? I've written and tried several Java Swing programs with the same result. The "popups" will still accept input but don't show the buttons or input fields.

I'm running Gutsy still, and I compile with "javac appname.java". I have Java 6 Web Start (the JRE) and Java 6 Console (the JDK) installed.

Is there anything you should do differently when working with Java on Linux? (My instructor at school has only used Java Swing on Windows).

---

### Post by Zugzwang on 2008-04-29
Would you mind posting a screenshot of such a case here? Did you really *use* Sun's java and javac executable? It doesn't suffice to install them. You need to tell Ubuntu to use them. See [here]("http://ubuntuforums.org/showthread.php?t=713622") for details.

Edit: The problem in [this thread]("http://ubuntuforums.org/showthread.php?t=684511&highlight=JOptionPane") looks similar to me (as these popup windows are usually made using JOptionPane). Maybe the solution is also the same?

---

### Post by jonathanmotes on 2008-04-29
I couldn't get Flickr to log me in for some reason, so here's a low res screenshot: [http://ubuntuforums.org/album.php?albumid=87&pictureid=193](http://ubuntuforums.org/album.php?albumid=87&pictureid=193).

I found some posts that say that Swing had some problems with Compiz and Beryl, but those were supposed to be fixed.
[http://ubuntuforums.org/showthread.php?t=362821](http://ubuntuforums.org/showthread.php?t=362821)

Sun says it is fixed:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6438179](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6438179)

However, I can't seem to cause the problem when Compiz is turned off.

I will go ahead and try ```
sudo update-alternatives --config java
```
and see if it fixes the problem.

Thanks for the help!

---

### Post by jonathanmotes on 2008-04-29
Running ```
sudo update-alternatives --config java
```

Gives me this:

```
myusername@dell-desktop:~/Desktop$ sudo update-alternatives --config java
[sudo] password for myusername:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:
```

That is right, isn't it?

---

### Post by txcrackers on 2008-04-29
Yes, the setting for using the Sun JVM is correct. However, the problem appears to be *behind* the dialog: I noticed that you have an exception showing. When an uncaught exception propagates back up to the JVM (especially from the Swing Event thread), your screen draws do not complete because the thread was interrupted. Hence, the "empty" dialog.

---

### Post by jonathanmotes on 2008-04-29
Thanks for the reply!

> I noticed that you have an exception showing. When an uncaught exception propagates back up to the JVM (especially from the Swing Event thread), your screen draws do not complete because the thread was interrupted. Hence, the "empty" dialog.

Yes, that error is because of a previous run where I had a input message box and I just hit enter without entering anything (I don't have any validation in my program). No errors are showing up on the command line when the popups start greying out, strangely enough. In the screenshot, you can see that I had ran the program three times before (it ran correctly the three previous times before graying out).

If it helps, my program just asks for 5 integers in 5 different popups, then displays them as entered, then sorted, and then has separate popups that show the min, max, sum, and average of the entered integers. 

The popup in the program that grays out seems to be completely random (it is a different one each time) as far as I can tell.

I added ```
export AWT_TOOLKIT="MToolkit"
```
to the bottom of my /etc/profile file and rebooted as suggested in the post reporting the [Beryl/Compiz problem]("http://ubuntuforums.org/showthread.php?t=362821").

The problem seems to be fixed. However, I am getting some run-time warnings that I didn't get before. 

```
myusername@dell-desktop:~/Desktop$ javac JavaProg11.java 
myusername@dell-desktop:~/Desktop$ java JavaProg11 
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl uming uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct

```

Do anyone know why those would be happening now?
Thanks!!

---

### Post by kavon89 on 2008-04-29
> **jonathanmotes said:**
> I couldn't get Flickr to log me in for some reason, so here's a low res screenshot: [http://ubuntuforums.org/album.php?albumid=87&pictureid=193](http://ubuntuforums.org/album.php?albumid=87&pictureid=193)

I have the same type of graphical problem with NetBeans 6.0.1, seperate popup windows often show up grey, seeminly oversized and they are empty. This isn't programs I'm working on either, it's the IDE itself.

I'm going to try the fix you posted and see how it goes. :D

---

### Post by jonathanmotes on 2008-04-30
Has anyone else had this problem on Gutsy and found a fix for it....??

Thanks!

---

### Post by gnuman on 2008-06-08
I'm getting gray windows about 65% of the time when I try to use JOptionPane.showMessageDialog. I spent over an hour on google and came up empty.

I'm running Hardy 64 bit and using the official Sun JRE and JDK.  I can try just about any posted java program and get the same result when it tries to use JOptionPane.  ](*,)

Does anyone else have this problem?  I've been using Java on here for command line stuff and my first attempts at GUI interaction is not promising. :confused:

---

### Post by mike_g on 2008-06-08
I'm not sure if its relevant to your situation, but I was getting grey windows recently. I discovered it was because I forgot to call pack() after adding all the components.

---

### Post by gnuman on 2008-06-08
> **mike_g said:**
> I'm not sure if its relevant to your situation, but I was getting grey windows recently. I discovered it was because I forgot to call pack() after adding all the components.

Thanks for that, but unfortunately it didn't work.

I did find a fix, however, after looking all day and finally finding this long thread:

[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775)

To get by: System/Preferences/Appearance/Visual Effects/None.

Turning off all visual effects works.  That not really a fix, but I don't care much for visual effects anyway.  Sure wish there was a real fix for this, though.

---

