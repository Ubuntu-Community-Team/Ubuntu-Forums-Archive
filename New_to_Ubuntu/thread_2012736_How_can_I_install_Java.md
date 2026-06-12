---
title: "How can I install Java?"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by Xoberful on 2012-06-29
Hello there,

I'm a relatively new member to Ubuntu OS and so far, I think it's a great OS, responds fast and has everything I need. But there is one problem, I need to have Java (the one from [www.java.com](www.java.com)) to play games and access some websites like games, RuneScape and my VPS.

I've looked everywhere on how to do it, but none of the guides I've come accross works. Can someone please help me download Java or write me a tutorial or find me one that works and is quite easy to follow.

Thanks,

Tommy.

---

### Post by Xoberful on 2012-06-29
Hello there,

I'm a relatively new member to Ubuntu OS and so far, I think it's a great OS, responds fast and has everything I need. But there is one problem, I need to have Java (the one from [www.java.com](www.java.com)) to play games and access some websites like games, RuneScape and my VPS.

I've looked everywhere on how to do it, but none of the guides I've come accross works. Can someone please help me download Java or write me a tutorial or find me one that works and is quite easy to follow.

Thanks,

Tommy.

---

### Post by zhanglini on 2012-06-29
[this one worked for me.]("http://rootzwiki.com/topic/23008-howto-install-java-7-on-ubuntu-1204/")

---

### Post by overdrank on 2012-06-29
Hi and welcome, please do not create multiple threads on the same issue. Threads merged.

---

### Post by Xoberful on 2012-06-29
> **zhanglini said:**
> [this one worked for me.]("http://rootzwiki.com/topic/23008-howto-install-java-7-on-ubuntu-1204/")

Doesn't work, in the last step where I have to type

```
sudo apt-get install oracle-java7-installer
```

it says the following in the terminal:

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Curtis6767 on 2012-06-29
> **Xoberful said:**
> Doesn't work, in the last step where I have to type

```
sudo apt-get install oracle-java7-installer
```it says the following in the terminal:

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Since you are the second person in the last couple of days to have this problem, it does appear that the eugenesan PPA has become corrupted.

Check this thread for a solution: [http://ubuntuforums.org/showthread.php?t=2011342](http://ubuntuforums.org/showthread.php?t=2011342)

---

### Post by Xoberful on 2012-06-29
> **Curtis6767 said:**
> Since you are the second person in the last couple of days to have this problem, it does appear that the eugenesan PPA has become corrupted.

Check this thread for a solution: [http://ubuntuforums.org/showthread.php?t=2011342](http://ubuntuforums.org/showthread.php?t=2011342)

I think that's the problem, there's a red circle with a white dash in it at the top right of my screen. What post should I follow to fix the problem on that thread?

---

### Post by Curtis6767 on 2012-06-29
Try going to the last page and working backwards from there because there is a lot of talk about the installation in the first few pages that don't actually address the issue.

What you want to do is remove that PPA, then remove any version of Java that may have been installed, and finally you want to go to the WebUd8 site that is mentioned several times. Follow those steps at WebUd8 to install Java.

---

### Post by Xoberful on 2012-06-29
> **Curtis6767 said:**
> Try going to the last page and working backwards from there because there is a lot of talk about the installation in the first few pages that don't actually address the issue.

What you want to do is remove that PPA, then remove any version of Java that may have been installed, and finally you want to go to the WebUd8 site that is mentioned several times. Follow those steps at WebUd8 to install Java.

Doesn't work D:

Someone please help..

---

### Post by nipunshakya on 2012-06-29
> **Xoberful said:**
> Doesn't work D:

Someone please help..

what exactly doesnt work? have u tried to remove eugenesan's ppa?? what sort of errors do u get?? some suggestions were suggested by someone already in this thread(im reminding it again)... the following link has it:):P
[http://ubuntuforums.org/showthread.php?t=2011342](http://ubuntuforums.org/showthread.php?t=2011342)

---

### Post by Xoberful on 2012-06-29
> **WinuxUser said:**
> what exactly doesnt work? have u tried to remove eugenesan's ppa?? what sort of errors do u get?? some suggestions were suggested by someone already in this thread(im reminding it again)... the following link has it:):P
[http://ubuntuforums.org/showthread.php?t=2011342](http://ubuntuforums.org/showthread.php?t=2011342)

I don't know how to remove Eugenesan's PPA or whatever. At this point, I just want to delete all previous versions of Java that I've installed, because none of them worked.

---

### Post by nipunshakya on 2012-06-29
with that attitude, you might want to wait for someone to help you out.

---

### Post by Xoberful on 2012-06-29
I have went into random files and in the File System I've come accross **user\lib\jvm\** , in this file I see heaps of folders that are Java related and I think I need to delete them, the files in **user\lib\jvm\** are as follows:

java-1.6.0-openjdk
java-1.7.0-openjdk-amd64
java-6-openjdk
java-6-openjdk-amd64
java-6-openjdk-common
java-7-openjdk-amd64
java-7-openjdk-common
java-7-oracle
jdk1.7.0

Could anyone please confirm with me if these are the correct files I should remove from my system or not? And if they should be removed, how can I remove them?

---

### Post by Xoberful on 2012-06-29
bump

---

### Post by czgirb on 2012-06-30
I face this problem too.

Please refer to my thread [http://ubuntuforums.org/showthread.php?t=2011342](http://ubuntuforums.org/showthread.php?t=2011342)
If you face a problem, please do not hesitate to ask to QIII ... trust him ... follow his guide ... and you will have a nice result. As what I do.
He's a very very nice man.

---

### Post by zhanglini on 2012-06-30
> **Xoberful said:**
> I have went into random files and in the File System I've come accross **user\lib\jvm\** , in this file I see heaps of folders that are Java related and I think I need to delete them, the files in **user\lib\jvm\** are as follows:

java-1.6.0-openjdk
java-1.7.0-openjdk-amd64
java-6-openjdk
java-6-openjdk-amd64
java-6-openjdk-common
java-7-openjdk-amd64
java-7-openjdk-common
java-7-oracle
jdk1.7.0

Could anyone please confirm with me if these are the correct files I should remove from my system or not? And if they should be removed, how can I remove them?

You don't delete applications by removing them from the file system in Ubuntu (or other OS for that matter).  Go to Synapsis or Softwarecenter, search for Java and select uninstall...

---

### Post by Xoberful on 2012-07-02
> **zhanglini said:**
> You don't delete applications by removing them from the file system in Ubuntu (or other OS for that matter).  Go to Synapsis or Softwarecenter, search for Java and select uninstall...

It won't let me install or remove anything on software center -

" Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now? "

I push the ' Repair ' button but it won't work.

There's also a red sign with a white dash going accross it at the top right of my screen.

---

