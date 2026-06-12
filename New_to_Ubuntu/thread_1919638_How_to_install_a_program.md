---
title: "How to install a program?"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by Agusia on 2012-02-03
Hi All :)
I'm new with Ubuntu and I don't know how to install a program. :( I can download it as .tar.gz or .deb. Which one i should download and what to do with it next??

---

### Post by haqking on 2012-02-03
> **Agusia said:**
> Hi All :)
I'm new with Ubuntu and I don't know how to install a program. :( I can download it as .tar.gz or .deb. Which one i should download and what to do with it next??

People are often confused by installing software in Linux, there is no real reason it is usually straight forward.

**First of all always search in the Software Centre or Synaptic Package manager to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)**

You can also use Gdebi package installer or look at dpkg for installation

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:

[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set 

Have fun

Regards

haqking

---

### Post by mörgæs on 2012-02-03
Downloading should be your very last resort. 

Which application are you searching for? Isn't it available in a repository?

---

### Post by Agusia on 2012-02-03
I want to install games from Humble Indie Bundle. ;)

---

### Post by haqking on 2012-02-03
> **Agusia said:**
> I want to install games from Humble Indie Bundle. ;)

There doesnt seem to be support on there website for installation.
However if you can get a .deb then get that and then install using that.

if you are unfamiliar then right click and choose install with gdebi, if you havent got that installed then install it or double click the .deb which should install it anyways unless you have things configured differently.

You can also use the CLI to install using dpkg

```
sudo dpkg -i debfile_name.deb
```

cheers

---

### Post by Agusia on 2012-02-03
I've installed it without any problems from the .deb file. ;) Thanks for all the help. :*
I've got another question, where the game should run better, on Windows or on Ubuntu??

---

### Post by haqking on 2012-02-03
> **Agusia said:**
> I've installed it without any problems from the .deb file. ;) Thanks for all the help. :*
I've got another question, where the game should run better, on Windows or on Ubuntu??

no idea, its your game, play it on both and see.

This is a Ubuntu forum though ;-)

Also dont forget to use thread tools to mark the thread as solved.

cheers

peace

---

### Post by Bölvaður on 2012-02-03
I just want to point out two things.
1. If you can get a .deb file you should only go for that one.
2. when you got the .deb file the first (and probably the only) thing you need to do:
> **haqking said:**
> double click the .deb


if you have a .tar file it just means the entire game is in it.
Double click the .tar file and drag and drop it somewhere into your file browser in some cool directory... Maybe you could create a directory named Games and put your game there.
So when you got: ~/Games/WorldOfGoo
Then you can just go into world of goo directory and double click the executable.

---

