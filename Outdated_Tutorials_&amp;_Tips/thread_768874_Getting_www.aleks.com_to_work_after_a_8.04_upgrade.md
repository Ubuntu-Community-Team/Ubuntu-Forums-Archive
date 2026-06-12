---
title: "Getting www.aleks.com to work after a 8.04 upgrade"
date: 2008-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by NWcustomcode on 2008-04-26
After an upgrade here is how I got [www.aleks.com]("http://www.aleks.com") to work again
[LIST=1]
[*]removed all old add-ons that are not compatible with firefox 3
[*]type locate aleksPack in a shell and remove all occurrences
[*]start the Synaptic Package Manager and remove all openJdk and all java6
[*]Install java5
[*]Download the aleks pack from [http://www.aleks.com/aleks/java/aleksPack10.jar]("http://www.aleks.com/aleks/java/aleksPack10.jar")
[*]copy the newly downloaded file to -> sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/aleksPack10.jar
[/LIST]

Note: If you have a different version of java installed replace the java-6-sun-1.6.0.06 with your version.

You can check your version of java by typing java -version on the command line
Here is my output

name@laptop:~$ java -version
java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)
Java HotSpot(TM) Client VM (build 1.5.0_15-b04, mixed mode, sharing)

Java 5 just seems to work better with aleks than java 6. You sometimes still have to clear you classpath with the java console but everything else seems to work smoothly.

If you are having trouble you can verify you java installation with the following link [http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")

---

### Post by NWcustomcode on 2008-04-26
To solve the problem of being unable to input answers open the java console and clear the classpath by hitting x.

Have fun!!

---

### Post by vitreoushumours on 2008-10-02
I am having a little trouble with Aleks text input, and I am very new to Ubuntu and Linux, Do you mind giving a step by step for opening the Java Console?  :)

---

### Post by NWcustomcode on 2008-10-20
I think you have to have the java console 6.0.02 installed.


[https://addons.mozilla.org/en-US/firefox/search?q=java+console&cat=all](https://addons.mozilla.org/en-US/firefox/search?q=java+console&cat=all)

I have 6.0.02 installed and everything seems to work fine. If you have aleks working then clearing the classloader cache (x) in the java console should fix the input issues.

Let me know how it goes!!!

---

### Post by jamesstansell on 2008-10-21
I hadn't heard of ALEKS before, but I just tried it briefly with the  "streaming" plug-in, for a pre-calculus module, and it seemed to work flawlessly.

This was on Ubuntu 8.04.1 using the Java 6 Update 10 version from the hardy-updates repository.

[http://www.aleks.com/faqs/aleks_plugin#streaming_plugin](http://www.aleks.com/faqs/aleks_plugin#streaming_plugin) means that you don't have to mess with the lib/ext/ folder.

---

### Post by belanger on 2009-02-10
Is Aleks still working for everybody?  I have done everything suggested here, but Aleks still won't work for me.  I was wondering if there could have been upgrades  (either in Aleks or Ubuntu) that prevent it from working.

Thanks,
Jay

---

### Post by belanger on 2009-02-10
I have Aleks running on a different machine, still Ubuntu GNU/Linux.  The one that works is x86, and the one that doesn't is amd64.  I'm guessing that it only works on x86; it'd be nice to hear if that is right.  Does anybody have Aleks running on 64 bits?

Jay

---

