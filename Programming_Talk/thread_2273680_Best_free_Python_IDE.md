---
title: "Best free Python IDE?"
date: 2015-04-14
forum: Programming Talk
---

### Post by Tom_Carr on 2015-04-14
What is the best free Python IDE for ubuntu?

---

### Post by TheFu on 2015-04-15
geany - but it isn't a full IDE - those are too bloated, IMHO.  Plus geany is cross-platform, so you don't have to use anything else on OSX or that other minor OS.

---

### Post by flaymond on 2015-04-15
I'm using Geany for every complex programming I do, and vim for general-purpose. You can hit f5 to run the program easily(other IDE also got this feature, but this easy to understand and small) , and don't need to worry about advanced features like in Eclipse. Geany is not a 'pure' IDE, but it's enough for me. I just use IDLE for Python though.

Thanks.

---

### Post by Tom_Carr on 2015-04-15
I tried spyder and IDLE yesterday and they both seem fine.  I will give Geany a try since you both suggested it.  
Is there anything that has a debugger that lets you step through the code line by line like in MS Visual Studio?
If step by step debugging is not available, which one makes it easiest to set breakpoints and look at the values of variables at the breakpoints?

---

### Post by Tom_Carr on 2015-04-15
In comparing the 3 (Geany, IDLE and Spyder) one thing I like about Geany is that it gives you a window listing all functions and variables, which I don't see in the other 2.

---

### Post by TheFu on 2015-04-15
[https://docs.python.org/3/library/pdb.html](https://docs.python.org/3/library/pdb.html) - might help. Perhaps you can tell geany to use it?

[http://www.findbestopensource.com/product/geanypdb](http://www.findbestopensource.com/product/geanypdb) - google found this - looks like what you want. I've never used it.

---

### Post by oldfred on 2015-04-15
I have used geany and like that you can quickly run a program.

But I found I had to add print statements, to export variables are various points. I then comment out print statements in case I need them again later. So I have lots of print statements scattered about.

---

### Post by TheFu on 2015-04-15
To be completely honest, I use vim for editing and have another window running with the pdb.  This is how I learned C/C++ and perl development. It is natural - especially if your mouse focus is "follows", not "clicks."  That focus policy change can be too much for people coming from Windows to swallow, I understand.

---

### Post by ofnuts on 2015-04-16
> **oldfred said:**
> I have used geany and like that you can quickly run a program.

But I found I had to add print statements, to export variables are various points. I then comment out print statements in case I need them again later. So I have lots of print statements scattered about.
I don't use print statements (plural),  I use a single one in a trace() function, with a static boolean that controls if things are printed:)

---

### Post by Dylan_Morshead on 2015-04-17
I would say pycharm community edition, It's what I personally use its amazing, the second being geany or idle, at the end of the day, its all personal preference.

If you're interested you can find it here.
[https://www.jetbrains.com/pycharm/](https://www.jetbrains.com/pycharm/)

---

### Post by flaymond on 2015-04-17
There's also Stani's Python editor. (I found it on Internet a while ago)

---

### Post by Tom_Carr on 2015-04-17
I downloaded pycharm but it's been so long since I installed anything outside of the software center that I have forgotten how.  I've looked for instructions online and they all seem unnecessarily complicated.  As I recall there is some quick and easy way to install something in a tar.gz folder.  Can someone refresh my memory?

---

### Post by TheFu on 2015-04-17
Best to avoid installing any software outside a package manager.  Look for PPA, so it integrates with your normal, weekly, upgrades.

---

### Post by Tom_Carr on 2015-04-17
Spyder has the winpdb debugger already set up, under the run menu.  I am going to use this and see how it works.

---

### Post by zacktu on 2015-04-17
I second the recommendation of PyCharm.  It has a debugger and seamless integration with a local git repository as well as github.  Refactoring works like a charm.   Although I've not tried PyCharm's sister products for other languages, I'm rather sure that one would be at home using any other of the IDEs that JetBrains provides.  I used Eclipse with Java and Python and found that keeping up with all the plugins was a chore.

---

### Post by Tom_Carr on 2015-04-18
> [COLOR=#000000]Best to avoid installing any software outside a package manager. Look for PPA, so it integrates with your normal, weekly, upgrades.[/COLOR]

You lost me.  I don't know what PPA means.  I did a google on ubuntu ppa and there are lots of instructions telling me how to install one, but nothing that tells me what it is.
If PyCharm is not in the software center, but I can download it from the pycharm web site, is there some better way to install it?  Please, if you have a few minutes, give me a few details or point me at a web site that will explain things.

I am obviously not an ubuntu power user.  I have been using ubuntu for years, but I mostly use it just like I would use windows or apple, with the GUI.

---

### Post by TheFu on 2015-04-18
Teaching to fish ... 

"What is a PPA?" Google found this: [http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them](http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them)

"pycharm ppa" found this:
[http://linuxg.net/how-to-install-pycharm-3-4-on-ubuntu-14-04-linux-mint-17-pinguy-os-14-04-and-other-ubuntu-14-04-derivatives/](http://linuxg.net/how-to-install-pycharm-3-4-on-ubuntu-14-04-linux-mint-17-pinguy-os-14-04-and-other-ubuntu-14-04-derivatives/)

A PPA is a way to add a repo from a trusted, cryptographically signed, location, to your ubuntu system. It is why we avoid downloading .deb files, avoid using install.sh and avoid tar.gz files to install software. With a trusted, updated PPA, managing software isn't any different than managing software from the offical repos. The only time it is complex is adding the PPA and when you do a release upgrade. The release upgrade process will remove unofficial PPAs (comment them out). If you are running 14.04, don't have to worry about that until June-ish 2016.

For a programmer, knowing and using PPAs should be 2nd nature. Most of us (All?) have gaps in our knowledge. You can fill in some of these with 3 hrs of background reading: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) It will save time and lots of frustration.

---

### Post by flaymond on 2015-04-19
Installing from ppa is easy as installing from repositories, you just need to know the commands and the address of ppa.

```
 sudo add-apt-repository ppa:<the/ppa/address> && sudo apt-get update && sudo apt-get install <program>
```

---

### Post by Misterio7 on 2015-04-20
I would recommend you **PyDev** ([http://pydev.org/](http://pydev.org/)), i use it a lot and personally think it is one of the best around!

**~[COLOR=#4b0082]Misterio[/COLOR]**

---

### Post by whereismymindat2 on 2015-11-29
> **Tom_Carr said:**
> What is the best free Python IDE for ubuntu?

@[**[COLOR=#000000]Tom_Carr[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844305")

You might like PyCharm 



Pycharm  (this provides the *.deb package). 
[http://www.ubuntuupdates.org/package/getdeb_apps/wily/apps/getdeb/pycharm](http://www.ubuntuupdates.org/package/getdeb_apps/wily/apps/getdeb/pycharm)


PyCharm PPA
[https://launchpad.net/~mystic-mirage/+archive/ubuntu/pycharm](https://launchpad.net/~mystic-mirage/+archive/ubuntu/pycharm)




Or the Install Script (from PPA--*****FOR TRUSTY******** (CHANGE TO YOUR VERSION)--IF NOT "TRUSTY"
```

############################################
PYTHON IDE (LAUNCHPAD PPD)
Pycham

sudo add-apt-repository -y ppa:mystic-mirage/pycharm;sudo apt-get update;sudo apt-get install -y --force-yes pycharm pycharm-community 
############################################



```

---

