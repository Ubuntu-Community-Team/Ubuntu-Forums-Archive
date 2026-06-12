---
title: "Source code for iwlist command in Java"
date: 2010-08-24
forum: Programming Talk
---

### Post by psychok7 on 2010-08-24
I there, i am writing an application in Java and as part of it i need a Java source code similar do the command iwlist wlan0 scan. I really have no idea how this works.
thanks

---

### Post by andrewc6l on 2010-08-24
If you have iwlist installed, you could just System.exec("/usr/bin/iwlist") and get the input stream / error stream back from the process. Then you'd have to parse what you got back.

If you don't have iwlist installed, I suspect you'll end up having to write a native which replicates what it does. (You might want to look at the source of iwlist for ideas.)

---

### Post by psychok7 on 2010-08-24
> **andrewc6l said:**
> If you have iwlist installed, you could just System.exec("/usr/bin/iwlist") and get the input stream / error stream back from the process. Then you'd have to parse what you got back.

If you don't have iwlist installed, I suspect you'll end up having to write a native which replicates what it does. (You might want to look at the source of iwlist for ideas.)

i there, im not sure how to do that... can you give an example??

---

### Post by KdotJ on 2010-08-24
As andrewc6l suggested, if you have it installed you can run the command *through* your java program.
Check out how to run system commands in Java...

[LINK HERE]("http://www.devdaily.com/java/edu/pj/pj010016")

However, if this is some kind of project that has been set for you, which requires performing the same tasks as iwlist, maybe this option stated is not the answer, as its just really using Java as a middle-man between the user and iwlist.

---

### Post by psychok7 on 2010-08-25
> **KdotJ said:**
> As andrewc6l suggested, if you have it installed you can run the command *through* your java program.
Check out how to run system commands in Java...

[LINK HERE]("http://www.devdaily.com/java/edu/pj/pj010016")

However, if this is some kind of project that has been set for you, which requires performing the same tasks as iwlist, maybe this option stated is not the answer, as its just really using Java as a middle-man between the user and iwlist.

sweet i had found this tutorial yesterday going to try that. But my problem is, i wanted to make this program crossplatform but iwlist wont work in windows for example, do you have any advices on that? is there a similar command for windows or so?

---

### Post by andrewc6l on 2010-09-10
Figuring out what's available in terms of wireless networks is by its nature very platform specific :-) Unless there's a JSR for it that exists on all the platforms you're targeting, you'll be stuck writing platform-specific natives.

(And worse luck: Java frequently uses "wireless" to mean "mobile devices", so a simple search on "Java wireless" doesn't get anything near what you want.)

You might be able to compile iwlist for Windows using the Cygwin toolkit ([http://cygwin.com/](http://cygwin.com/)) but I'm not sure if that's worth the effort.

---

