---
title: "How do i install those files that end with .gz ?"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by marino4 on 2014-09-21
How do i install those files that end with .gz ?

---

### Post by pissedoffdude on 2014-09-21
It depends on what type of file it is.  All *.gz means is that it's an archive, like a zip. If there's source code in there, then most likely ```
./configure
make
sudo make install
```

But even compilation varies by the source code, so you'll have to be specific.

---

### Post by slickymaster on 2014-09-21
The preferred way to install software in Ubuntu is to use the package manager, which you can access through Ubuntu Software Center. 

That said, a .gz file extension indicates the file is a compressed set of files and folders (the compressed files you see in Windows usually have a .zip extension). It can be compressed files that have a precompiled binary file, or it can be compressed files that have the source code allowing you to compile the application from source.

I recommend you to have a read at [CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by Lars Noodén on 2014-09-21
The best way would be to find the package in the repository and use that.  Manually installing can make a mess and will need to be manually updated.  Search using the Software Center, Synaptic or apt first.  It can save a lot of work and trouble.  

The next best way would be to find the package in a PPA and use that.

Then if there is really no other way.  Extract the contents of the tarball and look for a file called README or INSTALL.  One of those should exist and should tell the exact details.

---

### Post by marino4 on 2014-09-21
[ 						 							]("http://ubuntuforums.org/member.php?u=175192")[**[COLOR=#000000]pissedoffdude[/COLOR]**]("http://ubuntuforums.org/member.php?u=175192") I saw many people explaining it like that so lets say that i whant to install an java update Ive got that .vb file and i open my terminal!
Pls tell me step by step coz im new here!
Tnx in advance!

---

### Post by pissedoffdude on 2014-09-21
Sorry about that marino.  I'm usually brief, so sometimes details get left out.  Okay, can you explain what you're trying to do? A .vb file is usually part of a visual basic project (so it's not supposed to be run on linux).  If you're trying to install java, like others are saying, you should first look in the Ubuntu Software Center.  Installing software on linux distributions is different than installing software on Windows.

In Windows, you download an installer and go from there.  In linux, most software you want is grouped into 'packages,' which are approved and tested by various members of a community (usually).  So basically, I'm saying in Windows, you download an installer from a project's website, and that installer is the way you go about installing it, whereas in linux, rather than downloading an installer from a website, you install a program by downloading a package provided by your distro's repositories (so that just means you install programs via the Ubuntu Software Center, rather than an installer provided by a project's website).  

If you want to install java, you can get it from the Ubuntu Software Center.  Search java or jvm, and you should be able to get what you need from there.  Alternatively, you can be more precise and install software from the terminal.  So, to install java from the terminal, open up a terminal (just hit your windows button on your keyboard and type terminal) and type: ```
sudo apt-get update
sudo atp-get install openjdk-7-jre
```

---

### Post by marino4 on 2014-09-22
[ 						 							]("http://ubuntuforums.org/member.php?u=175192")[**[COLOR=#000000]pissedoffdude[/COLOR]**]("http://ubuntuforums.org/member.php?u=175192")! For <snip> sake that was the awnser i was searching for tnx m8!

---

