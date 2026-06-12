---
title: "Eclipse JVM terminated exit code error"
date: 2011-06-24
forum: Programming Talk
---

### Post by najdorfchess on 2011-06-24
Hi all. I had a problem running eclipse IDE as I get the following error as shown in Screenshot-1.  I already downloaded Sun Java JDK (now Oracle) from [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

Also I have shown whats the default version of Java when I type in "java -version" and the contents in my /usr/lib/jvm directory.

I have no idea why I get this error. Someone kindly help me out.

[[img]http://www.freeimagehosting.net/uploads/9bee01d033.png[/img]](http://www.freeimagehosting.net/)

[[img]http://www.freeimagehosting.net/uploads/47176a28c3.png[/img]](http://www.freeimagehosting.net/)

---

### Post by kagov on 2011-06-24
If this is on startup the problem may be that Eclipse is configured to use the wrong java version which may cause errors throughout the IDE causing the error you see.

---

### Post by najdorfchess on 2011-06-25
Yes I get this error when I try to start the launcher. I also do think that eclipse has been configured for open jdk by default while I changed my default java to be Sun (Oracle) java, as you can see from screenshot 2. Can u suggest me how to change eclipse configuration on this? I tried deleting eclipse and download a fresh copy and installing it.. But the problem persists  :(

---

### Post by fballem on 2011-06-25
I don't use the version of Eclipse from the repositories. I don't know how comfortable you are with Linux and the command line, but the instructions on this page may prove helpful: [https://wiki.ubuntu.com/fballem/Software/external/eclipse](https://wiki.ubuntu.com/fballem/Software/external/eclipse)
Regards,

---

### Post by najdorfchess on 2011-06-25
Yes I have followed more or less similar path and I installed my eclipse in ~/opt/eclipse directory. But I still get the error. And I did check if eclipse has executable permissions. I guess the error has got something to do with eclipse unable to detect proper JDK in my system. When converting sun java as my default I followed instructions in this video [http://www.youtube.com/watch?v=N3lNhkxcK5o](http://www.youtube.com/watch?v=N3lNhkxcK5o)

Someone kindly see through it and tell me if I have missed something. It's been more than 3 days since my eclipse was working and I'm missing it  :(

---

### Post by najdorfchess on 2011-06-25
Additional info: 
Eclipse works fine if I change my default java via 

"sudo update-alternatives --config java"

Do u recommend me reinstalling Sun java?

---

### Post by fballem on 2011-06-27
I remember reading somewhere (can't find the source at the moment) that eclipse does have occasional issues with open jdk. My bad, I should have twigged earlier. Yes, you should be running the Sun Java if you are going to be using eclipse.

---

### Post by najdorfchess on 2011-06-28
Yes thanks for ur reply.. What I did is to remove the jdk file from /usr/lib/ directory and then installed sun java via apt-get  
And then changed sun jdk to be the default one.. It somehow worked :)

Also read that eclipse works the best with sun java 6. But im not expert at all  :)

---

### Post by fballem on 2011-06-28
If your problem is solved, may I suggest that you use the thread tools to mark it solved. That way, others who may be having the same problem can easily find your post.

Glad to have been of at least small help,

---

