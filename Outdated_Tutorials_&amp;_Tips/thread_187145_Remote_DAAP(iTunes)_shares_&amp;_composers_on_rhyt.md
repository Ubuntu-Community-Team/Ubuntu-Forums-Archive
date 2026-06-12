---
title: "Remote DAAP(iTunes) shares &amp; composers on rhythmbox"
date: 2006-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Pausanias on 2006-06-02
One of the cool things about rhythmbox is the ability to recognize DAAP(=iTunes) shares. This means that if you have iTunes or another DAAP server on your local network, rhythmbox ought to be able to pick those up and show them as remote playlists. Then you can listen to them on your computer as long as you have the right codecs installed.

But what if the share is on a remote network? For example, I have a PowerMac running an iTunes server, and I want to be able to listen to the music on it wherever I am on my Ubuntu laptop. Is this possible? You bet, using rhythmbox, ssh, and avahi-daemon. Read on for a detailed HOWTO.

**Note that if you are using iTunes as your server, this hint will only work with iTunes 6 or below. Apple purposely broke iTunes 7 so that it would not work with 3rd party software**. To see instructions for downgrading to iTunes 6, see [my post here](http://ubuntuforums.org/showthread.php?t=435885&p=2610554).

First things first. Let's face it, you cannot listen to a lot of the formats used by iTunes without the right codecs. And those codecs don't come bundled with Ubuntu. However, you can easily enable them. You do this by enabling the universe and multiverse repositories and installing the right packages. To enable the repositories, go to System->Administration->Software Properties. In the list, activate all the items that contain the phrase "Non-free" or "Community Maintained," **except** for the ones that also say "Backports." Do not enable "Backports" unless you know what you are doing.

Once you have the non-free and community maintained (aka, "multiverse" and "universe") repositories enabled, you can install the right codecs using the Terminal (goto Accessories->Terminal and copy and paste the following in):

```

sudo apt-get update 
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse

```
Enter your password when it asks you, and answer yes (Y) to all the questions.

If you're happy listening to rhythmbox on your local network, you can stop here. You are all set; you should be able to launch "Rhythmbox Music Player" from the menu and it should recognize and play all your local iTunes shares.

OK, so if you're still reading you must be curious about listening to remote iTunes shares (and viewing composer tags in those shares). You will need an account on the machine that has the DAAP/iTunes share for this to work. It can be either a linux or Mac OS X machine.

Unfortunately, rhythmbox won't work out of the box here. I have built a modified version that can recognize tunneled shares broadcast with avahi.

Make a folder called "rbhack" on your desktop. Download all the attachments to this message (see below) to that directory. Then from the terminal, reconstruct the package:
```

cd ~/Desktop/rbhack
gunzip -c *gz > rhythmbox_0.10.0-0ubuntu1pausanias_i386.deb

```

Now install it:
```

sudo apt-get install avahi-daemon avahi-utils
sudo dpkg -i rhythmbox_0.10.0-0ubuntu1pausanias_i386.deb

```
Answer yes to all the questions.

That was easy, right? Now, everytime you want to connect to the remote host, issue the following commands
```

ssh -f -g -L 3689:127.0.0.1:3689 -N username@hostname 
avahi-publish-service sharename _daap._tcp 3689 &

```
where hostname is the host on which the iTunes/DAAP server sits, username is your username on that server, and sharename is the name of the share as advertised by the host.

That should be it! Now when you boot rhythmbox, you should be able to see your remote share listed under sharename. As a bonus, if your songs have composer information, that information will be listed under the artist column as Composer -- Artist.

The source code for the above changes will be provided in a post below.

---

### Post by jazer on 2007-07-02
This looks like exactly the help I need, but after installing avahi-daemon I get a "command not found" when I try to run avahi-publish-service

Any ideas? I am a total noob.

---

### Post by Pausanias on 2007-07-11
Hi jazer,

Thanks for your interest. The instructions you originally read were for Dapper. The packages have changed somewhat, so that now you need to install avahi-utils as well. In addition, my old deb didn't work with Feisty.

I have now modified the instructions above and posted a new deb which works with Feisty/7.04.

In addition, I am attaching the debdiff file needed if you want to compile the thing from source yourself (and also to fulfill my requirements under the GPL :wink:) If you're wondering just how to use the file, assuming you've saved it to a directory called rbcomp:

```

cd rbcomp
sudo apt-get install build-essential
sudo apt-get build-dep rhythmbox
apt-get -d source rhythmbox
tar xvzf *orig*gz
gunzip -c *paus* | patch -p0
cd rhythmbox-0.10.0
chmod u+x debian/*
dpkg-buildpackage -rfakeroot -uc -us
cd ..

```

Then follow the instructions above starting with "dpkg -i".

---

### Post by Rinnan on 2007-11-15
Pausanias - 

Does this work for Gutsy?

---

### Post by Pausanias on 2007-11-15
This patch will not work with gutsy; however, it is obsolete. The version of rhythmbox in gutsy will recognize local DAAP shares, so there is no need for a patch.

---

### Post by jesse0 on 2007-11-24
Just to be really clear, this is all you need to do now:

```

/usr/bin/avahi-publish -H remote -s "My Music" _daap._tcp 3689 &

```

Where remote is the fully qualified domain name of your remote DAAP share, I don't know if an IP would work but I would guess so. Then start rhythmbox and "My Music" will appear under your shared music section. I have the above command run when I log into GNOME.

Jesse.

---

