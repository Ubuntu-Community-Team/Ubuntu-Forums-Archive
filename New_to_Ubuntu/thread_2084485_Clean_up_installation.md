---
title: "Clean up installation"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by Esokra on 2012-11-15
Hello

I am a happy Ubuntu user since a few years. I have been using Ubuntu as my main operating system, as well in different Virtual machines etc. One issue I have run into very often is, running out of space, although I did not install any additional software (not even updates, as it was in a VM), nor did I save so many files etc. 
To make an experiment, I set up Ubuntu in a VM, used it a few months heavily and tried to clean up the installation, completely. 
I purged all additional software with 

```

sudo apt-get --purge remove 

``` 

removed all unneeded packages with 

```

sudo apt-get --purge autoremove 

```

and finally ran the following commands

```

sudo apt-get autoclean
sudo apt-get clean 

```

Finally I added a new user and deleted the old one (I did not need the data anymore). 
So I only had all packages left, which were installed by default (even less, as I had deleted libre office). Compared to a clean install (3.1 GB) there were 4.5 GB, so I am asking right now, where the 1.4GB come from? I even deleted all the track history under privacy in the system settings. Are this log files? I can warrant, that I have never saved anything in the root homefolder, or in the file system outsie home. 
Are this 1.4 GB all log files?
What else can be done in order to clean the installation?(I know it does not make sense, but I want to keep my installs clear over a longer period of time)

Thank you in advance!

---

### Post by mikewhatever on 2012-11-15
Let's see how many kernels and headers there are:
```
dpkg -l| grep -e linux-image-[0-9] -e linux-headers-[0-9]
```

Quite a few of them can get stacked up in a few months time.

---

### Post by oldsoundguy on 2012-11-15
Many use the third party "ubuntu tweak" to do the clean up.  I do,  Run it about once a month. (get rid of those excess kernels) But, I store my pictures, videos & music off of my main hard drive, so never run out of space using a 250gb HD.(storing off drive makes doing a back up a lot easier .. only need to copy my ~/home folder.)

---

### Post by Esokra on 2012-11-15
Thank you for answering!
I wanted to mention it first, that there are no additional kernels, but then I decided to not write it explicitly, as I thought it would be a consequence of not updating, which, I have to admit, is not always true. 
So there are no additional kernels, as the output confirms:

```

ii  linux-headers-3.2.0-23                 3.2.0-23.36                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-23-generic         3.2.0-23.36                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-23-generic           3.2.0-23.36                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP

```

I cleaned with Ubuntu tweak too and uninstalled it aftwerwards, so everything is clean, according to the Janitor of Ubuntu Tweak.

---

### Post by Esokra on 2012-11-16
Today I found an interesting issue:

While passing the wrong option to a tmpfs Ramdisk (in etc/fstab), the system did not boot, so I corrected the entry from shell. When I rebootet, there was a noticeable disk usage difference of several megabytes. Does Ubuntu make backups of system files?

---

### Post by mikewhatever on 2012-11-17
How about running something like this:
```
du -h | sort -nr | head -n20
```

That will show the list of 20 largest files in you home folder.

---

### Post by Esokra on 2012-11-17
Hello

I could find the problem: There were many folders left from arkose sandbox and lxc, by deleting them, I freed up much space.
Now I have nearly a clan install, but there are a few questions left for me:

Although exactly all the same packages are installed (comparing a new clean install with the old cleaned one) there are a few differences (All folders despite usr, lib and etc are approximately (only a few kb difference) equal in terms of space) I do not understand:

usr is 500 MB larger on the cleaned up (old) install 
lib is 4 MB larger on the cleaned up (old) install 
etc is 2 MB larger on the cleaned install 

(According to du)

So what makes this huge difference? (I really made sure to uninstall everything, which is not on a clean system (I did this with deborphan, apt-get --purge remove, autoremove and manually with find, for example: find | grep google-chrome | xargs rm -rf). Furthermore I cleaned up var (which made another 500 MB difference). 
What makes the huge difference for /usr ? As far as I am concerned this folder contains user programs, but how is the difference possible, if I removed all additional software?

I would be really glad if you could help me to solve that problem!

Thanks for all that help!

---

### Post by Esokra on 2012-11-17
Has anybody an idea how to examine the difference (I do not want and I do not have the time to go through the content of these directories. ) I have already tried to save the output of ls -lh of these directories and use diff for the files, but still I would have to go manually trough the lines. How to find out the additional files and directories for comparing to directories?

Another idea would be, to use the package manager to examine which packages are installes (all) and comapre it (but still I would need an comfortable way to compare this information on two different system). I think this would be sensible, as I must have missed packages, since the usr directory only contains programmes.

---

### Post by mikewhatever on 2012-11-18
Run 'du -h /usr | sort -nr | head -n20' on the clean and cleaned install to see the dufference of the /usr directories. I don't know of any other way to troubleshoot it.

---

### Post by Esokra on 2012-11-18
For both systems I did:

```

dpkg -l | grep ^ii | sed 's_  _\t_g' | cut -f 2 > installed-pkgs

```

in order to get a list of installed packages.
Then I named one file o and the other n. (o is cleaned up install, n is new install)
After this I sorted both files with:


```
sort -o so o
sort -o sn n
```

After this operation I ran

```
comm -31 so sn >> in-sn-notin-so.txt 
comm -32 so sn >> in-so-notin-sn.txt 
```

in order to sort out the packages which are installed on both systems. 
"in-sn-notin-so.txt" contains the packages which are missing on the cleaned up install, but are part of a new install (I decided to install these)
"in-so-notin-sn.txt" contains the packages which are on the cleaned up install, but are not part of a new install. This packages are the ones we want to remove.

!!!! But we have to be careful, as I noticed, that the clean install had a different kernel version, so we have to modify both files and remove the lines beginning with "linux-".  

As these are many packages and we want pack them in one command "sudo apt-get --purge remove ... "
we have to transform the files consisting of many lines in a file, containing all these packages in one line. This is done with:

```
tr '\n' ' ' < in-sn-notin-so.txt  > install.sh
tr '\n' ' ' < in-so-notin-sn.txt  > remove.sh
```

So finally I modifed remove.sh to: 

```
#! /bin/bash
apt-get --purge remove (here comes the content of remove.sh) 
```

and made it executable (chmod u+x remove.sh) . I did the same with "apt-get install" for the file install.sh.

After I ran both scripts finally both installs had the same size, so cleaning up the old system was sucessful! 

After all I ask myself why all these packages were not removed (as these packages were not deliberately installed, so they were dependencies) by the "apt-get --purge remove" command? For example I have never installes "apache2-utils" etc. 
An explanation would be, that I have installed packages from ppa (but not many) and apt-get can not find or uninstall all the dependencies? 
What can I do in order to prevent these things in the future? It seems apt-get is not fully capable of removing all dependencies coming with one package, is there a better alternative?
What to do in order to remove all dependencies while removing an application.?
I could write a script similar to the way we cleaned up the install, which captures the difference of installed packages while installing and then removes all this, when I want to remove the package. But is there a better way?

Thank you for all your help and ideas!

---

### Post by Zill on 2012-11-18
> **Esokra said:**
> ...Compared to a clean install (3.1 GB) there were 4.5 GB, so I am asking right now, where the 1.4GB come from?...
I have followed this thread, as an experiment, with interest and agree that there is possibly scope to improve the performance of apt-get.

Having said that, unused packages in a system generally do not cause any problems and, with HDD storage currently costing around 6p (10c) per GB, I do question if any such work would be cost-effective.

---

### Post by Esokra on 2012-11-18
It would still be nice, as the system would be more clean and transparent. I think if we have the power of a central package management system in unix like system, we should use the power. Suppose an app installs spyware libaries. In this case you want a reliable way to remove all the packages which were installed with a certain program. Furthermore, I do not want that ubuntu becomes such an untransperent system like windows, where every application can store as many registry keys as it wants. 
Now I have another question, what about the write access to directories like /usr? Is a program blocked to, for example save logs in /usr instead of /home or /var? (If I understood this right, yes, as far as it does not run as root).

---

### Post by Zill on 2012-11-18
Esokra:  FOSS cannot generally, due to it's open-sourcing, contain spyware or other malware.

In the unlikely event that a malicious "binary-blob" had been installed, I doubt if most users would be interested in trying to forensically remove affected packages.  The quickest and easiest way to get a "clean" installation is simply to re-install the system.
> **Esokra said:**
> ...Now I have another question, what about the write access to directories like /usr? Is a program blocked to, for example save logs in /usr instead of /home or /var? (If I understood this right, yes, as far as it does not run as root).
I don't quite follow your question.  /usr, like most system directories is owned by root with 755 permissions.  This means that only root can write to the directory.

---

### Post by Esokra on 2012-11-18
Still, I would be interested in having a clean system, but your argument about cost-effectiveness is absolutely right. 
Secondly, clean is not equivalent to new install, as I said, cleaning the system completely and get a system, that is like a new, makes no sense. This was only an experiment to prove, that apt-get does not catch all dependencies in terms of removing. 
But my vision is, to keep the system clean (without reinstalling everything, which is not sensible, as it costs too much time and ressources for very complex systems, remember, you would have to reconfigure everything). 
As said, this was an experiment, with the information i got, i hope to be able to write a script, which builds up on apt-get and is able to catch all dependencies when uninstalling a certain program (not turning a used system into a new). Sure, to make this possible, applications would have to be installed with my script. Maybe I will implement it in c++ (again, everything will be based on apt-get, but will be extended with information, apt-get is not able to get by design). 
I will post details of a possible implementation, as soon as my rough idea is more perfect (and considers all possible issues). I will also provide more information, about the experiment.
I hope you stay interested and help by sharing ideas.

Thank you

---

### Post by Zill on 2012-11-18
> **Esokra said:**
> ...This was only an experiment to prove, that apt-get does not catch all dependencies in terms of removing...
I agree that this is an interesting experiment.
> **Esokra said:**
> ...But my vision is, to keep the system clean (without reinstalling everything, which is not sensible, as it costs too much time and ressources for very complex systems, remember, you would have to reconfigure everything)...
With most systems, a straightforward reinstall (i.e. of the same OS release) is fairly quick.  Complex configurations can easily be restored from backups of, for example, the /etc directory.
> **Esokra said:**
> ...As said, this was an experiment, with the information i got, i hope to be able to write a script, which builds up on apt-get and is able to catch all dependencies when uninstalling a certain program (not turning a used system into a new)...
This is certainly one option.  Alternatively, could you produce a patch for apt-get that would produce the desired results?  This would probably be a "neater" solution. ;-)

---

### Post by Esokra on 2012-11-18
I have already read very much about this topic. As far as I understand there is nothing wrong about apt-get. 
All the requirements to keep the system clean do already exist, but it requires manual work and knowledge how to keep the system clean and remove a program with all its dependencies (I am not talking about dependencies needed by other apps, as this would make absolutely no sense).
I will continue to research an implement a confortable and automatic way.

---

### Post by Cheesemill on 2012-11-18
If you use the aptitude command instead of apt-get to install and remove all of your programs then all unneeded dependencies ***are*** removed. This is one of the reasons it's the first thing I install on any system before adding any other packages.

In your case I don't think it would have made a difference because it only tracks dependencies of packages that were installed using aptitude.

---

### Post by Esokra on 2012-11-22
I have read very much about dpkg and deb packages. But this issue seems impossible to solve for me because of one issue: dpkg scripts. There seems to be no automatical way to undo the changes made by these scripts. They can create files and folders where they like and if the remove script does not undo these, the changes remain. This information can be found in

```

/var/lib/dpkg/info 

```

I know a good package should not be any issue, still I ask myself, whether it is possible to undo really all changes made by the package manager, in case the package is of bad quality?

---

### Post by LuisGMarine on 2012-11-22
This might be a little off topic, but what about using Ubuntu Tweak?  After installing Ubuntu 12.10 and running all the updates, I ran the Janitor feature in Ubuntu Tweak and it was able to delete over 100MB in unused packages and random files that could be deleted.

Just my two cents, but I"m going to follow this thread considering it is a very interesting topic.:guitar:

---

### Post by Zill on 2012-11-22
> **Esokra said:**
> ...I know a good package should not be any issue, still I ask myself, whether it is possible to undo really all changes made by the package manager, in case the package is of bad quality?
As long as you stick to the official repos for a supported release you really should not get a package of "bad quality"!

In the unlikely event of a "rogue" package getting through, it should be a simple matter to manually remove the offending package(s) or to regress to an earlier version.  A full history of package changes, including dependencies, is logged in /var/log/apt/history.log.   Earlier versions are zipped with a numerical suffix eg. /var/log/apt/history.log1.gz etc.

---

