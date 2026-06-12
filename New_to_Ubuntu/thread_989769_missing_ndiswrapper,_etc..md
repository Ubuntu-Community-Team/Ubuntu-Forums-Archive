---
title: "missing ndiswrapper, etc."
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Lostin60's on 2008-11-21
Hi all. My disclaimer:I am the Sgt. Schultz of Ubuntu **I know nothing!** I just installed ubuntu 8.4.1, and started to config my internet. Ubuntu detected my Realtek RTL8139/810x NIC driver Following the users guide I discovered I have no ndiswrapper or ndisgtk. I went on line and got them, but don't know how to get them to ubuntu in the right file format. Once I get them there I can carry on until the next roadblock. Part of my problems will concern running command lines, so if there is a tut for that it sure would help. I prefer to do as much as I can in the terminal. Best way to learn is by doing.  I plan to be answering questions instead of asking them asap. All help will be appreciated (even helpful flames..lol)
Thanks,
Lostin

---

### Post by Skripka on 2008-11-21
IF you have a wired connection (i.e. working network) on your Ubuntu setup:

Open up Synaptic Package Manager, and search for "ndiswrapper" there should be 2 pacakages (Ndiswrapper-utils, there's another one can't remember the name OTTOMH), right click both and select "install" from the context menu, then Apply--you're done.  The same for Ndisgtk.


If you really WANT to do it by command line :KS ..........

---

### Post by pytheas22 on 2008-11-22
What Skripka says above will work if you want to install using a graphical interface (Synaptic), but if you want to install ndiswrapper from the terminal, you can just type:

```
sudo apt-get install ndiswrapper*
```

ndiswrapper is actually composed of two packages, 'ndiswrapper-common' and 'ndiswrapper-utils-1.9', but if you type 'ndiswrapper*', the * will serve as a wildcard character and match both packages.

Just thought I would explain this, since you say you prefer to do it the command-line way...but keep in mind that the command-line is not as essential in Linux these days as some of Linux's detractors would like you to think :)

---

### Post by Lostin60's on 2008-11-22
> **Skripka said:**
> IF you have a wired connection (i.e. working network) on your Ubuntu setup:

Open up Synaptic Package Manager, and search for "ndiswrapper" there should be 2 pacakages (Ndiswrapper-utils, there's another one can't remember the name OTTOMH), right click both and select "install" from the context menu, then Apply--you're done.  The same for Ndisgtk.


If you really WANT to do it by command line :KS ..........


I am on an HPZD8000 laptop running that  is not hardwired to the router, strictly wireless. ndiswrapper and ndisgtk are not in my package manager. I d/l them in windows, but I need to get them into ubuntu. My HDD is partitioned into 3, one is windows one is ubuntu and one is just an fat32 file system, if that helps.

---

### Post by Skripka on 2008-11-22
> **Lostin60's said:**
> I am on an HPZD8000 laptop running that  is not hardwired to the router, strictly wireless. ndiswrapper and ndisgtk are not in my package manager. I d/l them in windows, but I need to get them into ubuntu. My HDD is partitioned into 3, one is windows one is ubuntu and one is just an fat32 file system, if that helps.

I would highly recommend if at all possible to use a hardwired connection for this, if at all possible.


The alternative being to compile Ndiswrapper et al from source, it isn't that hard-if you follow the README (there are 5 or so very short and easy steps--if all goes well) docs....but for a newbie it can be a rough start, although we all have to start somewhere....odds are to do the compile you're going to need lots of other libraries that you don't currently have-which if you have a working wired net connection are easy to get and install.

Perhaps someone has precompiled Ndiswrapper binaries they know of?

---

### Post by pytheas22 on 2008-11-22
> I am on an HPZD8000 laptop running that is not hardwired to the router, strictly wireless. ndiswrapper and ndisgtk are not in my package manager. I d/l them in windows, but I need to get them into ubuntu. My HDD is partitioned into 3, one is windows one is ubuntu and one is just an fat32 file system, if that helps.

Conveniently, the ndiswrapper packages come on the Ubuntu live CD.  So just make sure your CD is in the drive, then go to System>Administration>Software Sources.  Under the 'Ubuntu Software' tab, you will see a section labeled 'Installable from CD-ROM/DVD'.  Check the box there to enable use of your CD as a repository.  Then close the window.  If you're asked about reloading the sources list, say yes.  Then just run these commands in a terminal:
```

sudo apt-get update
sudo apt-get install ndiswrapper*
```

That should work, but if it doesn't, there are other options (there are pre-compiled binaries for ndiswrapper available from packages.ubuntu.com)...

---

### Post by Lostin60's on 2008-11-22
Many thanks to all. Special thanks to Pytheas22. My issue was needing ndiswrapper, as it was not in my package manager. Pytheas22 hit the nail on the head. I am going to try it now. Again, I appreciate the time and effort of all who replied.

---

