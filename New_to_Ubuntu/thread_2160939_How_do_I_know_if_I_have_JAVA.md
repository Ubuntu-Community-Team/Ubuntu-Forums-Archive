---
title: "How do I know if I have JAVA?"
date: 2013-07-08
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-07-08
Hello All,
How do I know if I have Java installed?  If not, how do I install it?
Thanks

---

### Post by BBQdave on 2013-07-08
A good number of Linux distros utilize [OpenJDK]("http://openjdk.java.net/")

To my understanding, that is the JAVA environment in Ubuntu too.

---

### Post by 1clue on 2013-07-08
Easiest way, open a terminal and type 'java -version'.  That tells you the version and the vendor.  There are several.

If you want to check your browser to see if you have a correctly functioning plugin, go to [http://www.java.com/](http://www.java.com/) and click the 'do I have Java?' link.

---

### Post by Jaraxle on 2013-07-08
The command line is your best option but you can also open Synaptic Package Manager (may need to install it first), search for Java at the top, and see if anything is selected. You can also install/uninstall this way.

---

### Post by claracc on 2013-07-09
As it has been pointed, command ```
java -version
``` will inform you about what Java (if any), you have. You will be presented with an answer of this kind:
```
java version "1.7.0_25"
Java(TM) SE Runtime Environment (build 1.7.0_25-b15)
Java HotSpot(TM) Server VM (build 23.25-b01, mixed mode)

```

This link: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) gives you all the information about what and how java install in your ubuntu system.

I recommend oracle java through the webup8 ppa.

---

### Post by siddharth007 on 2013-07-09
To install openjdk package for Ubuntu,run this command from the terminal
```
apt-get install openjdk-7-jdk
```

---

### Post by newb85 on 2013-07-09
I'm surprised no one has asked you yet, are you looking for the Java Development Kit (needed for compiling java source code into programs), or just the Java Runtime Environment (needed to run java programs)?

To install the currently recommended and supported JDK:
```
sudo apt-get install default-jdk
```

To install the currently recommended and supported JRE:
```
sudo apt-get install default-jre
```

To check what version you have installed:
```
java -version
```

If you don't have java installed yet, that last command will return something like this:
```
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * gcj-4.7-jre-headless
 * openjdk-7-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
```

---

### Post by slickymaster on 2013-07-09
Or, you can just install Java 7 in Ubuntu via PPA. It will not only provides you provides Java JDK 7 (which includes Java JDK, JRE and the Java browser plugin) but also comes with the advantage of every time you run an update on your *buntu box it will automatically update your Java, if there's one available.
Just run the following at a terminal window:```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by GUZZLR on 2013-07-09
> **newb85 said:**
> I'm surprised no one has asked you yet, are you looking for the Java Development Kit (needed for compiling java source code into programs), or just the Java Runtime Environment (needed to run java programs)?

To install the currently recommended and supported JDK:
```
sudo apt-get install default-jdk
```

To install the currently recommended and supported JRE:
```
sudo apt-get install default-jre
```

To check what version you have installed:
```
java -version
```

If you don't have java installed yet, that last command will return something like this:
```
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * gcj-4.7-jre-headless
 * openjdk-7-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
```

Just the runtime...thank you
I think my question may have been answered. I'm trying to find a way which Java keeps itself updated with the latest version. I'll look into these suggestions after work today. 
Thanks for the help!

---

### Post by craig10x on 2013-07-09
> **GUZZLR said:**
> [QUOTE=newb85;12723904]I'm surprised no one has asked you yet, are you looking for the Java Development Kit (needed for compiling java source code into programs), or just the Java Runtime Environment (needed to run java programs)?

To install the currently recommended and supported JDK:
```
sudo apt-get install default-jdk
```

To install the currently recommended and supported JRE:
```
sudo apt-get install default-jre
```

To check what version you have installed:
```
java -version
```

If you don't have java installed yet, that last command will return something like this:
```
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * gcj-4.7-jre-headless
 * openjdk-7-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
```
Just the runtime...thank you
I think my question may have been answered. I'm trying to find a way which Java keeps itself updated with the latest version. I'll look into these suggestions after work today. 
Thanks for the help![/QUOTE]

In that case, slickymaster gave you the best suggestion of all...entering those three commands into the terminal will not only get you the licensed version of Oracle Java 7 (not the open source version which i find doesn't always work for everything like the way the licensed version does) but also adds a ppa to your software sources, and as each new version of the Java comes out you will get it through the ubuntu updater automatically!....You will have to say "ok" to the license agreement which is not biggie...it's a deb package created by this site to make it easy to install the licensed java....i use it myself and it works great...

You paste in one command at a time and hit enter...let the terminal do it's thing then go on to the next...and say ok to the agreement when it comes up on the screen...

And i have used it on a number of ubuntu installs over the past year...very reliable...I use a program that seems to only work right with the licensed version and i use it every time i install ubuntu...

Don't worry...they are a well trusted website in "linux land" :D

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by 1clue on 2013-07-09
Better yet, paste the line into a text file first, then read the line, and make sure it's doing what you expect.

It's not very difficult to embed malicious code into a forum page that does something very different from what is being shown.  Copying and pasting commands straight to the terminal is a bad habit to get into.

---

### Post by craig10x on 2013-07-09
> **1clue said:**
> Better yet, paste the line into a text file first, then read the line, and make sure it's doing what you expect.

It's not very difficult to embed malicious code into a forum page that does something very different from what is being shown.  Copying and pasting commands straight to the terminal is a bad habit to get into.

I know you are a bit obsessed with security but that linux website has been around for ages and is well known to the ubuntu forums as a very safe and reliable website that provides helpful ppas for things like this...i have been using that deb file package for 12.04, 12.10 and 13.04 and not only is it safe but installs the java beautifully...it's simple a pre-compiled package they made from oracle to save one the hassle of having to have to compile it yourself, since Oracle does not provide a deb file on their website for linux...

---

### Post by oldos2er on 2013-07-09
> **GUZZLR said:**
> Hello All,
How do I know if I have Java installed?  If not, how do I install it?
Thanks

No version of Java, not the OpenJDK or Oracle's, is installed by default, so you'd have to knowingly install one or the other.

---

### Post by 1clue on 2013-07-09
> **craig10x said:**
> I know you are a bit obsessed with security but that linux website has been around for ages and is well known to the ubuntu forums as a very safe and reliable website that provides helpful ppas for things like this...i have been using that deb file package for 12.04, 12.10 and 13.04 and not only is it safe but installs the java beautifully...it's simple a pre-compiled package they made from oracle to save one the hassle of having to have to compile it yourself, since Oracle does not provide a deb file on their website for linux...

Craig,

Yes I'm a bit obsessed about security, but is it better to explain which sites are safe, and then assert falsely that that site could never be hacked and have malicious content, or is it better to explain good practices in the first place so you can understand what's going on, and then be careful wherever you get the tip?

Maybe I've just been owned a few more times than you have.  I like to avoid doing lazy stuff that gets me in trouble.

---

### Post by craig10x on 2013-07-09
Sorry guy but i still think you are overly cautious...while i would not run windows and surf even one single web page before installing an anti virus scanner, i have run linux since 2008, various distros and installs and have NEVER got one single malware, virus, trojan, etc...with no scanners installed...so i don't have the feeling i am going to get zapped at any moment... ;)

I suspect if someone took a survey on this forum, you'd be hard pressed to find many who have ever had any problems like that...other then yourself, of course... :D

---

### Post by newb85 on 2013-07-10
> **1clue said:**
> It's not very difficult to embed malicious code into a forum page that does something very different from what is being shown.

Wait a minute.  Are you saying it's possible, on *this* forum, to post terminal commands that, when copied and pasted into the terminal, magically become something else?  I can't categorically say I know you're wrong, but I seriously doubt you're right.

---

### Post by slickymaster on 2013-07-10
> **newb85 said:**
> Wait a minute.  Are you saying it's possible, on *this* forum, to post terminal commands that, when copied and pasted into the terminal, magically become something else?  I can't categorically say I know you're wrong, but I seriously doubt you're right.

+1
My thoughts exactly.

---

### Post by 1clue on 2013-07-10
@newb85, yes that's exactly what I'm saying.  The moderators would fix the problem as soon as they knew about it, but after all it's just a forum, so any trick somebody finds can do it.  But I'm guessing the only way they'd know is if somebody tried it, got hacked and then complained about that post to the moderators.

@craig10x, If you never installed a scanner, you would never know you were hacked in many cases, especially if you never look at a log file.

Let me take a guess:  
[LIST=1]
[*]You didn't read [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) (which was generated from a thread on this forum about ways some very experienced Ubuntu users were hacked)
[*]You didn't read [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security) either.
[*]You DID read some random guys posting on a forum, asserting that it's not possible for Linux to be hacked as long as you keep up with updates.
[*]You feel that some random guy is much more reliable than CERT advisories, official Ubuntu members, and pretty much any other expert that might make a post.
[/LIST]

If you "never had a problem" meaning your computer didn't become unusable, then that means a 15-year-old wasn't the one who hacked you.  The real black hats want you to remain clueless, they want access to your computer and they will never do anything to let you know they're there.

There are several threads on this forum where a whole lot of people talk about the ways they were hacked on Linux in general, and on Ubuntu specifically.

You might be right that a whole lot of people would agree with you about not being hacked, but if you have your head in the sand you can't see the bad guys can you?

Come on dude, wake up!

---

### Post by QIII on 2013-07-10
Hello!

Thank you all for your input.

Suitable answers were given for the original question.  This has devolved into a discussion far removed from that.

Thread closed.

---

