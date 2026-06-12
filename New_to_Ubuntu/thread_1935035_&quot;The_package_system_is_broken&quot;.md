---
title: "&quot;The package system is broken&quot;"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by Cyle902 on 2012-03-03
Hello everyone,

In my class I am building a computer as a project. After installing most of the hardware, I installed ubuntu 11.10 as my OS. I installed it without any updates or third party software. After looking around for a while I decidewd it was time to install all the 344 available updates.
 
It took only half an hour but only 335 updates installed successfully and I get this error message:

[B]The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f[/B]

Details:

The following packages have unmet dependencies:

gir1.2-totem-1.0: Depends: libtotem0 (>= 3.0.1-0ubuntu7.1) but 3.0.1-0ubuntu5 is installed
totem-plugins: Depends: totem (= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu5 is installed
               Depends: libbluetooth3 (>= 4.91) but 4.96-0ubuntu4 is installed
               Depends: libtotem0 (>= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu5 is installed
               Depends: gir1.2-totem-1.0 (= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu7.1 is installed



Being a first time ubuntu user I have no idea what any of this means. :P

I would appreciate if someone would be willing to walk me through the process to solve this issue.

Thanks!

---

### Post by HermanAB on 2012-03-03
Howdy,

You learned a valuable lesson:
Don't fix it if it ain't broke.

In other words, if it works, don't apply updates willy nilly, since it cannot make things any better and therefore will either leave things the same, or worse!

Anyhoo, Totem is a video player.  There are many video player such as VideoLAN (VLC), Mplayer and so on.  SO you need not necessarily fix Totem - just use another player.

---

### Post by winh8r on 2012-03-03
Have a read through this:

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

to better understand how repositories work and how to manage them.

Hope this helps you.

---

### Post by Cyle902 on 2012-03-03
Thanks for all the useful information, but I still am not sure how to remove the error. Since the first error report I've had an icon at the top right of the screen, a red circle with a white line horizontally through it, and it bugs me. 

Also I can't install adobe, this is the error message I get:

**The package system is broken**

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details:

The following packages have unmet dependencies:

gir1.2-totem-1.0: Depends: libtotem0 (>= 3.0.1-0ubuntu7.1) but 3.0.1-0ubuntu5 is installed
totem-plugins: Depends: totem (= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu5 is installed
               Depends: libbluetooth3 (>= 4.91) but 4.96-0ubuntu4 is installed
               Depends: libtotem0 (>= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu5 is installed
               Depends: gir1.2-totem-1.0 (= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu7.1 is installed

---

### Post by MG&amp;TL on 2012-03-03
Try opening a terminal (Ctrl-Alt-T):

and running:

```
sudo apt-get install -f
```

Paste the output here.

---

### Post by Cyle902 on 2012-03-03
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libtotem0 totem totem-common totem-mozilla totem-plugins
Suggested packages:
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg
  gromit
The following packages will be upgraded:
  libtotem0 totem totem-common totem-mozilla totem-plugins
5 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,227 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?



Edit: I told it Y and this was the response:


Do you want to continue [Y/n]? Y
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-mozilla_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libtotem0_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-plugins_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-common_3.0.1-0ubuntu7.1_all.deb
debconf: apt-extracttemplates failed: 
dpkg-deb: error: `/var/cache/apt/archives/totem-mozilla_3.0.1-0ubuntu7.1_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/totem-mozilla_3.0.1-0ubuntu7.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: `/var/cache/apt/archives/libtotem0_3.0.1-0ubuntu7.1_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/libtotem0_3.0.1-0ubuntu7.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: `/var/cache/apt/archives/totem-plugins_3.0.1-0ubuntu7.1_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/totem-plugins_3.0.1-0ubuntu7.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: `/var/cache/apt/archives/totem_3.0.1-0ubuntu7.1_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/totem_3.0.1-0ubuntu7.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: `/var/cache/apt/archives/totem-common_3.0.1-0ubuntu7.1_all.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/totem-common_3.0.1-0ubuntu7.1_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/totem-mozilla_3.0.1-0ubuntu7.1_i386.deb

---

### Post by grahammechanical on 2012-03-03
You could try removing and re-installing Totem. That might bring in the packages that Totem uses and replacing those packages that are there but not needed.

The Ubuntu Software Centre provides applications that are tested as working with your version of Ubuntu. It is possible to get the latest version of a program from the developers and this is done by adding a Personal Package Archive (PPA) to the Software Sources.

The very latest version of a program might have bugs which is why you cannot get it through the Software Centre. It will also use different (the latest) libraries. This is not so much a problem until you do a standard update and that particular program is being updated but to not the very latest version.

So, Update Manager notices a conflict. It is about to replace some libraries but finds that even newer versions are installed. So, it does not continue with that part of the update. The job of Update manager is to replace older libraries with newer libraries. What can it do when the existing library is newer than the library that it has got?

You say that you have not install any third party software. That may be true but it seems that something was installed. To install did you use an ISO image downloaded from the Ubuntu web site?

Regards.

---

### Post by Cyle902 on 2012-03-03
Yes I downloaded the ISO image to a blank cd then installed to my machine that had no OS.

Edit:

I tried removing totem but I got the same error message.

I also got another error message:

**Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?**

Once Update Manager has finished the repairs, you can close it and return to the store.

I click the option to repair and this is the message I get:

**Package operation failed**

The installation or removal of a software package failed.

Details:

```
installArchives() failed: E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-mozilla_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libtotem0_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-plugins_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-common_3.0.1-0ubuntu7.1_all.deb
debconf: apt-extracttemplates failed: Illegal seek
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-mozilla_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libtotem0_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-plugins_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-common_3.0.1-0ubuntu7.1_all.deb
debconf: apt-extracttemplates failed: Illegal seek
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-mozilla_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libtotem0_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-plugins_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem_3.0.1-0ubuntu7.1_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/totem-common_3.0.1-0ubuntu7.1_all.deb
debconf: apt-extracttemplates failed: Illegal seek
dpkg-deb: error: `/var/cache/apt/archives/totem-mozilla_3.0.1-0ubuntu7.1_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/totem-mozilla_3.0.1-0ubuntu7.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
dpkg-deb: error: `/var/cache/apt/archives/libtotem0_3.0.1-0ubuntu7.1_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/libtotem0_3.0.1-0ubuntu7.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
dpkg-deb: error: `/var/cache/apt/archives/totem-plugins_3.0.1-0ubuntu7.1_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/totem-plugins_3.0.1-0ubuntu7.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
dpkg-deb: error: `/var/cache/apt/archives/totem_3.0.1-0ubuntu7.1_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/totem_3.0.1-0ubuntu7.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
dpkg-deb: error: `/var/cache/apt/archives/totem-common_3.0.1-0ubuntu7.1_all.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/totem-common_3.0.1-0ubuntu7.1_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/totem-mozilla_3.0.1-0ubuntu7.1_i386.deb
 /var/cache/apt/archives/libtotem0_3.0.1-0ubuntu7.1_i386.deb
 /var/cache/apt/archives/totem-plugins_3.0.1-0ubuntu7.1_i386.deb
 /var/cache/apt/archives/totem_3.0.1-0ubuntu7.1_i386.deb
 /var/cache/apt/archives/totem-common_3.0.1-0ubuntu7.1_all.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of gir1.2-totem-1.0:
 gir1.2-totem-1.0 depends on libtotem0 (>= 3.0.1-0ubuntu7.1); however:
  Version of libtotem0 on system is 3.0.1-0ubuntu5.
dpkg: error processing gir1.2-totem-1.0 (--configure):
 dependency problems - leaving unconfigured
```

---

### Post by inf1nity on 2012-03-03
well i suggest that you reinstall ubuntu.. since it is a new system so you have nothing to lose.
Most of the software you'll ever need comes preloaded. Just install VLC media player
by typing-
```
sudo apt-get install vlc
```

this will take care of all your multimedia needs. No need to install any updates. Most of them will never be used by you, and they will just occupy disk space. Cheeers..! :)

---

### Post by Cyle902 on 2012-03-03
Thats probably what I will end up doing if I can't fix this issue. But I would like to have all of these updates if possible.

For those that didnt see, my last post was edited with more information.

---

### Post by mörgæs on 2012-03-03
> **HermanAB said:**
> Howdy,

You learned a valuable lesson:
Don't fix it if it ain't broke.

In other words, if it works, don't apply updates willy nilly, since it cannot make things any better and therefore will either leave things the same, or worse!

Anyhoo, Totem is a video player.  There are many video player such as VideoLAN (VLC), Mplayer and so on.  SO you need not necessarily fix Totem - just use another player.


New version of packages should always be installed unless you know positively that a particular package does not work on the system.

Like all OS's Buntu has its share of bugs, some of them important security ones, and correcting them should be a priority.

---

### Post by inf1nity on 2012-03-03
> **Cyle902 said:**
> Thats probably what I will end up doing if I can't fix this issue. But I would like to have all of these updates if possible.

For those that didnt see, my last post was edited with more information.

alright. Mark this thread as solved, when you feel that you won't be needing any further help...

---

### Post by mörgæs on 2012-03-03
> **kaustbh said:**
> No need to install any updates. Most of them will never be used by you, and they will just occupy disk space.

Updates do not take up more disk space than the previous (buggy) package. Just run **sudo apt-get clean** and / or **sudo apt-get autoclean** once in a while.

---

### Post by Cyle902 on 2012-03-03
> **kaustbh said:**
> alright. Mark this thread as solved, when you feel that you won't be needing any further help...

I still would like to try to resolve this issue. The most recent information is near the bottom of page one. Post #8

---

### Post by MG&amp;TL on 2012-03-03
Okay, somebody suggested reinstalling totem, that might be a good idea. What do the following commands output?

```
sudo apt-get remove --purge totem
```(removes totem, purges config files)

```
sudo apt-get autoremove
```(removes totem's dependencies, let's see if we can download some un-broken ones)

```
sudo apt-get install totem
```Installs totem again.

@kaustbh-finding the root of the problem is better than working around it. :)

---

### Post by inf1nity on 2012-03-03
> **mörgæs said:**
> Updates do not take up more disk space than the previous (buggy) package. Just run **sudo apt-get clean** and / or **sudo apt-get autoclean** once in a while.

whats the difference between the two, BTW?

---

### Post by MG&amp;TL on 2012-03-03
> **kaustbh said:**
> whats the difference between the two, BTW?

Question for a separate thread, but see:

```
man apt-get
```

---

### Post by Cyle902 on 2012-03-03
```
[sudo] password for cyle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gir1.2-totem-1.0 : Depends: libtotem0 (>= 3.0.1-0ubuntu7.1) but 3.0.1-0ubuntu5 is to be installed
 totem-mozilla : Depends: totem (= 3.0.1-0ubuntu5) but it is not going to be installed
 totem-plugins : Depends: totem (= 3.0.1-0ubuntu5) but it is not going to be installed
                 Depends: gir1.2-totem-1.0 (= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu7.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


```
cyle@cyle-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gir1.2-totem-1.0 : Depends: libtotem0 (>= 3.0.1-0ubuntu7.1) but 3.0.1-0ubuntu5 is installed
 totem-plugins : Depends: gir1.2-totem-1.0 (= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu7.1 is installed
E: Unmet dependencies. Try using -f.

```


```
cyle@cyle-desktop:~$ sudo apt-get install totem
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gir1.2-totem-1.0 : Depends: libtotem0 (>= 3.0.1-0ubuntu7.1) but 3.0.1-0ubuntu5 is to be installed
 totem : Depends: libtotem0 (>= 3.0.1-0ubuntu7.1) but 3.0.1-0ubuntu5 is to be installed
         Depends: totem-common (= 3.0.1-0ubuntu7.1) but 3.0.1-0ubuntu5 is to be installed
 totem-mozilla : Depends: totem (= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu7.1 is to be installed
 totem-plugins : Depends: totem (= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu7.1 is to be installed
                 Depends: gir1.2-totem-1.0 (= 3.0.1-0ubuntu5) but 3.0.1-0ubuntu7.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by inf1nity on 2012-03-03
> **MG&TL said:**
> 
@kaustbh-finding the root of the problem is better than working around it. :)

Agreed, but the guy has just started using ubuntu, wouldn't it save him a lot of trouble? He can explore the technical parts later when he has time. :D

Cute Dog BTW.. :) ;)

---

### Post by Cyle902 on 2012-03-03
I have time now

---

### Post by JKyleOKC on 2012-03-03
> **Cyle902 said:**
> After installing most of the hardware, I installed ubuntu 11.10 as my OS.This may, or may not, have any bearing on your problem, but what part of the hardware have you not yet installed?

Most likely, one or more of the updates that did install properly replaced a library with a newer version, and the package for totem says that it requires the older version so will not install.

That huge number of updates, however, may indicate that the ISO that you downloaded to burn your CD isn't fully up to date. Canonical periodically updates the installation ISO files to include all the updates released since the previous ISO came out; they use a third number in the version label, such as 11.10.2 or 11.10.3, to indicate such integrated disks. This would be worth investigating...

---

### Post by inf1nity on 2012-03-03
Okay.. First of all install the synaptic package manager. It is used for installing packages like Ubuntu Software Centre, but it is better than the over-simplified Software Centre. 

Note-you will have to install it through the software centre, or by typing-
 ```
 sudo apt-get install synaptic
```Now purge totem from your system-

```
 sudo apt-get remove --purge totem 
```

There should be no problem now. From now on, use synaptic instead of software centre to install software. Trust me, its better.(Gives you more control over whats happening, ain't that a better thing..:D)

---

### Post by Cyle902 on 2012-03-03
> **JKyleOKC said:**
> This may, or may not, have any bearing on your problem, but what part of the hardware have you not yet installed?

Most likely, one or more of the updates that did install properly replaced a library with a newer version, and the package for totem says that it requires the older version so will not install.

That huge number of updates, however, may indicate that the ISO that you downloaded to burn your CD isn't fully up to date. Canonical periodically updates the installation ISO files to include all the updates released since the previous ISO came out; they use a third number in the version label, such as 11.10.2 or 11.10.3, to indicate such integrated disks. This would be worth investigating...

I have everything installed except for a DVD drive. I used an old (2006) temporary one to to install the OS. I will go through and look to see if there is a 11.10.1

---

### Post by mörgæs on 2012-03-03
> **JKyleOKC said:**
> This may, or may not, have any bearing on your problem, but what part of the hardware have you not yet installed?

Most likely, one or more of the updates that did install properly replaced a library with a newer version, and the package for totem says that it requires the older version so will not install.

That huge number of updates, however, may indicate that the ISO that you downloaded to burn your CD isn't fully up to date. Canonical periodically updates the installation ISO files to include all the updates released since the previous ISO came out; they use a third number in the version label, such as 11.10.2 or 11.10.3, to indicate such integrated disks. This would be worth investigating...


No, this is only the case for long time support releases, not the normal ones.

We are now four months after release of 11.10, so it is getting a mature system. A couple of hundred updates is as expected.

---

### Post by Cyle902 on 2012-03-03
My package system is still broken! :P

---

### Post by mörgæs on 2012-03-04
Please don't bump a thread. It does not help you getting an answer.

In #18 you posted the likely solution yourself: 
```
sudo apt-get -f install
```

How did that work?

Are you booting the computer after a major change like 300+ new packages?


If everything else fails, try this when you reinstall:
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

