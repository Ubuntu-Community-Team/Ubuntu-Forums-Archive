---
title: "Replacing OpenJDK with Sun Java"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by CalderCoalson on 2008-11-25
Ok, so I have this application, jDip, which is extremely glitchy and rather useless under OpenJDK.  The thing randomly freezes up, and on top of that I get a 'Fatal Error' every time I try to save.  So I tried installing Sun's Java, via apt-get, but 'java' still points to the OpenJDK version, and I can't find the Sun-Java command for the life of me.  Posted in Absolute Beginner Talk, because it's not even really a bug, just me being stupid.  I already wasted a couple hours on a solution to this, so I promise I'm only wasting your time as a last resort.

Thanks in advance for any help,
-Calder Coalson

---

### Post by CalderCoalson on 2008-11-25
lol, I knew this would happen.  The second I post, I find the answer.  Anyway, for anyone encountering the same trouble, all you need to run is the following command:
```
sudo update-java-alternatives --set java-6-sun
```

Thanks to Hibble for his helpful post: [http://ubuntuforums.org/showpost.php?p=3643854&postcount=6](http://ubuntuforums.org/showpost.php?p=3643854&postcount=6)

---

### Post by gandaran on 2008-11-25
I would rather remove open-java! you don't need it once you install sun-java!

---

### Post by gakon77 on 2013-04-02
> **CalderCoalson said:**
> lol, I knew this would happen.  The second I post, I find the answer.  Anyway, for anyone encountering the same trouble, all you need to run is the following command:
```
sudo update-java-alternatives --set java-6-sun
```

Thanks to Hibble for his helpful post: [http://ubuntuforums.org/showpost.php?p=3643854&postcount=6](http://ubuntuforums.org/showpost.php?p=3643854&postcount=6)

This piece of code has been very useful. So much trouble for changing to Sun's java version without updating with the command.

> **gandaran said:**
> I would rather remove open-java! you don't need it once you install sun-java!

Although, I wouldn't be so sure about removing open java. In my case, without it, one application in particular (Brettspielwelt) doesn't load properly.  

Thanks again.

---

### Post by QIII on 2013-04-02
From the Ubuntu Forums CoC

> If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

This thread is so old that it is before Oracle bought Java, Java 6 has passed its end of life and there are much easier methods of installing Oracle Java 7.

*Thread **closed.***

---

