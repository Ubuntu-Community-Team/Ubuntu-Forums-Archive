---
title: "[SOLVED] frostwire"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Captain Cole on 2008-10-01
I am trying to download frostwire, but every time I try to download it, it wont work.

---

### Post by bubba_169 on 2008-10-01
OK what exactly wont work? You need to help us help you by giving as much detail as possible. How are you trying to download, what happens when you do?

---

### Post by raul_ on 2008-10-01
How are you trying to download it? 

What do you mean with "it won't work" ? The download won't work? Or frostwire?

---

### Post by fooman on 2008-10-01
where are you trying to d/l from?

i just went [[COLOR="Red"]HERE[/COLOR]]("http://www.frostwire.com/?id=downloads") and got it without a problem.

---

### Post by Therion on 2008-10-01
The version in the repo has "issues" with Java; the latest version not so much.

---

### Post by Captain Cole on 2008-10-01
I go to frostwire.com, then go to downloads and click download for Ubuntu. then it says it download finished. I go to applications, internet and there it says it's there but there is no logo beside it.

---

### Post by raul_ on 2008-10-01
Did you run it after downloading it? You don't have to go to frostwire.com (a la Windows)

you can probably install it in "Add/Remove programs" in the "Applications" tab, OR, by opening the package manager (System->Administration->Synaptic) and looking for frostwire, checking the box, and then click on "apply changes"

This is valid for virtually all applications you wish to install in the future

---

### Post by fooman on 2008-10-01
when you d/l-ed it from frostwire,  did you choose to "save file"? ....if not,  then try it again.

it should d/l to your desktop.  it wll be a .deb file....just double click on it to install.

then go to applications > internet > frostwire and see if it works.

you will get an older version from synaptic or add/remove...you get the latest from frostwire.com.

---

### Post by Captain Cole on 2008-10-01
Nether of those ideas worked. any other suggestions.

---

### Post by bubba_169 on 2008-10-01
The no icon thing is just ubuntu need to update its cache and a reboot usually sorts that out. Talking about icons Im assuming there is an entry for frostwire in your [Applications -> internet] menu. If not then you have probably just downloaded it and not installed it. The deb file you download is like an .exe for windows and must be installed before you can use it.

Try opening a terminal, typing 'frostwire' and then pressing enter then copy and paste what appears in the terminal and post it here. This will give us more information about what the problem could be...

---

### Post by Captain Cole on 2008-10-01
Here is what came up when I typed 'Frostwire' in the terminal...

cole@captain-desktop:~$ frostwire
HOSTNAME IS captain-desktop
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
cole@captain-desktop:~$

---

### Post by bubba_169 on 2008-10-01
Right now were getting somewhere, you havn't got java installed. Just open synaptic, search for "java" and install it.

The packages will most likely be called java-common and sun-java-something.

---

### Post by houbysoft.xf.cz on 2008-10-01
Try to do what it tells you to do : upgrade to JRE 1.5.x or newer.

---

### Post by fooman on 2008-10-01
yeah, open synaptic and install sun-java5-jre or sun-java6-jre

---

### Post by Captain Cole on 2008-10-01
There are many 'Java' files... Can you tell which ones I will need ?

Java2html, Javacc, Javacc-doc, java-common, Java-gcj-compat, Java-gcj=compat-dev, Java-gcj-compat-plugin, Java-package, 

Sub-java5-demo, sun=java5-doc. sun-java5-fonts, sun-java5-jdk, sun-java5-jre, sun-java5-plugin, sun-java5-source, sun-java6-bin, sun-java6-demo, sun-java6-doc, sun-java6-fonts, sun-java6-javadb, sun-java6-jdk, sun-java6-jre, sun-java6-plugin, sun-java6-source.

Thanks

---

### Post by Forbees on 2008-10-01
newbie use torrents!!!! :-p

---

### Post by fooman on 2008-10-01
like i said above...install sun-java6-jre

it will most likely install sun-java6-bin, sun-java6-fonts and sun-java6-plugin as dependencies.  that should be all you need.

---

### Post by Captain Cole on 2008-10-01
I am d/l sun-java6-jre.
then i'm going to reboot.

---

### Post by Captain Cole on 2008-10-01
that worked fine... I do have a question about what 'Forbees' said. I've seen the term 'Torrents' used before... What is that & how do you use it ?

---

### Post by lisati on 2008-10-01
> **Captain Cole said:**
> that worked fine... I do have a question about what 'Forbees' said. I've seen the term 'Torrents' used before... What is that & how do you use it ?

It's a method of downloading that amongst other things tries to share the workload by getting the file from multiple sources, rather than just one place.

---

### Post by deLay15 on 2008-10-01
I know this is a very stupid question, but how do you open a terminal?  ;)

---

### Post by fooman on 2008-10-01
not stupid at all.

in the top panel,  go to applications > accessories > terminal

---

### Post by deLay15 on 2008-10-01
mmk, I have 2 problems now, When I tried to open a terminal it would start 
loading on my task bar, then disappear.  And, i was following the steps in other posts to get my frostwire to work, and when I open it it asks to make a shared folder for my music to go into after i dl it.. and an error occurs..   

Frostwire was unable to use the specified folder for saving files please choose a different folder.

FrostWire could not create share folder /home/delay/frostwire/shared, it will not be shared..

---

### Post by bigdee973 on 2008-10-01
just go here and install the deb and you should be good to go
[http://www.frostwire.com/](http://www.frostwire.com/)

but frostwire i believe is the new limewire so you should go to limewire.com and install the deb too from there... but either way they are both simple and easy to install

---

### Post by bigdee973 on 2008-10-01
just go here and install the deb and you should be good to go
[http://www.frostwire.com/](http://www.frostwire.com/)

but frostwire i believe is the new limewire so you should go to limewire.com and install the deb too from there... but either way they are both simple and easy to install 

i would go to limewire though..if you need to install java just go to applications add/remove type in java and install java 6 but Limewire will install it java for you automatically limewire is more in development and for torrents i would go with azureus or transmission

---

### Post by deLay15 on 2008-10-01
it seems I have totaly ruined my laptop.  It won't let me login not even thru failsafe I can only log into failsafe terminal and god knows I have no idea what I'm doin there. (on here on my phone)

It's hard to explain what I did because I don't know all the terminology.  So does anyone know how I can make my laptop let me on my acc. On the regular failsafe not the terminal one? If so then I can fix it.

---

### Post by kseunder84 on 2009-06-18
I cannot get Frostwire to work. I keep getting an error message. I've installed sun java 6 but still will not work. This is what I get from the terminal.

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./looks.jar:./mp3spi.jar:./httpclient-4.0-alpha3.jar:./messages.jar:./httpcore-niossl-4.0-alpha7.jar:./onion-fec.jar:./gettext-commons.jar:./jorbis.jar:./onion-common.jar:./jython.jar:./jaudiotagger.jar:./ProgressTabs.jar:./daap.jar:./tritonus.jar:./jl.jar:./jflac.jar:./foxtrot.jar:./clink.jar:./vorbisspi.jar:./commons-codec-1.3.jar:./guice-1.0.jar:./forms.jar:./aopalliance.jar:./themes.jar:./commons-logging.jar:./FrostWire.jar:./jdic_stub.jar:./jmdns.jar:./icu4j.jar:./httpcore-4.0-beta2.jar:./log4j.jar:./httpcore-nio-4.0-beta2.jar:./lw-all.jar:./junit.jar:./jdic.jar:./jcraft.jar:./jogg.jar
java.lang.ExceptionInInitializerError
    at com.limegroup.gnutella.gui.ResourceManager.setLocaleOptions(Unknown Source)
    at com.limegroup.gnutella.gui.ResourceManager.resetLocaleOptions(Unknown Source)
    at com.limegroup.gnutella.gui.ResourceManager.<clinit>(Unknown Source)
    at com.limegroup.gnutella.gui.GUIMediator.getThemeImage(Unknown Source)
    at com.limegroup.gnutella.gui.LimeJFrame.initialize(Unknown Source)
    at com.limegroup.gnutella.gui.LimeJFrame.<init>(Unknown Source)
    at com.limegroup.gnutella.gui.GUIMediator.<clinit>(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.installResources(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.initialize(Unknown Source)
    at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.util.MissingResourceException: Resource bundle not found
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at com.limegroup.gnutella.gui.I18n.<clinit>(Unknown Source)
    ... 15 more
java.lang.NoClassDefFoundError: Could not initialize class com.limegroup.gnutella.gui.GUIMediator
java.lang.NoClassDefFoundError: Could not initialize class com.limegroup.gnutella.gui.GUIMediator
    at com.limegroup.gnutella.bugs.LocalClientInfo.<init>(Unknown Source)
    at com.limegroup.gnutella.gui.LocalClientInfoFactoryImpl.createLocalClientInfo(Unknown Source)
    at com.limegroup.gnutella.bugs.FatalBugManager.handleFatalBug(Unknown Source)
    at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ExceptionInInitializerError
    at com.limegroup.gnutella.gui.ResourceManager.setLocaleOptions(Unknown Source)
    at com.limegroup.gnutella.gui.ResourceManager.resetLocaleOptions(Unknown Source)
    at com.limegroup.gnutella.gui.ResourceManager.<clinit>(Unknown Source)
    at com.limegroup.gnutella.gui.GUIMediator.getThemeImage(Unknown Source)
    at com.limegroup.gnutella.gui.LimeJFrame.initialize(Unknown Source)
    at com.limegroup.gnutella.gui.LimeJFrame.<init>(Unknown Source)
    at com.limegroup.gnutella.gui.GUIMediator.<clinit>(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.installResources(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.initialize(Unknown Source)
    ... 6 more
Caused by: java.util.MissingResourceException: Resource bundle not found
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at com.limegroup.gnutella.gui.I18n.<clinit>(Unknown Source)
    ... 15 more
Error: FrostWire version 4.17
Java version 1.6.0_0 from Sun Microsystems Inc.
Linux v. 2.6.28-13-generic on i386
Free/total memory: 1579120/5812224

java.lang.NoClassDefFoundError: Could not initialize class com.limegroup.gnutella.gui.GUIMediator
    at com.limegroup.gnutella.bugs.LocalClientInfo.<init>(Unknown Source)
    at com.limegroup.gnutella.gui.LocalClientInfoFactoryImpl.createLocalClientInfo(Unknown Source)
    at com.limegroup.gnutella.bugs.FatalBugManager.handleFatalBug(Unknown Source)
    at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ExceptionInInitializerError
    at com.limegroup.gnutella.gui.ResourceManager.setLocaleOptions(Unknown Source)
    at com.limegroup.gnutella.gui.ResourceManager.resetLocaleOptions(Unknown Source)
    at com.limegroup.gnutella.gui.ResourceManager.<clinit>(Unknown Source)
    at com.limegroup.gnutella.gui.GUIMediator.getThemeImage(Unknown Source)
    at com.limegroup.gnutella.gui.LimeJFrame.initialize(Unknown Source)
    at com.limegroup.gnutella.gui.LimeJFrame.<init>(Unknown Source)
    at com.limegroup.gnutella.gui.GUIMediator.<clinit>(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.installResources(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.initialize(Unknown Source)
    ... 6 more
Caused by: java.util.MissingResourceException: Resource bundle not found
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at com.limegroup.gnutella.gui.I18n.<clinit>(Unknown Source)
    ... 15 more

STARTUP ERROR!




******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu10)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)


Any help please?

---

### Post by Fraser Parlane on 2009-06-21
I have the exact same problem as [kseunder84]("http://ubuntuforums.org/member.php?u=817494"). I miss Frostwire. I've installed Java-common from the synaptic package manager. I've re-installed the frostwire deb package. :confused: Help, anyone?

---

### Post by Darwinfish on 2009-06-21
Ditto on the Java issue.

---

