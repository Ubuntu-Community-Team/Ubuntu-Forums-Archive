---
title: "[SOLVED] Assitance making a custom launcher"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by evilkastel on 2008-10-16
Since I had such a good experience with the help here, I'm going to ask for help (because I am such a total noob). I downloaded FreeRapid Downloader, with no problems. But I want to add a launcher in my panel, so... the thing is, the way to open the FRD is, right click, Open with Java 6 Runtime... how do I make the laucher to use java? bacause if I dont, It won't run... I guess is something with -jar... but i won't know how to make it work. the file is frd.jar, as in /home/david/.frd/FreeRapid-0.65/frd.jar
Ok, thankx already for the help!

---

### Post by fooman on 2008-10-16
right click on the .jar file and choose "properties".  click the "open with" tab then add (if its not there already) sun java 6 runtime to the list and put a check next to it.  then click the "permissions" tab and put a check next to "allow executing file as program".

after that you should be able to add a workable launcher to your menu or panel.

---

### Post by evilkastel on 2008-10-17
Well, I did what you said and worked just fine, but list night i reinstalled ubuntu to make it my primary OS and now the launcher won't work no matter what I do. If I start the .jar in the folder, it runs nicely, but If i intend to make a launcher, it won't start. Is "permitted" to run as an application, and also is defaulted to run with Java RTE 6. Help pleasee!

Edit: I solved it myself. i decided to try running 
```
java -jar home/localusr/.frd/frd.jar
``` in terminal to see if this launched the app, and since it surprisely did, I put that in the path of the launcher. Worked like magic.:)

---

