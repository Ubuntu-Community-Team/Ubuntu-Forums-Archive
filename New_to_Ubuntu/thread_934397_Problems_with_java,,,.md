---
title: "Problems with java,,,"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by TheFly on 2008-09-30
Hi.
I'm trying to download a video from youtube by typing kiss before the url, but there is no "download now". Instead a message telling me that it has not detected java appears.

I tried to install java from Firefox (as an add-on), but it still doesn't work. 

Any ideas how to get this to work properly?

Thanks!

---

### Post by blithen on 2008-09-30
Oh wow...Java on linux doesn't work very well but I can try. I might not be of as much help 'cause I'm at school and I can't remember exactly what the package is, but go to Add/Remove, and install Java 6 runtime I believe it's called or something similar.

---

### Post by GhentK on 2008-09-30
Sometimes, installation of Java is a breeze; sometimes it's a pest -- at least with Ubuntu.

To verify that it is indeed your Java installation that's borked, visit the [Java tester](http://www.java.com/en/download/installed.jsp) on java.com.

If it's not properly installed or up-to-date, try visiting [Java's guide on installing Java on Linux](http://www.java.com/en/download/help/5000010500.xml) to see if you can fix the problem. Remember reading the guide *very* carefully. I'd forgotten to switch on Java in Firefox, and it took me a month to get it to work, though admittedly with very sporadic and unenthusiastic effort. ;)

---

### Post by TheFly on 2008-09-30
> **GhentK said:**
> Sometimes, installation of Java is a breeze; sometimes it's a pest -- at least with Ubuntu.

To verify that it is indeed your Java installation that's borked, visit the [Java tester](http://www.java.com/en/download/installed.jsp) on java.com.

If it's not properly installed or up-to-date, try visiting [Java's guide on installing Java on Linux](http://www.java.com/en/download/help/5000010500.xml) to see if you can fix the problem. Remember reading the guide *very* carefully. I'd forgotten to switch on Java in Firefox, and it took me a month to get it to work, though admittedly with very sporadic and unenthusiastic effort. ;)

I have installed the self-extracting ( i think it was called that) on my desktop using sudo commands... but i want to remove it...  how?

---

### Post by blithen on 2008-09-30
> **TheFly said:**
> I have installed the self-extracting ( i think it was called that) on my desktop using sudo commands... but i want to remove it...  how?

Remove what exactly?

---

### Post by TheFly on 2008-09-30
I installed java from this file (i think) jre-6u7-linux-i586.bin, using the guide on how to install java on linux. 

But I also installed java from add/remove, without uninstalling the first java i installed... Can I just delete the folders where I installed jre-6u7-linux-i586.bin? (/home/Desktop/java)

---

### Post by Crafty Kisses on 2008-09-30
What are the results of > java --version

---

### Post by GhentK on 2008-10-01
> **TheFly said:**
> I installed java from this file (i think) jre-6u7-linux-i586.bin, using the guide on how to install java on linux. 

But I also installed java from add/remove, without uninstalling the first java i installed... Can I just delete the folders where I installed jre-6u7-linux-i586.bin? (/home/Desktop/java)
Nope, it's not that easy, unfortunately; several files are also installed in other places of the file system. The two shouldn't conflict, though, but if you really want to, you can try and see if this [java uninstaller](http://www.java.com/en/download/help/5000011600.xml#jre) works. :)

Edit: I just saw that the uninstaller is intended for 1.5.0, as opposed to 1.6, which I believe you've installed. It might work like a charm, wreak havoc, or leave bits for all I know -- just so you're aware of it.

---

### Post by GhentK on 2008-10-02
I come to correct myself; after performing a small test, i can see that the installer only installs files in the directory you ask it to, i.e. ~/Desktop/java in your case. Sorry to have misinformed you.

To uninstall it, you can just:

```
sudo rm -R ~/Desktop/java/jre1.6.0_07
```

and it should be gone. :) Subsequently, you can delete the ~/Desktop/java directory if there's nothing in it; I'm unsure whether the APT installer uses that directory or some other. It's better to air on the side of caution when sudo rm'ing is my philosophy. :D

---

