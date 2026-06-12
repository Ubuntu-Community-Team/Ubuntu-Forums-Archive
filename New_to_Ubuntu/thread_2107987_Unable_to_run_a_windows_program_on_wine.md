---
title: "Unable to run a windows program on wine"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by nooblinux007 on 2013-01-23
Hi all

 I have an exe program that's based on java ---said to be cross platform enabled.  

This exe program runs well on windows.  I have tried numerous times to install it via wine on ubuntu--latest attempt being on 12.04 lts 64 bit, but it always returns an error 'Launch 4J--Can't find Java 1.5.0'.  I have installed oracle java using terminal command i found on net that went something like sudo apt-get install ......  

How can i make this program install ?

Any help is appreciated.

Thanks in advance.

---

### Post by arpanaut on 2013-01-23
I don't know for sure, but from a cursory search about this ,
I think that you need to install the Windows version of Java within wine.

But like I said I don't know, Never tried, I just use wine for Netflix.

---

### Post by mikewhatever on 2013-01-23
What do you mean by "said to be cross platform enabled"? Who said that?

---

### Post by jbcohen on 2013-01-23
I too am trying to get Wine to run some windows software for me from within Ubuntu.  The only thing that I have been able to figure out is that I need to run wine from the prompt.  I installed it from the software center and I have been unable to wine the external command to invoke the software.  I might be very confused here but that is far  as I have been able to figure out.  I do understand that I need to install Java from within Windows however in order to accomplish that I need wine to give me the windows desktop.

---

### Post by na5h on 2013-01-23
It would help if you would tell us what program you are trying to install.

If the application is truly "cross-platform", then there should be no need to use Wine. Are you sure you downloaded the correct version of the program?

If it is a Windows application, then you should check the [Wine application database]("http://appdb.winehq.org/") about compatibility.

---

