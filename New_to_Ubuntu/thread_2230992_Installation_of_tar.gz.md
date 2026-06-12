---
title: "Installation of tar.gz"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by kev5 on 2014-06-22
As the thread says, I have read and watched videos but have no idea how to install peerguardian or any other tar.gz.

I have literally only just installed this and is my second time on this OS.

If some one could give me a THOROUGH talk through or even a link (as I presume this has been posted before) that would be grateful. 

I have installed this OS previously but wiped immediately due to this problem, but now I have a bit of time I would like to learn as it seems 100 times better than other OS.

Thanks in advance 

Kev

---

### Post by Mark Phelps on 2014-06-22
There are several different ways to install apps in Ubuntu, and you have chosen the one that involves the most work, is the most difficult, and least friendly to changes.

You should use either the Software Manager (easiest way) or Synaptic Package Manager (Second easiest way) to install apps.

---

### Post by Vladlenin5000 on 2014-06-22
Peerguardian isn't in the Ubuntu repositories therefore it can't be installed via Software Center or Synaptic...
The second best things concerning software installation are the PPAs and fortunately there's one for Peerguardian. Use this instead of compiling - compiling definitely ISN'T for noobs.
Instructions here: [http://ubuntuhandbook.org/index.php/2013/07/install-peerguardian-ubuntu-13-10-13-04-ppa/](http://ubuntuhandbook.org/index.php/2013/07/install-peerguardian-ubuntu-13-10-13-04-ppa/) (although the article only mentions previous Ubuntu versions the PPA already has packages for trusty (14.04)).

---

### Post by jahidul hamid on 2014-06-22
The installation process depends on the content of the archives. As i don't know what that archive contents i simply can't help you that much. Bu here's a tutorial that can help you with much more information about installing processes of various packages:
[http://community.linuxmint.com/tutorial/view/1525](http://community.linuxmint.com/tutorial/view/1525)

---

### Post by Vladlenin5000 on 2014-06-22
> **jahidul hamid said:**
> The installation process depends on the content of the archives. As i don't know what that archive contents i simply can't help you that much. Bu here's a tutorial that can help you with much more information about installing processes of various packages:
[http://community.linuxmint.com/tutorial/view/1525](http://community.linuxmint.com/tutorial/view/1525)

Useful indeed but completely unrelated. There's only the source code available at sourceforge, where the OP got his/hers. As such, instructions for compiling are in order. OTOH, the article I posted has the complete instructions for installing it via a PPA - much easier for noobs-.

---

### Post by jahidul hamid on 2014-06-22
> **Vladlenin5000 said:**
> Useful indeed but completely unrelated. There's only the source code available at sourceforge, where the OP got his/hers. As such, instructions for compiling are in order. OTOH, the article I posted has the complete instructions for installing it via a PPA - much easier for noobs-.

But kev5 is talking about installing from an archive (tar.gz) not from repo or ppa. That archive may contain source code or precompiled package or just a installer....

---

### Post by kev5 on 2014-06-22
Thanks for your help people but.............. its just totally put me off the length of time it takes just to install an application.

I love the OS just cant get to grips with the lengthy ways around the smallest of tasks.

I've had 4 replies and each has a different answer and way of doing it, and some not knowing as they don't know what the package contains.

But thanks again to the people who have replied, I appreciate your help

Kev

---

### Post by kev5 on 2014-06-22
this is what I was trying to install  [http://sourceforge.net/projects/peerguardian/files/PeerGuardian%20Linux/2.2.4/](http://sourceforge.net/projects/peerguardian/files/PeerGuardian%20Linux/2.2.4/)

but I also have other apps to install which I really don't want to have to open a forum to do each time...............

---

### Post by coffeecat on 2014-06-22
> **kev5 said:**
> Thanks for your help people but.............. its just totally put me off the length of time it takes just to install an application.

I love the OS just cant get to grips with the lengthy ways around the smallest of tasks.

I've had 4 replies and each has a different answer and way of doing it, and some not knowing as they don't know what the package contains.

But thanks again to the people who have replied, I appreciate your help

Kev

Let me try and help. Installing from source code in a tar.gz, if you are relatively new to Linux, should be your absolute last option when every other avenue has been exhausted. Use Software Centre and the repository apps if you can. If you can't, search for a PPA. Activating a PPA requires a simple command in the terminal and you can then install the PPA packages in the Software Centre in minutes with a few mouse clicks, or from the terminal with a couple of simple commands. For Peerguardian, follow the link in Vladlenin5000's post. It's quite straightforward.

If you want to install other apps that are not in the Software Centre, you are very welcome to start a new thread. Forum members will be able to advise you on the best PPA.

---

### Post by oldos2er on 2014-06-22
Post #3 answers your question; all you need do is copy and paste three commands into a terminal to install peerguardian.

---

### Post by buzzingrobot on 2014-06-22
> **kev5 said:**
> Thanks for your help people but.............. its just totally put me off the length of time it takes just to install an application.




In so many words, you are doing it wrong.  Tar.gz are only rarely packages containing software ready to be installed.

A tar.gz file in Linux almost always contains a compressed archive containing source code that needs to be compiled.  I.e., it is intended for developers, not users. It contains text files, not software.  It is the direct equivalent of a Windows zip file that contains source code, not ready-to-run software.

Software packaged for installation in Ubuntu will end in a '.deb' extension. Tens of thousands of these packages are available in the Ubuntu repositories for point-and-click installation via Ubuntu's Software Center or other similar applications. As mentioned, PPA's also offer software built and ready-to-run on Ubuntu.  The difference:  Canonical is not responsible for software in the PPA's.

As mentioned, PeerGuardian has been built for Ubuntu and is available here: [https://launchpad.net/~jre-phoenix/+archive/ppa](https://launchpad.net/~jre-phoenix/+archive/ppa).  Be sure to read the section titled "Adding this PPA to your system".  It's dead simple. After that, you can search for PeerGuardian in Software Center or open a terminal and enter "sudo apt-get install pgl".

---

### Post by kev5 on 2014-06-23
Ok thanks everyone, ive decided to have another go, will uodate if necessary

Thanks

---

