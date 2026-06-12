---
title: "Can I generate a Synaptic download script from the command line?"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by cortman on 2011-12-08
I don't have internet access at home, but it's quite convenient to make download scripts on my home computer of any software I want and download it at work with my virtual box. I was wondering how I could do that (generate download script) strictly from the command line?
Thanks!

---

### Post by MikeJParry on 2011-12-08
Check 
apt-mirror.sourceforge.net
```
apt-get install apt-mirror
```

---

### Post by cortman on 2011-12-08
> **MikeJParry said:**
> Check 
apt-mirror.sourceforge.net
```
apt-get install apt-mirror
```

That's not at all what I'm asking or looking for.

---

### Post by Lars Noodén on 2011-12-08
> **cortman said:**
> That's not at all what I'm asking or looking for.

Can you clarify what it is that you are looking for?  [apt-get](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html) allows you to install and remove packages in the shell.  And so it is usable in scripts.

---

### Post by oldfred on 2011-12-08
Is something like this what you want?
Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

If running similar systems, you can just copy debs. But if you get out of sync, you may get into the old dependency hell issue.
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

---

### Post by Paqman on 2011-12-08
How many packages are we talking about? Using apt-get you can string together any number of packages to install:
```
sudo apt-get install package1 package2 package3
```

So a simple copy and paste to/from a text file would be perfectly workable for relatively small numbers of packages.

---

### Post by cortman on 2011-12-08
Sorry for not being clear. What I meant is this: I open Synaptic on my offline computer, select which packages I want to install, and then go File>Generate Package Download Script, which creates a .sh file with instructions on which packages to download. It's all done in the Synaptic GUI, and I was wondering if I could do the same thing with apt-get in the command line.

---

### Post by cortman on 2011-12-08
The advantage for me of using download scripts is that, like oldfred was saying, I make sure I get all the libraries and dependencies resolved for my particular Ubuntu installation,
I can do it with the Synaptic GUI, can I do it from the command line as well?

---

### Post by Paqman on 2011-12-08
> **cortman said:**
> The advantage for me of using download scripts is that, like oldfred was saying, I make sure I get all the libraries and dependencies resolved for my particular Ubuntu installation,
I can do it with the Synaptic GUI, can I do it from the command line as well?

Syn**apt**ic is just a front-end for APT, so using the command line will pull in all the dependencies just like Synaptic will. Btw, the same goes for Ubuntu Software Centre, Update Manager and even installing using a .deb file. They all use the same underlying package manager.

---

### Post by cortman on 2011-12-08
> **Paqman said:**
> Syn**apt**ic is just a front-end for APT, so using the command line will pull in all the dependencies just like Synaptic will. Btw, the same goes for Ubuntu Software Centre, Update Manager and even installing using a .deb file. They all use the same underlying package manager.

That's right, so my question is what is the command for apt-get to generate a download script that includes not only the main program I want to install, but all dependencies that aren't currently installed as well?

---

### Post by Lars Noodén on 2011-12-08
[apt-get](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html) will download and install the package and any dependencies it might have all automatically. 

You might try specifying [font=Courier New]--dry-run[/font]

What are you trying to do with the script?

---

### Post by cortman on 2011-12-08
> **Lars Noodén said:**
> [apt-get](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html) will download and install the package and any dependencies it might have all automatically. 

You might try specifying [font=Courier New]--dry-run[/font]

What are you trying to do with the script?

I want to download the package and all dependencies as .deb files, put them on flash drive, take them to my offline computer, and install them there. The script would come from my offline computer and would simply tell my online computer what dependencies ARE already installed on my PC.
I want to download all the packages, but not install them.

---

### Post by casperlingus on 2012-03-17
ARGH! Are people even reading the question before answering?  I have been searching for hours to figure out how to do this with no success, and reading through this thread has been so painful...

**OFFLINE COMPUTER** needs packages installed.  It does not have an internet connection, so it cannot download them.  Synaptic Package Manager has a cool **Graphical User Interface** for doing this, but I would like to do it from the command line instead.  

So to be *even more clear*... If my computer was on the internet, I would type 

```
sudo apt-get install progA progB progC
```

**But I can't**.  Instead I have to go to Synaptic, manually select progA progB and progC and use the "Generate Download Script" which not only tells the online computer what packages to download, but also which dependencies it needs. 

It is shuttled to the online computer to download, and then the packages are shuttled back, and installed **again** using Synaptic.  

I would like to remove Synaptic Package manager from this process, entirely.

```
sudo apt-get install progA progB progC --createOfflineScript
```

But so far, I haven't found any evidence that this exists...

---

