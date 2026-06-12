---
title: "Open Office Crashes"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by yo_pandabear on 2008-06-08
After several weeks of light use of Open Office Word Processor, it now crashes.  I found several others have had this same problem, however there were no real fixes only suggestions to load another word processor.

Since I am a newbie trying to migrate from XP to Ubuntu, I am sure there is a fix for it.



"If man made it; man can fix it."

---

### Post by SunnyRabbiera on 2008-06-08
It might be java related, I know I had issues with it when I used the default java preinstalled with hardy.
Did you try to enable extra repositories and install the normal java?
and do you use a 64bit kernel?

---

### Post by xravexheavenx on 2008-06-08
sudo apt-get remove openoffice.org
sudo apt-get install openoffice.org

Could just be something happened during an update.

---

### Post by SunnyRabbiera on 2008-06-08
> **xravexheavenx said:**
> sudo apt-get remove openoffice.org
sudo apt-get install openoffice.org

Could just be something happened during an update.

thats possible too

---

### Post by xravexheavenx on 2008-06-08
> **SunnyRabbiera said:**
> It might be java related, I know I had issues with it when I used the default java preinstalled with hardy.
Did you try to enable extra repositories and install the normal java?
and do you use a 64bit kernel?

We all do love java don't we...

*sigh*

---

### Post by SunnyRabbiera on 2008-06-08
> **xravexheavenx said:**
> We all do love java don't we...

*sigh*

Java is win some loose some, thank goodness sun is making it open source.

---

### Post by xravexheavenx on 2008-06-08
> **SunnyRabbiera said:**
> Java is win some loose some, thank goodness sun is making it open source.


Indeed.  May save us all some stress.

---

### Post by yo_pandabear on 2008-06-08
> **SunnyRabbiera said:**
> It might be java related, I know I had issues with it when I used the default java preinstalled with hardy.
Did you try to enable extra repositories and install the normal java?
and do you use a 64bit kernel?

I thought I loaded every thing required.  I would think I use the 32 bit kernel since this is on an old Dell GX 270 with 1+ gb memory.  I am doing a trial setup on an old IDE 15 gb HD mounted in a removable HD tray.  I also have a 250 gb HD I want to use but I have not got the partitioning down yet.  I did the following partition.

12 gb ext3 for OS
4 gb swap
194 gb file ext3
40 gb  ext3 reserve space for Clonezilla & other backups

The problem is the OS is on the 40 gb part.

Thanks for the help.

---

### Post by SunnyRabbiera on 2008-06-08
Hmm, well in synaptic tell me what version of java you have installed... you know how to use it right?

---

### Post by yo_pandabear on 2008-06-08
I am looking for the Java 32, however I did not install Open Office.  It was included with the live CD.

---

### Post by SunnyRabbiera on 2008-06-08
yeh open office is pre installed.
but I found out that if you replace OpenJDK with normal java it helps big time

---

### Post by yo_pandabear on 2008-06-09
I am looking for Open JDK now.  What is Open JDK?  There must be a zillion.  How do I know which to load?

Any ideas on the partition or site where I can get info?

thanks again

---

### Post by SunnyRabbiera on 2008-06-09
Open jdk is the current open source version of java, all that is linked to it must be removed before trying regular java.
when searching for open JDK remove its packages, after that we will cover how to install regular java via synaptic.

---

### Post by rockerphil on 2008-06-09
as stated before be sure to remove open JDK first. then to install regular Java run this in the terminal (i'm not too great with Synaptic. i live in the terminal)

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

then completely uninstall Open Office


sudo apt-get remove --purge openoffice.org


then reinstall Open Office


sudo apt-get install openoffice.org


hope this helps

---

### Post by yo_pandabear on 2008-06-09
Thanks, it will be next week or so before I can try this out.  We are leaving for a vacation today.

---

### Post by yo_pandabear on 2008-06-18
> **xravexheavenx said:**
> sudo apt-get remove openoffice.org
sudo apt-get install openoffice.org

Could just be something happened during an update.

I ran above command.  Open Office will not load or loads so fast and closes I can not tell it is loading.  I now can not use synaptic.  I get the message below.  What now?

Failed to run /usr/sbin/synaptic as user root.
Unable to copy the user's Xauthorization file.

Thanks.

---

