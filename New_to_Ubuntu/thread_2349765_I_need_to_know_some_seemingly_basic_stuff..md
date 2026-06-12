---
title: "I need to know some seemingly basic stuff."
date: 2017-01-18
forum: New to Ubuntu
---

### Post by ninjaking922 on 2017-01-18
Ok I am new to linux (kind of) I have tried out several distributions and keep running into the same problems with each of them. The first problem is when I go to install it on my desktop I get taken to this busybox shell. The install media works on VMware and my laptop so I know that is not bad. Ok so I overcome that issue by not using linux on my desktop unless its in a virtual machine. Now comes the 2nd issue which is installing things. I know this is going to sound really really dumb but right now I am over here feeling like pulling my hair out over this. Im fine until whatever it is is not in the software center. I cant install VMware tools on my virtual machine as it is a Tar.gz and I have no idea what to do with it. I try installing my graphics drivers so I can at least get the darn thing at a resolution I can use and nothing. It is a .rpm file and dont get me started on needing to install crap like java which is also a .rpm file. Every time I try to use linux and I have tried several times it is stuff like this that drives me away. Can someone give me an actual good explanation of it? I not only want to know how to do it but I want to know why it works that way so I can actually understand it rather then go through the motions without knowing why. Can someone on here help me? If not then oh well. I tried asking somewhere at least.

---

### Post by igdfpm on 2017-01-18
Ubuntu does not use rpm files - they are for RedHat based distributions (Fedora, Opensuse etc) and will not work in Ubuntu or any Debian based distro. The equivalent for Ubuntu/Debian is ".deb". Installing java in this way is unnecessary anyhow.

Which vmware client are your attempting to install?

---

### Post by howefield on 2017-01-18
> **ninjaking922 said:**
> I have tried out several distributions and keep running into the same problems with each of them. The first problem is when I go to install it on my desktop I get taken to this busybox shell. The install media works on VMware and my laptop so I know that is not bad.

Which version of Ubuntu are you asking about ?

The actual hardware that the installer sees will be different on your physical machine compared to what VMware will present. You could try the [nomodeset setting]("https://ubuntuforums.org/showthread.php?t=1613132"). 

> I cant install VMware tools on my virtual machine as it is a Tar.gz and I have no idea what to do with it.

[Installing VMware Tools from the Command Line with the Tar Installer]("https://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html") - scroll down to the scenario that suits your situation.

> Can someone give me an actual good explanation of it? I not only want to know how to do it but I want to know why it works that way so I can actually understand it rather then go through the motions without knowing why. Can someone on here help me? If not then oh well. I tried asking somewhere at least.

Try asking a specific question with relevant details, one per thread.

---

### Post by ian-weisser on 2017-01-18
> **ninjaking922 said:**
> The first problem is when I go to install it on my desktop I get taken to this busybox shell.
At what point in the install process does that happen?
Can you please lead us through the process that gets you there?

> **ninjaking922 said:**
> I cant install VMware tools on my virtual machine as it is a Tar.gz and I have no idea what to do with it.
A common VMWare question. See [https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525)

The rest of your problems are mostly due to your Windows power-user skills. Your prior experience is leading you to do very unwise things.
You are not the first. Many of us have been there.

howefield's advice is wise, listen to him. Slow down, handle one problem at a time, one per thread.
Your new skills will develop quickly that way.

---

### Post by mastablasta on 2017-01-19
in short - methods of install:

1. from software center usign default repositories
2. by adding a PPA, then program will appear in software center
3. by downloading a .deb file an dthen double clicking it
4. by using tar.gz compressed binaries - by extracting them into folder, finding the excetutable, marking it as executable and then running it
5. compiling from source - instructions should be in a readme file found after extracting the soruce. dependdencies have to be satisfied first though....

additional note - to install graphics drivers run additonal drivers utility. it should be found there. if it's not then there are (usually) no additional drivers to install and you need ot work with the opensource ones. various settings exist for those as well. however as noted above one quesiton per thread. this would, for example, belong to hardware or general help section. 

oh and when posting, particulary regarding hardware issues, help us help you - read this: [SIZE=2][https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)
[/SIZE]

---

### Post by vasa1 on 2017-01-19
> **ian-weisser said:**
> ...
howefield's advice is wise, listen to him. Slow down, handle one problem at a time, one per thread.
Your new skills will develop quickly that way.
+1 to one problem, one thread, especially with a descriptive title :) That would help future users as well.

---

