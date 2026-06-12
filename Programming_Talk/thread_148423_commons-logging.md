---
title: "commons-logging"
date: 2006-03-22
forum: Programming Talk
---

### Post by edwardaux on 2006-03-22
I have recently migrated from XP to Ubuntu 5.10 (and have been extremely impressed, BTW), but am having some troubles getting my Tomcat 4.1 instance working properly.  When I try to start tomcat (either by using startup.sh or /etc/init.d/tomcat4 start), I get the following error:

[FONT="Courier New"]org.apache.commons.logging.LogConfigurationException: Invalid class loader hierarchy.  You have more than one version of 'org.apache.commons.logging.Log' visible, which is not allowed.
[/FONT]

My webapp has a copy of commons-logging.jar in its /WEB-INF/lib (which as best I can tell, is where that jar is supposed to be), but another version of that jar that seems to be getting picked up is from my /usr/share/java directory.  There are a bunch of other jars in that directory too (such as commons-digester.jar, struts.jar, etc) that seem to be getting added to my Tomcat classpath, and thus screwing it up for my webapp.  The problem is that I don't understand how Tomcat is finding them.  I have grep'd high and low, but can't find anything that references that directory or those files.  

I contemplated just deleting them but, looking at synaptic, it tells me that my tomcat4 package (which I installed using apt-get) is dependant on them.

FWIW, I know that this application works just fine under Redhat, SUSE and Windows, so I suspect that it is just something I have screwed up when installing Tomcat on my local Ubuntu.  Does anyone have any suggestions as to how I can get up and running?

Many thanks.

--
edwardaux

---

### Post by edwardaux on 2006-03-26
Just in case anyone else comes across this problem, I thought I would post how I managed to get up an running.  Unfortunately, I could not find a way to get it working with Tomcat 4.1 - once I uninstalled 4.1, and installed 5.0, things managed to sort itself out.  Who knows why, but there you go...

--
Edwardaux

---

