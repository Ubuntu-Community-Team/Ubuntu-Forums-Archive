---
title: "Jboss - Installation problem"
date: 2007-07-03
forum: Programming Talk
---

### Post by zoobave on 2007-07-03
Hi,
when i try to install jboss from source, i got the following error. But, i have installed java. Am i missing something?

[B]
checking for JDK location (please wait)... checking Try to guess JDK location... configure: error: can't locate a valid JDK location
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
[/B]

Thanks,
Zoobave,
[http://zoobave.blogspot.com/]("http://zoobave.blogspot.com/")

---

### Post by sgordon on 2007-07-03
My first guess would be that when you say you 'have Java', you have the Java Runtime Environment (JRE) but not the Java Development Kit (JDK), which is needed to compile java source.

The package you want, is:
sun-java6-jdk
or
sun-java5-jdk

(from memory, go for Java 6 if you aren't sure. Search for 'jdk' if I haven't got those right)

Also run:
sudo update-java-alternatives -s java-6-sun
or
sudo update-java-alternatives -s java-1.5.0-sun

Which will make the installed version the default JRE/JDK for your setup.

Give that a try. I can't try these out myself for a few days myself.

  S

---

### Post by shrek on 2007-07-04
I was able to install the sun SDK 6 following instruction from another post on this site (Thanks guys) and installed Eclipse with the package manger. I had to manually install JBoss and after putting it /opt/jboss I notice that I am having permissions problems i.e it could not crate the log folder. After I created the folder then it was unable to write to the log etc. I see some folks say just install under /usr but there has to be a way to get JBoss to work properly when from opt. Can any one point me in the right direction?

---

### Post by commonlyUNIQU3 on 2007-10-29
> **shrek said:**
> I was able to install the sun SDK 6 following instruction from another post on this site (Thanks guys) and installed Eclipse with the package manger. I had to manually install JBoss and after putting it /opt/jboss I notice that I am having permissions problems i.e it could not crate the log folder. After I created the folder then it was unable to write to the log etc. I see some folks say just install under /usr but there has to be a way to get JBoss to work properly when from opt. Can any one point me in the right direction?

Without more specifics on how you want to configure jboss, you could allow everyone & everything to have rwx access to the /opt/jboss directory by the following:

```
sudo chmod -R 777 /opt/jboss
```

---

### Post by dcostelloe on 2007-12-01
I found this a great helper to install and run Jboss worked for me in no time.
I changed from JDK 5 to 6
:popcorn:

[http://www.hoatu.fr/en/home/details/article/install-jboss-404-application-server-on-linux-ubuntu-with-the-sun-java5-jdk.html]("http://www.hoatu.fr/en/home/details/article/install-jboss-404-application-server-on-linux-ubuntu-with-the-sun-java5-jdk.html")

---

