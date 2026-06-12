---
title: "how to install java"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by bzik06 on 2012-05-17
Hi all.

How do I install java.

this is the link I wish to use.
[http://java.com/en/download/index.jsp](http://java.com/en/download/index.jsp)

What do I do now ?

Thanks.

---

### Post by Vereinfachen on 2012-05-17
Don't use that Java version!!

Instead, just install OpenJDK 7 from the repos!

openjdk-7-jre
icedtea-7-plugin

```
sudo apt-get install openjdk-7-jre icedtea-7-plugin
```

---

### Post by bzik06 on 2012-05-17
OK. thanks.

is there anything else I will need to do besides writing that line in the terminal ?

Why not use it ?
What is the difference between them ?

Thanks :)

---

### Post by Vereinfachen on 2012-05-17
The Oracle Java Version is not open source, the OpenJDK version is open source. It shouldn't matter what you use, your Java programs will be exactly the same. But OpenJDK is tightly integrated into Ubuntu and easy to install using the package manager, while the Oracle Java version needs to be manually downloaded and doesn't fit perfectly into the system.

Just use OpenJDK, everyone does ;)

---

### Post by bzik06 on 2012-05-17
OK. thanks.
I will try it and let you know...

---

### Post by bzik06 on 2012-05-17
are you sure that you wrote it correctly ?
tried it, this was the result:


angel@angel-laptop:~$ sudo apt-get install openjdk-7-jre icedtea-7-plugin
[sudo] password for angel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openjdk-7-jre

---

### Post by QIII on 2012-05-17
> **Vereinfachen said:**
> It shouldn't matter what you use, your Java programs will be exactly the same. 

Incorrect.  OpenJDK will NOT work in many cases.  I wish it did in all cases.

> **Vereinfachen said:**
> while the Oracle Java version needs to be manually downloaded and doesn't fit perfectly into the system.

Incorrect.  At least two PPAs exist that use scripts to download, install and update Oracle Java as Oracle makes updates available.

> **Vereinfachen said:**
> Just use OpenJDK, everyone does ;)

Incorrect.  Many developers do not.  Many websites do not recognize OpenJDK.

Please see my post here, webupd8 version is preferable:

[http://ubuntuforums.org/showthread.php?t=1977358](http://ubuntuforums.org/showthread.php?t=1977358)

---

### Post by Vereinfachen on 2012-05-17
QIII, yes I know that some applications MAY not work correctly. In reality I never found one, though I am not a heavy Java user.
But still, it is advisable to first install OpenJDK and only if you have problems switch to Oracle Java.

> a smart man always says the truth, a wise man says the things that need to be said.

bzik06, what Ubuntu version are you using? I can download it just fine on my 12.04 setup. It is advisable that you upgrade. If you don't want to you can install the old openjdk-6-jre and icedtea6-plugin. Just change the 7s to 6es.

---

### Post by QIII on 2012-05-17
I have encountered many that will not work.

I do use Java quite a bit, since I develop with Java.

Please read the post.  I suggest OpenJDK as a first choice.

I would recommend very STRONGLY against installing 6.  The reason that 7 is available is that 6 has security and usability issues.  Oracle Java 6 reaches EOL in November 2012.  OpenJDK 6 will accompany it to the grave.

---

### Post by idoitprone on 2012-05-17
> **QIII said:**
> I have encountered many that will not work.

I do use Java quite a bit, since I develop with Java.

Please read the post.  I suggest OpenJDK as a first choice.

well iced tea runs runescape. I wonder what type of sites do not work

---

### Post by bzik06 on 2012-05-17
Tank you!
works like a charm :)

---

### Post by Cavsfan on 2012-05-17
Check out the links in my signature. I have always used them. The current version is 6.32.

---

### Post by Cavsfan on 2012-05-17
You do realize that version 7 is a beta right?

---

### Post by QIII on 2012-05-17
Check your link.

It has been updated to Oracle Java 7.

;)

---

### Post by bzik06 on 2012-05-17
there are some snags. but I am happy.

sure that it will all go away in a few days with an update.

---

### Post by Cavsfan on 2012-05-17
> **QIII said:**
> Check your link.

It has been updated to Oracle Java 7.

;)

My link still shows 6.32 is the most current but, I have researched a bit and I see that 6 is no longer to be supported.

I will install 7.  :wink:

---

### Post by QIII on 2012-05-17
> **Cavsfan said:**
> You do realize that version 7 is a beta right?

I don't think Oracle thinks it is.

[http://www.java.com/en/download/faq/why_upgrade.xml](http://www.java.com/en/download/faq/why_upgrade.xml)

---

### Post by Cavsfan on 2012-05-17
See my previous post. Even my link on how to install it has been updated to 7.4.
Not quite sure why that check version link pulls in 6.32.

---

### Post by QIII on 2012-05-17
> **Cavsfan said:**
> See my previous post. Even my link on how to install it has been updated to 7.4.
Not quite sure why that check version link pulls in 6.32.

I was typing when you posted it.  Short round.  No friendly fire intent.

If you install 7 and go to the "Do I have Java" page, you'll get a congratulations for having the latest installed.  Lazy web page admin?

---

### Post by Cavsfan on 2012-05-17
> **QIII said:**
> I was typing when you posted it.  Short round.  No friendly fire intent.

If you install 7 and go to the "Do I have Java" page, you'll get a congratulations for having the latest installed.  Lazy web page admin?

I agree! It pulled in my kernel version in the link and said that I am using the right java version 6.32. :confused: I have 7.4 installed now.
Thanks!

---

