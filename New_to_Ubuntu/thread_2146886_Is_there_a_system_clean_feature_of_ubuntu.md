---
title: "Is there a system clean feature of ubuntu"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by saracen666 on 2013-05-20
Hi All,
         Just started with ubuntu 12.04 LTS and wandered if there is a system cleaner equivalent for Ubuntu? Similar to what ccleaner does for windows.

---

### Post by rrich1974 on 2013-05-20
just some simple commands:
sudo apt-get update
sudo apt-get autoremove
sudo apt-get clean

that is all you need!

---

### Post by ajgreeny on 2013-05-20
It is not really needed in Linux as it is in Windows, but nevertheless if you regularly run the commands ```
sudo apt-get autoclean
sudo apt-get autoremove
``` you will remove a lot of unnecessary cruft from the system.  You can also use synaptic, which you will need to install first, to remove cleanly any unwanted kernels that have been installed by normal updates to the system.  Always keep the most recent and the previous kernel, but I recommend you remove all the rest.  You can find all kernels that you have by running ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
```

There are also some applications such as **bleachbit** which can remove a lot of files/folders/applications etc etc that it thinks are not needed, but personally, I dislike that, and others like it, as they have a tendency to be rather draconian in action, removing applications they think are superfluous that you may have installed for particular good reasons.  Use them by all means but look carefully at any list of proposed removals before going ahead.

---

### Post by siddharth007 on 2013-05-20
Try TweakUI.Its a GUI tool which has features of Ccleaner.There are lot of other stuff to explore as well.For more info visit this [link]("http://bluesteel007india.blogspot.com/2013/03/tweak-your-ubuntu-with-this-smart-tool.html")

---

### Post by richierich1986 on 2013-05-20
Ubuntu Tweak has a cleaning function as well. It works very well and can remove old kernels and old cached installation files safely. It also removes old configuration files.

I used to use bleachbit, but it kept destroying my system stability, even though I knew what to uncheck before cleaning.

---

### Post by 3rdalbum on 2013-05-20
There is not really any need for such things. The package manager keeps track of what files are installed and will remove them again when you remove the package. The only exceptions are dependencies (use the Autoremove function mentioned above, but dependencies will not use any CPU time, only a small amount of disk space) and preferences files (which wont slow down your system and will take up less than 100k each)

---

### Post by saracen666 on 2013-05-20
Thanks will try tonight. UK time.

---

### Post by saracen666 on 2013-05-21
Thanks for the advice guys. Worked a treat. Ran terminal commands and installed ubuntu tweak. Cleaned about a 2GB off and running well!

---

### Post by monkeybrain2012 on 2013-05-21
install bleachbit from the repository. sudo apt-get autoremove and sudo apt-get autoclean doesn't clean your home directory,

---

### Post by ajgreeny on 2013-05-21
> **monkeybrain2012 said:**
> install bleachbit from the repository. sudo apt-get autoremove and sudo apt-get autoclean doesn't clean your home directory,

As I said before, be very careful with bleachbit and other "cleaners" as they can remove things you want and need if you just blindly remove everything they list.

---

### Post by Archit88 on 2013-05-21
"Ubuntu Tweak"
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by saracen666 on 2013-05-21
Thanks ajgreeny. What should I be looking for when determining what not to clean? Are there things that definately should not be touched?

---

### Post by todorakiggg on 2013-05-21
The last question was a good one. Guys please share what we (the beginners) can safely clean and what we shouldn't touch.
I recently used Ubuntu Tweak, which resulted in fatal errors ....

---

### Post by ibjsb4 on 2013-05-21
I guess anything is possible, but I have been using BleachBit since version 8.04 without any major issues.  What I have used as a general rule is anything you check that gives you a pop-up should not be used.  Also when cleaning your browser(s) take a close look.  There are good cookies, do you really want to wipe your passwords?  Things like that.

---

### Post by Mark Phelps on 2013-05-21
BIG +1 for what ajgreeny warned about ...

What many folks do NOT realize is that there is absolutely no need for the registry cleaners that are used in Windows.  The registry is a collection of databases, and apart from taking up some space (which is readily available these days!) does absolutely no harm to have unused entries still present.  On the Win7 forums, we regularly advise AGAINST using cleaners as they often do more harm than good.

That said, there is no registry in Linux, so there is no need for such a cleaner.

Furthermore, I made the mistake myself of using a "janitor" Linux product a while back -- and it trashed my system so bad, I had to reinstall from scratch.

So basically, the safest thing to do is leave things alone.

---

### Post by monkeybrain2012 on 2013-05-22
janitor and deborphan are dangerous. Bleachbit is very safe. People who warn you about the sky falling likely haven't used it. Just check the boxes for what you want to delete, usually cache and stuffs like that in the home directory.

The screenshots show my configurations. For the home directory I left out "session" for Firefox and Chrome because I want to restore my tabs on restart. The flash cache shouldn't be checked if you made some changes in your flash settings. You probably don't want to remove passwords, but I don't like to save them as sometimes other people use my computers.

For the root directory basically it just automates standard operations like apt-get autoremove, autoclean and emptying the cache along with getting rid of unused localizations(that alone takes up more than 1/2 a G) and other random debris. Sure I can use the command lines to do this but it is just handy. Computer was invented for labour saving, so I make no apologies for being lazy :)  I have multiboot machines and have installed Linux distros on external drives and usb drives etc Sometimes,especially for testing I don't make very big partitions. Bleachbit is very useful and convenient in reclaiming space.

Never tried deep cleaning and cleaning memory. Those sound a bit involved and there are warning pop ups for those.

Ubuntu tweak on the other hand is overkill IMO, all its options are already available in the standard gui tweak tools, too many duplications for me to see its purpose.

---

