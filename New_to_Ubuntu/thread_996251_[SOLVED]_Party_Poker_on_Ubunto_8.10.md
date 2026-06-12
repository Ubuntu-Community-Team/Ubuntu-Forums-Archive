---
title: "[SOLVED] Party Poker on Ubunto 8.10"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by wheelerrver on 2008-11-28
I have just started using Ubuntu 8.10.  I found that Party Poker supposedly has an 'anywhere' method that will work on firefox.  [www.partypoker.com/anywhere](www.partypoker.com/anywhere) 

The Party Poker web site says that it requires Sun JDK 1.4/1.5 so I used Synaptic Package Manager to install 1.5.  I followed the instructions for configuring it, so it should be working.  

However, when I click on Instant Play it goes through a download process, then nothing else ever happens except that it tells it is "loading the party poker anywhere lobby, please wait"   I went through the same process on a Windows machine I have access to and it loaded, gave me a chance to accept the applet and went straight to the game site where I could log in.

Any suggestions on what I need to do so I can use this on Ubuntu?

---

### Post by LowSky on 2008-11-28
try using user agent switcher

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

change it to windows, it might fool the program and work

---

### Post by wheelerrver on 2008-11-28
No luck with switiching, same result on the Party poker site. This may be a useful tool for me, however.  I appreciate it.  How do you post a thanks, anyway?  I see there must be a way to do it easily.

---

### Post by alzie on 2008-11-28
I went to the link you provided and I was able to get the lobby to load.  I tried to log in but I can't remember my partypoker name and p/w (its been a while) I could go into a room to watch though.

I am still running 8.04 but that shouldn't be an issue.

When you installed sun-java5-plugin from the repositories did you remove icedtea-java as well?

---

### Post by wheelerrver on 2008-11-28
Alas, the instructions said nothing about removing anything.  How would I do that?

---

### Post by stoogiebuncho on 2008-11-28
You can remove packages from the Synaptic Package Manager.  Just search for the package you want to remove, and when you find it, right click on it.  There will be options for removal.

When you're set, click "Apply."

---

### Post by wheelerrver on 2008-11-29
My thanks to all who replied.  While trying to do what the last reply suggested, I noticed that Java 6 Runtime and Java 6 Plugins were not installed.  I did that and Party Poker worked, but I still need to know how to mark this as solved!  Incidentally, 8.10 apparently does not include icetea-java since I did not find that as installed either.

---

### Post by wheelerrver on 2008-11-29
I finally found help on how to mark this as solved.  It is certainly a learning experience just trying to find help for these forums.  For any other newbie trying to find help on forums, I suggest going to the tutorial on forum basics.  Just do a search for "forum basics" and there is a thread about it with lots of helpful stuff.  I suspect I am not the only 60+ user who does not use a lot of other forums, so maybe this will help any others who are trying to get started.

---

### Post by jamesstansell on 2008-11-30
> **wheelerrver said:**
> My thanks to all who replied.  While trying to do what the last reply suggested, I noticed that Java 6 Runtime and Java 6 Plugins were not installed.  I did that and Party Poker worked, but I still need to know how to mark this as solved!  Incidentally, 8.10 apparently does not include icetea-java since I did not find that as installed either.

Glad you got it working! :)

By the way, in 8.10 the icedtea packages mostly start with the name openjdk-6 but the firefox plugin name is icedtea6-plugin.  (OpenJDK is the future of Java, but I'll leave that can-o-worms for another thread.  Let's just say that if you're the inquisitive type there is fertile ground here for your investigations.)

-james.

---

