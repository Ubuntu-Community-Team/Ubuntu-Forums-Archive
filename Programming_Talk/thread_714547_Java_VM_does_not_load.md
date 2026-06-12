---
title: "Java VM does not load"
date: 2008-03-03
forum: Programming Talk
---

### Post by swordphsh on 2008-03-03
I don't know if this is the correct place to post this, but I figured someone with some programming experience might be able to help me out. 

That said, my college uses a student information java applet called STINF, its hosted at 
[https://webts.bloomu.edu/txn/stinf]("https://webts.bloomu.edu/txn/stinf")
and I cannot get it to load under Ubuntu in Firefox or in Wine. When I go to the page, I get an error message:

```
java.lang.NullPointerException
	at Form.init(Form.java:584)
	at sun.applet.AppletPanel.run(AppletPanel.java:419)
	at java.lang.Thread.run(Thread.java:619)
```

It works fine under Windows and usually on Macs, but I cannot figure out why it doesn't work on Ubuntu.
Any help is appreciated. Thanks in advance.

---

### Post by mrsteveman1 on 2008-03-04
Are you using the sun JRE or the one that ubuntu installs by default for some things? I can't remember what its called.....

Run update-java-alternatives -l (lowercase L) and see whats installed

---

### Post by swordphsh on 2008-03-04
It says:
```
java-6-sun 63 /usr/lib/jvm/java-6-sun
```
When Firefox prompted me I chose something like Sun Java JRE 6. I tried using Sun Java 5, that one doesn't crash, but it fails to load, and two other alternatives, something like gjc and icedtea, neither of which worked.

---

### Post by mrsteveman1 on 2008-03-04
Do you have sun-java6-plugin installed?

---

### Post by swordphsh on 2008-03-04
Yes I do. Thats where the error message comes from. I turned on error debugging, so it comes up with that error instead of just crashing.
Then link I gave in the first post goes directly to the page with the Java VM, if you want to take a look at it. A friend of mine with Ubuntu tried it and it does not load for him either.

---

