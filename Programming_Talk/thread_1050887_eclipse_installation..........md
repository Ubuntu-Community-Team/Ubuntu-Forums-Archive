---
title: "eclipse installation........."
date: 2009-01-26
forum: Programming Talk
---

### Post by abhilashm86 on 2009-01-26
i went to install eclipse through synaptic for program in python,following error occured when i tried opening it

abhilash@abhi:~$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...not found
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...not found
  testing /usr/lib/j2sdk1.5-ibm...not found
  testing /usr/lib/j2sdk1.4-ibm...not found
  testing /usr/lib/j2sdk1.6-sun...not found
  testing /usr/lib/j2sdk1.5-sun...not found
  testing /usr/lib/j2sdk1.4-sun...not found

what are other packages i need to install in order to sort it out.......

---

### Post by jespdj on 2009-01-26
You need to install Java, because Eclipse itself is written in Java.
```
sudo apt-get install sun-java6-jdk
```

---

### Post by abhilashm86 on 2009-01-26
> **jespdj said:**
> You need to install Java, because Eclipse itself is written in Java.
```
sudo apt-get install sun-java6-jdk
```

ok i am in process of installing jdk,then for writing python scripts what are other codecs i need to install?

---

### Post by Kilon on 2009-01-26
> **jespdj said:**
> You need to install Java, because Eclipse itself is written in Java.
```
sudo apt-get install sun-java6-jdk
```


if you do not like typing things into terminal there is always synaptic. 

Check "sun-java6-jre" this will install the runtime only. "sun-java6-jdk" will give you the JAVA SDK for developing Java applications. 

What Java SDK has to do with python ? Well by itself nothing but there is a version of python called "jython" that gives you the ability to access java libraries directly as you would do with java. Also when you need performance critical code faster than python it does not use C or C++ like python but JAVA which is much easier to use. 

The good news is that Jython is supported by PyDev thus developing for Jython will be exactly the same as developing for python inside Eclipse using PyDev. 

The only additionally thing you need is jython itself. 

[http://www.jython.org/Project/](http://www.jython.org/Project/)

If you are interested in using Java libraries from inside python , I could help you . I develop in Jython and I love it.

---

### Post by abhilashm86 on 2009-01-26
friends i installed eclipse,but i couldn't find pydev and how to continue installing pydev in eclipse?

---

### Post by Kilon on 2009-01-26
> **abhilashm86 said:**
> friends i installed eclipse,but i couldn't find pydev and how to continue installing pydev in eclipse?

ok do this

1) go to Help ->Software Updates -> Find and Install -> Search for new features to install 

2) Click "New Remote Site"

3) Enter " http://pydev.sourceforge.net/updates/" for adress and "PyDev" as title . This will create a entry inside the update database with the title and the adress you entered to tell Eclipse where to search for PyDEv. 

4) Follow the instructions in the Eclipse Dialogs

That is it PyDev is installed

Then you need to set up it. 

Go to Windows -> Preferences -> Pydev -> Python Interperter and choose your Python Interpreter.

This will tell PyDev where and which is your Python interpreter. 

That is all.

---

### Post by abhilashm86 on 2009-01-26
> **Kilon said:**
> 

If you are interested in using Java libraries from inside python , I could help you . I develop in Jython and I love it.

so how is jython,haven't heard it before,is it more compatible than python or what,i really liked python,i'm still learning python,actually i used vim and wrote programs of python:)

now when i started quite big programs,indentation errors killed me,so went on installing eclipse:)

---

### Post by Kilon on 2009-01-26
> **abhilashm86 said:**
> so how is jython,haven't heard it before,is it more compatible than python or what,i really liked python,i'm still learning python,actually i used vim and wrote programs of python:)

now when i started quite big programs,indentation errors killed me,so went on installing eclipse:)

Jython is 100% python. The syntax is EXACTLY the same. 

What is different is that you DO NOT USE some of the python libraries. That is because jython does not support C/C++ which is what the python libraries are based on. But on the other hand it fully support JAVA. 

And while python it requires a fairy lengthy procees to allow you to use C/C++ libraries , Jython requires no extra process at all, you can call ANY java library Directly or even implement any JAVA code or again directly call your jython code directly FROM java. In short in Jython **JAVA CODE EQUALS TO PYTHON CODE**!!!

I prefer using JAVA from Python libraries or C/C++ libraries. Python libraries are as a general rule easier to use but they are fewer out there and lack in some cases documentation. I do not like to code in C/C++ .On the other hand the JAVA world is HUGE, so many choices that is impossible not to find videos, tutorials and exactly the library you need specially tailored to your needs. Also if jython is not fast enough at execution I can code in Java instead of C/C++ and Java is alot easier.    

Of course with PyDEv you can use Jython or Python so that gives you even more freedom.

---

### Post by abhilashm86 on 2009-01-26
thanks kilon for that information,i am going to learn java in further days in college, but now i just know c and c++ with python learning on my own,i'll keep an eye on java with jython:)

---

### Post by abhilashm86 on 2009-01-26
hey i'm getting error at this stage when i goto help,select features to install,what is wrong actualy?its almost done

Pydev Mylyn Integration (0.3.0) requires plug-in "org.eclipse.mylyn (2.0.0.v20070627-1400)", or later version.

---

### Post by Kilon on 2009-01-26
> **abhilashm86 said:**
> thanks kilon for that information,i am going to learn java in further days in college, but now i just know c and c++ with python learning on my own,i'll keep an eye on java with jython:)

Exactly , remember that JYTHON **IS **PYTHON. Anything you learn in Python concerning only the language itself will be exactly the same in Jython. 

When you learn Java in college then you will be able to use Jython with **NO ADDITIONAL learning at ALL** . So for someone that knows Java and Python there is **NOTHING** new .

Obviously JYTHON is for people who know java very well and want to use python instead while keeping the same JAVA libraries.

Or for people already knowing python very well and want to start using JAVA libraries instead of python libraries.

---

### Post by Kilon on 2009-01-26
> **abhilashm86 said:**
> hey i'm getting error at this stage when i goto help,select features to install,what is wrong actualy?its almost done

Pydev Mylyn Integration (0.3.0) requires plug-in "org.eclipse.mylyn (2.0.0.v20070627-1400)", or later version.

oups forgot about that!!!

ok you just need to deselect PyDev-Mylyn from the installation process (it is actually an optional package). You do not need it to use PyDev. It reports an error because the installation requires the Mylyn to be already installed. But this is no big issue. Just deselect it.

---

### Post by abhilashm86 on 2009-01-26
ha ha i had doubted that i needed to re-install!!!!!!!
thanks for support freind:)now installed finally...............

---

### Post by Kilon on 2009-01-26
> **abhilashm86 said:**
> ha ha i had doubted that i needed to re-install!!!!!!!
thanks for support freind:)now installed finally...............

I told you it was easy. Ok now make sure you know where python interpreter is as you will need to know its location for setting up PyDev. Unfortunately I use Jython only and have not set up PyDEv for Python. It should nto be difficult to find though.

---

