---
title: "M2Eclipse plugin"
date: 2008-08-05
forum: Programming Talk
---

### Post by jamesdcarroll on 2008-08-05
I have the newest version of Eclipse and everything was working fine.  I then installed to m2Eclipse plugin and now I'm getting errors (lots of NPE's).

My guess at this point is that its a permissions thing. 

Any ideas/tips to get this set up right?

Thanks,

---

### Post by tinny on 2008-08-05
> **jamesdcarroll said:**
> I have the newest version of Eclipse and everything was working fine.  I then installed to m2Eclipse plugin and now I'm getting errors (lots of NPE's).

My guess at this point is that its a permissions thing. 

Any ideas/tips to get this set up right?

Thanks,

Unfortunately that m2Eclipse plug-in is not very good. The organization that I work for tried using it for our Maven built projects and we where very disappointed. Eclipse has poor support for Maven unfortunately (right now, there is a project in development). So we just reverted to using Maven from the command line. I think that even if you get it working you will be disappointed.

Is NetBeans an option for you? NetBeans has VERY good support for Maven! Not only does it support the standard "build", "clean", "test" type functionality but it also has a Maven dependency finder as well as a Maven archetype library. [http://wiki.netbeans.org/MavenBestPractices#section-MavenBestPractices-CreateNewProject](http://wiki.netbeans.org/MavenBestPractices#section-MavenBestPractices-CreateNewProject)

Edit: If you still want to use m2Eclipse...

How did you install eclipse? What version is it? Can you post the error messages?

---

### Post by Ruhe on 2008-08-05
I have had a lot troubles with M2E too.
One of the most stupid things is requirement to run eclipse on jdk.
And finally I found how I should run it.
U have to add this to eclipse.ini:
```

-vm
C:\Program Files\Java\jdk1.6.0_01\bin\javaw.exe

```
This is from my windows installation at work. I guess something like 
```
/usr/lib/jvm/java-6-openjdk/bin/java
```
is the right way to jdk on ubuntu.

Now everything works well.

---

### Post by tinny on 2008-08-05
> **Ruhe said:**
> I have had a lot troubles with M2E too.
One of the most stupid things is requirement to run eclipse on jdk.
And finally I found how I should run it.
U have to add this to eclipse.ini:
```

-vm
C:\Program Files\Java\jdk1.6.0_01\bin\javaw.exe

```
This is from my windows installation at work. I guess something like 
```
/usr/lib/jvm/java-6-openjdk/bin/java
```
is the right way to jdk on ubuntu.

Now everything works well.

You can do this from within the IDE.

"Window" > "Preferences" > "Java" > "Installed JREs"

The Sun JDK is the way to go!

---

### Post by Ruhe on 2008-08-06
> **tinny said:**
> You can do this from within the IDE.

"Window" > "Preferences" > "Java" > "Installed JREs"

The Sun JDK is the way to go!

Nope.
So you specify JREs for your projects, not for eclipse.
To run eclipse on specific java machine you have to point it to jvm at startup.
And there're only two ways:
 - modify eclipse.ini as I wrote
 - run eclipse from comand line and specify the vm option there

---

### Post by Quikee on 2008-08-07
> **Ruhe said:**
> Nope.
So you specify JREs for your projects, not for eclipse.
To run eclipse on specific java machine you have to point it to jvm at startup.
And there're only two ways:
 - modify eclipse.ini as I wrote
 - run eclipse from comand line and specify the vm option there

I don't need to do anything you mentioned and m2eclipse works as expected for me with Eclipse 3.4, m2eclipse 0.96 dev and openJDK that shipped with Ubuntu (intrepid). Maybe you have to run "update-java-alternatives" and set to your preferred JDK as your Java might not have been set up properly.

BTW even archetypes work as expected now for me now with 0.96 with which I had problems in the past.

Worth to mention is also the alternative to m2eclipse - [Q4E]("http://code.google.com/p/q4e/").

---

### Post by Vishal Agarwal on 2008-08-07
Hi,
I am not starting new thread,and want some help. [COLOR="DeepSkyBlue"]I want to install PHP Development plugin in eclipse 3.2.[/COLOR] I am unable to do that. Can any one help me how to do that ?

---

### Post by tinny on 2008-08-07
> **Vishal Agarwal said:**
> Hi,
I am not starting new thread,and want some help. [COLOR="DeepSkyBlue"]I want to install PHP Development plugin in eclipse 3.2.[/COLOR] I am unable to do that. Can any one help me how to do that ?

Why not? 

PHP is completely different from Maven!

Have a look at this [http://dev.phpeclipse.com/wiki/Installation](http://dev.phpeclipse.com/wiki/Installation)

You will get more help if you start a new thread ;)

---

### Post by ekuleshov on 2008-08-21
> **jamesdcarroll said:**
> I have the newest version of Eclipse and everything was working fine.  I then installed to m2Eclipse plugin and now I'm getting errors (lots of NPE's).

My guess at this point is that its a permissions thing. 

Any ideas/tips to get this set up right?

  Some details, especially stack traces for those errors would help to identify what is happening there. You can as well report issues directly to the project at [http://jira.codehaus.org/browse/MNGECLIPSE](http://jira.codehaus.org/browse/MNGECLIPSE)

  Thanks

  Eugene

---

### Post by ekuleshov on 2008-08-21
> **tinny said:**
> Unfortunately that m2Eclipse plug-in is not very good. The organization that I work for tried using it for our Maven built projects and we where very disappointed. Eclipse has poor support for Maven unfortunately (right now, there is a project in development). So we just reverted to using Maven from the command line. I think that even if you get it working you will be disappointed.

  I'd be interested to hear some more specifics what you find problematic between Eclipse and Maven and what caused your grief.

  regards,
  Eugene

---

### Post by ekuleshov on 2008-08-21
> **Ruhe said:**
> I have had a lot troubles with M2E too.
One of the most stupid things is requirement to run eclipse on jdk.


  Unfortunately it is not m2eclipse, but Maven requirement. There is more details on this in the project FAQ at [http://docs.codehaus.org/display/M2ECLIPSE/Project+FAQ#ProjectFAQ-UnabletolocatetheJavacCompilerError](http://docs.codehaus.org/display/M2ECLIPSE/Project+FAQ#ProjectFAQ-UnabletolocatetheJavacCompilerError)

  regards,
  Eugene

---

### Post by tinny on 2008-08-21
> **ekuleshov said:**
> I'd be interested to hear some more specifics what you find problematic between Eclipse and Maven and what caused your grief.

  regards,
  Eugene

Hi Eugene

Its was about 4 months ago when I used M2Eclipse so unfortunately I cant remember the specifics. Basically I remember getting a bunch of runtime errors when trying to do anything basic.

---

### Post by Ruhe on 2008-08-22
> **ekuleshov said:**
> Unfortunately it is not m2eclipse, but Maven requirement. There is more details on this in the project FAQ at [http://docs.codehaus.org/display/M2ECLIPSE/Project+FAQ#ProjectFAQ-UnabletolocatetheJavacCompilerError](http://docs.codehaus.org/display/M2ECLIPSE/Project+FAQ#ProjectFAQ-UnabletolocatetheJavacCompilerError)

  regards,
  Eugene

Wow, you are creator of this plugin?
Thanks a lot for your work and sorry about my comments! I didn't know that maven itself requires jdk.

---

### Post by galland on 2008-09-20
Hello guys,

I packaged several Eclipse tools in addition to whose already provided by the PPA of the eclipse-team ([https://launchpad.net/~eclipse-team/+archive):](https://launchpad.net/~eclipse-team/+archive):)

- AspectJ (ajdt)
- Data tools
- EMF
- GEF
- Webtools (wtp)
- Mylyn
- subclipse
- Maven 2 Integration for Eclipse (m2eclipse)

The ajdt and mylyn packages are only for Eclipse 3.4.

Feadbacks are welcome.

Website: [http://www.arakhne.org/](http://www.arakhne.org/)
Dowload and Package Server: [http://www.arakhne.org/download.html](http://www.arakhne.org/download.html)

Stéphane

---

