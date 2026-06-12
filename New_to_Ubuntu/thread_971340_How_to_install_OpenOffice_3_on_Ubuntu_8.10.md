---
title: "How to install OpenOffice 3 on Ubuntu 8.10?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by manilaph on 2008-11-04
I noticed that the openoffice that comes with the Intrepid is the 2.4 version.

How do I download (what do i download) so that it is easy to install openoffice 3.

I was looking for a deb file but there is none.

I do not know how to install Tar.GZ files.

I tried once but all it did was extract and nothing seems to have happened.

Thank you

---

### Post by abn91c on 2008-11-04
follow this guide for OpenOffice.org 3.0
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by lbarnes on 2008-11-04
wow, thank you so much

---

### Post by Tom.Servo on 2008-11-04
This may also be of help:

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

But the other way mentioned above is MUCH easier. :)

---

### Post by hyper_ch on 2008-11-05
why do you need OOo 3? What new featuers can't you ilve without?

---

### Post by stinger30au on 2008-11-05
piece of cake, here is how it is done

remove open office core first off by 

system
administration
synaptic package manager

search on open office core

scroll down and find it and right click on it and select

REMOVE

click ok or apply and follow the prompts

now follow the first post in this thread and you will be right as rain

[http://ubuntuforums.org/showthread.php?t=947924](http://ubuntuforums.org/showthread.php?t=947924)

i have done this on 8.04 and 8.10 installs with no problems

---

### Post by togo59 on 2008-11-05
> **hyper_ch said:**
> why do you need OOo 3? What new featuers can't you ilve without?
OO 2.4 (and earlier versions) has a "crash feature" built into Impress. I use Impress for lectures but scrolling through my slides sometimes causes it to crash. It does this under Ubuntu and windoze and on each one of my PCs.

I'm hoping that 3.0 has that feature, which I can live without, disabled.

---

### Post by hyper_ch on 2008-11-05
> **togo59 said:**
> OO 2.4 (and earlier versions) has a "crash feature" built into Impress.

Fair enough :) good luck with v. 3.

---

### Post by rickbeton on 2008-11-13
Here's my tip [i386 users only):

1. Download the 150MB OpenOffice 3 linux .deb version
e.g for en-US version use [http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0)

2. uninstall openoffice 2 using

```
sudo apt-get remove $(dpkg -l |grep ^ii|grep openoffice|cut -f3 -d' ')
```

3. Unpack the .tar.gz using

```
tar zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
```

4. Install the main packages

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb
```

5. Now tidy up

```
sudo apt-get autoremove
```

You may notice that the menu icons have gone wrong but they all come back next time you log in.

Hope this works for you as well as it did for me.  :-)

64bit cpu owners will need to get a different download. I guess if you have a 64bit machine you're likely to be savvy enough to work this out for yourself ;-)

---

### Post by krtica on 2008-11-19
I used this:
[FONT="Courier New"][http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")[/FONT]
It's very simple and with pictures. :D

---

### Post by RamiroS on 2008-11-25
> **krtica said:**
> I used this:
[FONT="Courier New"][http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")[/FONT]
It's very simple and with pictures. :D

That repository doesn contain the version for 8.10 anymore

---

### Post by odieman on 2008-11-28
Hmmm, sad. I was using the repo to create pre-installed images so I could clone UBUNTU 8.10 with OO3 :-(.
I just needed to finish few more PC models :-(.

Any other repo I could use? :-)

Thanks

---

### Post by manilaph on 2008-11-29
yes i noticed that the softpedia tutorial no longer works.

how do we install openoffice 3.0 now?

---

### Post by HotShotDJ on 2008-11-29
> **manilaph said:**
> yes i noticed that the softpedia tutorial no longer works.

how do we install openoffice 3.0 now?Just wait a few days.  There was a problem with the packages in the ppa.launchpad.net/openoffice-pkgs/ubuntu repositories.  They will be back up as soon as the issue is solved.

---

### Post by XanTrax on 2008-12-04
> **manilaph said:**
> yes i noticed that the softpedia tutorial no longer works.

how do we install openoffice 3.0 now?

You can always follow this:

[http://ubuntuforums.org/showpost.php?p=6172120&postcount=9](http://ubuntuforums.org/showpost.php?p=6172120&postcount=9)

Its really all you need.  Probably will take a lot less time to do it that way then waiting for the repos to become available, then re-adding the repos, and then installing it.  This way, you can do it yourself.  Download openoffice 3 and then install it like it says above.

---

### Post by Laibcoms on 2008-12-09
I think it's back.  When I updated today and checked the ppa, OOo3.0.0.6 shows up now.

Although I'm not sure how far the project has gone compared to installing the non-Ubuntu version.

---

### Post by jbernardo on 2008-12-09
It is back, but at least on kubuntu it is absolutely worthless. When I try to open a document, it shows a "recovering document" window empty, with a ok button. When I press it, it dies. :(

---

### Post by hobo89 on 2008-12-09
I've just reinstalled from the repositories (after having installed it from the source last night) and have no problems at all. All working fine for me.

---

### Post by shk76 on 2009-01-09
> **manilaph said:**
> I noticed that the openoffice that comes with the Intrepid is the 2.4 version.

How do I download (what do i download) so that it is easy to install openoffice 3.

I was looking for a deb file but there is none.

I do not know how to install Tar.GZ files.

I tried once but all it did was extract and nothing seems to have happened.

Thank you


You can visit the blog

"http://sayeed-linux.blogspot.com/"

To me that is the easier way for ubuntu

---

### Post by babloo75 on 2009-01-09
Another method here:

[http://ubuntuforums.org/showpost.php?p=6210799&postcount=1](http://ubuntuforums.org/showpost.php?p=6210799&postcount=1)

---

