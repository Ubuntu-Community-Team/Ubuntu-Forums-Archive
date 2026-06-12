---
title: "HOWTO: Using apt-p2p (torrent) For Faster Upgrades From Hardy To Intrepid"
date: 2008-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by hyper_ch on 2008-10-29
[SIZE="5"]HOWTO: Using apt-p2p For Faster Upgrades From Hardy To Intrepid[/SIZE]

Author: ernesto (torrentfreak.com)


**[SIZE="4"]Introduction[/SIZE]**

[ernesto]("http://torrentfreak.com/author/ernesto/") has today published on [TorrentFreak]("http://torrentfreak.com/use-bittorrent-to-upgrade-to-ubuntu-intrepid-ibex-081029/") a great howto on how to lessen the burden of the Canonical Servers for the upgrade to the new stable release of Ubuntu 8.10 - Intrepid Ibex. With his permission I publish this howto here also.


**[SIZE="4"]What is apt-p2p?[/SIZE]**

According to the [Ubuntu package]("http://packages.ubuntu.com/intrepid/apt-p2p") information Apt-P2P is a helper for downloading Debian packages files with APT. It will download any needed files from other Apt-P2P peers in a peer-to-peer manner, and so reduce the strain on the Debian (resp. Ubuntu) mirrors.

However there is no apt-p2p packages yet in Hardy. However we can use the version directly from Intrepid.


**[SIZE="4"]Step 1: Setting sources.list to a close-local mirror[/SIZE]**

First off, it's definitely recommended to reset to a local mirror. This way, you will download any needed files from a closer and supposedly faster source.

Either do an auto-check: *System --> Administration --> Software Sources --> Download From: --> Other --> Select Best Server* (this will run a couple hundred tests [takes less than five minutes] and select the best mirror for you. Make sure to remember which mirror it is, because you will need that later.)

Or select your local mirror yourself according to your country.


**[SIZE="4"]Step 2: Disable 3rd Parties repositories[/SIZE]**

It is also very much recommended to disable 3rd party
repositories! If you don't know exactely what you are doing, go to the 3rd Parties tab and deselect all of the entries there.


**[SIZE="4"]Step 3: Install apt-p2p[/SIZE]**

Next you need to install "apt-p2p". Version 0.2.5 is needed because of a major bug in older versions. This is beta software, so it might not be stable for everybody. If it can't download the file via BitTorrent, however, it will revert to http download.

As apt-p2p is not in the hardy repos yet, we have to fetch it from a server directly. Below I have have two scripts for 32-bit and 64-bit. Use the according one:

For 32-bit versions use this script:

```

#!/bin/bash

mkdir /tmp/apt-p2p
cd /tmp/apt-p2p

wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/universe/a/apt-p2p/apt-p2p_0.1.5_all.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/p/python-debian/python-debian_0.1.11_all.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/t/twisted/python-twisted-core_8.1.0-4_all.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/t/twisted-web2/python-twisted-web2_8.1.0-1_all.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/p/python-pysqlite2/python-pysqlite2_2.4.1-1_i386.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/t/twisted/python-twisted-bin_8.1.0-4_i386.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/z/zope3/python-zopeinterface_3.3.1-7build1_i386.deb

dpkg -i python-zopeinterface_3.3.1-7build1_i386.deb
dpkg -i python-twisted-bin_8.1.0-4_i386.deb
dpkg -i python-twisted-core_8.1.0-4_all.deb
dpkg -i python-twisted-web2_8.1.0-1_all.deb
dpkg -i *.deb</pre>

```

For 64-bit versions use this script:

```

#!/bin/bash

mkdir /tmp/apt-p2p
cd /tmp/apt-p2p

wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/universe/a/apt-p2p/apt-p2p_0.1.5_all.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/p/python-debian/python-debian_0.1.11_all.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/t/twisted/python-twisted-core_8.1.0-4_all.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/t/twisted-web2/python-twisted-web2_8.1.0-1_all.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/p/python-pysqlite2/python-pysqlite2_2.4.1-1_amd64.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/t/twisted/python-twisted-bin_8.1.0-4_amd64.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/z/zope3/python-zopeinterface_3.3.1-7build1_amd64.deb

dpkg -i python-zopeinterface_3.3.1-7build1_amd64.deb
dpkg -i python-twisted-bin_8.1.0-4_amd64.deb
dpkg -i python-twisted-core_8.1.0-4_all.deb
dpkg -i python-twisted-web2_8.1.0-1_all.deb
dpkg -i *.deb

```

Save the according script into a file called "apt-p2p.sh" on your desktop. Then open a terminal (*Applications --> System --> Terminal*) and issue those commands (you'll be prompted for your user password):

```

cd ~/Desktop
sudo sh apt-p2p.sh

```

[SIZE="1"]
Those little scripts will create a apt-p2p folder in the /tmp folder.
Then it will enter that folder.
Then it will download apt-p2p from the intrepid repositories (they work fine on hardy) including all dependencies.
At the end it will install them in the required order.
[/SIZE]


**[SIZE="4"]Step 4: Prepare the sources.list[/SIZE]**

Once installed type the following:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-apt-p2p-backup
gksudo gedit /etc/apt/sources.list

```

Now you are looking at the sources.list file for Ubuntu; this specifies which servers to contact for updates and new programs. You should see a bunch of lines that look similar to this:

```

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://*mirror-address*/ubuntu/ hardy main universe restricted multiverse
deb-src http://*mirror-address*/ubuntu/ hardy main universe restricted multiverse

```

where ***mirror-address*** is the address of the mirror you chose earlier.

Don't worry, you may not have all of these, and you may have more. However, you only want to change ones that are similar to these. You want to change these to look like this:

```

deb http://localhost:9977/archive.canonical.com/ubuntu hardy partner
deb-src http://localhost:9977/archive.canonical.com/ubuntu hardy partner
deb http://localhost:9977/*mirror-address*/ubuntu/ hardy main universe restricted multiverse
deb-src http://localhost:9977/*mirror-address*/ubuntu/ hardy main universe restricted multiverse

```

So basically just insert *"localhost:9977"* after the *"http://"* Now close the program and save the file.

[SIZE="1"]Note: If you messed anything up, go back to the terminal and run this command:

```

sudo cp /etc/apt/sources.list-apt-p2p-backup /etc/apt/sources.list

```

This WILL overwrite your sources.list file with your backup and we are almost done![/SIZE]


**[SIZE="4"]Step 5: Update the packages &amp; upgrade to Intrepid[/SIZE]**

In order to update the packages now type in the terminal:

```

sudo apt-get update

```

This will update the list of software, as well as fully integrate apt-p2p. If you get any errors, run the following commands (*Warning:* If not done carefully, these commands could destroy your system):

```

sudo rm -rf /var/cache/apt-p2p/cache/*<br>
sudo apt-get update

```

Once everything looks okay, you'll want to forward the ports for apt-p2p to your system (if you have a router, see [http://portforward.com]("http://portforward.com"), port for apt-p2p is *9977 TCP and UDP*). At this point, you're all set to receive regular updates via BitTorrent. If you want to upgrade to Intrepid ahead of time you may type one of the following commands in the terminal:

```

sudo update-manager -d

```

Click then on the "upgrade" button on the top right of that window and follow the wizard. When asked, that no valid mirror was found and whether it shall replace hardy with intrepid, then select "Yes".

or

```

sudo apt-get dist-upgrade

```

*Note: When issuing a "dist-upgrade" in the terminal you will first need to manually alter the entries in the sources.list from "hardy" to "intrepid".*

Now you're all set, and by using BitTorrent to update Ubuntu you will be updated much faster, and help relieve the strain on the update servers on launch day. As always, tips and suggestions are welcome in the comments.

---

### Post by jdong on 2008-10-29
It is **NOT SUPPORTED** and **NOT RECOMMENDED** to directly install Intrepid debs on Hardy. I highly recommend building the necessary packages in a Hardy PPA instead. Proceed at your own risk. In addition, the .debs being installed bypass GPG checking -- there is no guarantee they are authentic.

---

### Post by NeoFax on 2008-11-12
This was working fine and now I receive connection refused to localhost:9977.  Other than reverting back, what can I do?

SOLVED my problem.  Just needed to start the background daemon (sudo invoke-rc.d apt-p2p).  Which is strange as it is started in every runlevel.

---

### Post by hyper_ch on 2008-11-12
neofax:

maybe have a look at the logs why it went down :)

---

### Post by zika on 2009-01-02
I've made this work on my computer a while ago, in October I think. since then it worked OK but it seems it uses too much of my network and make congestion in times I would least want it ... so, question is simple: how can I revert back to doing updates without p2p? I know that by removing localhost:9977/ in all sources.list entries I will do updates 'normally' but the real question is: how to disable apt-p2p? I have several ideas but I'm not sure so I don't want to make a mistake. I've noticed that there was no updates for some time, but that might be normal ...
```
/etc/init.d/apt-p2p stop
``` works but network traffic doesn't stop with it.
**update**1: it works, I've closed ports 9977 and 51413 on router that were assigned to this machine and traffic stopped. now **I need just a hint how to stop apt-p2p from getting up on boot** so I do not have to stop it. I've made entry in Sessions so, for now it is kind of solved.
**update**2: wow, in the meantime my bandwidth got from 1024/128 Kbps to 4096/256 Kbps and I can finally see the benefits since those torrents used a big part of my upload rate and ... never mind now its solved ... ;)

---

### Post by hyper_ch on 2009-01-03
simply remove the package and restore the sources.list to the original state :)

---

### Post by zika on 2009-01-03
> **hyper_ch said:**
> simply remove the package and restore the sources.list to the original state :)
that won't do, as You can see from my post, I hope. > works but network traffic doesn't stop with it with apt-p2p stopped there is bless full silence on my network but I still have to figure out how to prevent that piece of daemon (or whatever) being called at boot.

---

### Post by hyper_ch on 2009-01-03
it works because
(a) you did not remove the package, just stop the service
(b) if you stop a p2p app the connection won't drop instantly dead

---

### Post by zika on 2009-01-03
> **hyper_ch said:**
> it works because
(a) you did not remove the package, just stop the service
(b) if you stop a p2p app the connection won't drop instantly dead

OK we agree ... ;) isn't that just the thing I've just wrote ...?

how do I prevent it from waking up every time I boot?

I, momentarily do not want to remove the package (for one reason is because I am not sure how to do that and do not do the damage to the rest of the system, even though I would, probably know how to make a remedy, the other reason is that it might get useful in april, again) but I just want to put it on hold.

am I right when I say that You are suggesting:```
sudo apt-get remove --purge apt-p2p python-debian python-twisted-core python-twisted-web2 python-pysqlite python-twisted-bin python-zopeinterface
```should do the trick and it will not take with it nothing that was here before I did the script given above ... ?

my idea was less radical, just to disable it from the boot list or whatever is the right name ... after some thought, it's OK the way it is right now ...

---

### Post by hyper_ch on 2009-01-03
[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

---

### Post by zika on 2009-01-03
thanks. I'll consider it. link clarified things to me.

---

### Post by puppe on 2009-11-07
Anyone still using apt-p2p?
Would like to know if there is a way to limit upload speed in any way. Otherwise I'm afraid my line will soon get clogged.
Thanks for reply.

---

