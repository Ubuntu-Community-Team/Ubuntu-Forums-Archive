---
title: "Making Java GUI's look good"
date: 2008-07-08
forum: Programming Talk
---

### Post by dhimes on 2008-07-08
I was asked to start a new thread on this question, which I posed elsewhere:  Why does my Java GUI stuff look so poor on Linux?  I am using native Look and Feel, which works fine in Win XP and Vista, but in Java it seems to not paint properly.

I am hoping that someone who has had some experience with this may recognize this as a familiar problem.  I don't mean for this to be a discussion of how to subclass JButton, or what-not.  I just mean that if I take a .jar file that looks good elsewhere, what might be happening (what might I have forgotten?) that would render that Linux version poorly?  

For example, when I install (apt-get) Netbeans, it also installed Java.  Sun's Java?  How can I be sure?  If not, that may explain it.  

Or perhaps the problem lies elsewhere.  (I'm fairly new to Linux, and very new to Ubuntu....)

Anyway, I'd love to hear (read) ideas on this.  Thanks!

---

### Post by HotCupOfJava on 2008-07-08
I'm not sure exactly what you're seeing, but different versions of Java WILL look different. I use Java on all of my machines. I have an old machine that I installed Xubuntu on, and I installed GNU's java compiler. It worked fine, but did look kind of cheap. I later put a new hard drive in and reinstalled Xubuntu. This time I installed Sun's java. Still doesn't have the look of a Windows GUI, but it DOES look different from the GNU version. I have Netbeans recently installed on this (Ubuntu) machine, but I haven't played with it yet so i don't know what this implementation looks like. I am familiar with Netbeans from my Windows use, but I use the command line and VIM editor for Java programming on my old machine. Hold on....

OK it DOESN'T look like the Netbeans install grabs the Sun java packages - it is a hodgepodge of stuff, some of which is from GNU. That could explain it. You can check yourself by opening Synaptic Package Manager, searching for "java", then looking to see which packages are installed.

---

### Post by bruce89 on 2008-07-08
Java's "GTK+" theming is crap. It'd be better to just use good old Metal.

---

### Post by dhimes on 2008-07-08
Thank you, HotCupOfJava.  The Synaptic Package Manager says that the sun-java6-jdk is not installed.  Thus, I'm probably using OpenJava (or whatever that was called).

---

### Post by HotCupOfJava on 2008-07-08
Yeah - I believe the "Metal" theme is the IcedTea default......

---

### Post by bruce89 on 2008-07-08
> **dhimes said:**
> Thank you, HotCupOfJava.  The Synaptic Package Manager says that the sun-java6-jdk is not installed.  Thus, I'm probably using OpenJava (or whatever that was called).

No, that's the old non-free Java 1.6. *openjdk-6-** is the OpenJDK one.

> **HotCupOfJava said:**
> Yeah - I believe the "Metal" theme is the IcedTea default......

It's Java's native LaF.

---

### Post by dhimes on 2008-07-08
So, is openjdk-6-jre Sun's version?  I thought they just open-sourced what they had.

---

### Post by bruce89 on 2008-07-08
> **dhimes said:**
> So, is openjdk-6-jre Sun's version?  I thought they just open-sourced what they had.

Suprisingly, no. I think it's a forked version of Sun's OpenJDK with the non-free bits replaced.

OpenJDK when released had about 95% source available, meaning the other 5 had to be replaced.

---

### Post by dhimes on 2008-07-08
OK--thanks for the info.  My best move is to try Sun's version, and see if it renders better.

---

### Post by HotCupOfJava on 2008-07-08
Yeah - I guess what I should have said was "Metal is the original, and thats what IcedTea uses"......But hey - I've never paid close attention to the GUI themes - I'm just glad the code works.

---

### Post by tinny on 2008-07-08
I've been happy with the Sun JRE version.

The following command will tell you for sure what JRE you are using.

```

java -version

```

You may have multiple JRE's on your machine, if this is the case then synaptic package manager may tell you that you have the Sun JRE installed but you will not actually be using it when you invoke the "java" command. The above java version command will tell you what JRE you are using.

Also, there are three things you can do to get Java GUI's looking better without too much work.

1. Using the "native look and feel".
2. Create your own base JPanel class and enable antialiasing.

```

public class JBasePanel extends JPanel {
    @Override
    public void paint(Graphics g){
        Graphics2D g2d = (Graphics2D) g;
        g2d.setRenderingHint(RenderingHints.KEY_TEXT_ANTIALIASING, 
                RenderingHints.VALUE_TEXT_ANTIALIAS_ON);
    }
}

```

All panels you create should extend this.

3. Manually set your fonts to something sensible like arial.

There are a lot of other things you can do, the above tips are just the easy ones.

---

### Post by dhimes on 2008-07-08
Yeah, thanks Tinny.  I'm using native L&F, and setting the antialiasing, etc.  The most obvious "ick" I have is I override JButton to paint my own border and generally give it my own look.  The border doesn't paint nicely.  

I read here (and confirmed on the fedora 9 release notes) that the openjdk (which I am using) is a blend of Sun and IcedTea.  I suspect that the "blending" is causing me trouble.  I'll check it out when I get the chance, and come back here if I figure something else out.  Thanks again!

---

### Post by tinny on 2008-07-08
> 
Yeah, thanks Tinny. I'm using native L&F, and setting the antialiasing, etc. The most obvious "ick" I have is I override JButton to paint my own border and generally give it my own look. The border doesn't paint nicely.


Have a look at the [Substance]("https://substance.dev.java.net/see.html") l&f library, it has some very nice buttons.

You can see these in the [Demo application by using web start.]("https://substance.dev.java.net/webstart/test.jnlp")

---

### Post by HotCupOfJava on 2008-07-08
> **tinny said:**
> 

1. Using the "native look and feel".


Good call - best way to change the "platform" appearance. You can actually alter the look-and-feel from the native to some other style in the UIManager  (packaged in javax.swing). You can load the installed versions into an array using UIManager.getInstalledLookAndFeels() (the array should be of type UIManager.LookAndFeelInfo) You can then use UIManager.setLookAndFeel(<array reference>[value].getClassName()) to test out the look-and-feels until you find one you like! There should be one that looks very much like Windows GUIs.

---

### Post by Phristen on 2008-07-11
> 1. Using the "native look and feel".Yeah, unless it happens to be GTK+ :) If you don't believe me, create a JComboBox and see what happens. I had to go back to metal in some of my apps because of that.


Though it seems like Sun is about to release a new default look and feel called Nimbus. There is a screenshot at this page:
[http://java.sun.com/developer/technicalArticles/javase/java6u10/](http://java.sun.com/developer/technicalArticles/javase/java6u10/)

---

### Post by tinny on 2008-07-11
> **Phristen said:**
> Yeah, unless it happens to be GTK+ :) If you don't believe me, create a JComboBox and see what happens. I had to go back to metal in some of my apps because of that.


Though it seems like Sun is about to release a new default look and feel called Nimbus. There is a screenshot at this page:
[http://java.sun.com/developer/technicalArticles/javase/java6u10/](http://java.sun.com/developer/technicalArticles/javase/java6u10/)

Sorry its not default. :(

> 
For compatibility reasons, Metal is still the default Swing look and feel, but updating applications to use Nimbus couldn't be simpler. It only takes a single line of code:


Maybe you meant that it is one of the default "set" of look and feels?

[Here]("http://javadesktop.org/swinglabs/demos/nimbus/nimbus.jnlp") is a web start application that demos this look and feel. Looks like they have borrowed some ideas from apple.

---

### Post by Phristen on 2008-07-11
> Maybe you meant that it is one of the default "set" of look and feels?Evidently :)

---

### Post by jespdj on 2008-07-11
> **dhimes said:**
> So, is openjdk-6-jre Sun's version?  I thought they just open-sourced what they had.
> **bruce89 said:**
> Suprisingly, no. I think it's a forked version of Sun's OpenJDK with the non-free bits replaced.

OpenJDK when released had about 95% source available, meaning the other 5 had to be replaced.
[OpenJDK](http://openjdk.java.net/) is Sun's project to make a 100% open source Java. It is exactly the same as Sun Java, but with the last proprietary parts (partly) replaced by open source parts. It's not 100% complete yet, but works well for almost everything.

---

