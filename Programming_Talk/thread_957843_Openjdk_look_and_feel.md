---
title: "Openjdk look and feel"
date: 2008-10-24
forum: Programming Talk
---

### Post by aaargh486 on 2008-10-24
For my classes 'Logic for computer scientists' I take, we have to use a program called LogicPalet. My professor was kind enough to package a version for Linux (there is really pro-Linux atmosphere here) but I have a little problem.

I use the OpenJDK JRE because I understand it's fully open source. But the program looks weird in it.

Here's how the program should look, with the Sun Java6 JRE.
[img]http://ubuntuforums.org/attachment.php?attachmentid=89546&stc=1&d=1224886204[/img]


And here is how it looks with the OpenJDK JRE on the same computer with the same settings.

[img]http://ubuntuforums.org/attachment.php?attachmentid=89547&stc=1&d=1224886278[/img]

Is there a solution for this? Or should I use the Sun JRE? I understand it's partly open source now?

And for another question, is it possible to use GTK widgets for Java programs. Because right now, they kinda stand out a lot.

Thanks in advance,
Kasper

---

### Post by Devineman on 2008-10-24
I would imagine it's to do with the way that the JRE implements AWT (or Swing).  If it is that problem, short of rewriting the AWT library yourself there isn't really much you can do about it.  
Personally, if I go over to Java I tend to use the Sun JRE but that's only because I have never looked in to OpenJDK too much.  
As far as GTK/Java go, take a look at Eclipse, I swear they've got plugins for everything now, I'm sure it will be possible.

---

### Post by drubin on 2008-10-25
I would highly HIGHLY recommend switching to sun jdk. especially since this is school/studying related. (See my link for installing it) Then read this [link]("https://help.ubuntu.com/community/JavaInstallation") to convert to it. taking a look at Selecting the default Java version

I have heard nothing but issues with the openjdk. and sun is open sourcing their jdk as on 1.7. so they aren't all mean :)

For something like studing it is important to be using their tools or as close to it as possible the open jdk has some unexpected results and might cause you to miss something/spend unnecessary time working on a section of code.

---

### Post by drubin on 2008-10-25
On your last point 
[http://www.ensode.net/java_swing_mustang_screenshots_gtk.html](http://www.ensode.net/java_swing_mustang_screenshots_gtk.html)
[http://www.javalobby.org/java/forums/t69361.html](http://www.javalobby.org/java/forums/t69361.html) 
[http://www.linuxjournal.com/article/8111](http://www.linuxjournal.com/article/8111)

---

### Post by aaargh486 on 2008-10-25
> **drubin said:**
> I would highly HIGHLY recommend switching to sun jdk. especially since this is school/studying related. (See my link for installing it) Then read this [link]("https://help.ubuntu.com/community/JavaInstallation") to convert to it. taking a look at Selecting the default Java version

I have heard nothing but issues with the openjdk. and sun is open sourcing their jdk as on 1.7. so they aren't all mean :)

For something like studing it is important to be using their tools or as close to it as possible the open jdk has some unexpected results and might cause you to miss something/spend unnecessary time working on a section of code.

I understand, thanks. I have both installed, I just have to enter
sudo update-alternatives --config java

Since Sun is open sourcing their JDK, I guess it's OK. And if it rids me of a horrible layout, that's good too.

---

### Post by drubin on 2008-10-25
> **aaargh486 said:**
> I understand, thanks. I have both installed, I just have to enter
sudo update-alternatives --config java

Since Sun is open sourcing their JDK, I guess it's OK. And if it rids me of a horrible layout, that's good too.

Yes just type that command. 

At the start of this year I was also thinking of converting to openJDK and just not worth the effort.. Since Sun is becoming opensource.

---

### Post by nvteighen on 2008-10-25
Can someone explain me why those differences still exist? Are Sun's Java GUI toolkits still proprietary or is it just that OpenJDK is not advancing quickly enough?

And I fear that when Java gets 100% Free Software/Open Source, OpenJDK will be bound to death (and what about GCJ/GIJ?)

---

### Post by drubin on 2008-10-25
> **nvteighen said:**
> Can someone explain me why those differences still exist? Are Sun's Java GUI toolkits still proprietary or is it just that OpenJDK is not advancing quickly enough?

And I fear that when Java gets 100% Free Software/Open Source, OpenJDK will be bound to death (and what about GCJ/GIJ?)

I think Suns GUI toolkits are /still/ proprietary. 

Is that such a bad thing? I mean to have the main Java Platform being open source would mean that every one can contribute to this branch?

---

### Post by jespdj on 2008-10-25
> **nvteighen said:**
> Can someone explain me why those differences still exist? Are Sun's Java GUI toolkits still proprietary or is it just that OpenJDK is not advancing quickly enough?

And I fear that when Java gets 100% Free Software/Open Source, OpenJDK will be bound to death (and what about GCJ/GIJ?)
[OpenJDK](http://openjdk.java.net/) is Sun's project to make their Java implementation 100% open source. They couldn't make their original Java implementation open source just like that, because they used a number of closed source third party parts that they didn't have the rights to.

There are still some differences between Sun Java 6 and OpenJDK 6. As far as I know, font rendering was one of the proprietary parts in Sun Java 6, so that's why it might look different in OpenJDK 6.

Sun's next Java implementation (Java 7) will be 100% open source, and Java 7 is just one of the projects in the OpenJDK initiative. So it's not the case that "OpenJDK will be bound to death" - Java 7 *is* OpenJDK.

GIJ/GCJ (GNU Java, also known as [GNU Classpath](http://www.gnu.org/software/classpath/) is obsolete.

---

### Post by Vox754 on 2008-10-25
> **jespdj said:**
> 
So it's not the case that "OpenJDK will be bound to death" - **Java 7 *is* OpenJDK**.

GIJ/GCJ (GNU Java, also known as [GNU Classpath](http://www.gnu.org/software/classpath/) is obsolete.

Exactly!

Actually, I was just searching your post history because I recalled you were the only member of this forum who can explain this correctly, without biases.
Some of those posts are now buried in extensive flame wars.

Now, I just checked Launchpad, and apparently they are still shipping GCJ 4.3. Why?
When is this thing going away?

---

### Post by nvteighen on 2008-10-25
> **jespdj said:**
> 
Sun's next Java implementation (Java 7) will be 100% open source, and Java 7 is just one of the projects in the OpenJDK initiative. So it's not the case that "OpenJDK will be bound to death" - Java 7 *is* OpenJDK.

In other words, the old proprietary-based code is bound to death and OpenJDK is the future? Great! :D

> GIJ/GCJ (GNU Java, also known as [GNU Classpath](http://www.gnu.org/software/classpath/) is obsolete.

Sad, but here the GNU guys seem to have failed miserably.

---

### Post by Vox754 on 2008-10-25
> **nvteighen said:**
> Can someone explain me why those differences still exist? Are Sun's Java GUI toolkits still proprietary or **is it just that OpenJDK is not advancing quickly enough?**


Also remember that Ubuntu only carries "stable" packages in the repositories.
They included "OpenJDK" in Hardy 8.04, but improvements since then won't be evident until Intrepid 8.10.
Same thing with other applications like Eclipse; people always complain how the repos carry old versions.

Actually, the first open java was "Icedtea7" in Gutsy 7.10, already based on OpenJDK. It was sort of a hack to get rid of the proprietary stuff.

---

### Post by drubin on 2008-10-25
> **jespdj said:**
> Sun's next Java implementation (Java 7) will be 100% open source, and Java 7 is just one of the projects in the OpenJDK initiative. So it's not the case that "OpenJDK will be bound to death" - Java 7 *is* OpenJDK.

Thanks for clearing this up..

---

### Post by Vox754 on 2008-10-25
> **nvteighen said:**
> In other words, the old proprietary-based code is bound to death and OpenJDK is the future? Great! :D

Well, considering that 95% of the old Sun Java is now OpenJDK, the old code is not going away, it was simply open sourced.
The remaining 5% is going away.

As I see it, it's basically a name change "Sun Java = OpenJDK"
```

sun-java5    sun-java6    sun-java7     ----        ----
   ----      openjdk6     openjdk7     openjdk8    openjdk9 ...

```

> 
Sad, but here the GNU guys seem to have failed miserably.
You could say they actually succeeded in getting a free version available.

Before the GNU Classpath there was no free java implementation, but after them there was, and few years later Sun open sources their implementation, so it actually payed out.

And thinking about it, what stops GNU from incorporating code from OpenJDK? I imagine that now they'll be able to fully support at least Java 4 and 5.

---

### Post by drubin on 2008-10-25
> **nvteighen said:**
> in other words, the old proprietary-based code is bound to death and openjdk is the future? Great! :d

+1

---

### Post by nvteighen on 2008-10-25
> **Vox754 said:**
> Well, considering that 95% of the old Sun Java is now OpenJDK, the old code is not going away, it was simply open sourced.
The remaining 5% is going away.


OK, then it's much better than I thought!

> 
And thinking about it, what stops GNU from incorporating code from OpenJDK? I imagine that now they'll be able to fully support at least Java 4 and 5.

Well, it's a mystery to me... Are you sure they haven't abandoned that project?

---

### Post by jespdj on 2008-10-26
I don't know what the GNU Java project is planning to do, and if they're even going to continue developing their Java implementation. I guess the main reason that the project was started was because there was no free and open source Java implementation. Since Sun is open sourcing their Java implementation, the main reason for GNU Java to exist has fallen away.

Sun's Java implementation is very good - the HotSpot JIT (Just-in-Time) compiler, which converts Java bytecode to native code on the fly to make Java run really fast, is very sophisticated. The garbage collection algorithms in Sun's Java are also very efficient and sophisticated.

GNU Java hasn't reached the performance and compatibility that's necessary to be a serious competitor to Sun Java.

On Ubuntu 8.10, OpenJDK Java will be the default Java implementation, replacing GNU Java: [Java related changes in intrepid](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-July/000460.html)

---

### Post by nvteighen on 2008-10-26
> **jespdj said:**
> 
On Ubuntu 8.10, OpenJDK Java will be the default Java implementation, replacing GNU Java: [Java related changes in intrepid](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-July/000460.html)

That's good news!

---

### Post by endresma on 2008-11-16
This issue seems to be related to this bug report:
[https://bugs.launchpad.net/ubuntu/hardy/+source/openjdk-6/+bug/234314](https://bugs.launchpad.net/ubuntu/hardy/+source/openjdk-6/+bug/234314)

---

### Post by jeffreyldavidson on 2009-02-14
I too was having the problem with the Sun JRE not displaying properly. I use Moneydance financial program which is written in Java and it just displayed out of proportion. After running 

sudo update-alternatives --config java 

and selecting the Sun Java and not the Open JRE the program displays great.

Thanks!

---

### Post by eye208 on 2009-02-14
> **aaargh486 said:**
> Is there a solution for this? Or should I use the Sun JRE? I understand it's partly open source now?
Both the Sun JRE and OpenJDK use the Lucida font family for the default Swing look & feel. Installing sun-java6-fonts should fix the problem. No need to switch back to the Sun JRE.

> And for another question, is it possible to use GTK widgets for Java programs. Because right now, they kinda stand out a lot.
You can activate the native platform look & feel this way:
```
javax.swing.UIManager.setLookAndFeel(
    javax.swing.UIManager.getSystemLookAndFeelClassName()
);
```

---

