---
title: "How to convert .bat-syntax to .sh-syntax?"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by kramer65 on 2011-09-20
Hello,

I've been using Ubuntu for years now, and I love it. I now have a [small java application]("http://sourceforge.net/projects/ibcontroller/") which is supposedly cross-platform. I need to edit a file (.bat) which should start the application. In the readme of the program it says "*Linux users should have no difficulty adapting the sample command files to the appropriate command syntax.*". Apparently people still think that all Linux users are hardcore hackers.. :(

I do know a little bit about Linux though :P. As far as I know I should convert the .bat file to an .sh file. So I simply changed the extension of the file to .sh . This didn't help, since the command line tells me that the file contains all kinds of things that it doesn't know, like "*:::*", and "*Syntax error near unexpected symbol '('*".

Could anyone help me with some tips to convert the following lines to Linux-compatible syntax?
```
set IBCDIR=/home/kram/IBController/
set TWSCP=jts.jar;hsqldb.jar;jcommon-1.0.12.jar;jfreechart-1.0.9.jar;jhall.jar;other.jar;rss.jar
set JAVAOPTS=-Dsun.java2d.noddraw=true -Xmx512M -XX:MaxPermSize=128M
pushd %TWSDIR%
java.exe -cp  %TWSCP%;%IBCDIR%\IBController.jar %JAVAOPTS% ibcontroller.IBController %IBCINI% %TWSUSERID% %TWSPASSWORD%
popd
```

All tips, hints and lessons are welcome!

---

### Post by Azdour on 2011-09-21
Hi,

Here's my initial go at the conversion:

```
set IBCDIR=/home/kram/IBController/
set TWSCP="jts.jar:hsqldb.jar:jcommon-1.0.12.jar:jfreechart-1.0.9.jar:jhall.jar:other.jar:rss.jar"
set JAVAOPTS=-Dsun.java2d.noddraw=true -Xmx512M -XX:MaxPermSize=128M
pushd $TWSDIR
java -cp  $TWSCP:$IBCDIR/IBController.jar $JAVAOPTS ibcontroller.IBController $IBCINI $TWSUSERID $TWSPASSWORD
popd
```

The path separator under Linux is the ':' character and variables in the script change from %TWSCP% to $TWSCP

---

### Post by mcduck on 2011-09-21
Something like this, perhaps:
```
#!/bin/bash

IBCDIR="/home/kram/IBController"
TWSCP="jts.jar:hsqldb.jar:jcommon-1.0.12.jar:jfreechart-1.0.9.jar:jhall.jar:other.jar:rss.jar"
JAVAOPTS="-Dsun.java2d.noddraw=true -Xmx512M -XX:MaxPermSize=128M"

pushd "$TWSDIR"
java -cp  "$TWSCP":"$IBCDIR"/IBController.jar "$JAVAOPTS" ibcontroller.IBController "$IBCINI" "$TWSUSERID" "$TWSPASSWORD"
popd
```

...however the script seems to contain a couple of variables that are not defined in the script ($TWSDIR, $IBCINI, $TWSUSERID and $TWSPASSWORD). Make sure they are defined and properly exported *somewhere*. :)

---

### Post by kramer65 on 2011-09-22
> **mcduck said:**
> 
...however the script seems to contain a couple of variables that are not defined in the script ($TWSDIR, $IBCINI, $TWSUSERID and $TWSPASSWORD). Make sure they are defined and properly exported *somewhere*. :)


That's true. I took a couple variables out since I presumed that once I knew how to set variables correctly I could just replicate the trick to all the variables. So that's what I did.

Thanks to you guys I get a bit further now (seriously, thank you!! :D). The program seems to do something, but then I get the following:

```
09:09:29:191 IBController: ini file is /home/kram/GT/IBControllerV2-9-0/IBController.kram.ini
09:09:29:196 IBController: IBControllerServer is started.
09:09:29:205 IBController: IBControllerServer listening on address: kram-desktop/127.0.1.1 port: 7462
Exception in thread "main" java.lang.NoClassDefFoundError: jclient/LoginFrame
	at ibcontroller.IBController.startTws(IBController.java:418)
	at ibcontroller.IBController.startTwsOrGateway(IBController.java:425)
	at ibcontroller.IBController.load(IBController.java:188)
	at ibcontroller.IBController.main(IBController.java:168)
Caused by: java.lang.ClassNotFoundException: jclient.LoginFrame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 4 more
```

I guess this is beyond your knowledge, since it concerns the contents of the program specifically. But if you have any clue of what I can do I would be very very grateful!

---

### Post by kramer65 on 2011-09-22
NEVERMIND!!

I forgot two times to remove the "SET" before the variables. I removed them and it all works like a charm now. From now on I can sit back, relax and let my computer trade when I'm on holiday. (which means I'm probably broke once I get home.. but whatever.. :-)  )

---

### Post by draculaxxx on 2012-04-08
I made the changes requested to the script, but I am only able to start TWS running it as a super user: $ sudo ./starttws.sh
When it comes to scheduling it in cron it just doesn't start up which makes me think I should set up some environment variables to make it work.  Can you please let me know what's your crontab line?

---

