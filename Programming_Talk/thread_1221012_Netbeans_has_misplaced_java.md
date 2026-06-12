---
title: "Netbeans has misplaced java?"
date: 2009-07-23
forum: Programming Talk
---

### Post by a7ndrew on 2009-07-23
Hi, I installed Netbeans 6.5 a while ago and it ran fine. I am using the Sun jre and jdk. 

A week or two ago approximately I noticed an upgrade or two to Java -- I think it may have been the jdk and the jre, but I'm not 100% sure. 

Now Netbeans does not work. It gives the error "Cannot find java, please use the --jdkhome switch."

The command "which java" returns 
```
/usr/bin/java 
```
The command "which javac" returns
```
/usr/bin/javac
```
The command "java --version" returns 
```
java version "1.6.0_14"
Java (TM) SE Runtime Environment (build 1.6.0_14-b08)
Java Hotspot(TM) Client VM (build 14.0-b16, mixed mode, sharing)
```

I tried running netbeans from the commandline with the option --jdkhome /usr/bin and with --jdkhome/usr/bin/javac and with --jdkhome/usr/bin/java and each of these just returns the same error message, asking me to use the --jdkhome switch. 

I'm getting a little frustrated here. Could anyone point out to me what I need to do to fix this apparent misconfiguration?

P.S. I don't really feel like upgrading to 6.7 because I'd like to do a bit with JavaFX.


Regards.


EDIT: I also tried moving my ~/.netbeans off to another location but this has had no effect on the error.

---

### Post by hoboy on 2009-07-23
> **a7ndrew said:**
> Hi, I installed Netbeans 6.5 a while ago and it ran fine. I am using the Sun jre and jdk. 

A week or two ago approximately I noticed an upgrade or two to Java -- I think it may have been the jdk and the jre, but I'm not 100% sure. 

Now Netbeans does not work. It gives the error "Cannot find java, please use the --jdkhome switch."

The command "which java" returns 
```
/usr/bin/java 
```
The command "which javac" returns
```
/usr/bin/javac
```
The command "java --version" returns 
```
java version "1.6.0_14"
Java (TM) SE Runtime Environment (build 1.6.0_14-b08)
Java Hotspot(TM) Client VM (build 14.0-b16, mixed mode, sharing)
```

I tried running netbeans from the commandline with the option --jdkhome /usr/bin and with --jdkhome/usr/bin/javac and with --jdkhome/usr/bin/java and each of these just returns the same error message, asking me to use the --jdkhome switch. 

I'm getting a little frustrated here. Could anyone point out to me what I need to do to fix this apparent misconfiguration?

P.S. I don't really feel like upgrading to 6.7 because I'd like to do a bit with JavaFX.


Regards.


EDIT: I also tried moving my ~/.netbeans off to another location but this has had no effect on the error.

When you said that Netbeans doesn't work, you mean that it doesn't start/ you can not launch the ide ?
if you can launch the ide
Tools/java platforms
add platform then select the correct jdk

---

### Post by a7ndrew on 2009-07-23
> **hoboy said:**
> When you said that Netbeans doesn't work, you mean that it doesn't start/ you can not launch the ide ?

Correct.
When I try to start it from my menu icon, nothing happens. When I try to start it from the command line, I get the message I mentioned above.

---

### Post by hoboy on 2009-07-23
> **a7ndrew said:**
> Correct.
When I try to start it from my menu icon, nothing happens. When I try to start it from the command line, I get the message I mentioned above.

OK set your java path /home/netbeans-6.5.1/bin/netbeans

---

### Post by hoboy on 2009-07-23
> **hoboy said:**
> OK set your java path /home/netbeans-6.5.1/bin/netbeans

run
sudo update-alternatives --config java
then you will se witch jdk you are runing

---

### Post by a7ndrew on 2009-07-23
Thank you very much for your help so far.

sudo update-alternatives--config java tells me that
```

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

```

I am not too sure how to set my java path.

---

### Post by froggyswamp on 2009-07-23
> **a7ndrew said:**
> 
I am not too sure how to set my java path.
You'll be sure after you google.

---

### Post by HotCupOfJava on 2009-07-23
I think I know what caused the problem. If you are using the Sun's jdk for Java 6 from the repos, the update changed the folder /usr/lib/jvm/java-6-sun-1.6.0.07 to /usr/lib/jvm/java-6-sun-1.6.0.14

All relevant subdirectories retained their names, from what I can tell.

---

