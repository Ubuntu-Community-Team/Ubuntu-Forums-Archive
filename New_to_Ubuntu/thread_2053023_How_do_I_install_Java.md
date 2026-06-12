---
title: "How do I install Java?"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by SirRoverofIvories on 2012-09-04
How do I install Java on Lubunto?   Nothing seems to work and as I click Extract, Open, etc, I just keep going around in circles.   This is soooooooooooo frustrating.

Thank for the help!

---

### Post by Cavsfan on 2012-09-04
> **SirRoverofIvories said:**
> How do I install Java on Lubunto?   Nothing seems to work and as I click Extract, Open, etc, I just keep going around in circles.   This is soooooooooooo frustrating.

Thank for the help!

If you like the CLI way, the instructions are in my sig. I used them a lot and they work well. :)

---

### Post by raja.genupula on 2012-09-04
I think you should see this 
[http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7](http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7)

---

### Post by Cavsfan on 2012-09-04
> **raja.genupula said:**
> I think you should see this 
[http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7](http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7)


Looks like the same thing only harder to understand. Oh well, the OP can choose...

---

### Post by Cheesemill on 2012-09-04
The quick way:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
This method will also keep Java up to date along with the rest of your system.

---

### Post by raja.genupula on 2012-09-04
> **cheesemill said:**
> the quick way:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```this method will also keep java up to date along with the rest of your system.

+1

---

### Post by QIII on 2012-09-04
Thanks, cheesemill.

Guys, cheesemill's suggestion is contained in the wiki in my signature under "Using webupd8's strikingly simple method."

We maintain that wiki specifically for Ubuntu users to make things as easy as possible within the community.  There is no reason to go down a difficult path when webupd8.org has done the work to make it so simple for Ubuntu users.

---

### Post by Cavsfan on 2012-09-04
Aww, you guys like doing it the easy way...... ;)

---

### Post by gavv on 2012-09-04
> **SirRoverofIvories said:**
> How do I install Java on Lubunto?   Nothing seems to work and as I click Extract, Open, etc, I just keep going around in circles.   This is soooooooooooo frustrating.

Thank for the help!  I installed java on my Ubuntu box a couple of days ago following [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java). I went with OpenJDK since it's an open source implementation.   

Perhaps I went a different route as recommended, but all I did was use the apt-get tool to install   the following packages: openjdk-6-jre, openjdk-7-jre, icedtea6-plugin, icedtea-7-plugin, openjdk-6-jdk, openjdk-7-jdk.

---

### Post by beezworld on 2012-09-04
hello everyone

I just tried the "easy way" and it looked like i imported launchpad? is this correct? I don't know where I go from there. Still no signs of java anywhere LOL

---

### Post by Cavsfan on 2012-09-04
> **beezworld said:**
> hello everyone

I just tried the "easy way" and it looked like i imported launchpad? is this correct? I don't know where I go from there. Still no signs of java anywhere LOL

The way to install java in my sig is from google. It's just a matter of cutting and pasting as it is already setup for JRE 7 update 7.
If you do not have java already installed is makes it much easier.

If you have a 32 bit machine the instructions are on the left and if you have a 64 bit machine the directions are on the right.
It takes me about 5-10 minutes, but I have done it a few times.

---

### Post by QIII on 2012-09-04
The Easy Linux Tips method requires that a user watch for updates and reinstall as they come out.  I recommended that method for years and had several pleasant conversations with the maintainers.  Unfortunately, it isn't the easiest, most efficient or nimble way to go any longer.  It is still in the wiki, but I pushed the webupd8 link above it in the text.

webupd8's installer updates automatically via their PPA whenever Oracle puts out an update -- including new builds within an update version.  Users don't have to delete and reinstall.  They need only do their normal updates.

beezworld - Did you use all three commands?  Would you please post the results of

```
java -version
```

---

### Post by garyjh on 2012-09-04
Im brand new to linux. But I was having the same problem trying to download Java 7. Im using Xubuntu 12.04 I couldnt figure out how to download the file! Should be the simplest thing, but it didnt seem like it saved anywhere. I didnt know if I was suppose to extract it, open or what.

I surfed the internet and used different peoples things of typing get this apt or sudo this or that. They werent working. I was getting permission denied and all kinds of stuff. 

I finally tryed what cheesemill had. That seemed like it said it loaded it up. I thought I had finally got it working. But when I go to a test page for testing Java. It is showing an error???

Do you have any ideas what to do to fix this. Im thinking I loaded a bunch of half files with all the experimenting I did. Starting to think I should just reinstall Xubuntu, and start fresh.

Gary.
Thanks for any help. I need it.

---

### Post by lswartz on 2012-09-04
Isn't using the package manager to install **icedtea **the easy method. I do wonder how it got that name though.

---

### Post by QIII on 2012-09-04
IcedTea is the browser plugin for OpenJDK, which is in the repo.

OpenJDK is the open source reference implementation for Oracle Java 7.  It is preferred because it is open source.  However, it is not universally recognized as Java by developers who are unaware of the relationship and, therefore, does not always work for Java applications or applets.

---

### Post by QIII on 2012-09-04
garyjh -

Would you please post the results of 

```
java -version
```

---

### Post by alphacrucis2 on 2012-09-04
Has the nasty security hole in Java been patched yet?

---

### Post by lswartz on 2012-09-04
> **QIII said:**
> IcedTea is the browser plugin for OpenJDK, which is in the repo.

OpenJDK is the open source reference implementation for Oracle Java 7.  It is preferred because it is open source.  However, it is not universally recognized as Java by developers who are unaware of the relationship and, therefore, does not always work for Java applications or applets.

Thank you very much. It certainly explains why some of the things my wife looks at don't work, even though I thought I had Java installed.

---

### Post by QIII on 2012-09-04
> **alphacrucis2 said:**
> Has the nasty security hole in Java been patched yet?

The latest one has.  This week's is still waiting to be uncovered.

Lest you think OpenJDK is invulnerable, the hole brought to light 10 days ago also affected OpenJDK 7 (despite strident claims to the contrary) and IBM Java 7.

And OpenDNS's claim that you are safe by using their service is a crock.  They didn't "fix" anything to do with the vulnerability.  They just redirected traffic generated by the particular payload delivered to take advantage of the vulnerability.  They didn't fix the hole.  They just tackled the one guy who had crawled in.

---

### Post by beezworld on 2012-09-04
Found my problem, I was copying and pasting all three lines of commands at 1 time.  Now I have it installed...on to see if I can find out how to launch it.
Thank you

---

### Post by garyjh on 2012-09-04
Hi QIII

[I]java version "1.7.0_07"
Java(TM) SE Runtime Environment (build 1.7.0_07-b10)
Java HotSpot(TM) Client VM (build 23.3-b01, mixed mode)[/I]

See if that looks out of the ordinary. Probably wont be able to get back to this tonite though. Need to get up for work. Ive had it with Windows, thats why Im trying Linux. Too many updates to pay for with a Windows system. All I need is some simple drivers, and they dont seem to feel any urgency for it. Just selling all brand new stuff with more bugs!!

Thanks for the help.

Gary

---

### Post by QIII on 2012-09-04
> **beezworld said:**
> Found my problem, I was copying and pasting all three lines of commands at 1 time.  Now I have it installed...on to see if I can find out how to launch it.
Thank you

You don't "launch" Java.  It's a platform, not a particular "application".

---

### Post by QIII on 2012-09-04
> **garyjh said:**
> Hi QIII

[I]java version "1.7.0_07"
Java(TM) SE Runtime Environment (build 1.7.0_07-b10)
Java HotSpot(TM) Client VM (build 23.3-b01, mixed mode)[/I]

Gary

You have Java installed successfully.  What error are you getting when you try to test it?  What are you doing to test it?

---

### Post by garyjh on 2012-09-04
I tryed a couple different web sites. I just did a search for "testing Java". At first it just shut down my Firefox browser. After restarting the computer and doing the test.....it opened up a small window and said something like "Error, click here for deatils". There wasnt a whole lot of explanation of what the error was.. 

Im on another computer right now, When I go to those pages, it just shows little pop up boxes with goofy animations in them. Im guessing thats what I should be seeing on the Xubuntu machine.

Do I have to activate it somehow for the Firefox Browser???

---

### Post by QIII on 2012-09-04
In Firefox, type

```
about:plugins
```and let me know if you see a listing for

Java(TM) Plug-in 1.7.0_07

You can also go [here](http://www.java.com/en/download/installed.jsp) to test.

---

### Post by ramsharan065 on 2012-09-05
I would prefer to use java from oracle.
Download it.
Extract it anywhere you like. But I would prefer to extract on /usr/java/.
Now java is installed.
running java:
-entering full path for example: "/home/ramsharan/Desktop/linux software/jdk1.7.0_03/jre/bin/java" file.java
-or, go to the location of java and do:    ./java file.java
-if you donot want to enter full path or go to the location of java, you can make alias of it. For this,
open file   ~/.bashrc using any editor you want.
Then on last line add
alias java='full_location_of_java/java' 
for example: alias java='/usr/local/jdk1.7.0_05/jre/bin/java'
and save the file.
Then open command line and your can run command java.
If you want to run javac or javaw, you can repeat above option as done with java.

---

### Post by QIII on 2012-09-05
Again:  webupd8.org's scripts DO install ORACLE JAVA.  webupd8 has automated th process for Ubuntu.

With Ubuntu, there is no reason to download and install directly.  Additionally, the webupd8 PPA keeps Oracle Java 7 updated automatically as Oracle releases updates, which does not happen if you install it manually.  All required entries are made in environmental files and a symlink is created in your browser profile to point to the browser plugin.  Your method now requires you to have to know when updates come out, reinstall the files and edit other files.

garyjh has Oracle Java 7 installed.  It will be automatically updated as changes occur to Oracle Java 7 when he does his normal Ubuntu updates.

---

### Post by garyjh on 2012-09-05
QIII

Just an update. I ended up doing a fresh install of Xubuntu 12.04. Installed the standard updates. And then type in the 3 Java commands from earlier in this post. Checked if it was working on a couple web sites. SUCCESS!!!!!

Thank you very much.

1 thing figured out. Now on to the printer.

---

### Post by gavv on 2012-09-06
> **QIII said:**
> 

OpenJDK is the open source reference implementation for Oracle Java 7.  It is preferred because it is open source.  However, it is not universally recognized as Java by developers who are unaware of the relationship and, therefore, does not always work for Java applications or applets.

Qiii, with your expertise at hand, what do you mean by this? I'm currently learning how to program using Java at school, and I suspect I only need the OpenJDK implementation. I'd only install the Oracle version if I absolutely needed to..if I need to take the long route I'll take it

Also, I'm rather concerned about this security update that I've been hearing about. I went through the OpenJDK install several days ago, and I'm not sure whether or not I need to hunt down an update somewhere or take some precautions.

---

### Post by QIII on 2012-09-06
@VishnuNJ: That's the webupd8 method given in the wiki and that is what I directed the posters to.

The reason I point people to the wiki is twofold:

1.  So that people know the community wikis exist.

2.  The Java wiki contains a lot of other important information as well.

---

### Post by QIII on 2012-09-06
> **gavv said:**
> Qiii, with your expertise at hand, what do you mean by this? I'm currently learning how to program using Java at school, and I suspect I only need the OpenJDK implementation. I'd only install the Oracle version if I absolutely needed to..if I need to take the long route I'll take it

Also, I'm rather concerned about this security update that I've been hearing about. I went through the OpenJDK install several days ago, and I'm not sure whether or not I need to hunt down an update somewhere or take some precautions.

What I mean is best explained by Henrik Stahl, Senior Director of Product Management in the Java Platform Group at Oracle:

"The role of the Reference Implementation (RI) is to be used as the gold  standard for all Java implementations. In order to have an  implementation certified as Java SE compatible, an implementor must pass  a large number of compatibility tests - the Technology Compatibility  Kit (TCK). Furthermore, implementations may be compared to the RI as an  additional check of compatibility. Basically, if your implementation has  been certified to have the same behavior as the RI then it is Java  compatible. "

Oracle itself agrees to abide by this.  Oracle still maintains the specification and Oracle is heavily involved in the development of OpenJDK.

Whether or not you can use OpenJDK is determined by what is required by the course material and the instructor.

The security update,* for the time being*, is complete.  If you use the webupd8 method for Oracle Java 7, you will get Oracle's latest release -- Oracle Java 7 Update 7 (build 10).  There is nothing else to hunt down.  Oracle Java 7 is closed-source and proprietary.  The only place it can be found is from Oracle.

Java has a sordid history when it comes to security.  When Java belonged to Sun, it was more likely to be patched quickly.  Now that Oracle bought Sun (and Java with it), updates can be slow in coming.  Oracle normally has a quarterly patch schedule.  In this case, they got egg on their faces and moved more quickly.  (Don't tell anyone I said that, or they may kick me out of the OTN.)

---

### Post by testcees on 2012-09-09
> **Cavsfan said:**
> The way to install java in my sig is from google. 
For clarity, from a *personal* page of another forum member on *[sites.google.com]("http://sites.google.com")* (credits for making these Ubuntulinux pages)

---

