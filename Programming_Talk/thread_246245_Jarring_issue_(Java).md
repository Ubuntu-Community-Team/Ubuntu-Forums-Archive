---
title: "Jarring issue? (Java)"
date: 2006-08-29
forum: Programming Talk
---

### Post by Griff on 2006-08-29
I can't figure out if this problem is on my end or the server I'm sending it to.  I just needed to jar a couple things for submission so I did the following:
```
jar cvf archive1 Submission.txt Chain.java
```
Get the following output:
```
adding: META-INF/ (in=0) (out=0) (stored 0%)
adding: META-INF/MANIFEST.MF (in=56) (out=56) (stored 0%)
adding: Submission.txt (in=3823) (out=1569) (deflated 58%)
adding: Chain.java (in=7317) (out=1838) (deflated 74%)
Total:
------
(in = 11188) (out = 3887) (deflated 65%)

```

Here's the problem: I submit archive1 to server.  I then download what I just submitted.  The submission now has a new name: archive1.ata.  I can open it in Linux just fine, but Windows can't do a thing with it.  Where does this .ata extension come from?

---

### Post by chonger on 2006-08-29
I'm guessing the extension comes from the server. 

What kind of server is this? Does change all .jar files into .ata files or just this particular one? Have you tried using the jar xf archive1.ata command on windows? Do you get an error?

---

### Post by Griff on 2006-08-29
> **chonger said:**
> 
What kind of server is this? Does change all .jar files into .ata files or just this particular one? Have you tried using the jar xf archive1.ata command on windows? Do you get an error?

It changes all my .jar files to .ata files, however, eveyone else that sends .jar files to it gets .program files returned.  I even tried jarring on my windows partition, but the result is the same. .ata files are returned.  I talked to the admin at the school about this and they had no idea what .ata was or why it was returning like that.  I can unjar these archives, but the .ata thing is really nagging at me.

---

### Post by yaaarrrgg on 2006-08-30
Are you adding a .jar extension?  The syntax should be:

```

jar cvf archive1.jar Submission.txt Chain.java

```

Otherwise, what browser or client are you using to submit this file (to the server)?  The ".ata" makes me think "attachment."  It could also be the client tools you are using.  Might also try submitting with a different tool.

---

### Post by Griff on 2006-08-30
> **yaaarrrgg said:**
> Are you adding a .jar extension?

Otherwise, what browser or client are you using to submit this file (to the server)?  The ".ata" makes me think "attachment."  It could also be the client tools you are using.  Might also try submitting with a different tool.

:P That was an error writting into the forum, I did do that when I jarred it.  I used firefox browser.  I'll try something else.

---

### Post by yaaarrrgg on 2006-08-30
> **Griff said:**
> :P That was an error writting into the forum, I did do that when I jarred it.  I used firefox browser.  I'll try something else.

ah...I wasn't sure.  

If that doesn't work, I would file a bug report about the server you are submitting to.  It's fiddling with the extensions (not sure why they want to do this), and doesn't seem to be getting it right all the time.

It sounds like you are doing everything correct, to me...

---

### Post by Griff on 2006-09-01
Well, it seems like everything is ok.  Everying is jarred properly and I can unjar the .ata it gives to me.  Nobody on the server side new what .ata even meant.  So long as I can send and recieve jars I'll just ignore the .ata thing for now.  Thanks for help all.

Griff

---

