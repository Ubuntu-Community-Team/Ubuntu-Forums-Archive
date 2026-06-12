---
title: "[SOLVED] Installing jHeidi (Java program)"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by TRiG_Ireland on 2008-08-17
In Widows, I'm used to using HeidiSQL for managing SQL databases. I was trying to find an equivalent to use in Ubuntu, and came accross jHeidi, a platform-independent program which runs in Java. Apparently.

I have installed Java (Sun Java 6 Runtime), and have downloaded the jHeidi bin file ([http://www.heidisql.com/jheidi/](http://www.heidisql.com/jheidi/)). Now what?

TRiG.:confused:

---

### Post by y-lee on 2008-08-17
Extract the jheidi-alpha-bin.zip archive someplace like your home folder, and then open a terminal cd into the folder you created. If you extracted it in your home directory

```
cd jheidi-alpha-bin/
```

 and run

```
./jheidi
```.

hope this helps and btw I have never used the program just downloaded it and look thru the zip file. good luck.

---

### Post by TRiG_Ireland on 2008-08-18
Thanks. Now working.

---

### Post by glitterball on 2008-10-16
How do I add jHeidi to the main menu?

---

### Post by TRiG_Ireland on 2008-11-06
I've downloaded the latest version of jHeidi (apparently I won't have to do this again, as it has an inbuilt updater from now on).

But it won't run. I get the response "bash: ./jheidi: Permission denied"

Any clever ideas? Bear in mind that I'm still a neonate. I've been using Ubuntu for a bit, but I've not yet had time to do any proper experimenting with it.

TRiG.

---

### Post by y-lee on 2008-11-06
> I get the response "bash: ./jheidi: Permission denied"


Do you have permission to run the file? An easy way to check is to right click jheidi in your file manager and chose properties, click on the permissions tab, is execute checked for owner? if not check it also of course be sure read is checked for owner.

---

### Post by TRiG_Ireland on 2008-11-06
Well, something's happening now, anyway. But it's still not actually working.

The file runs, but I get the error message

```
Exception in thread "AWT-EventQueue-0" java.lang.RuntimeException: Cant load AutoUpdater:AppProps!
```

I imagine that this is a Java problem or a specific jHeidi problem, rather than a TRiG not understanding Linux problem. Perhaps I should try downloading an earlier version of jHeidi.

TRiG.

---

### Post by TRiG_Ireland on 2008-11-06
> **TRiG_Ireland said:**
> Well, something's happening now, anyway. But it's still not actually working.

The file runs, but I get the error message

```
Exception in thread "AWT-EventQueue-0" java.lang.RuntimeException: Cant load AutoUpdater:AppProps!
```

I imagine that this is a Java problem or a specific jHeidi problem, rather than a TRiG not understanding Linux problem. Perhaps I should try downloading an earlier version of jHeidi.

TRiG.That wasn't very clear. I'll try explaining myself again. I set the permissions, to allow myself to execute the file (hadn't thought of that at all; thanks!). And now, when I run the file from the terminal, I get a very long error message, of which the above is the first line.

And older versions of jHeidi do not appear to be available for download. Argh! I could do with Heidi running natively in Linux, instead of through Java. That would probably be simpler.

I've downloaded a bunch of other SQL editors, but none work as simply or intuitively as Heidi.

TRiG.

---

### Post by y-lee on 2008-11-06
What version of Java are you using?

```
java -version
```

---

### Post by TRiG_Ireland on 2008-11-06
version "1.6.0_07"

build 1.6.0_07-b06



I've tried chmoding (is that a word?) the entire folder to 777, instead of just the jheidi file itself, but this has made no difference. I'm now trying to sign up to the Heidi forums, to see whether they know what's going on.

(As a by-the-way, is there any way of taking the "solved" tag off a conversation?)

TRiG.:)

---

### Post by y-lee on 2008-11-06
I am not at sure if it will help but you seem to be missing Javas Runtime Environment

```
sudo apt-get install sun-java6-jre 
```

Edit. And btw I am not sure if you can mark a thread as unsolved after it has changed to solved. If it is not in the thread tools probably you can't.

---

### Post by jamesstansell on 2008-11-06
> **y-lee said:**
> I am not at sure if it will help but you seem to be missing Javas Runtime Environment

It looks to me like TRiG has the java runtime, but that part of heidi isn't loading properly.

TRiG, this probably won't make a difference, but it's worth a try.

```

$ sudo update-java-alternatives -s java-6-sun

```

---

### Post by TRiG_Ireland on 2008-11-06
> **y-lee said:**
> I am not at sure if it will help but you seem to be missing Javas Runtime Environment

No. That's not it. This is the full response I get when I check for the Java version.

```

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

```

I'll try not to abbreviate in future, but I don't know how to copy responses from the terminal. I have to rewrite them by hand. (I am a novice, aren't I?)

TRiG.:)

---

### Post by Buzzdee on 2008-11-06
can't help you with your actual problem, but try marking the text in the terminal, right click and select 'copy', then later 'paste' it with a right-click where you want

---

### Post by TRiG_Ireland on 2008-11-06
> **Buzzdee said:**
> can't help you with your actual problem, but try marking the text in the terminal, right click and select 'copy', then later 'paste' it with a right-click where you want
Ah, once again Ubuntu shows its strange habit of not being keyboard-friendly. You cannot highlight with the keyboard, and pressing Ctrl+C on highlighted text achieves nothing in the Terminal, though it works fine for me here in Firefox.

On Windows, I took great pride in avoiding the mouse, but it seems a lot more difficult to do in Ubuntu. I'm sure there are keyboard shortcuts for all sorts of things, but they're not made obvious.

TRiG.:)

---

### Post by jamesstansell on 2008-11-06
> **TRiG_Ireland said:**
> Ah, once again Ubuntu shows its strange habit of not being keyboard-friendly. You cannot highlight with the keyboard, and pressing Ctrl+C on highlighted text achieves nothing in the Terminal, though it works fine for me here in Firefox.

On Windows, I took great pride in avoiding the mouse, but it seems a lot more difficult to do in Ubuntu. I'm sure there are keyboard shortcuts for all sorts of things, but they're not made obvious.

TRiG.:)

Are any keyboard shortcuts obvious before you've learned them?

Windows and Linux keyboard shortcuts largely overlap, but of course there are differences.  In the Linux terminal ctrl-c has historically been used to send an interrupt, so by default the mapping is ctrl-shift-c.  Likewise for paste ctrl-v has a historical meaning so ctrl-shift-v is used.

Or, if if you're just pasting to another (or even the same) terminal, no copy is needed.  Highlight the text you want, then on the target terminal (get focus if you don't have it already) hit shift-insert.  Voila!

-james.

---

### Post by jamesstansell on 2008-11-06
I gave it a try and it seemed to work for me.  (All I did was exit from the connect screen, since I don't have a mySQL server handy.)

$ ./jheidi

configuring logging from system property log4jconfig=logs/log4jconfig.xml

app=jHeidi
version=Alpha 3 Update 5
timestamp=20081002000000
url=http://heidisql.com/jheidi/files/autoupdater/bin/jheidi-bin-autoupdater
processKey=jheidi
libPath=lib
propPath=.
releaseNotes=jHeidi Alpha 3 Update 5 Release Notes
=====================================

Change log:
change highlite color
fix search text on windows
dont use cache for some queries
fix refresh
make refresh worker aware
use non-cached data for dialogs
cache enhancements
remove unused script
flush show tables from cache on create
flush show databases from cache on create
add ability to flush individual results
enable drop table and drop db on selection only
exclude user queries from caching
make refresh button flush DB cache
fix cache flush
turn on DB result cache
make user queries asynch
fix handling of multiple overlapping tasks
fix startup state of toolbar buttons
update ajl jar 
enable/disable table toolbar buttons
cleanup classes dir when building libs
get rid of clone use copy constructor
fix insets issue
handle when the worker is cancelled vs done
make show table status asynch
add generic progress indicator to status bar






jar=autoupdater.jar

------

Note, this is Ubuntu 8.10 (Intreped) using the 6u10 version of sun-java6:

$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)

---

### Post by TRiG_Ireland on 2008-11-07
```

$ cd sql
$ ./jheidi

```

```

configuring logging from system property log4jconfig=logs/log4jconfig.xml

Exception in thread "AWT-EventQueue-0" java.lang.RuntimeException: Cant load AutoUpdater:AppProps!
	at com.rendion.ajl.AutoUpdater$AppProps.<init>(Unknown Source)
	at com.rendion.ajl.AutoUpdater.<init>(Unknown Source)
	at jheidi.run(jheidi.java:19)
	at com.rendion.ajl.AjlScript.run(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.rendion.ajl.Loader.run(Unknown Source)
	at com.rendion.ajl.Loader.runScript(Unknown Source)
	at com.rendion.ajl.Loader.runScript(Unknown Source)
	at com.rendion.ajl.ScriptHelper.script(Unknown Source)
	at com.rendion.ajl.AjlScript$1.run(Unknown Source)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Caused by: java.io.FileNotFoundException: .autoupdater (No such file or directory)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:106)
	at java.io.FileInputStream.<init>(FileInputStream.java:66)
	... 21 more



```

I'll try doing the simple thing: I'll delete it and download it again in case I have a corrupt version. (Though I have already tried that once.)

TRiG.:)

---

### Post by freshinstall on 2008-11-07
> **TRiG_Ireland said:**
> ```

$ cd sql
$ ./jheidi

```

```

configuring logging from system property log4jconfig=logs/log4jconfig.xml

Exception in thread "AWT-EventQueue-0" java.lang.RuntimeException: Cant load AutoUpdater:AppProps!
	at com.rendion.ajl.AutoUpdater$AppProps.<init>(Unknown Source)
	at com.rendion.ajl.AutoUpdater.<init>(Unknown Source)
	at jheidi.run(jheidi.java:19)
	at com.rendion.ajl.AjlScript.run(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.rendion.ajl.Loader.run(Unknown Source)
	at com.rendion.ajl.Loader.runScript(Unknown Source)
	at com.rendion.ajl.Loader.runScript(Unknown Source)
	at com.rendion.ajl.ScriptHelper.script(Unknown Source)
	at com.rendion.ajl.AjlScript$1.run(Unknown Source)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Caused by: java.io.FileNotFoundException: .autoupdater (No such file or directory)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:106)
	at java.io.FileInputStream.<init>(FileInputStream.java:66)
	... 21 more



```

I'll try doing the simple thing: I'll delete it and download it again in case I have a corrupt version. (Though I have already tried that once.)

TRiG.:)

Trig, from the directory sql I can see you have relocated the files, the problem is that when you copied the files you did not have "show hidden files" enabled in Nautilus and you did not pick up all the files.

---

### Post by TRiG_Ireland on 2008-11-08
> **freshinstall said:**
> Trig, from the directory sql I can see you have relocated the files, the problem is that when you copied the files you did not have "show hidden files" enabled in Nautilus and you did not pick up all the files.That would explain a lot. Me idiot. The first time I installed jHeidi I renamed the folder, but this time I was moving the files. The difference hadn't occurred to me.

I got it working last night merely by not bothering to move the files. I'll move them now, carefully, and see if it still works.

The updated version doesn't seem much different to the previous version, but apparently it does contain an autoupdater, so I'll get the updates without difficulty from now on.

Thanks all!

TRiG.[IMG]http://www.bbc.co.uk/h2g2/skins/Alabaster/images/Smilies/f_doh.gif[/IMG]

---

### Post by bwoodward on 2009-03-12
Sorry if this is resurecting a dead thread, but I noticed that some other people were asking about adding this to the Menu too.

jHeidi runs fine from the command line for me

Launcher Properties 
Type: Tried both Application and Application in Terminal
Name: Heidi
Command: /home/[username]/apps/jheidi-bin/jheidi
Comment: Heidi

I select the menu item and nothing happens. If I am an Application in Terminal, then I see about 4 lines for a fraction of a second and then the terminal window closes.

I know running it from the Menu is just a cherry on top, but does anyone have any ideas?

Many thanks, Ben

---

### Post by Tom_T on 2009-04-21
I'd like to know the answer to this...

How to get jheidi working from a launcher ??

Thanks :)

---

### Post by mezzovento on 2009-10-29
> **Tom_T said:**
> I'd like to know the answer to this...

How to get jheidi working from a launcher ??

Thanks :)

Modify your jheidi.sh script in this way:

[COLOR=Blue][B]
[FONT=Courier New]#!/bin/bash

BASEDIR=`dirname $0`
cd $BASEDIR

CLASSPATH=$BASEDIR

CLASSPATH=$CLASSPATH:$BASEDIR/lib/ajl.jar
CLASSPATH=$CLASSPATH:$BASEDIR/lib/drizzle-jdbc-0.1.jar
CLASSPATH=$CLASSPATH:$BASEDIR/lib/editor.jar
CLASSPATH=$CLASSPATH:$BASEDIR/lib/libquaqua.jnilib
CLASSPATH=$CLASSPATH:$BASEDIR/lib/log4j-1.2.13.jar
CLASSPATH=$CLASSPATH:$BASEDIR/lib/mysql-connector-java-5.0.7-bin.jar
CLASSPATH=$CLASSPATH:$BASEDIR/lib/ojdbc14.jar
CLASSPATH=$CLASSPATH:$BASEDIR/lib/quaqua.jar
CLASSPATH=$CLASSPATH:$BASEDIR/lib/slf4j-api-1.5.6.jar
CLASSPATH=$CLASSPATH:$BASEDIR/lib/slf4j-nop-1.5.6.jar
CLASSPATH=$CLASSPATH:$BASEDIR/lib/swing-worker-1.1.jar

java -DstartEDT=true -DusePrecompiledClassFiles=true -cp jheidi.jar:lib/ajl.jar:lib/swing-worker-1.1.jar:lib/editor.jar:lib/drizzle-jdbc-0.1.jar:lib/slf4j-api-1.5.6.jar:lib/slf4j-nop-1.5.6.jar:lib/ojdbc14.jar:lib/mysql-connector-java-5.0.7-bin.jar:lib/log4j-1.2.13.jar -Dlog4jconfig=logs/log4jconfig.xml com.rendion.ajl.AjlScript jheidi[/FONT][/B][/COLOR] 


Then add a launcher in you menu...

---

