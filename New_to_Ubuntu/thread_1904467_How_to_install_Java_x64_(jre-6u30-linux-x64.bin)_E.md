---
title: "How to install Java x64 (jre-6u30-linux-x64.bin) EASY!"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by FlameHead269 on 2012-01-04
Hello users of Ubuntu 11.10!   :p

When I first started using Linux (Ubuntu).. getting Java to work on my computer was completely horrible and always failed! The java tutorial on Java.com is a little misleading.. I finally got it to work sooo today in this tutorial we will be installing java and getting the (.so) files into the plugins folder of the firefox browser, so you can accomplish adding java to your computer so you can play java games on your firefox browser!!

LETS START! (*)= Tutorial (#)= Comment

(*) Download the x64 Bit Java LINK --->[http://javadl.sun.com/webapps/download/AutoDL?BundleId=58119](http://javadl.sun.com/webapps/download/AutoDL?BundleId=58119)
(*)Drag the (.bin) file from your downloads file to your Desktop!
(*)Open up your terminal
(#)You're gonna need root permissions! I realize this is hard for new users to figure out so I'll show you how! 
(#)[Look at spoiler]
(*)```
 $ sudo adduser (your name)
 $ sudo -i 
 $ (your login pass)
 
```(#)Now that your the root I advise that you use caution.. don't worry just follow this tutorial you'll be fine!
(#) Back to the tutorial!
(#)[Look in spoiler]
(*)```
$ mkdir /usr/java
$ cd /usr/java
$ mv /home/(username)/Desktop/jre-6u30-linux-x64.bin /usr/java

```(#)Now since you got your file to your location! simply make the file EXECUTABLE!
```
$ chmod a+x jre-6u30-linux-x64.bin
(#)Now we got it to be executable! lets install it!
$ ./jre-6u30-linux-x64.bin

```(#)Now that we have it installed.. we need to install it to the firefox browser.
```
$ cd /usr/lib/mozilla/plugins
$ ln -s /usr/java/jre1.6.0_30/lib/amd64/libnpjp2.so
```(#)GREAT! Now that the plugin is inside your plugins, we're finished! You now have Java installed on your browser! ;D It's been an honor helping you!

Please comment if this was helpful! Please! Thanks guys, remember to ask for more tutorials I will make a thread!

---

### Post by QIII on 2012-01-04
While I appreciate your willingness to help, I must point out a few things that immediately catch my eye.

There should be no need for the person who installed Ubuntu to be added to sudoers.

Your link is not where you want to go for the download.   It appears to be legit, but there is no way for anyone to know since it simply downloads a .bin.

Your instructions do not include updating Java alternatives.

Your last command to be executed in the terminal will throw an exception.

Please use the tutorial found here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

There are instructions for both 32 bit and 64 bit users.

---

### Post by FlameHead269 on 2012-01-04
Ok thanks for pointing that out.. excuse my mistakes..

---

### Post by Miljet on 2012-01-04
@QIII
Can you explain to me why the link that you reference insists on creating a directory in the user's home directory for the java plugin instead of placing it in /usr/lib/mozilla/plugins with the rest of Firefox plugins? I have never tried it there, but it just seems to me that java would only be available to the user who installed it.

---

### Post by QIII on 2012-01-04
The JRE works for anyone.  The plugin works by user.

The instructions describe how to make it available to other users.

---

### Post by QIII on 2012-01-04
No need for apologies, FlameHead.  We all learn here.  Me most of all!

I spend far more time here reading through other people's solutions to problems I have than I do offering advice of my own.

---

### Post by Miljet on 2012-01-04
I understand that the JRE is available to all users. And I understand that you can make links in each user's home. But my question is, why? If you put one link in /usr/lib/mozilla/plugins, it is already available to all users.

---

### Post by sammiev on 2012-01-04
I seen this post much the same on another site which I tested and worked for what I was doing. Wish he would of just copied the post here with the instructions or added a link instead of trying to take the credit for someones work and paste incorrectly. Then again, my biggest mistake was they gave me a computer. :)

---

### Post by QIII on 2012-01-04
I can't provide you the why and wherefore, Miljet.  I didn't create the tutorial.  I recommend that tutorial because I have great confidence that it actually works and that it is as simple as copying and pasting.  It works and it's not messy.  The maintainer gives some clear comments about what is happening.

I suspect that the answer to your specific question is that the instructions for "uninstallation" in preparation for an update would be less difficult.  As you see from the instructions, the process of updating is little more than deleting some files and running the same instructions over again with a new Java update.

There is a tutorial for Fedora that is very similar -- and which I recommend to Fedora users

[http://www.if-not-true-then-false.com/2010/install-sun-oracle-java-jdk-jre-6-on-fedora-centos-red-hat-rhel/](http://www.if-not-true-then-false.com/2010/install-sun-oracle-java-jdk-jre-6-on-fedora-centos-red-hat-rhel/)

and it does put the plugin in a central location.

But I don't maintain that tutorial either.

---

### Post by mastablasta on 2012-01-05
there used to be a .deb file for a bit older version of Java. what happened to those?

---

### Post by QIII on 2012-01-05
As I understand it, Oracle decided to withdraw licenses from those who had them in their repos.  Alas.  Just before Oracle's takeover, it seemed that Sun was starting to make the most current update available to the Ubuntu MOTUs as soon as they were available.

---

### Post by sbqsam on 2012-01-06
> **QIII said:**
> ...

Your instructions do not include updating Java alternatives.

Please use the tutorial found here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

.

I followed those instructions. Now when I execute the command:

```
update-java-alternatives -l

```I do not see my newly installed java.  Why is that?  When I say:

```
java -version
```I can see it is executing my new Java.

-Sam

---

### Post by zika on 2012-01-06
Not much changed since February 2009... ;)
[http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)
@sbqsam Just register Your Java using update-alternatives...
These days I prefer to use packages from [http://jdk7.java.net/download.html](http://jdk7.java.net/download.html) ...

---

### Post by QIII on 2012-01-06
What do you mean when you say you can't see your new Java?

What are the results of  java -version?

---

### Post by zika on 2012-01-06
> **QIII said:**
> What do you mean when you say you can't see your new Java?

What are the results of  java -version?He does not see new Java in results of &#8222;update-java-alternatives -l&#8220; but can see new Java working using &#8222;java -version&#8220;. Java is working but is not registered as an alternative...
Sorry for my little excursion out of Ubuntu+1 Forum... ;)

---

### Post by sbqsam on 2012-01-06
Yes, Zika is correct.  What is the relationship between the commands update-alternatives and update-java-alternatives?  The instructions QIII cites say to use update-alternatives.  We use update-java-alternatives to switch between Java versions, so I want that to work.

---

### Post by QIII on 2012-01-06
I have a virgin install at home, so I'll check this out.  I believe those instructions should leave you with that listed in Java alternatives.  If OpenJDK is installed, I would expect both to show.  Do you see OpenJDK in your alternatives?

The ... update-alternates ... zika mentioned is part of the instructions.

---

### Post by sbqsam on 2012-01-06
I am installing on Ubuntu 10.04 64-bit.  I must use this OS version.  I installed it fresh yesterday and took all the updates today.  Then started working on installing Oracle's (Sun's) Java.  Initially "update-java-alternatives -l" showed just openJDK and "java -version" showed openJDK.  After I followed the instructions at [http://sites.google.com/site/easylinuxtipsproject/java; ]("http://sites.google.com/site/easylinuxtipsproject/java")"update-java-alternatives -l" still only showed openJDK, but "java -version" showed Oracle's Java.

Google recommends this for Android (see [http://source.android.com/source/initializing.html](http://source.android.com/source/initializing.html), Installing the JDK):

```
$ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
$ sudo apt-get update
$ sudo apt-get install sun-java6-jdk
```[FONT=Arial]After that, "update-java-alternatives -l" displays this newly installed java in addition to OpenJDK[/FONT][FONT=Arial], but it is v26, not 30.[/FONT]
[FONT=Arial] 
-Sam
[/FONT]

---

### Post by QIII on 2012-01-06
It will never be updated in the repos because Oracle changed its license policy.

---

### Post by QIII on 2012-01-06
OK.  What you are seeing is normal.  That is listing the alternatives available.  The alternatives are those that are not being used.

It took getting home and opening the terminal to get in my zone.

I believe that what you are thinking of is

```
sudo update-alternatives --config java
```

which is what allows you to switch back and forth between which Java you want to use.

---

### Post by hdaf on 2012-01-07
Thnks 
that was really useful

---

### Post by matza55 on 2012-01-07
I think this was very helpfull! I have a 64-bits pc, but choose often to use 32-bits os for installation - because of java....
So - thanks. Maybe next timme i choose 64-bit?!
Another question is: how much better/faster is 64-bit compared to 32-bit?

---

### Post by ubu19821 on 2012-04-14
I came across  this post when searching for a way to update java jre to the latest version on ubuntu.

[http://blog.flexion.org/2012/01/16/install-sun-java-6-jre-jdk-from-deb-packages/](http://blog.flexion.org/2012/01/16/install-sun-java-6-jre-jdk-from-deb-packages/)

This uses a script to download java and builds the packages locally on your computer.

Can a senior take a look and comment on this method when they have a chance? I know this thread is a bit old but the tutorial hosted on the google site seems more complicated.

Thanks

---

### Post by zika on 2012-04-15
No need for complicating an easy thing. It is a 3 piece drama:
1. download
2. extract
3. fulfill certain update-alternatives forms
enjoy... ;)
The way I've used in #13 is a lot outdated. Neverthelsee it works... And it is easy...
If there is a need for look at a skeleton of the latest (shortest and easiest) way to do it: [http://forum.ubuntu-rs.org/Thread-64-bit-java-flash-i-script-za-brihttp://jdk7.java.net/archive/7u6-b05.htmlsanje-prethodnih-install-acija-flash-a?pid=123032#pid123032]("http://forum.ubuntu-rs.org/Thread-64-bit-java-flash-i-script-za-brisanje-prethodnih-install-acija-flash-a?pid=123032#pid123032")
Or use [http://jdk7.java.net/archive/7u6-b05.html](http://jdk7.java.net/archive/7u6-b05.html) and You have only to extract folder and fulfill update-alternatives and symbolic links... [http://forum.ubuntu-rs.org/Thread-64-bit-java-flash-i-script-za-brisanje-prethodnih-install-acija-flash-a?pid=188918#pid188918](http://forum.ubuntu-rs.org/Thread-64-bit-java-flash-i-script-za-brisanje-prethodnih-install-acija-flash-a?pid=188918#pid188918)
Just change archives (to suit a today's state) accordingly...

---

### Post by dcstar on 2012-05-05
If people want the Sun Java packages then follow the instructions here:

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-10-10-maverick-using-ppa.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-10-10-maverick-using-ppa.html)

---

