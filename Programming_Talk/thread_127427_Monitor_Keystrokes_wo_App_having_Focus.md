---
title: "Monitor Keystrokes w/o App having Focus"
date: 2006-02-08
forum: Programming Talk
---

### Post by SSTwinrova on 2006-02-08
First off, as much as this sounds like it, I'm not trying to make a keylogger (although I bet the underlying concepts are pretty similar). One of my friends asked me if I could write a program that when started would just live in the system tray as an icon and allow for the following functionality:

1. Detects whenever a specified hotkey is pressed (for example, Print Screen)
2. Takes a screen capture of whatever happens to be up on the screen (I believe he wants to primarily use this for games like WoW, CS, etc.)
3. Connects to a specified FTP server and uploads the just captured image
4. (Optional) Sets the system clipboard to the URL of the uploaded picture (otherwise, he could settle for just having a log available with the last 5 URLs or so)

Now, I've had the most experience with Java, so I started looking there. I was able to find classes that would be able to handle everything except the hotkey because the application will not have focus while it needs to be listening (and as an aside, it shouldn't steal focus either). So, I'm curious if anyone has some language suggestions for the easiest way of implementing this (and preferably some sample code for me to look at). Granted, he uses XP, (therefore I can't use anything that would be Ubuntu/Linux specific), so a solution that would be as cross-platform as possible would be the best. That way, I can not only write the program for him, but also provide a small program to the Ubuntu community which maybe at least a few people might find useful.  :cool: 

Thanks for any help you can offer.

---

### Post by SSTwinrova on 2006-02-15
Well, here's where I am now:

Apparently Java can't interface at that low of a level with the OS natively, so it was either create a JNI wrapper or switch languages. Wasn't a hard chioce to start looking at .NET languages, and I settled on J#. Windows has a nick RegisterHotKey function that does pretty much exactly what I need, but that keeps it from having any hope of being cross-platform with Mono (that function is in a DLL and not part of the .NET framework). So unless someone can point me to a good resource where I might be able to find something similar in Linux, probably not going to be able to make it work on Ubuntu  :(

---

