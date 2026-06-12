---
title: "[Java] Trying to Get Original Source Code From a Decompiled File"
date: 2010-01-18
forum: Programming Talk
---

### Post by user1397 on 2010-01-18
Attached is the source code of a simple yet fun little game called World Cup Soccer Slime.  (Link to play it [here]("http://homepage.ntlworld.com/bartle/soccer/"))

I made the html file, and I retrieved the .class file from a website that was hosting the game.

The .java file was lost in the wilds of the internet, until in another [thread]("http://ubuntuforums.org/showthread.php?t=1351645") I made, someone found it on a random chinese (I think) website.

Yet this .java file is not the original, because (it was described this way on the chinese site, and in the file itself) it was made by de-compiling the .class file.  Therefore it was a bit messy (like it had line numbers as part of the code...I had to vertically delete them)

So when I tried to compile it I got many errors.  I don't know much about java (next to nothing actually), and I'm not  really looking to develop this or anything: my sole aim is to clean up  this source code and make it publicly available again for anyone else  who might want to mess with it.

EDIT: cammin seems to have gotten rid of the errors, now it compiles but the resulting .class file does not work properly.  I re-uploaded the source code in this post with cammin's edits.  If anyone can edit it further to make it fully operational, that would be awesome, thanks.

---

### Post by cammin on 2010-01-18
Patched the missing parts so it builds.

I may have some of the > < symbols wrong in the AI, though.

---

### Post by cammin on 2010-01-18
disregard this post

---

### Post by user1397 on 2010-01-18
> **cammin said:**
> Patched the missing parts so it builds.

I may have some of the > < symbols wrong in the AI, though.
so I tried compiling it, and this is the output: ```
$ javac WorldCupSoccerSlime.java 
Note: WorldCupSoccerSlime.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
$
```I tried the .class file with the .html file and it isn't working properly (like the game is not functional only the left player appears and such)

thanks for continuing with this though, I hope we can arrive at the original code at some point! ;)

---

### Post by Reiger on 2010-01-18
EDIT: Nevermind.

---

### Post by user1397 on 2010-01-20
how does decompiling work anyway?

---

### Post by Reiger on 2010-01-20
You could look up the .class file specs (there are docs on the SUN website that detail the .class file structure). Decompiling would work along the lines of: look up the symbols (class files have symbol tables as well as debug symbols for line number and file name and so on) and rebuild the source file with it.

---

### Post by user1397 on 2010-01-22
> **Reiger said:**
> You could look up the .class file specs (there are docs on the SUN website that detail the .class file structure). Decompiling would work along the lines of: look up the symbols (class files have symbol tables as well as debug symbols for line number and file name and so on) and rebuild the source file with it.
heh...sounds more complicated than I thought...I'll have to set some time aside for this one day, got a lot of stuff to do.

thanks for the advice.

---

### Post by user1397 on 2010-01-25
In the meantime if someone with a lot of java experience wants to take this as a side project, that would be awesome too! :popcorn:

---

### Post by Perfect Storm on 2010-02-08
Thread title changed.

---

### Post by user1397 on 2010-02-08
> **Artificial Intelligence said:**
> Thread title changed.
Thank you.

---

### Post by user1397 on 2010-02-14
bump

---

