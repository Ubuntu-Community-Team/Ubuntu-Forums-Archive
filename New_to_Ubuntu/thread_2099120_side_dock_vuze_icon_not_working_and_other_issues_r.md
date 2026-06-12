---
title: "side dock vuze icon not working and other issues relating to ( novice)"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by buntuo on 2012-12-28
came back to my computer this afternoon , and on trying to initialize Vuze by selecting the side dock icon , no responce....

I also have a widget called cairo dock , where I have a bottom dock also with a vuse icon , also non responsive.

Being a complete noob , tried a very simply command line in the terminal start vuze ! lol start wasnt recognized , tried sudo vuze , imputed my password.

So vuze window pops up , but the scrip is also running in the terminal ? Is this normal and acceptable ? when i tried to close the terminal it said , warning will cause script to stop , ie vuze.

Another problem is the file I downloaded is not in its /home folder/ vuze download place ???

on looking at properties of the file whilst still set in vuze , says its in root/vuze downloads folder ?
When I try to go into root its say i dont have permission ? is that right ?

Please any advice on things to try for this complete beginner



thanks in advance !:KS

---

### Post by buntuo on 2012-12-29
anyone !!!

Aww come on , my 1st day here was like wow , 4 responces in 20 mins , my second post Im feeling like Im in a wasteland ? Any advice........

Ive searched other threads , but all seem unique problems to specific versions of os , Im running 12.10 , From what I gather from the script I wrote below is that its still running somehow ??? but clicking the icon still dosent work , removed and re installed through download centre , and still nothing....

And the simple commmmand I put in that started it that last time dosent work now ! I know this is the best way for me to learn linux , but a little help wouldnt hurt please lol

thanks



janos@janos-System-Product-Name:~$ azureus
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.16.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/usr/lib/java/swt-gtk-3.8.0.jar ; file:/home/janos/
StartServer ERROR: unable to bind to a local port listening for passed torrent info: Other instance detected
StartSocket: passing startup args to already-running Azureus java process
janos@janos-System-Product-Name:~$ sudo vuze
[sudo] password for janos: 
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.16.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/usr/lib/java/swt-gtk-3.8.0.jar ; file:/home/janos/
StartServer ERROR: unable to bind to a local port listening for passed torrent info: Other instance detected
StartSocket: passing startup args to already-running Azureus java process

---

### Post by Horrid Troll on 2012-12-29
Hello

I wouldn't run it as root (sudo..)

From the CLI bunf you posted I wonder if its already running in the background. Try

```
killall java
azureus
```

and tell me what happens =)

Edit:

Installed Unity and it looks like Vuze tries to minimise itself to the system tray, but as that doesn't really exist anymore in Unity, it just ends up hidden in the background.  You can just re-enable the system tray with:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

..but this brings it back for all applications and that may not be so great for those applications that work with the launcher properly.

[This](http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html) article shows you how to re-enable the system tray for just single applications..which would seem much more sensible.

---

