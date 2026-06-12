---
title: "how to install open office or thunderbird?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Okliw on 2008-11-16
i downloaded open office 3 and thunderbird as tar.gz packages. 
how can i tell the machine to install those programs?
i have installed other applications that way (just right click on the file and choose GDebi) but in those cases they where just made up of a single file. now in the case of openoffice for example its a whole lot of files once unpacked, so what do i do with them?

and should i uninstall the old version of open office first?

i am new to unbuntu and used to run (in windows) just the setup.exe file to install a program...

my machine is running on intrepid btw.

---

### Post by laffinet on 2008-11-16
It's better to install software via Synaptic.

Go to System -> Administration -> Synaptic Package Manager 

and search for Thunderbird. Left click and choose "install", click apply. Done.

For Open Office 3 see here (GUI): [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

Or here (terminal): [http://kshoster.net/node/56]("http://kshoster.net/node/56")

In Ubuntu you normally don't have to go to a website, download the software and then install it. It's all done through a package manager (like Synaptic), where you can search for software and install it. That way it also is kept updated automatically (so you don't have to worry about checking every isntalled software seperately for updates).
Only if you want to install a software that isn't in the repositories you might have to go to the actual software website.

---

### Post by zzHanks on 2008-11-16
Both of these applications are available in Synaptic Package manager. I'm not sure about the versions though (I'm running 8.04)

System > Administration > Synaptic Package Manager.

---

### Post by Okliw on 2008-11-16
hey thanks for the fast reply :)

my internet is fairly slow, thats why i rather wanted to use the already downloaded files instead of having synaptic start downloading them again...


[I]In Ubuntu you normally don't have to go to a website, download the software and then install it. It's all done through a package manager (like Synaptic), where you can search for software and install it. That way it also is kept updated automatically (so you don't have to worry about checking every isntalled software seperately for updates).
Only if you want to install a software that isn't in the repositories you might have to go to the actual software website. [/I]

that explaination helps. so i guess i'll better spend half a day downloading again :/


anyways, what steps would i take if i had to manually install a program that is made up of lots of individual files?

---

### Post by InfectedWithDrew on 2008-11-16
> **Okliw said:**
> hey thanks for the fast reply :)

my internet is fairly slow, thats why i rather wanted to use the already downloaded files instead of having synaptic start downloading them again...


[I]In Ubuntu you normally don't have to go to a website, download the software and then install it. It's all done through a package manager (like Synaptic), where you can search for software and install it. That way it also is kept updated automatically (so you don't have to worry about checking every isntalled software seperately for updates).
Only if you want to install a software that isn't in the repositories you might have to go to the actual software website. [/I]

that explaination helps. so i guess i'll better spend half a day downloading again :/


anyways, what steps would i take if i had to manually install a program that is made up of lots of individual files?

Almost all programs are made of individual files!  But, in Linux, what you do is you create a makefile, and use the makefile to compile the source.  See this handy little bit of information: [http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

A .tar.gz is a compressed archive of source, usually.  That's what you downloaded.  However, Synaptic connects to repositories to install the programs for you, making it much easier (but as a result, you're stuck with what the repositories have, namely, OOo 2.4).  You can also find compiled source that will extract and sort itself in .deb installers, which are akin to the .msi or .exe installers.

---

### Post by 73ckn797 on 2008-11-16
Try it this way:
[http://ubuntuforums.org/showthread.php?p=6090196#post6090196](http://ubuntuforums.org/showthread.php?p=6090196#post6090196)

Why does it have to be so complicated? This post has my solution and works perfectly. Please read slowly to not miss the simplicity.

---

### Post by laffinet on 2008-11-16
There are many solutions to installing Open Office 3 but it looked like the OP had not yet used Synaptic to install any applications, therefore I tried to make a point about using Synaptic and repositories in general.

---

### Post by fullofbeans on 2008-11-16
You can istall microsoft office on ubuntu just install wine windows program loader

---

### Post by laffinet on 2008-11-16
Unless you absolutely have to use MS Office, why would you install it instead of Open Office ?

It's free, native linux, open source, reads and writes MS office formats, has a built in pdf creator...

---

