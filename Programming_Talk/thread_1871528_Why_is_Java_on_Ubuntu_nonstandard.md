---
title: "Why is Java on Ubuntu nonstandard?"
date: 2011-10-29
forum: Programming Talk
---

### Post by 1clue on 2011-10-29
Hi everyone.

Ubuntu does not set JAVA_HOME.  Ubuntu does not put a standard java directory anywhere, they break the thing up and hide the various directories wherever seems appropriate to a Linux developer, which is by definition extremely inappropriate to a Java developer.

For years now, I've attempted to use the supported JDK, ran into compatibility problems, installed the ubuntu-supported Sun jdk, tried to figure out where JAVA_HOME is and realized it is not there.

As soon as I see that fact, I go out to grab a standard archive from the official website, extracted it into /opt/java/jdk-a.b.c, symbolic linked that directory to 'current' and set JAVA_HOME to be /opt/java/current.  Set the path so my installation comes before /usr/bin and I'm done.

This time I've gone a bit further and tried to find some sort of documentation regarding this, and still come up mighty confused.  I would like to understand the rationale behind splitting the installation into its various parts, why we need a tool to choose which environment to use, and why it's so hard to get rid of the supported installations once they're in there.

So I ask you guys:

Why does Ubuntu make it so complicated?  It takes a whopping 5 minutes to install Java on any system I've ever used it on, with the exception of an AS/400 which takes a whole lot longer.

---

### Post by gsmanners on 2011-10-29
I'm guessing it's because Java uses a lot of space, and nearly every essential script in Linux is either Bash, Perl or Python.

---

### Post by 1clue on 2011-10-29
Please be serious.

---

### Post by gsmanners on 2011-10-29
Seriously? I think it's weird that anyone uses Java at all. Why not use Python for all your scripting?

---

### Post by khelben1979 on 2011-10-29
Since Ubuntu is based on Debian, Debian classifies Sun Java as a non-free component of their distribution which could explain why everything isn't perfect from the start when they decide to include it in Ubuntu as default (if the Sun Java is default that is..). Personally I think it's up to the Ubuntu developers to make sure the Sun Java installation works correctly and configures as expected.

Have you tried [NetBeans]("http://en.wikipedia.org/wiki/Netbeans")?

---

### Post by 1clue on 2011-10-29
I use Java because:
[LIST=1]
[*]I'm developing a cross-platform enterprise application, the first version of which was sold in early 2000.
[*]It has been Java from day 1.
[*]Most of my customers use Windows as servers, although our application works fine on UNIX as well.
[*]I just happen to prefer developing on Something Which Is Not Windows.
[*]What I'm doing is not even remotely scripting.  It's a multi-tier enterprise application which interfaces with ERP applications like Oracle Financials.
[/LIST]

None of you have even noticed my actual question yet.

As for non-free, there is a GPL version of Sun Java.  That's old news.  Second, I could care less if it's free or not, I'm using the non-free version, for which Ubuntu claims support.

I would prefer to talk to an Ubuntu developer who is familiar with the reasoning behind Ubuntu's installation of Java on the distro and why they chose to break it up in a nonstandard way.

---

### Post by Reiger on 2011-10-29
What do you need JAVA_HOME for anyway?

---

### Post by 1clue on 2011-10-29
> **gsmanners said:**
> Seriously? I think it's weird that anyone uses Java at all. Why not use Python for all your scripting?

Seriously?  Why use Linux at all?  Why not use Windows for all your computing?

One size does not fit all.  There is no one language that satisfies all needs.  I can give detailed reasoning behind our choice of language but that has absolutely nothing to do with the purpose of this thread.

---

### Post by Reiger on 2011-10-29
> **1clue said:**
> 
I would prefer to talk to an Ubuntu developer who is familiar with the reasoning behind Ubuntu's installation of Java on the distro and why they chose to break it up in a nonstandard way.

The reason has to do with the ability of Debian to support multiple coexisting versions of Java (from different vendors) and making it easy for the sysadmin to select/manage defaults. Hence on Debian and derivatives one can switch default “java” using “sudo update-alternatives --configure java”.

Why, specifically, do you need JAVA_HOME?

---

### Post by lykwydchykyn on 2011-10-29
> **1clue said:**
> 
I would prefer to talk to an Ubuntu developer who is familiar with the reasoning behind Ubuntu's installation of Java on the distro and why they chose to break it up in a nonstandard way.

In that case, launchpad would probably be a better place to post your question.  Launchpad allows you post questions related to a specific package, which will get copied to the packaging team.

The vast majority of people on this forum are users, most of whom don't know the answers to the "why was it done this way" questions, and most of whom are bent on defending the way it was done no matter how silly the response looks. ;)

---

### Post by 1clue on 2011-10-29
I manage multiple installations of Java running concurrently for different applications by using a bit of forethought on where to put things, and symbolic links.

For example:
/opt/sunjdk/current -> /opt/sunjdk/jdk-x.y.z

/opt/blackdown/current - /opt/blackdown/jdk-x.y.z

Each app can pick the proper version for whatever they want, and I can change that default without a reboot, and the mechanism is immediately obvious to anyone who does a directory listing.

There are lots of reasons why JAVA_HOME is desirable.  For one thing, it's part of the Java spec that it be there, and for my particular case at the moment I'm trying to install grails, which requires JAVA_HOME.

I will definitely ping launchpad.

Thanks for the help, Reiger and lykwydchykyn.

---

### Post by gsmanners on 2011-10-29
I'm not being argumentative. I really do like to know these things. As for asking the devs. LOL (I highly doubt the devs at Launchpad would be any more helpful than us.)

Yeah, Debian is probably a big part of the reason for all this. There's a lot more going on than just politics, too I'm sure. Part of it is probably whether anyone working at Debian or Canonical has the time and energy to put in the work to put together the packaging or whether they hand it off to the MOTUs.

---

### Post by 1clue on 2011-10-30
> **gsmanners said:**
> I'm not being argumentative. I really do like to know these things. As for asking the devs. LOL (I highly doubt the devs at Launchpad would be any more helpful than us.)

Yeah, Debian is probably a big part of the reason for all this. There's a lot more going on than just politics, too I'm sure. Part of it is probably whether anyone working at Debian or Canonical has the time and energy to put in the work to put together the packaging or whether they hand it off to the MOTUs.

So you're saying that the guy who built the Java Ubuntu package doesn't know any more than you do why he chose to break the structure out the way he did?

---

