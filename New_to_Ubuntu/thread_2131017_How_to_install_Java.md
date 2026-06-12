---
title: "How to install Java?"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by DarrenVortex on 2013-03-31
so as a newbie, I'm used to either .bin, .run or .deb binaries, software center or apt-get app names and repositories. Java website gives me a tarball. I'm not sure what exactly I'm supposed to do with it. :confused: Do I just extract it? If I do, where? How do I add binaries to PATH so that terminal can find them?

---

### Post by Cheesemill on 2013-03-31
If it's OpenJDK you are after then it's in the repositories, you can install it with...
```
sudo apt-get install openjdk-7-jre
```

If for some reason you need to install Oracle Java instead of OpenJDK then you can use the following commands...
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

All of this information can be found on the Java page of the Ubuntu wiki.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by DarrenVortex on 2013-03-31
Thanks a lot that was really useful!
However, since I really want to learn more about linux, I'd like to know how to install from that tarball anyway. Just to know.
Also when executing java programs, will I ever sense a difference between OpenJDK and Oracle Java? Like, are there programs out there that are compatible with only one?

---

### Post by gordintoronto on 2013-03-31
"How do I install a tarball" is a lot like "how do I compile a .zip": it depends on what is inside.

Your learning project will be much more fruitful if you begin with something a lot smaller and simpler than Java.

If you plan to develop programs, learning about tarballs is essential. If you want to learn about Linux, install Linux From Scratch on a spare machine. [http://www.linuxfromscratch.org](http://www.linuxfromscratch.org)

---

### Post by daslinkard on 2013-03-31
Since you are eager to learn more about Linux...one of the first things that I would recommend doing would be becoming very familar with Google.  As you progress through your Linux learning curve you will find that others have plotted the same course you're on and with proper searching the answers to your questions are just your fingertips away.  Good luck with your Linux adventure!

---

### Post by DarrenVortex on 2013-04-01
The tarball contained Java: the compilers and JVM binaries. So basically all I had to do was copy it where all the other applications are installed.
Google doesn't always help. There are times when I encounter things that haven't been discussed before on a search-engine friendly website, so I can't find those subjects easily, hence I come to forums! :)
So... Where are Ubuntu applications installed?

---

### Post by oldos2er on 2013-04-01
Here's a rundown of Linux file system hierarchy: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

You can see where each file in a package is installed with ```
dpkg -L <package name>
```

---

