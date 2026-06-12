---
title: "Java and Minecraft"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by Elect GMax on 2012-12-03
I installed Oracle Java 7 update 9 successfully (as far as I can tell) on Pangolin. When I set the Minecraft.jar to be run as an executable, Java doesn't show up on the list of programs that I can use to open it. What's the deal?

---

### Post by Paqman on 2012-12-03
What did you do to install Java?

FWIW I find OpenJDK runs Minecraft just fine, and is available in the Software Centre. Mojang do say they only support official Java but it's not actually compulsory to use it to get Minecraft working.

---

### Post by Elect GMax on 2012-12-03
> **Paqman said:**
> What did you do to install Java?


I followed [some online instructions]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux").

Also, if I wanted to purge Oracle Java to clear the way for OpenJDK, how would I do that?

EDIT: The instructions that I followed said that I should get a line saying this:

> **Java HotSpot(TM) Server VM (build 23.1-b03, mixed mode)**

But I get one saying this instead:

> **Java HotSpot(TM) Client VM (build 23.1-b03, mixed mode)**

Is this bad?

---

### Post by Paqman on 2012-12-03
Wow, those are some mighty complicated instructions for something as simple as installing software.

AFAIK there's no real reason to purge one version to install another. If you went to Software Centre, installed OpenJDK and ran the command:
```
sudo update-alternatives --config java
```
The you should be able to pick whichever one was working for you.

---

### Post by Elect GMax on 2012-12-03
Does the Software Center require an active Internet connection? If so, it's not of much use to me.

---

### Post by Paqman on 2012-12-03
To get the packages, yes it does. On Ubuntu the normal way to install software is to pull it down from the online repositories. Do you not have the machine online?

---

### Post by Elect GMax on 2012-12-03
The wireless card is behaving questionably. My only *reliable* way to get things onto the Ubuntu drive is to download them via Windows, then reboot into Ubuntu and transfer them from the Windows drive to the Ubuntu drive.

---

### Post by Paqman on 2012-12-08
So the wifi is working in Windows? Sounds like you've got a bug. Open a thread in the networking section of this forum and you might be able to get some help that will sort that for you?

Even if your wifi is cream crackered you should still be able to plug straight into your router with a cable to get downloads done. Less hassle than doing it via Windows, surely?

---

### Post by [Linuxdave] on 2012-12-08
This is my workaround for the problem of making minecraft work on Linx 10.10.  Much Like the Paqman,  I tried JDK and it worked.  To get JDK in place of Sun Java open a terminal.

From a terminal enter:

```
 sudo synaptic package manager 
```this will open synaptic package manager's User Interface. 

Select the tab on the rightmost side of the window that contains the package and descriptions.  This will highlight all the packages that you have on your machine. Find the ones marked Sun Java.  

if you have a question,  Open the properties of a package, and observe the dependencies.  Mark for removal any Sun-Java packages, and mark for re-installation and JDK packages.  

When you click "apply" from the Synaptic User interface,  return to your terminal.  When the update process is done, Try these codes. 

java is the program code to open a program 
-jar is an argument telling the program what kind of operation to undertake
an the name of the file in my folder where I downloaded the Jar is "minecraft.jar". 

I put them together like this: 

```
 /sampleUser/sampledirectory~$: java -jar minecraft.jar 
```This structure for the argument tells the computer which program to open, which type of task the program should engage in, and where to look for the file to complete that task.  

This process worked well,  and now my minecraft is working, fully updated,  and I"m excited.

---

### Post by Paqman on 2012-12-08
> **'[Linuxdave] said:**
> 
From a terminal enter:

```
 sudo synaptic package manager 
```this will open synaptic package manager's User Interface. 


If you did want to launch Synaptic the correct command would be:
```
gksudo synaptic
```
However, you don't need to use Synaptic, and it's not actually pre-installed on recent versions of Ubuntu. You can get OpenJDK (and Synaptic if you want it) from the Ubuntu Software Centre.

---

