---
title: "Need help getting rid of java"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by chairsgotoschool on 2012-08-08
i tried getting java Runtime envirement 7 but it didnt work and people said java 7 didnt work on ubuntu anyway so i got 6 instead, now some things are conflicting, i tried getting preload cause people said it makes it run faster but it gets an error cause of oracle java 7.

---

### Post by QIII on 2012-08-08
Do NOT use Java 6.  It is vulnerable to security exploits and is due to reach end of life in November 2012.  Uninstall *that *not Java 7.

Furthermore, a serious exploit targets versions earlier than even Java 7 Update 5.

Who on Earth told you that Java 7 will not work on Ubuntu?


> i tried getting java Runtime envirement 7 but it didnt work  What do you mean by that?  What didn't work?

> and people said java 7 didnt work on ubuntu anyway  What people? 

> now some things are conflicting,  What is conflicting and how?

> i tried getting preload What does this mean?

> cause people said it makes it run faster  Do they?

> but it gets an error cause of oracle java 7.  What error?

---

### Post by chairsgotoschool on 2012-08-08
1.they must have fixed 7 in an update, a few videos said it wouldnt work right
2.i tried getting 7 but it wouldnt work, i dont know why, ill get rid of 6 and get 7 through software center i guess
3.see 1
4.i tried installing preload, some people said it speeds up ubuntu by managing files, it remembers what files you open most and puts them close so it loads faster and when i install it get this error

"Errors were encountered while processing:
    oracle-java7-installer

a few other things have said the same thing

OH forgot i think i got the java 7 plugin for browser but i could never get it to work in browsers

another thing, i just tried getting rid of java 6 and it had an error removing

---

### Post by QIII on 2012-08-08
I don't know what videos you have been watching, but I assure you Oracle Java 7 and OpenJDK 7 work with Ubuntu.  

There were some questions when Oracle Java 7 was first released. There never was anything wrong with Java that needed fixing for it to "work in Ubuntu".

How did you install Java 7 when you tried before?

How did you install Java 6, because it will dictate how you should uninstall it.

At this point we need to make sure that Java 6 and 7 are both completely removed so that we can start fresh.

Preload may be running in to problems due to a partial or defective installation of Java.

You can install OpenJDK 7 from the Application Center, but you cannot install Oracle Java 7.  If you want to do that, you'll have to use the wiki in my signature and I can tell you how to do that.

---

### Post by chairsgotoschool on 2012-08-08
thanks, the java 7 stuff is just plugins for browser i guess they didnt get installed right, i tried unistalling java 6 the way i got it but it has an error

edit: i tried unistalling 6 again to post the error report but it said it was gone :D

---

### Post by QIII on 2012-08-08
Would you please post back the results of 

```
java -version
```

---

### Post by chairsgotoschool on 2012-08-08
java version "1.7.0_05"
Java(TM) SE Runtime Environment (build 1.7.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 23.1-b03, mixed mode)

i think i got oracle java 7 to work, and im pretty sure i got rid of java 6

---

### Post by acimi66 on 2012-08-08
I just went to the software center and down loaded java 7

and followed this

"After installation use the following command to select the desired version of Java, i.e. version 7
**sudo update-alternatives --config java**
You can check your version selection using the following command...
**java -version**
It should respond with the following...
java version "1.7.0_03" "

worked perfectly

---

### Post by QIII on 2012-08-08
> **acimi66 said:**
> I just went to the software center and down loaded java 7

That is OpenJDK 7, which is fine.

It's not Oracle Java 7 Update 5.  The repo does not have Oracle Java 7 because Oracle does not authorize anyone to have Oracle Java 7 in their repositories.

OpenJDK should be used if you can because it is open source.  However, it is not universally recognized as Java by the world and sometimes the use of Oracle Java 7 is necessary.

---

### Post by chairsgotoschool on 2012-08-08
ok im just going to get rid of all the java stuff, could someone post how to do that cause i cant seem to get them to get completely removed ill post all the java programs i can find that are running, i dont know how i got them all going
oracle java 7 console
oracle java 7 visualvm
oracle java 7 webstart
oracle java 7 policy tool
oracle java 7 plugin control panel

and i have openJDK java 6 and java 7 Runtime

---

### Post by QIII on 2012-08-08
> **chairsgotoschool said:**
> java version "1.7.0_05"
Java(TM) SE Runtime Environment (build 1.7.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 23.1-b03, mixed mode)

That's the JRE.  You probably want to make sure the browser plugin is the correct one.

If you use Firefox, type

```
about:plugins
```into the navigation bar.

For the Oracle Java 7 Plugin, Update 5, look for

```
Java(TM) Plug-in 1.7.0_05
```If it is 1.7.0_04 or earlier, you risk a very dangerous exploit vulnerability.

---

### Post by QIII on 2012-08-08
> **chairsgotoschool said:**
> 
oracle java 7 console
oracle java 7 visualvm
oracle java 7 webstart
oracle java 7 policy tool
oracle java 7 plugin control panel

How do you know they are running?

> and i have openJDK java 6 and java 7 RuntimeYou should get rid of OpenJDK 6, but OpenJDK 7 can exist on the machine without problems.  I would not bother installing OpenJDK at this point.

How did you install OpenJDK 6?  That will have some bearing on how you uninstall it.

Edit:

Post the results of 

```
sudo update-alternatives --config java
```

so I can see exactly what you have.

---

### Post by chairsgotoschool on 2012-08-08
There are 4 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-7-oracle/jre/bin/java          1062      auto mode
  1            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1051      manual mode
  3            /usr/lib/jvm/java-7-oracle/jre/bin/java          1062      manual mode
  4            /usr/lib/jvm/jre1.7.0/bin/java                   0         manual mode

Press enter to keep the current choice[*], or type selection number: 

thats the result of typing sudo update-alternatives --config java

i believe i got java 6 from software center but it says i dont have it and i tried using terminal to get rid of it too

i know all those are running cause i hit the windows key and typed java then those came up and on my task bar it has java 6 and 7

---

### Post by QIII on 2012-08-08
For the alternatives, I'd change that to the first selection, number 0.  I say that because I am not sure if OpenJDK 7 Update 3 has the patch to fix the vulnerability I spoke of.  After you change it, run

```
java -version
```

to be sure which update you are running.  You want it to be 5.

Did you check out what you see when you type

```
about:plugins
```in the navigation bar in Firefox?

I'm going to have to boot a Unity machine to see what happens when I hit the "Window" key.  I'm on Xubuntu and I think the shortcuts are different.

Edit:

OK, don't worry about that list of things.  The "Window" key is just bringing up the Dash and listing some items you can start if you want. Those are components of Java that you want to have.  Leave them alone.

---

### Post by chairsgotoschool on 2012-08-08
about:plugins said command not found, and im using google chrome not fire fox, isnt there a way i can unistall all this java stuff and start fresh, i got them to work but i dont want OpenJDK java 6, i would rather use 7

---

### Post by QIII on 2012-08-09
OpenJDK Java 6 Runtime should show up in the Software Center and can be removed from there.

Again:  To get Oracle Java 7 set as your alternative, just do the update alternatives thing and select item 0.

Don't worry about the other entries.  You probably don't want to unistall OpenJDK 7 at this point, come to think of it, because you may already have installed other things that expect it to be there -- LibreOffice, for instance.

The list of things you gave 

```
oracle java 7 console
oracle java 7 visualvm
oracle java 7 webstart
oracle java 7 policy tool
oracle java 7 plugin control panel
```
are items that belong to Java and you don't want to uninstall them.

I'll have to do some research on Chrome, since I don't use it.

---

