---
title: "Installing jre-7u25...tar.gz error &quot;bash: etc/profile: No such file or directory&quot;"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by unknown24 on 2013-07-11
hi,iwant to install jre-7u25-linux-i586.tar.gz in my Ubuntu 13.04 (lubuntu). I follow the instruction for installation from here [http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux](http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux). On step 14, I've got an error when entered this command :
```
./etc/profile
```
The error is :
```
bash: etc/profile: No such file or directory
```
But if skipped that and go to step 16. The result when i entered "*java -version*" is
```
java version "1.7.0_25"
Java(TM) SE Runtime Environment (build 1.7.0_25-b15)
Java HotSpot(TM) Server VM (**build 23.25-b01**, mixed mode)
```
It's little different result in "**build 23.1-b03" **that showed in the wikihow installation guide.
How can I fix that? If i skipped step 16, is there a problem when using java? please help me,

---

### Post by BreezyBrooke on 2013-07-11
```
sudo add-apt-repository ppa:webupd8team/java && sudo apt-get update && sudo apt-get install oracle-java7-installer
```

There, that installs Java 7. No fuss, and is updated regularly with each Java 7 release!

What you have at the moment, and what was shown in terminal was openjdk-1.7. TheOpen Source Java for Linux.

---

### Post by unknown24 on 2013-07-11
Thank for your replying, but reason i use tar.gz is to have installation offline. 
If i want to reinstal my OS no need to use internet connection again to install JRE.
I have limited internet connection.

---

### Post by steeldriver on 2013-07-11
I agree it's not the best way to install the Oracle jre

However, your specific error is likely because you copied #14 wrongly - it's not

```
./etc/profile
```
(meaning "try to execute a command called 'profile' in a directory 'etc' relative to the current directory") it's
```
. /etc/profile
```
(note the space!) meaning "re-read ('source') the /etc/profile file that you just modified"

I haven't read the whole thing but /etc/profile will get re-read anyway next time you login so as far as I can tell step #14 really only there so you get an 'instant' check of whether your changes took effect

---

### Post by oldos2er on 2013-07-11
Moved to Absolute Beginners.

---

### Post by unknown24 on 2013-07-11
excellent,,, there is no error found,,,
thanks a lot,,,

---

