---
title: "[SOLVED] azureus appears as 'java' in the list of running processes, can I change thi"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by philphil on 2008-05-08
Hi,

I'm trying to set up a Kcron task (i'm using Gnome so if there are any better solutions please let me know) to run Azureus at 12midnight and to stop it at 6am as I'm having trouble with Internet browsing speed going to practically zero while downloading torrents.  

I start it by calling /usr/bin/azureus but the thing is that when I do a killall on the task at 6am there is no task called Azureus, for some reason the process appears in the list as 'java' so I have to do a /usr/bin/killall java to stop Azureus, which I find a bit weird.  

So my question is: Is there any way of changing the process name of Azureus ? Either when I run it by adding a parameter or in some configuration file or, if it is open source, changing the files and re-compiling it...I'd love to know....

Cheers

---

### Post by wootah on 2008-05-08
Hey Philphil:

> **philphil said:**
> Hi,

I'm trying to set up a Kcron task (i'm using Gnome so if there are any better solutions please let me know) to run Azureus at 12midnight and to stop it at 6am as I'm having trouble with Internet browsing speed going to practically zero while downloading torrents.

May I recommend an easier approach? There is an additional plugin that you may install for Azureus to allow scheduling based on the time and day (much similar to uTorrent's). It's called Speed Schedule. Here is the link: [http://azureus.sourceforge.net/plugin_details.php?plugin=SpeedScheduler]("http://azureus.sourceforge.net/plugin_details.php?plugin=SpeedScheduler")

> **philphil said:**
> 
I start it by calling /usr/bin/azureus but the thing is that when I do a killall on the task at 6am there is no task called Azureus, for some reason the process appears in the list as 'java' so I have to do a /usr/bin/killall java to stop Azureus, which I find a bit weird.


The reason that you find azureus listed as 'java', is because it is a Java based program. From the website ([http://azureus.sourceforge.net/]("http://azureus.sourceforge.net/")):
> 
Azureus implements the BitTorrent protocol using java language and comes bundled with many invaluable features for both beginners and advanced users
Essentially, it is run with the Java runtime engine.

> **philphil said:**
> 
So my question is: Is there any way of changing the process name of Azureus ? Either when I run it by adding a parameter or in some configuration file or, if it is open source, changing the files and re-compiling it...I'd love to know....

Cheers

Hope that helps!

---

### Post by philphil on 2008-05-21
sorry, I forgot to reply...

The bad thing about SpeedScheduler is that you have to have Azureus running to begin with and I don't want it running 24/7.  I only want it to run when I want it to download stuff.

I know it's a java based program but that's no reason for its process name to be java.  It's process name should be the name of the program not the language in which it was written.  Nevermind, it's no major problem, just an annoyance...

I have it working now anyway, the scheduled cron job I made works fine.

---

