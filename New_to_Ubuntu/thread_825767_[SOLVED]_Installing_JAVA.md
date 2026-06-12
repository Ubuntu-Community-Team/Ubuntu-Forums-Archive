---
title: "[SOLVED] Installing JAVA"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Ryan_A on 2008-06-11
I have just installed Ubuntu 8.04 and figured out how to install vmware tools and adjust the basic settings such as resolution.  Now I am trying to login to a web site that requires Java but I am having no luck at all.  I downloaded jre-6u6-linux-i586.bin from Java's website and was able to run the install with the command line and everything appeared to run ok.  But when I goto [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) to verify java is installedit says it is not.  the page I am trying to get to also says I do not have have java.  I have also tried to load java through Synaptic Package Manager and still nothing.

Any Thoughts?

---

### Post by Inxsible on 2008-06-11
> **Ryan_A said:**
> I have just installed Ubuntu 8.04 and figured out how to install vmware tools and adjust the basic settings such as resolution.  Now I am trying to login to a web site that requires Java but I am having no luck at all.  I downloaded jre-6u6-linux-i586.bin from Java's website and was able to run the install with the command line and everything appeared to run ok.  But when I goto [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) to verify java is installedit says it is not.  the page I am trying to get to also says I do not have have java.  I have also tried to load java through Synaptic Package Manager and still nothing.

Any Thoughts?Why would you go thru the trouble of manually installing the jre from a bin file, when the same version is also in the repos?
You can try installing java from the repo```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
```and see if that works for you. The plugin is actually for the browsers which enabled Java content in the browser

---

### Post by Ryan_A on 2008-06-11
> **Inxsible said:**
> Why would you go thru the trouble of manually installing the jre from a bin file, when the same version is also in the repos?
You can try installing java from the repo```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
```and see if that works for you. The plugin is actually for the browsers which enabled Java content in the browser

I had not learned of the repositories untill after the failure of the install through the command window.  Searches on forums lead me to the Synaptic package manager.  I am a windows admin and just installed ubuntu yesterday for the first time.  My goal over the summer is to learn as much as possible and see how much of my day to day task I can do not being on windows.  Getting vmware tools and the citrix client installed yesterday went well but java isnt going as easily as the other two.  I ran that code and returns:

sudo: aptitude: command not found

---

### Post by Inxsible on 2008-06-11
> **Ryan_A said:**
> I had not learned of the repositories untill after the failure of the install through the command window.  Searches on forums lead me to the Synaptic package manager.  I am a windows admin and just installed ubuntu yesterday for the first time.  My goal over the summer is to learn as much as possible and see how much of my day to day task I can do not being on windows.  Getting vmware tools and the citrix client installed yesterday went well but java isnt going as easily as the other two.  I ran that code and returns:

sudo: aptitude: command not foundNow that is strange ! 
What version of Ubuntu did you install ? aptitude should be there by default.

---

### Post by Ryan_A on 2008-06-11
8.04

---

### Post by prostar on 2008-06-11
I believe the default command for installing should be "apt-get" not "aptitude".  You can install aptitude if you want a text/graphic UI.

---

### Post by Inxsible on 2008-06-11
> **prostar said:**
> I believe the default command for installing should be "apt-get" not "aptitude".  You can install aptitude if you want a text/graphic UI.If you install ubuntu 8.04, you get apt-get and aptitude both !

---

### Post by jamesstansell on 2008-06-12
> **Ryan_A said:**
> Searches on forums lead me to the Synaptic package manager.  I am a windows admin and just installed ubuntu yesterday for the first time.  My goal over the summer is to learn as much as possible and see how much of my day to day task I can do not being on windows.  Getting vmware tools and the citrix client installed yesterday went well but java isnt going as easily as the other two.

Hi Ryan,

You certainly should install the sun-java6-plugin package.  Either synaptic or the Add/Remove tool should work for you.

Please let us know if you continue to have problems.

-james.

---

### Post by josuan on 2008-06-12
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Paqman on 2008-06-12
Put this into a terminal:
```

sudo dpkg --configure -a

```

---

### Post by Ryan_A on 2008-06-12
IT WORKED!!!!


Once I ran the dpkg command then went into Synaptic it said I had a broken install then removed a java install.  Then I searched for sun-java6-plugin and let synaptic handle the install and everything worked great.

Thanks for everyones help

jamesstansell I see your from Broken Arrow.  I grew up there graduated BAHS in 1995.  Small world

Thanks again

Ryan

---

