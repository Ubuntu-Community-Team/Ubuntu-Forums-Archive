---
title: "j2sdk install"
date: 2007-02-11
forum: Programming Talk
---

### Post by docetes on 2007-02-11
how do i install sun's j2sdk?

any help would be appreciated thanks

---

### Post by Ramses de Norre on 2007-02-11
I'm not sure what you mean, the jdk (java development kit)?
If so: enable the backports multiverse repo by adding one of the following to /etc/apt/sources.list (choose the right ubuntu version):
```
deb http://archive.ubuntu.com/ubuntu/ edgy-backports multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports multiverse
```
Then do this:```
sudo aptitude update && sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-jdk
```
Then do ```
sudo update-java-alternatives -s java-6-sun
```
Now you've got all the tools like java, javac, ... installed.

---

### Post by phossal on 2007-02-11
You download it from SUN. 
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) (Current)
[http://java.sun.com/javase/downloads/previous.jsp](http://java.sun.com/javase/downloads/previous.jsp) (Previous Versions)

---

### Post by docetes on 2007-02-11
will it be easy to get eclipse working with that?

---

### Post by phossal on 2007-02-11
You can download Java from SUN, eclipse from eclipse.org and be using eclipse about two minutes after you've downloaded it. The instructions for such an installation are in included in my signature.

---

### Post by Ramses de Norre on 2007-02-11
Why not use the repo... It's much more secure and you get security fixes as soon as they are released. Java and eclipse are both in the repo and work fine, I suggest you use those.

---

### Post by phossal on 2007-02-11
> **Ramses de Norre said:**
> Why not use the repo... **It's much more secure and you get security fixes as soon as they are released**. Java and eclipse are both in the repo and work fine, I suggest you use those.

Interesting that you would think packages prepared by a third party (which is why they're in *backports*) are either a) more secure or b) come with faster security fixes. [COLOR="SlateGray"]**Downloading the files from their respective vendors *eliminates* any security risk associated with the packages that could be fixed by Ubuntu or the package authors**[/COLOR]. By definition, the security risks are created by those same third parties. While both Eclipse and Java *are* in the repo, installing either is no more work (but *is* less secure and more of a hassle to diagnose when problems occur) than what the vendors offer. Any argument to the contrary is nonsense. Plus, for anyone installing the *latest* JDK (or an earlier one) there isn't any other option. Finally, having installed the JDK hundreds of times using every method, I can attest to the fact that there is no easier way than simply downloading and extracting them. Be serious.

---

### Post by docetes on 2007-02-11
thats great guys i used the one in the backports 
thanks for the help,
Dave

---

