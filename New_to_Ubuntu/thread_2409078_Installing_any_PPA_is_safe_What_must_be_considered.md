---
title: "Installing any PPA is safe? What must be considered?"
date: 2018-12-27
forum: New to Ubuntu
---

### Post by dimmetrix on 2018-12-27
As is well known, there are multiple repositories where the Linux  software (Main, Universe, Multiverse, restricted) is stored. Does any of  these contain reliable software?

  
On the other hand, is any ppa safe? How to know if it is official?

  
Assuming that I have these two repositories and I do not know if they  are official or reliable to install the software. How do I know if they  are reliable?


  sudo add-apt-repository ppa: nvbn-rm/ppa


  sudo add-apt-repository ppa: notepadqq-team/notepadqq

---

### Post by howefield on 2018-12-27
The trust level for any particular PPA is down to you to assess, by their very nature Personal Package Archives can be created by anyone, including those with ill intent. Certainly you can ask around if you are unsure of the validity of any particular PPA but in the end only you can decide if you trust them. 

The  first PPA that you post above has no current repository available for anything later than Ubuntu 15.04, so probably not a good idea to use it and the second one that you post has no Cosmic repository. What version of Ubuntu are you running ?

---

### Post by #&amp;thj^% on 2018-12-27
A fairly complete post found here: [https://askubuntu.com/questions/35629/are-ppas-safe-to-add-to-my-system-and-what-are-some-red-flags-to-watch-out-for](https://askubuntu.com/questions/35629/are-ppas-safe-to-add-to-my-system-and-what-are-some-red-flags-to-watch-out-for)
Just for the record though, I have not found an "Offical" PPA.

The only way to be absolutely certain is by reading the code and checking if it is repoerted as malicious.

If you can't read code or don't have the time to do so (almost no one does :p) you can verify how safe it is by:

  [list][*]  Use a search engine to get more information about the ppa.
    Check if there are articles describing the ppa (if a ppa has a lot of hype around itself, there is a good change someone did check how safe it is).
   [*] The amount of contributors. If there are a lot of different people working on a project, it gets really hard to implement malicious features (unless they work together on the malicious features of course) without getting noticed by the other contributors.[/list]

If besides all these options you still don't trust a ppa, you could install it in a virtual machine and test it there yourself.
Ninja'd by howefield :)

---

### Post by dimmetrix on 2018-12-27
I thought that a PPA before being able to be created had to go through a series of standards, so sometimes it is better to ask.

The version that I am currently using (provisionally at the moment) is version 16.04 LTS. How did you find out that you do not have a current repository for anything after Ubuntu 15.04? Can you find out how many users download it? (It could also help to make the decision to download the package)

---

### Post by howefield on 2018-12-27
> **dimmetrix said:**
> .....How did you find out that you do not have a current repository for anything after Ubuntu 15.04? Can you find out how many users download it? (It could also help to make the decision to download the package)

Go to the PPA launchpad page.. [https://launchpad.net/~nvbn-rm/+archive/ubuntu/ppa](https://launchpad.net/~nvbn-rm/+archive/ubuntu/ppa) for details about the PPA. Don't think there is a way of telling how many downloads there are, but could be wrong about that.

---

### Post by #&amp;thj^% on 2018-12-27
> **howefield said:**
> Go to the PPA launchpad page.. [https://launchpad.net/~nvbn-rm/+archive/ubuntu/ppa](https://launchpad.net/~nvbn-rm/+archive/ubuntu/ppa) for details about the PPA. Don't think there is a way of telling how many downloads there are, but could be wrong about that.

+1 :)
The 2 things that matter to myself **_after I do a search for PPA info_**, is
[list][*]If it supports the current version of Ubuntu that I/You are running.
[*]And how current it is kept or maintained.[/list]
In my screenshot it will show you how to check all of this.
The PPA that howefield mentions has not received any changes for over 2 years now. (So I would not use it)
Opps forgot to add how to view stats/Downloads on a PPA: [https://fosspost.org/tutorials/how-to-get-the-download-stats-of-any-ubuntu-ppa](https://fosspost.org/tutorials/how-to-get-the-download-stats-of-any-ubuntu-ppa)

---

### Post by ubname on 2018-12-27
I would add that if you use a software, lets say "Remmina", and the very devs of remmina are maintainers of remmina ppa, it is reasonable to trust the ppa.

---

### Post by oldrocker99 on 2018-12-27
I use Aqualung, a gapless music player, for my college radio show. It was in the repos, then a PPA was available for it. That PPA has not been updated since Xenial, so I have to compile it myself, which requires a raft of necessary and optional dependencies, and made the first compilation Dependency Hell.  It does indeed work, and I've been happy with the intermediate knowledge of compilation I possess.

---

### Post by Tadaen_Sylvermane on 2018-12-27
I avoid compiling like the plague. As such my general rule for ppa's, or any external repo is simple. If I have no choice, I use the ppa. For example, Makemkv and Kodi are 2 things I need the latest stable versions of. Makemkv isn't in the official repos and I need it to rip DVD's (it can rip stuff handbrake chokes on in my experience), and the supplied version of Kodi is to old to work with the Xenial release of Mythtv. As such I have no choice if I want my media center to work. But I don't blindly add ppas for everything like many websites suggest one does. Always stick to the main repos if possible > external and you will have a smoother ride nearly every time.

It's also worth noting that when people suggest ppas they are pointing you toward newer releases. SNS syndrome. Newer doesn't always mean better. In some cases they are less stable because they haven't gone through the testing period for a stable release. The so called improvements aren't usually even noticeable to the end user. The stuff in the repos I can count on to work every time.

---

### Post by dimmetrix on 2019-01-02
> **1fallen said:**
> +1 :)
The 2 things that matter to myself **_after I do a search for PPA info_**, is
[LIST]
[*]If it supports the current version of Ubuntu that I/You are running. 
[*]And how current it is kept or maintained. 
[/LIST]
In my screenshot it will show you how to check all of this.
The PPA that howefield mentions has not received any changes for over 2 years now. (So I would not use it)
Opps forgot to add how to view stats/Downloads on a PPA: [https://fosspost.org/tutorials/how-to-get-the-download-stats-of-any-ubuntu-ppa](https://fosspost.org/tutorials/how-to-get-the-download-stats-of-any-ubuntu-ppa)

Great contribution! Thank you very much for this.

I'll keep it in mind.

> **oldrocker99 said:**
> I use Aqualung, a gapless music player, for my college radio show. It was in the repos, then a PPA was available for it. That PPA has not been updated since Xenial, so I have to compile it myself, which requires a raft of necessary and optional dependencies, and made the first compilation Dependency Hell.  It does indeed work, and I've been happy with the intermediate knowledge of compilation I possess.

It is excellent to have that level of knowledge. I'm still in the beginning (sometimes I do not even know where to start with the programming) but I also believe that for this to be reliable, you also have to have computer security knowledge to detect the BUG that may be violated. In addition, a single person is not the same as hundreds of thousands of people reviewing the code.

> **Tadaen_Sylvermane said:**
> I avoid compiling like the plague. As such my general rule for ppa's, or any external repo is simple. If I have no choice, I use the ppa. For example, Makemkv and Kodi are 2 things I need the latest stable versions of. Makemkv isn't in the official repos and I need it to rip DVD's (it can rip stuff handbrake chokes on in my experience), and the supplied version of Kodi is to old to work with the Xenial release of Mythtv. As such I have no choice if I want my media center to work. But I don't blindly add ppas for everything like many websites suggest one does. Always stick to the main repos if possible > external and you will have a smoother ride nearly every time.

It's also worth noting that when people suggest ppas they are pointing you toward newer releases. SNS syndrome. Newer doesn't always mean better. In some cases they are less stable because they haven't gone through the testing period for a stable release. The so called improvements aren't usually even noticeable to the end user. The stuff in the repos I can count on to work every time.

Thanks for your opinion. I agree with what you say.

---

### Post by oldrocker99 on 2019-01-02
> **Tadaen_Sylvermane said:**
> I avoid compiling like the plague. As such my general rule for ppa's, or any external repo is simple. If I have no choice, I use the ppa. For example, Makemkv and Kodi are 2 things I need the latest stable versions of. Makemkv isn't in the official repos and I need it to rip DVD's (it can rip stuff handbrake chokes on in my experience), and the supplied version of Kodi is to old to work with the Xenial release of Mythtv. As such I have no choice if I want my media center to work. But I don't blindly add ppas for everything like many websites suggest one does. Always stick to the main repos if possible > external and you will have a smoother ride nearly every time.

It's also worth noting that when people suggest ppas they are pointing you toward newer releases. SNS syndrome. Newer doesn't always mean better. In some cases they are less stable because they haven't gone through the testing period for a stable release. The so called improvements aren't usually even noticeable to the end user. The stuff in the repos I can count on to work every time.

Compiling isn't all that frightening, and, as I said, when I needed that program, I had little choice but to compile. Archived source code almost always come with a file called "configure."

```
./configure
```

This will go through the dependencies, and end, if you have missing dependencies, it'll tell you which ones they are. It also, if all dependencies are present, will generate a makefile. Once that is done,
```
make
sudo make install
```

If you do have to install dependent libraries, you install those files with **-dev** at the end, which are the files necessary for compilation. It really isn't hard, and you just might need a program not in the repos, or in a PPA.

---

### Post by Tadaen_Sylvermane on 2019-01-02
Fortunately I haven't hit the block where I had to compile something. That being said, I have debated looking into it. I know that I would prefer to be running CentOS on my server/htpc instead of Ubuntu, only because of the 10 year support cycle. Kodi and mythtv would need to be compiled by me in that case.

I have debated looking into it more and learning. I do like to learn, but now that I've achieved my goals with Linux in my home, I've drifted away from spending my free time tinkering and fiddling about. Lost interest. Everything is working just great in my home, no need to fix anything or rework. Everything seems to be perfect and most importantly, stable.

---

### Post by mc4man on 2019-01-02
> **howefield said:**
> Go to the PPA launchpad page.. [https://launchpad.net/~nvbn-rm/+archive/ubuntu/ppa](https://launchpad.net/~nvbn-rm/+archive/ubuntu/ppa) for details about the PPA. Don't think there is a way of telling how many downloads there are, but could be wrong about that.

A python script was created years ago by Alin Andrei that can report the latest downloads for a ppa. (if package A was upgraded then it will show number of dl's of the current upgraded package, not lifetime.

```
#!/usr/bin/python
#usage python ppastats.py PPATEAM (ex: webupd8team) PPA (ex: gthumb) DIST (Ubuntu version eg maverick) ARCH (ubuntu arch eg i386 or amd64)

#example - highest downloaded file: python ppastats.py webupd8team y-ppa-manager maverick amd64 | tr '\t' ',' | cut -d ',' -f3 | sort -gr

import sys
from launchpadlib.launchpad import Launchpad

PPAOWNER = sys.argv[1]
PPA = sys.argv[2]
desired_dist_and_arch = 'https://api.launchpad.net/devel/ubuntu/' + sys.argv[3] + '/' + sys.argv[4]



cachedir = "~/.launchpadlib/cache/"
lp_ = Launchpad.login_anonymously('ppastats', 'edge', cachedir, version='devel')
owner = lp_.people[PPAOWNER]
archive = owner.getPPAByName(name=PPA)

for individualarchive in archive.getPublishedBinaries(status='Published',distro_arch_series=desired_dist_and_arch):

       x = individualarchive.getDownloadCount()
       if x > 0:
              print individualarchive.binary_package_name + "\t" + individualarchive.binary_package_version + "\t" + str(individualarchive.getDownloadCount())
       elif x < 1:
              print '0'

```

I place it in ~/bin marked as executable. Requires python-launchpadlib  package installed.

Ex. 
I want to see what current interest is for mpv in 18.04, i.e how many amd64 users upgraded mpv build from 2 weeks ago.
```

$ python /home/doug/bin/ppastats.py mc3man mpv-tests bionic  amd64
libdav1d-dev	0.1.0-1	7
libdav1d0	0.1.0-1	6627
mpv	2:0.29.1+git1~zzbionic	3645
mpv2	2:0.29.0+wm4.2~zzbionic3	192
```

So I see there is still some interest but down quite a bit from the initial 18.04 amd64 release in that ppa.
What does surprise me is the number for libdav1d0  , almost double those upgrading mpv.. (mpv is only player supporting libdav1d atm..

---

