---
title: "I need help installing a program or else I have to drop out of my college class"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by PirateKarma on 2012-10-23
Hi guys, my school requires me to use a program that is made for windows however there is a way to install it on Linux according to the website. The instructions are. 

```
Installation instructions:  

[LIST=1]
[*]Point your mouse at the link below and press down your mouse left button.
[LIST]
[*][aleksPack10.jar]("http://www.aleks.com/aleks/java/aleksPack10.jar") (6.4M)
[/LIST]
  
[*]A pop-up window should appear asking you **"What should Netscape do with this file?"**.
[*]In the menu choose the option **"Save this file to disk"** and click on **"OK"**.
[*]A new window should appear to ask you where you want to save the file.
[*]Save the file in your home directory by clicking on the button **"Save"** to start the transfer.
[*]Open a terminal and type: (adapt the directory to your own Java VM lib/ext directory) **> su root **
**Password: ***(Type in the root password)*
**> cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/**
**> exit ** 
[*]Restart Netscape
[/LIST]

```

I have java installed, but its not at the directory they stated. And I'm not sure where it is. Please help!!! :( Also please note this is a web browser based program. SO i think i need to install it into the directory of java that handles web applets.

---

### Post by Hadaka on 2012-10-23
Hi, try

```
cd /usr/share/java 
```and per the instructions..in root

also..whereis command is a good way to locate files.

whereris java

---

### Post by PirateKarma on 2012-10-24
> **Hadaka said:**
> Hi, try

```
cd /usr/share/java 
```and per the instructions..in root

also..whereis command is a good way to locate files.

whereris java

This has not solved the problem for me :C Is there anything else I could do??

results of whereis 

> @xephos:~/Desktop$ whereis java
java: /usr/bin/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz


---

### Post by squakie on 2012-10-24
Ok, maybe I can make a little more of an intelligent post now.  I downloaded that .jar and copied it to where I see a lot of other .jar files on my 12.10 system:

/usr/share/java

What I don't have a clue about:  what the heck is one supposed to do to test to see if it works?  Could you maybe tell me how to do that so I can see if it works?  If so, I can tell you simply what I did.  If it doesn't work....well.....we'll have to see.

---

### Post by PirateKarma on 2012-10-24
> **squakie said:**
> Ok, maybe I can make a little more of an intelligent post now.  I downloaded that .jar and copied it to where I see a lot of other .jar files on my 12.10 system:

/usr/share/java

What I don't have a clue about:  what the heck is one supposed to do to test to see if it works?  Could you maybe tell me how to do that so I can see if it works?  If so, I can tell you simply what I did.  If it doesn't work....well.....we'll have to see.
 
There is a website called [http://www.aleks.com/](http://www.aleks.com/) it's used for my math class at my University. I test it by trying to log into my account. It cost money to make an account, and they disable accounts if logged in from mutiple sites, so I'm not at leisure to disclose account info. There is an option to make a trial account, however  I would never wish someone to go through that entire process. If this cannot be done, I understand. I may just have to drop the class for now, unless I can somehow get my hands on a Windows computer.

---

### Post by squakie on 2012-10-24
If you have a copy of Windows XP perhaps you could install something like VirtualBox and create a virtual machine to run XP within Ubuntu.  You would have internet access.  Don't know if that is possible for you or not.

Sorry I can't be of more help - I don't know a thing about java so I was trying things at my end.

---

### Post by newb85 on 2012-10-24
Did no one else find it suspicious that the instructions were written with the assumption that the browser in use is *Netscape*?!

---

### Post by squakie on 2012-10-24
Yeah, but I assumed it was old instructions that never got updated (the Java version seems old, too).  I thought it was just the idea of getting the jar and finding the proper place to put it.  But who knows?

---

### Post by muteXe on 2012-10-24
> **newb85 said:**
> Did no one else find it suspicious that the instructions were written with the assumption that the browser in use is *Netscape*?!
Yup. As does the title of the thread.

---

### Post by Paddy Landau on 2012-10-24
I have tried this in a Virtual Machine (where it cannot do any damage).

Here is what I did.


[LIST=1]
[*]Download your [FONT=Lucida Console]aleksPack10.jar[/FONT] file.
[*]Open Nautilus as root (press Alt-F2, type [FONT=Lucida Console]gksudo nautilus[/FONT]).
[*]Move the [FONT=Lucida Console]aleksPack10.jar[/FONT] to the folder [FONT=Lucida Console]/usr/share/java[/FONT].
[*]Close Nautilus and restart Firefox.
[/LIST]

Now, I have no way of testing your program, so try what I did and test. Let us know.

---

### Post by Mark Phelps on 2012-10-24
Suspicious or not, I tried a quick Google on this and found no less than a dozen links on this, several with step-by-step instructions on HOW to install it.

Seems to me that spending 5 minutes Googling this, and then trying those instructions, is preferable to dropping a class!

---

### Post by stinkeye on 2012-10-24
You may see a few different places stated where to copy the aleksPack10.jar file.
It depends if your using sun or open java and what version.

Here's one if your using the default open java in 12.04.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=12285223&postcount=4[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12285223&postcount=4")

---

### Post by PirateKarma on 2012-10-24
> **Mark Phelps said:**
> Suspicious or not, I tried a quick Google on this and found no less than a dozen links on this, several with step-by-step instructions on HOW to install it.

Seems to me that spending 5 minutes Googling this, and then trying those instructions, is preferable to dropping a class!

Sorry, but I wouldn't be dumb enough to not have tried that, before posting on a forum..... So please refrain from assuming inaccurately. I got it to work by uninstalling java, and re-installing and then coping the file into every possible java directory.

---

### Post by squakie on 2012-10-24
> **Paddy Landau said:**
> I have tried this in a Virtual Machine (where it cannot do any damage).

Here is what I did.


[LIST=1]
[*]Download your [FONT=Lucida Console]aleksPack10.jar[/FONT] file.
[*]Open Nautilus as root (press Alt-F2, type [FONT=Lucida Console]gksudo nautilus[/FONT]).
[*]Move the [FONT=Lucida Console]aleksPack10.jar[/FONT] to the folder [FONT=Lucida Console]/usr/share/java[/FONT].
[*]Close Nautilus and restart Firefox.
[/LIST]

Now, I have no way of testing your program, so try what I did and test. Let us know.

That's what I was trying as well.  I went 1 step further and did a chmod with +wx, since the rest of the jar files in that folder seemed to have all permissions - maybe only the executable flag needs to be set.  I also was unable to test, and given the explanation by the OP, doubt I could.

I like how you post - always very knowledgable and quite to the point.  I've read many of your posts and they have always been helpful!

---

### Post by Paddy Landau on 2012-10-25
> **squakie said:**
> I like how you post - always very knowledgable and quite to the point.  I've read many of your posts and they have always been helpful!
Thank you for the kind words. I try my best. But I do sometimes make royal screw-ups!

---

### Post by Mark Phelps on 2012-10-25
> **PirateKarma said:**
> Sorry, but I wouldn't be dumb enough to not have tried that, before posting on a forum..... So please refrain from assuming inaccurately.

Well ... good for you .. but WHERE in your thread did you tell us that? We're not mind readers here -- when folks don't bother to tell us what they've already tried, we HAVE to guess and, sometimes, we guess wrong.

---

