---
title: "HOWTO: Install mediatomb 0.9 UPnP Media Server from source"
date: 2007-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Blues- on 2007-03-30
The guys who develope the mediatomb upnp mediaserver have finally released version 0.9.
Both SQLite and Mysql are supported as storage drivers, so I'll just add support for them both in the installation process and then you can choose which one you will use.

When this is written there are no deb packages available so I took some notes on the packages needed for the package to compile.  Here are the results:

NB. this a HOWTO is for Ubuntu Edgy or Feisty Fawn

**1)  Download the mediatomb source and extract it**
```

wget http://kent.dl.sourceforge.net/sourceforge/mediatomb/mediatomb-0.9.0.tar.gz
tar -xvzf mediatomb-0.9.0.tar.gz
cd mediatomb-0.9.0

```

**2) Install the required packages so the package will compile**
If you do not have the build essentials required to build packages from source ..
install them
```

sudo apt-get install build-essential

```

Then head on to install the required libraries and development headers.
a) install mysql storage support
```
sudo apt-get install libmysqlclient15-dev
```
b) install sqlite storage support
```
sudo apt-get install sqlite3 libsqlite3-dev
```
c) install libmagic headers and id3lib headers
```
sudo apt-get install libmagic-dev libid3-dev
```
d) Now the tricky part .. installing the Spidermonkey Javascript engine.
There are known dependancy problems with the spidermonkey package and some mozilla packages.  To avoid that problems .. we will do this another way ..

First install the none problematic package, (do not install package "libmozjs-dev")
```

sudo apt-get install libmozjs0d

```

Then create symlink to avoid name clashes with old libraries
```
sudo ln /usr/lib/libmozjs.so.0d /usr/lib/libmozjs.so
```

Then d/l the updated header files from the mediatomb website ..
and unpack it ..
```

wget http://mediatomb.org/edgy_mediatomb_libmozjs-h.tar.gz
tar -xvzf edgy_mediatomb_libmozjs-h.tar.gz

```

Run the configure command to check the build environment, and point to the new header files.  Substitute "/full/path/to/headers" with the directory where you extracted the edgy_mediatomb_libmozjs-h.tar.gz tarball.
```

./configure --with-js-h=/full/path/to/headers

```

Then compile the source with make
```

make

```

Then install the package, you can use "sudo make install" but to keep my system tidy and
having the uninstall option .. i recommend using checkinstall to build the package ..
```

sudo checkinstall

```

If you used the checkinstall method, you can now install the deb package ..
```

sudo dpkg -i mediatomb_0.9.0-1_i386.deb

```


If everything went ok ..
start mediatomb from your console
```
mediatomb
```

Now you have mediatomb up and running.
open browser to [http://localhost:49152](http://localhost:49152)

The config file for mediatomb is here: ~/.mediatomb/config.xml
I recommend reading the docs on the mediatomb web before messing around with it.

Now you can add content to your mediaserver and start watching on your media receiver connected to mediatomb.

More details about mediatomb here: [http://mediatomb.cc](http://mediatomb.cc)

Hope someone finds this tutorial useful,
Cheers,
Blues-

---

### Post by jcconnor on 2007-03-31
Great how-to!!!

I had been having some trouble with some other UPNP devices and my Netgear MP101 device.  But Mediatomb appears to work perfectly.

Thanks for putting this together!!

John

---

### Post by christopher_2 on 2007-04-25
This worked great for me and I have never used Linux. How do I set this up so it starts when I log in ?*

---

### Post by lww on 2007-05-03
From now on there are .deb packages for Ubuntu available. See [http://mediatomb.cc/pages/download](http://mediatomb.cc/pages/download) for more information. These packages provide startup scripts, so you will be able to automatically start MediaTomb as daemon at startup.

greets, Leo (one of the developers of MediaTomb)

---

### Post by buckminster on 2007-05-30
I'm fairly unfamiliar with configuring apt repository stuff and the mediatomb download page states this:

> If you want APT to automatically install all dependencies on Ubuntu, you have to enable the “universe” component. (Spidermonkey isn’t part of the “main” component there.)

I assumed it meant for me to add "universe" to the end of this line:

> deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) feisty main

in my /etc/apt/sources.list file, but when I try to update the repository, I get the following message:

> Failed to fetch [http://apt.mediatomb.cc/dists/feisty/Release](http://apt.mediatomb.cc/dists/feisty/Release)  Unable to find expected entry  universe/binary-i386/Packages in Meta-index file (malformed Release file?)

From the looks of [http://apt.mediatomb.cc/dists/feisty/Release](http://apt.mediatomb.cc/dists/feisty/Release), it doesn't list any universe components. What do I need to do to get this to work? Install the dependencies separately? If so, the mediatomb guys should update their download page.

---

### Post by buddaboy on 2007-07-05
> **lww said:**
> From now on there are .deb packages for Ubuntu available. See [http://mediatomb.cc/pages/download](http://mediatomb.cc/pages/download) for more information. These packages provide startup scripts, so you will be able to automatically start MediaTomb as daemon at startup.


Using Ubuntu 6.06.1 LTS I cannot get MediaTomb installed directly from the MediaTomb repos.

```
$ sudo apt-get install mediatomb 
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  mediatomb: Depends: libsmjs1 but it is not installable
E: Broken packages
```

From a bit of searching I discovered the above dependancy is the SpideMonkey javascript lib which is related to Mozilla. It seems it's a bit of a troublespot.

As mentioned at the start, I'm running Ubuntu server edition with no desktop and apps installed like FireFox.

What can I do to rectify this issue? nobody seems to have a solution looking at the search results :(

---

### Post by AndyCat on 2007-07-11
Is there any way to change the ip of the mediatomb server???

---

### Post by TheBogieMan on 2008-01-20
At last !
This is one of the few things that was stopping me moving over completely from XP !
This works a treat with my dusty old MP101 :)

Just one slight problem...well possibly two slight problems, you'll have to bear with me as the last time I got my hands dirty with shell was back in the days of Amiga 500's....yes I am that old.

Everything is working fine with the exception of the database is everything, all I want it to pull is .mp3 files, is there any way of restricting it to pull just one file type or mime type ?

And the next question is can this be started as a service before log on like Twonky can on XP ?

I'm sure there are very simple answers to my questions but I'm more at home with nut's bolt's and bits of motorcycle engine 

Thanks in advance !

---

### Post by ourmaninhavana on 2008-06-26
It all works up until I make, when I get the following:

"Make: *** No targets specified and no makefile found. Stop."

I'm relatively new to linux, and have had a lot of trouble getting any media server working. I had the UI working a while back but couldn't get the PS3 to find the media server. Not even sure that it was running, but that's another issue. I tried uninstalling and reinstalling but to be honest my inexperience may not have achieved this (any tips on uninstalling?) Anyway, I tried reinstalling using the Add/Remove applications method, but when I ran Mediatomb from the menu, the browser returned an address that did not exist (something like ///var/lib/mediatomb/mediatomb.html) and I had no idea how to change it. I figured I'd install from source...and that's when I came up against the current problem.

OMIH

---

### Post by bluesmoke on 2008-09-25
[LIST=1]
Hi,
 I am trying to install the mediatomb on my asus eee pc. I follwed the how to and installed all the required packaages but my problem is that when i run the command ./configure (from inside the mediatomb extracted directory). it displays as:

bash: ./configure:No such file or directory.

Any body can suggest????
regards



[/LIST]

---

### Post by whiteman on 2010-12-22
I tried Blues method subbing lynx for edgy. Pretty silly huh? This is what I ended up with
wth@xps:~$ wget [http://mediatomb.org/lynx_mediatomb_libmozjs-h.tar.gz](http://mediatomb.org/lynx_mediatomb_libmozjs-h.tar.gz)
--2010-12-22 13:25:23--  [http://mediatomb.org/lynx_mediatomb_libmozjs-h.tar.gz](http://mediatomb.org/lynx_mediatomb_libmozjs-h.tar.gz)
Resolving mediatomb.org... 78.47.110.2
Connecting to mediatomb.org|78.47.110.2|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://mediatomb.cc/lynx_mediatomb_libmozjs-h.tar.gz](http://mediatomb.cc/lynx_mediatomb_libmozjs-h.tar.gz) [following]
--2010-12-22 13:25:24--  [http://mediatomb.cc/lynx_mediatomb_libmozjs-h.tar.gz](http://mediatomb.cc/lynx_mediatomb_libmozjs-h.tar.gz)
Resolving mediatomb.cc... 78.47.110.2
Reusing existing connection to mediatomb.org:80.
HTTP request sent, awaiting response... 404 Not Found
2010-12-22 13:25:25 ERROR 404: Not Found.
Any Ideas?

---

