---
title: "Oneiric install - can't access my online banking (Java issue)"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by aquascrotum on 2011-10-23
Upgraded to 11.10 earlier, and am now having problems accessing my banks online system.

The ebanking uses a java setup for its secure login - I've tried using Firefox and Chromium, have also tried installing OpenJDK Java 7 and IcedTea.

I can track where the script goes wrong - see screenshot below from Chromium.

[IMG]http://i636.photobucket.com/albums/uu89/kylesom/ubuntu/EbankingProblem.jpg[/IMG]

I've checked and the problem is not mirrored in Windows - so the problem is at my end, not the banks.

Where do I start to remedy this?  Customer support for my e-banking does not include Ubuntu (surprise surprise).  The system was working fine when I was using 10.04 before the clean install.

---

### Post by ikt on 2011-10-23
Have you tried a fresh install? or try using the live cd to see if it affects just your computer.

I just tried it then in 11.10 with chrome and the login screen loaded ok.

---

### Post by critin on 2011-10-23
Just a suggestion that you've probably already tried.  Make sure Java is enabled in the browser.  Your bank may not work with any browser but Firefox or IE.  Clear the cache and retype the url, being careful that it is correct.  A 404 and Syntax Error makes me think a mistake is in the url. 

I just used 11.10 and firefox to test if I had any problems and it worked smoothly.  I hadn't tried on this os yet.  I haven't changed anything so it worked 'out of the box'.  I'd say the issue is with the browser.

---

### Post by aquascrotum on 2011-10-23
> Have you tried a fresh install? or try using the live cd to see if it affects just your computer.

I just tried it then in 11.10 with chrome and the login screen loaded ok.

This is a fresh clean install, literally a couple of days old.

The bank seems to use a 2-stage login screen.  I do have Flash / Java enabled, and the first stage loads fine (which I presume is what you've replicated).  

After I enter my login credentials (which I can't share on here!), a second stage appears in the Java area - in this stage there is a section where I have to enter a code, however I cant put my cursor in the box.  Am assuming that this is where the error codes start.

There's not even any way of me putting up a screenshot of the 2nd stage without giving away info that I don't want in the public domain.

I've tried on another computer (also Oneiric) which is the same problem, and with a Live CD.  All same problem. Windows works fine with out of date Java and with Java updated.

---

### Post by sadaruwan12 on 2011-10-23
It seems to be like a compatibility issue with the linux platform I use same type of a banking system that works like a charm on a 10.04 and a 11.10.

In your case did the same system worked for you earlier with a linux distribution to be exact with ubuntu.

Oh! and it's not a java issue.

---

### Post by Dry Lips on 2011-10-23
I recommend:

**1.** removing the OpenJDK/IcedTea java and installing Sun Java instead.
(This can be done from the Ubuntu Software Centre) I had the same problem, 
and it seems like some online bank systems simply don't like OpenJDK...

**2.** What you need to do is to open up synaptic, (install it if you haven't got it) 
then make sure you have enabled the independent repositories + Canonical Partners, 
and search for **sun-java6-jre** + **sun-java6-plugin**

**3.** Mark for installation, click apply.

---

### Post by aquascrotum on 2011-10-23
> **sadaruwan12 said:**
> It seems to be like a compatibility issue with the linux platform I use same type of a banking system that works like a charm on a 10.04 and a 11.10.

In your case did the same system worked for you earlier with a linux distribution to be exact with ubuntu.

Oh! and it's not a java issue.

I'd used the banking system on a 10.04 system on the same machine with no problems.  I would have upgraded that system but the upgrade became corrupt, so had to resort to a clean install.

---

### Post by aquascrotum on 2011-10-23
> **Dry Lips said:**
> I recommend:

**1.** removing the OpenJDK/IcedTea java and installing Sun Java instead.
(This can be done from the Ubuntu Software Centre) I had the same problem, 
and it seems like some online bank systems simply don't like OpenJDK...

**2.** What you need to do is to open up synaptic, (install it if you haven't got it) 
then make sure you have enabled the independent repositories + Canonical Partners, 
and search for **sun-java6-jre** + **sun-java6-plugin**

**3.** Mark for installation, click apply.

Can you elaborate which repos I need to add and where to get them/how to add them?

EDIT:  just checked, Java was deleted from the Partners repo for Oneiric?

---

### Post by Dry Lips on 2011-10-23
> **aquascrotum said:**
> Can you elaborate which repos I need to add and where to get them/how to add them?

EDIT:  just checked, Java was deleted from the Partners repo for Oneiric?

I just checked in 11.10, and actually I think you may be right... (11.04 is my main OS at the moment.)
> 
[SIZE=1][COLOR=#000000][SIZE=2]Oracle (Sun) Java Runtime  Environment (JRE) has been removed from the official software  repositories of Ubuntu. In Ubuntu 11.10, it has even disappeared from  the Partner repository[/SIZE]. [/COLOR][/SIZE][http://sites.google.com/site/easylinuxtipsproject/java#TOC-Oracle-Sun-Java:-removed-from-all-r](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Oracle-Sun-Java:-removed-from-all-r)
[http://ubuntuforums.org/showthread.php?t=1855292](http://ubuntuforums.org/showthread.php?t=1855292)
[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

### Post by Dry Lips on 2011-10-25
You asked about a repo for java6 in 11.10... Here goes:

```
sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin
```If you install this you would also have to remove OpenJDK/IcedTea...

---

### Post by beew on 2011-10-25
> **Dry Lips said:**
> You asked about a repo for java6 in 11.10... Here goes:

```
sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin
```If you install this you would also have to remove OpenJDK/IcedTea...

You don't need to uninstall OpenJDK/IceTea, but to make sun-java the default you need to run in the terminal

```
sudo update-java-alternatives -s java-6-sun
```

There may be some occasions that you want to use the OpenJDK, just in case. :)

---

### Post by Dry Lips on 2011-10-25
> **beew said:**
> You don't need to uninstall OpenJDK/IceTea, but to make sun-java the default you need to run in the terminal

```
sudo update-java-alternatives -s java-6-sun
```There may be some occasions that you want to use the OpenJDK, just in case. :)

I didn't know that... Thanks! But what would you do if sun-java6 was the default 
and you wanted to use enable OpenJDK?

---

### Post by aquascrotum on 2011-10-28
Installed Sun Java from the website (6 version 29) as per this instruction

[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

and my problem is solved - so its an OpenJDK issue.

---

