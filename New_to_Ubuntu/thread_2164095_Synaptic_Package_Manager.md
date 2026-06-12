---
title: "Synaptic Package Manager"
date: 2013-07-30
forum: New to Ubuntu
---

### Post by Shoalster on 2013-07-30
I would like to know how to find Synaptic Package Manager.  I'm getting low disc space messages and understand there is a way to clean the disc up.   Am I on the right track?
[h=2][/h]

---

### Post by oldos2er on 2013-07-30
Post moved to its own thread.

---

### Post by deadflowr on 2013-07-30
> **Shoalster said:**
> I would like to know how to find Synaptic Package Manager.  I'm getting low disc space messages and understand there is a way to clean the disc up.   Am I on the right track?


Run
```
sudo apt-get update
```
This will update the package lists, bringing the packages you install up to date.
Then run
```
sudo apt-get install synaptic
```
Click Y(yes) if asked.
Then look for the program synaptic in the menu system(dash if unity)

OR

find it in the software centre(center)

---

### Post by mojo706 on 2013-07-30
> **Shoalster said:**
> I would like to know how to find Synaptic Package Manager.  I'm getting low disc space messages and understand there is a way to clean the disc up.   Am I on the right track?


Follow the instructions given above then follow [this]("https://sites.google.com/site/easylinuxtipsproject/clean") tutorial to clear some disk space. Hope this helps if you have any other questions feel free to ask. :D

---

### Post by gordintoronto on 2013-07-30
The tutorial is mostly good, but it misses two steps:
sudo apt-get clean
sudo update-grub

The first command deletes the .deb files for updates which have been installed, the second one removes deleted kernels from the Grub list.

---

### Post by oldfred on 2013-07-30
The sudo update-grub only updates the grub menu with currently found kernels.

 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

To houseclean kernels, I prefer to use synaptic.

 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by Gadgetech on 2013-07-30
I wrote a tutorial a while ago to clean up old kernels from Ubuntu. You can find it here. [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

It's one real long bash command.

---

### Post by JoseeAntonioR on 2013-07-30
Also, ```
 sudo apt-get autoremove 
``` will remove packages your system doesn't need anymore.

---

### Post by mbabar96 on 2013-07-30
hi! You can use ubuntu-tweak to clean your pc or bleachbit then can install synaptic by
sudo apt-get update && sudo apt-get install synaptic

---

### Post by NikTh on 2013-07-30
> **mbabar96 said:**
> hi! You can use ubuntu-tweak to clean your pc or bleachbit then can install synaptic by
sudo apt-get update && sudo apt-get install synaptic

+1 

Use ubuntu-tweak or bleachbit. Be aware that bleachbit is a bit dangerous, read the options and warnings before proceed in any cleaning. 

[B]To install ubuntu-tweak 
[/B]
```
sudo add-apt-repository ppa:tualatrix/ppa 
sudo apt-get update
sudo apt-get -y install ubuntu-tweak
```
Open it, locate the "Janitor" button (low at right) and click it. 

[B]To install bleachbit 
[/B]
```
sudo apt-get update 
sudo apt-get -y install bleachbit
``` 
more on bleachbit can be found here: [http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

[B]To install Synaptic package manager
[/B]```
sudo apt-get update
sudo apt-get install -y synaptic
``` 

Synaptic How To can be found here: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Regards
 NikTh

---

### Post by ian-weisser on 2013-07-30
> **Shoalster said:**
> I'm getting low disc space messages and understand there is a way to clean the disc up.

Not using Synaptic, which is merely a (great) graphical frontend to the package manager.
The real question is: Do you know what is filling up your disk?
Old kernels? Data? Old logs? Cached packages? Localization files? Movies?

Most of the advice so far is great...if the problem is old kernels and/or cached packages. Sometimes it is, sometimes it's something else.

Look for packages that chart you disk usage for you. Find out what's taking up your storage.

For example:
Boabab (gnome)
xdiskusage(X)
ncdu (ncurses)

Once you know what the problem is, we can better recommend how to fix it.

---

### Post by deadflowr on 2013-07-30
Baobob is Disk Usage Analyzer.

Run the "scan file system" option at the top.(next to scan home)
It'll list usage from fullest to least fullest.

Edit: I forgot to ask which version of Ubuntu you're currently running?
Not that it matters much, just that it'll be easier to pin point solutions.

---

### Post by Shoalster on 2013-07-31
Good job.  Thanks.

---

### Post by Shoalster on 2013-07-31
Wow!  Thanks for all the good info here guys.  Will work on this in the A.M. and post results.

---

### Post by Shoalster on 2013-07-31
Thanks everyone.  Problem solved and I learned alot.

---

