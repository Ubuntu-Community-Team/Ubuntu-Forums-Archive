---
title: "Java can not compile my code, even if my code is correct"
date: 2013-09-20
forum: Programming Talk
---

### Post by pavelexpertov on 2013-09-20
Hello, I have spent about a month designing code for my textprocessor and the compiler compiled it fine and it ran fine. I developed it on xubuntu 13.04 by the way. When I moved my files from xubuntu to ubuntu 13.04 with same version of java compiler. for really awkward, it produced errors. Basicaly it informed me that switch statements did not accept string type data, but they wanted int type data. Even if the same code was compiled in xubuntu with no problem!!!!!!. I know what to fix in the code, but it does not make sense to me that the same code, which was compiled with same version of compiler in both systems, can work in one system and can not work in another!!!! Plz respond if you had same trouble and a solution!!!!!! Thank you!!
UPDATE!!!!!: Hello guys, my mistake, actually the cause of the problem was the different version of javac(I did look in the wrong place). I know this post has been wasted, but can anyone help on how to update my javac from 1.6 to 1.7? Plz reply!!! Thanks guys!!

---

### Post by fadhil-hakadir on 2013-09-21
How did you install the 1.6 or 1.7 compiler?

If you have them installed and you are asking to change the default javac, just skip to --config. But I might be wrong 

I normally install Oracle Java JDK7 manually, by downloading the tar file and moving it to /usr/lib/jvm.

normally you can install javac by:
sudo update-alternaives --install "/usr/bin/javac" 1 "/usr/lib/jvm/<java 1.7 folder>/bin/javac"

then do:
sudo update-alternatives --config javac

 finally, choose java 7

I hope this helps

---

### Post by pavelexpertov on 2013-09-21
Hi, thanx for reply, for some reason I can not copy tar file to another folder, how do i get root access in order to do that?

---

### Post by ofnuts on 2013-09-21
In Ubuntu you don't get root access... your usual ID has all sudo privs, so you just prefix commands by sudo and enter your pwd at the prompt. There are also ways to get sudo privs in a graphics app (explorer, editor...).

---

### Post by fadhil-hakadir on 2013-09-22
Yes just sudo your way.

untar the file where you put it.maybe its best to do this in your Download folder (im assuming you downloaded it):
tar xvfz yourjdk.tar.gz

then move it to the jvm folder:
sudo mv yourjdk /usr/lib/jvm

good luck!

---

