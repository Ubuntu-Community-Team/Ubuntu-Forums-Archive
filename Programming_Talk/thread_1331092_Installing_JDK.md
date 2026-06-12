---
title: "Installing JDK"
date: 2009-11-19
forum: Programming Talk
---

### Post by Abadon125 on 2009-11-19
Sorry if this is a simple question. I am trying to install Eclipse and the JDK on Ubuntu 9.10 and it is much harder than I expected.  

I have Eclipse installed (from Software center) but I can not find any current documentation on installing the JDK.  Can someone please help?  I am new to ubuntu so the simpler the instructions the better.  Thanks so much!

---

### Post by myrtle1908 on 2009-11-19
> **Abadon125 said:**
> Sorry if this is a simple question. I am trying to install Eclipse and the JDK on Ubuntu 9.10 and it is much harder than I expected.  

I have Eclipse installed (from Software center) but I can not find any current documentation on installing the JDK.  Can someone please help?  I am new to ubuntu so the simpler the instructions the better.  Thanks so much!

You can do it easily in the bash shell with apt-get but as you are new to Ubuntu this may be a more comfortable method:-

1. Start the Synaptic Package Manager which should be found in System->Administration->Synaptic Package Manager

2. Type *java6* in the quick search box and press enter.

3. It should find a bunch of 'sun-java6-*' packages.  Tick the ones you want eg. sun-java6-jdk and press the 'Apply' button in the toolbar.

---

### Post by Abadon125 on 2009-11-19
I actually did try that but for some reason keep getting an error.  I posted a screen shot below.

---

### Post by MonoDeem on 2009-11-19
Documents package have been laying broken for *years*. Exclude it from the list and you'll have no errors :)

---

### Post by Abadon125 on 2009-11-19
> **MonoDeem said:**
> Documents package have been laying broken for *years*. Exclude it from the list and you'll have no errors :)

How do I do that?  When I type no it then does something and asks me the question again and I say no again then it quits.  
Thanks again :)

---

### Post by MonoDeem on 2009-11-19
To not to make things too complicated:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts
```
License agreement - [COLOR=Green]Tab + Enter[/COLOR] ..

---

### Post by Abadon125 on 2009-11-19
Sorry this is so difficult.  I got another errors so i followed its instructions and it brought me to the same prompt.  See Screenshot

---

### Post by Abadon125 on 2009-11-19
I believe I got it all installed.  Now if its ok, one more probably very simple question.  Lets say I have a nice little .java file that I wrote.  How do I compile and run it in Ubuntu?

EDIT: I actually was able to figure this one out on my own.  Thanks anyways

---

### Post by itsme33 on 2010-02-07
i am also having problem with installing java-jdk.I've installed several times but i got the same error.i've the screenshot below,somebody help..... I've a project on java to be done..

---

### Post by ashokjbp on 2010-05-23
Hi! I am new to Ubuntu. I installed JDK following this forum. I received the follwowing message. 

Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-jre_6.20dlj-0ubuntu1.9.10_all.deb
 /var/cache/apt/archives/sun-java6-bin_6.20dlj-0ubuntu1.9.10_i386.deb
 /var/cache/apt/archives/sun-java6-jdk_6.20dlj-0ubuntu1.9.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Was my JDK installed properly?

---

