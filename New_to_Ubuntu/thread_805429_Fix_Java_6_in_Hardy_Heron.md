---
title: "Fix Java 6 in Hardy Heron"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by y0uiip on 2008-05-23
I am a relative Ubuntu newbie, but felt I should post this as I did not see it on these forums.

I have been having a lot of troubles with Java 6 working in the new Hardy Heron upgrade in Ubuntu.  After trying all the commonly posted workarounds that sadly did not work for me (posted at [http://ubuntuforums.org/archive/index.php/t-621864.html]("http://ubuntuforums.org/archive/index.php/t-621864.html")) **I finally found one that did work for me and wanted to share it!**

I found it at this link: [http://blog.eirikhoem.net/index.php/2008/04/30/firefox-java-problem-with-ubuntu-804-solved/]("http://blog.eirikhoem.net/index.php/2008/04/30/firefox-java-problem-with-ubuntu-804-solved/"), feel free to go there, for I don't know why this fix worked for me.  

**It says to remove the package called icedtea-gcjwebplugin.**  

I easily did this through my synaptic package manager.  It was like magic, it all seems to work!  I tested it using the testing page at java, here is the link: [http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")

I hope this helps someone!

---

### Post by ubuntu-freak on 2008-05-24
Yes, the restricted-extras package installs the IcedTea plugin and OpenJDK Java instead of the Sun Java versions. This is because the OpenJDK/IcedTea browser plugin has both 32/64-bit compatible builds, unlike Sun Java.
 
Overall compatibility isn't yet on-par with Sun Java yet though, so 32-bit users are better off using the Sun Java packages instead.
 
If anyone is still having problems with Java, have a look at my [how-to](http://ubuntuforums.org/showthread.php?t=766683). Part 1 will remove the IcedTea plugin and OpenJDK Java for 32-bit users, and there is a troubleshooting section at the bottom also. 
 
Nathan

---

