---
title: "Opening JNLP files in Ubuntu 12.04?"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by kramer65 on 2012-03-26
Hello,

I'm running the latest (updated) version of Ubuntu 12.04 and I just wanted to open a jnlp file from the web. I've got openjdk-6-jdk and the icedtea-netex package installed (through synaptic) which I think is the package I need to run jnlp files. Unfortunately firefox still doesn't know what to do with the jnlp file. So do I need to direct firefox to the location of icedtea or something?

Does anybody know how I can solve this? All tips are welcome!

---

### Post by winh8r on 2012-03-26
This thread might help:

[http://ubuntuforums.org/showthread.php?t=1007384]("http://ubuntuforums.org/showthread.php?t=1007384")


However, due to the fact that 12.04 is still in beta testing , there is a possibility that you may discover one or two as yet unresolved issues in some applications, although these will be sorted out fairly soon as the official release date gets nearer.

If you are still having issues then it might be a good idea to post in the Ubuntu +1 Precise Pangolin area of the forum.

Hope this helps you.

---

### Post by bonzini on 2012-03-26
I seem to recall having this problem in 11.10 and if memory serves (a sometimes poor assumption) you DO have to tell Firefox which application to use to open the JNLP file - even though you've installed the extension.

Perhaps something is missing in the install procedure.  Anyway, give it a try.

---

### Post by dimalen on 2012-10-16
Hi all.
I want to continue this topic and ask about JNLP file on Ubuntu 12.04.
This is release version. I installed Oracle Java and get this

dimal@Dimal-U10:~$ java -version
java version "1.7.0_04"
Java(TM) SE Runtime Environment (build 1.7.0_04-b20)
Java HotSpot(TM) 64-Bit Server VM (build 23.0-b21, mixed mode)
dimal@Dimal-U10:~$ javac -version
javac 1.7.0_04
dimal@Dimal-U10:~$

When I try to run Java application from Firefox, for example Oneclick from Spectrum. It must to open JNLP file but do nothing.
Where is the catch?

---

