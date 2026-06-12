---
title: "Does linux slow down over time  via collection of redundant file leftovers like Win?"
date: 2014-09-03
forum: New to Ubuntu
---

### Post by garycheng12 on 2014-09-03
Does linux slow down over time  via collection of redundant file leftovers like Windows? I just installed Kubuntu on a crappy laptop to play around with it as a long time Windows users. I get the sense that Linux, because of its famed stability over Windows, that Linux never slows down. In Windows, you have useless registries left over from uninstalling and installing applications that can not only slow down your machine but also create problems in the future. As a result, It is almost expected that an avid Windows user reformat his computer every 6 months/a year or so.

On Kubuntu (or linux in general), I just freshly installed the OS and I am at the point where I remove any unnecessary pre-installed applications and install the ones I want. If I uninstall Firefox via the software manager (is this the best way to accomplish this task?), how can I be sure that all associated files of Firefox, such as its cache, cookies, etc.. and all its dependencies unique only to Firefox be deleted? In Windows, I can check that the Firefox folder is gone on Program Files and I can run a registry cleaner such as CCleaner to track down Firefox registries that are lfet behind after it is uninstaled. What about Linux?

Essentially, can an avid computer user that wants to keep his computer optimized expect to use a Linux distro for years without reformatting? 

Thanks!

P.S. Currently trying to find an article that explains how repostories, packages, sources, and source codes work because one does not simply go to an application's homepage to download and run an installer to get an application.

---

### Post by uRock on 2014-09-03
I've only had one install that I've let run for as much as a year without doing a fresh install. But I have never run a fresh install due to the system getting slow. It usually happens because I want to check out a newer release. I do plan to run Ubuntu 14.04 until ubuntu 18.04.1 comes out.

I haven't seen the slow down over time with Windows 7. I just deleted my Windows install yesterday, as I only need it for one application and I'd rather run it in a VM than have to restart my system every time I need to download and convert a video file from my security cam DVR or change its settings. One day I'll learn enough about coding to write my own OS to flash to the server, but until them I have to use Windows for it.

---

### Post by Impavidus on 2014-09-03
I have a computer that has run Ubuntu for 8 years without fresh installs (but with 4 release upgrades) and it still is quite snappy, at least for a machine with only 1GB ram.

Ubuntu has no registry. If you simply uninstall something using the software centre or (what most consider a better program) synaptic, the software is gone and can't slow down your computer any more. Most software doesn't slow down your computer anyway by just being installed, as most software isn't started automatically in the background. Dependencies that are no longer needed can be autoremoved, for which there is an autoremove function. After uninstalling without purging some config files may remain, which only take disk space. User files belonging to the uninstalled software also remain somewhere in your home directory, where they just take some disk space. You have to delete them manually if you want the space back. In case of firefox, they are in the hidden directory **.mozilla**. These files contain user settings, cookies, cache etc.

---

### Post by Bashing-om on 2014-09-03
garycheng12; Hello !

I too will aver there is no slowdown in extended use of 'buntu !
I have ran this box also for years and on my present 'work' install I have online release upgraded (testing/verification of process) from 12.04 through 13.04, 13.10 and now on 14.04; all on that same initial install of 12.04. I only perform the nominal housecleaning on rare occasions; this ole box continues to meet and exceed my needs. 


[INDENT][INDENT]it just works
[/INDENT][/INDENT]

---

### Post by ThatBum on 2014-09-03
Not really. The file system doesn't need defragmenting, there's no malware to speak of, all installed software (from repos) updates automatically, and as previously mentioned there's no registry as such. I'd only do a clean install if I managed to screw it up somehow, or if I wanted to upgrade my LTS release to the next one.

---

### Post by vasa1 on 2014-09-03
> **Impavidus said:**
> ... In case of firefox, they are in the hidden directory **.mozilla**. These files contain user settings, cookies, cache etc.
Hi, for sometime, I don't know how long exactly, there's ~/.mozilla and also ~/.cache.

---

### Post by Howl7 on 2014-09-03
Ubuntu Tweak has a "Janitor" that will automatically clean out old, unused files for you such as caches, old kernels, and configs, although these only take up disk space and shouldnt impact Ubuntu's speed. You can get ubuntu Tweak by running ```
sudo apt-get install ubuntu-tweak
```

---

### Post by garycheng12 on 2014-09-03
Thanks everyone for the responses.

---

### Post by mcduck on 2014-09-04
> **Howl7 said:**
> Ubuntu Tweak has a "Janitor" that will automatically clean out old, unused files for you such as caches, old kernels, and configs, although these only take up disk space and shouldnt impact Ubuntu's speed. You can get ubuntu Tweak by running ```
sudo apt-get install ubuntu-tweak
```

more often than not cleaning those files actually does impact speed, although not in the direction you'd want it to... :D

Ubuntu Tweak doesn't know if the files are old and unusedor not, and cleaning cached files, for example from the internet browser's cache or file amnager's thumbnail cache, will simply slow things down slightly as the browser will ahve to download the fiels again the next time you visit a website, and the file manager will have ro recreate the thumbnail images etc...

...of course you might gain some free drive space, at least temporarily,  and in some cases such cleanup will indeed also end removing actually unused files, but I'd definitely advice against just cleaning everything Ubuntu Tweak (or any other cleanup tool) suggests automatically without thinking about what the files in question might be. And inf the programs actually have their own tools for cleaning old caches (as is the case with every web browser), thsoe would have much better chance at knowing which files are not needed any more and which ones should still be kept around.

---

### Post by buzzingrobot on 2014-09-04
> **garycheng12 said:**
> Does linux slow down over time  via collection of redundant file leftovers like Windows? ...

Whatever goes on in Windows to clutter up the system to the extent that it slows down doesn't happen in Linux.  

Individual applications create their own configuration files on Linux.  Depending on the packaging and dependency resolution system used in a distribution, those files may or may not be removed when their applications are removed.  In Ubuntu, the 'purge' option needs to be used with apt-get to ensure a packages config files are deleted along with it. (This makes sense so we don't need to reconfigure an app every time it's upgraded.)

Inadequate hardware is a more likely cause of Linux slowness.  Inadequate graphics hardware can result in slow screen draws which is very noticeable, even if the rest of the system is zipping along.

---

### Post by mcduck on 2014-09-04
> **buzzingrobot said:**
> Whatever goes on in Windows to clutter up the system to the extent that it slows down doesn't happen in Linux.  

Individual applications create their own configuration files on Linux.  Depending on the packaging and dependency resolution system used in a distribution, those files may or may not be removed when their applications are removed.  In Ubuntu, the 'purge' option needs to be used with apt-get to ensure a packages config files are deleted along with it. (This makes sense so we don't need to reconfigure an app every time it's upgraded.)

Inadequate hardware is a more likely cause of Linux slowness.  Inadequate graphics hardware can result in slow screen draws which is very noticeable, even if the rest of the system is zipping along.

It's worth to add here that even the "purge" option will only remove system-wide configuration files, the package manager will never automatically remove any of the user's own config files located in user home directories (doing that could result in some nasty surprises for the suers, especially in a multi-user system).

However all these files are just small text files and won't slow the system down in any way, and hardly even use any noticeable amount of disk space. So cleaning them up is really only a question of removing clutter you see when you show any hidden files in your home. Nice thing to do every now and then if you often need to deal with the hidden files, but at the same time you'll be perfeclty fine if you never do anything to them at all. :D (I usually just wipe my home directory while upgradng to new Ubuntu versions and only restore the files I know I need from backups after the update)

---

### Post by garycheng12 on 2014-09-04
So in most cases, left over files have no impact on the speed of the system as they only take up a trivial amount of space. As for installing applications, what exactly does a software center do (I know you can install popular programs there, but not everything), what are repositories and sources, and why is it that in order to download python, I have to do "./configure, make, make install"? Keep in mind that I have only used Windows and that installing applications consists of literally going to the application's website and downloading and running the installer.

I only know that the difference between Ubuntu and Kubuntu is that Kubuntu is KDE based and it generally has more options available for the user to tinker with for the system and Ubuntu is Unity/Gnome-based and seems to be geared  toward a more simplistic but practical approach. If I were to watch a tutorial on learning command lines, how to install applications, and more advanced stuff for Ubuntu, can I follow the exact steps on Kubuntu? Is the difference between Kubuntu and Ubuntu only in the desktop environment?

---

### Post by Impavidus on 2014-09-04
The software centre is an interface to the package management system, like synaptic and command line tools like apt-get. They have different looks and feels and the software centre is more tuned to beginning users, others more to advanced users. All of them provide access to the Ubuntu repositories and any private package archives that you might add to them, from which you can download and install software. You'll even get automatic bug fixes, something that won't work if you download and run an installer and you can be sure you won't get malware from the repos. This has been a common concept in the Linux world for a long time and has been copied by the smartphone and tablet world. I have only two programs installed not coming from the Ubuntu repositories.

The ./configure; make; make install sequence is for manual installation, and even there only a guideline. Best to avoid is whenever possible. Python is in the repositories and even installed by default. Some parts of the system depend on it.

The difference between Ubuntu, Kubuntu and the other flavours is the desktop environment and the set of default applications. The default applications in Kubuntu are more designed to work well with KDE, where the Ubuntu default applications are more designed to work with gnome. The command line stuff is identical, whether you have Unity, KDE, xfce or no GUI at all.

---

### Post by JKyleOKC on 2014-09-04
To expand on Impavidus's reply, all of the various software update and installation programs in the various flavors of *buntu end up at the same place, which is a program called the Debian Package Manager and named "dpkg." This program reads a specially formatted file called a DEB file, which contains not only the program to be installed itself, but also a list of its dependencies, a description of it, and often wizards that can be run during or immediately after the installation to handle the setup chores.

Some of the "wrapper" or "front end" programs that lead to "dpkg" are for use at the command line, some are set up for running in a window, and some have a lot more extra utilities built in to help you manage things. "Software Center" is designed especially for newcomers, and hides as much of the behind-the-scenes work as possible. "Synaptic Package Manager" has the same purpose but offers a lot more in the way of user control. As a result it can be quite a bit more confusing. The "apt-get" command line program, which you'll see quite often in suggestions here, provides even more control capability but it's very easy to post a single apt-get command line, while spelling out how to use Software Center or Synaptic is much more complicated and will vary widely depending on which flavor of *buntu you run.

Repositories are simply central locations that store DEB files. The settings for whichever package manager you use allow you to select from a list of official repositories; all of these have the same files. The reason for so many is simply to reduce congestion on the net; it's best to choose the one physically closest to you. This avoids having so many hops to make the connection.

In addition to the official repositories, there are private sites known as PPAs that are maintained by individuals. While the official sites take great care to stay clean of all forms of malware, and post only programs that are as bug-free as they can make them, the same isn't necessarily true of PPAs. When dealing with them, be cautious. That said, I have a number of PPAs included in my /etc/apt/sources.list file to provide more recent versions of such packages as Ubuntu Tweak. You simply have to be careful.

In general, it's best to avoid going the download source/configure/make route, at least until you have plenty of experience in troubleshooting. When you use this method to install a program, you won't get any notification of security updates for it. In the beginning, it was the only way to install new software, but with the development of package managers and repository lists it became possible to automate notifications, and to make certain that programs were compatible with the specific operating system for which they're offered.

Hope this helps a bit!

---

### Post by garycheng12 on 2014-09-04
Thank you both for the informative answers.

---

### Post by jamapii on 2014-09-20
For me, I think Linux never slowed down much over time by adding files to the home directory, except maybe locate helpers, things that index everything, cause slowdowns and battery waste.

However, software updates seem to introduce bugs, slowdowns, and cause stuff to no longer work. Virtual machines where updates are avoided may help here. This also goes for Android and other smartphone platforms, maybe less so for Windows as long as no major update is done (2000->XP or 8->9). Always keep the old installations for important applications.

I have never seen a Windows installation that does not slow down a lot after a year or sooner, and no claims to the contrary have ever been anything else than utterly false. It has always surprised me negatively, even after accounting for this very fact.

---

### Post by buzzingrobot on 2014-09-20
Adding files should have a minimal imact on the speed of any OS, including Windows, since those files are static data on a drive. There will be an impact on any indexing that goes on, especially full-text indexing. (KDE does full-text unless a user opts out. Unity, Gnome and every other interface I can think of defaults to indexing only file names, not their contents.  In both kinds of indexing, incremental indexing after the initial pass is finished should not really be noticeable on any modern hardware.)

The defragging Windows does occasionally will obviously be affected by the number of files.

What does have a much more substantial impact on a system's perceived speed is the number of startup programs and background processes. Windows apps, especially free ones, are notorious for installing junk startup/background processes, including malware. Users can prune unessential entries from their startup list, but I imagine few do.

And, the registry grows larger, etc., etc.

I've very rarely had bugs or breakage introduced by updates on any OS.  Users who alter or replace core system components (people do it with PPA's in Ubuntu and don't know it) should understand that they are increasing their chances of an update going bad:  The updates (must) assume they're updating a stock, standard, system.

---

