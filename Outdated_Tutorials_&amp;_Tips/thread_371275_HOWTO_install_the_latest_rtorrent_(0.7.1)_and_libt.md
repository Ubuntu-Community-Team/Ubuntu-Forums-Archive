---
title: "HOWTO: install the latest rtorrent (0.7.1) and libtorrent (0.11.1)"
date: 2007-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by bruenig on 2007-02-26
The repos are a bit behind in their rtorrent packaging. The version there is 0.5.3. So on that premise, I have the following howto for the latest.

**1.** Alright, first dependencies. The following command should install them all.

```
sudo apt-get install build-essential libsigc++-2.0-dev pkg-config comerr-dev libcurl3-openssl-dev libidn11-dev libkadm55 libkrb5-dev libssl-dev zlib1g-dev libncurses5 libncurses5-dev
```

Also make sure you have removed the repository rtorrent and libtorrent, assuming you have them installed.

```
sudo apt-get remove rtorrent libtorrent7
```

**2.** Get and install libtorrent 0.11.1. It installs in /usr/local.
```
cd
wget http://libtorrent.rakshasa.no/downloads/libtorrent-0.11.1.tar.gz
tar xf libtorrent-0.11.1.tar.gz
cd libtorrent-0.11.1
./configure
make
sudo make install
```

**3.** Get and install rtorrent 0.7.1. Also installs in /usr/local.

```
cd
wget http://libtorrent.rakshasa.no/downloads/rtorrent-0.7.1.tar.gz
tar xf rtorrent-0.7.1.tar.gz
cd rtorrent-0.7.1
./configure
make
sudo make install
```

**4.** Assuming you want to remove all the packaging and extracted directories.

```
cd
rm -rf rtorrent-0.7.1.tar.gz rtorrent-0.7.1 libtorrent-0.11.1.tar.gz libtorrent-0.11.1
```

And just run "rtorrent" to use it.

EDIT: Apparently some people are having problems when they run rtorrent after the install and it not working. It looks like right after you install it is looking for /usr/bin/rtorrent when you do this instead of /usr/local/bin/rtorrent which is where the new one is installed. It is said below that logging out and logging back in will fix this, and I assume also that just typing /usr/local/bin/rtorrent will work too if you don't want to log out. 

Comments are welcome.

---

### Post by myrek on 2007-02-27
Great HOWTO, worked perfectly for me. Thank you very much.

---

### Post by HwyXingFrog on 2007-02-28
Also worked perfectly for me, I probably wouldn't have tried it if I hadn't found this How-To.

Thanks.

Now I just have to figure out how to use it. Any easy way of leaving it running, and still check it whenever you want?

One more step keeping me from upgrading to Vista, and utorrent & wine do work quite nicely.

---

### Post by Koaesica on 2007-03-04
Worked great. Thank you!

---

### Post by kotti on 2007-03-07
I had the repository rtorrent installed (never noticed it was that outdated) and tried this guide to update it. First removed the old version using your "sudo apt-get remove rtorrent libtorrent7" line and then installed the newer versions. The install seemed to go without any hitch (or, at least it didn't give out any apparent error messages) but when I type rtorrent into the console I get "bash: /usr/bin/rtorrent: No such file or directory"

Any idea what might be causing this and how to fix it?

---

### Post by lprofil on 2007-03-07
**@kotti**

> **kotti said:**
> ... but when I type rtorrent into the console I get "bash: /usr/bin/rtorrent: No such file or directory"

Any idea what might be causing this and how to fix it?

Log out and in again. 
It worked for me.

/lprofil

ps:
> **kotti said:**
>  (never noticed it was that outdated)
Well, the philosophy of any distributor is to assemble a bunch of packages around the linux-kernel which work flawless together.
Once it (almost) all works, the dirstro is released.

To the time Edgy Eft (01-October-2006) was released, that version of rtorrent (0.5.3 - 23-May-2006 07:21) was quiet up to date.
If you want to garantee that a distro works stable, you usually just upgrade few things and security issues.
Newer versions of the programms are then available in the testing (later stable)  releases - currently "Feisty Fawn".

---

### Post by watson540 on 2007-03-07
Thank you for bringing it to my attention that rtorrent from repo's are seriously outdated. rtorrent has always been my favorite (azureus bloat can burn along with anyone fool enough to use it). rtorrent does however like to seg fault a lot, namely when i start and stop various files with it or maybe open up 1 too many torrents. I'm interested to see the stability of this new release

---

### Post by kotti on 2007-03-07
> **lprofil said:**
> **@kotti**

Log out and in again. 
It worked for me.

/lprofil

Ah that did the trick. I was a bit puzzled when everything seemed to go fine with the install and it didn't work. Thanks!

Edit: and of course thanks bruenig for the guide :)

---

### Post by lprofil on 2007-03-08
If you are fine with the bleeding edge unstable verion of rtorrent here are my adds to bruenigs tutorial.

I describe how you install the current unstable version.
They are 'libtorrent 0.11.[COLOR="Red"]2[/COLOR]' and 'rtorrent 0.7.[COLOR="Red"]2[/COLOR]'

I also shrinked the commands to one line each and added the option **-y** to avoid **apt-get** 
asking you if you want to update, remove or whatever something.


**bruenigs modified composition:**

**#1.** Dependcies

```
sudo apt-get install -y build-essential libsigc++-2.0-dev pkg-config comerr-dev libcurl3-openssl-dev libidn11-dev libkadm55 libkrb5-dev libssl-dev zlib1g-dev libncurses5 libncurses5-dev
```

**#2.** Remove all old version of rtorrent

```
sudo apt-get remove -y rtorrent libtorrent*
```


**#3.** Get packages and unpack them

```
cd /opt && wget http://libtorrent.rakshasa.no/downloads/libtorrent-0.11.2.tar.gz && wget http://libtorrent.rakshasa.no/downloads/rtorrent-0.7.2.tar.gz && tar xf libtorrent* && tar xf rtorrent*
```

**#4.** Configure / Compile / Install

First for libtorrent:

```
cd /opt/libtorrent-0.11.2 && ./configure --prefix=/usr && make && sudo make install
```

Then for rtorrent:
```
cd /opt/rtorrent-0.7.2 && ./configure --prefix=/usr && make && sudo make install
```

**#5.** Cleaning up
```
cd /opt && rm -R libtor* && rm -R rtorr*
```

If rtorrent does not start because you see this error message:

```
bash: /usr/bin/rtorrent: No such file or directory
```

logout and login. It should work then


Cheers
/lprofil

---

### Post by shirilover on 2007-03-08
The newer versions you refer to are from the unstable branch.
When I compiled it, I had no such problems with the file not being found.
You may wish to try the follwing instead:

```
screen rtorrent
```

Also, if you wish the files to be installed in /usr/bin and /usr/lib you can use the following configure syntax:

```
./configure --prefix=/usr && make && sudo make install
```

---

### Post by bruenig on 2007-03-08
> **lprofil said:**
> To update bruenigs tutorial: there are even newer versions available.
They are 'libtorrent 0.11.[COLOR="Red"]2[/COLOR]' and 'rtorrent 0.7.[COLOR="Red"]2[/COLOR]'

I also shrinked the commands to one line each and added the option **-y** to avoid **apt-get** 
asking you if you want to update, remove or whatever something.

Some problems:

1. Your newer version is unstable, might want to mention that.

2. using --purge removes configuration directories and if people want to keep their rtorrent configurations, that would not be a good thing.

3. /opt doesn't have write permissions for the user, so wgetting them into /opt won't work unless you use sudo and is kind of unnecessary anyways.

---

### Post by lprofil on 2007-03-08
Thank you bruenig and shirilover for your critics.

I have changed my commands as you recommended.

> **bruenig said:**
> 
3. /opt doesn't have write permissions for the user, so wgetting them into /opt won't work unless you use sudo and is kind of unnecessary anyways.

Nope. I use /opt only for unpacking configuring and making. The binaries (for my understanding) are installed in /usr/bin so a regular user has permisson to run rtorrent.

/lprofil

---

### Post by bruenig on 2007-03-08
lprofil,

What I meant by the /opt part is that by default unless maybe you chmodded or chowned it, /opt is owned by root and has 755 permissions which means that you can't write to it as a user. So that wget command will fail because it won't be able to put those downloads in /opt due to lack of permissions.

Your setup may be different but by default the
```
cd /opt && wget http://libtorrent.rakshasa.no/downloads/libtorrent-0.11.2.tar.gz && wget http://libtorrent.rakshasa.no/downloads/rtorrent-0.7.2.tar.gz && tar xf libtorrent* && tar xf rtorrent*
```

command will fail and will return a wget error of permission denied. Doing it in /home/username would fix that problem.

Oh and an just a personal preference thing, it installs in /usr/local by default. That to me seems like a better idea just for organization sake, segregating compiled stuff from repo stuff.

---

### Post by AngryGnome on 2007-03-10
I'm getting this error:

"Could not read resource file: ~/.rtorrent.rc"

And I'm kind of a linux noob... so... any help?

---

### Post by bruenig on 2007-03-10
But is it still launching? The rtorrent.rc is just for preferences. If it doesn't exist, it just doesn't read any of the preferences and goes with the default. When I launch it, that same message shows up, but rtorrent still works.

---

### Post by AngryGnome on 2007-03-11
Yeah... but some of us NEED those preferences.  I need to be able to change some of those things.

---

### Post by bruenig on 2007-03-11
> **AngryGnome said:**
> Yeah... but some of us NEED those preferences.  I need to be able to change some of those things.

Well if you need them just
```
gedit ~/.rtorrent.rc
```
and set it up.

---

### Post by AngryGnome on 2007-03-11
> **bruenig said:**
> Well if you need them just
```
gedit ~/.rtorrent.rc
```
and set it up.


Wow... heh... I feel dumb. (Don't know why I didn't think of that.) Thanks for your help. :-)

---

### Post by chomafin on 2007-03-13
cross posting from: [http://www.ubuntuforums.org/showthread.php?p=2290946&posted=1](http://www.ubuntuforums.org/showthread.php?p=2290946&posted=1)


It seems the default install may not include the rtorrent settings. If you go to the official website of libtorrent, there is a default .rtorrent.rc file. Just grab and edit that to your likeing. The rtorrent.rc file is pretty easy to follow w/ the comments, and if not check the FAQ [http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)

To get the Default settings, this *should* work.:
```

cd ~/
wget http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest
mv rtorrent.rc\?rev\=latest .rtorrent.rc

```and then to Edit the settings of rTorrent,
```

gedit ~/.rtorrent.rc

```

---

### Post by gyaresu on 2007-05-24
Thanks bruenig.

Simple little upgrade to stop a segfaulting rtorrent.

Nice work.

---

### Post by jakethecake on 2007-06-11
Simpler solution; you don't have to strip the config file of the line numbering and html tags.


```

gedit 'http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest&format=raw'

```
Edit the file to your liking and save the file as ~/.rtorrent.rc

(Installed libtorrent 0.11.4/rtorrent 0.7.4 on ubuntu server (64bit) with the instructions at the beginning of this post.)

/Jake

---

### Post by Aberrix on 2007-08-20
thank you very very much for this guide!

worked perfect for rtorrent 0.7.6 and libtorrent 0.11.6

thank you again!

---

### Post by sfed on 2007-08-29
When I type rtorrent in terminal it displays I get this  *** rTorrent 0.7.1 - libTorrent 0.11.1 ***
which means that I have installed it successfully .But when I type 
```
sudo apt-get remove rtorrent libtorrent7
```
 I get this message
```
sudo apt-get remove rtorrent libtorrent7
```

---

### Post by ge5239 on 2007-11-04
followed the guide, which have helped me previously, but this time i got; 
rtorrent: error while loading shared libraries: libtorrent.so.10: cannot open shared object file: No such file or directory

..and from whatever i understood from the info, i did install everything. 
this is the latest unstable version of rtorrent, 
    * libtorrent-0.11.9.tar.gz
    * rtorrent-0.7.9.tar.gz 

*.8 gave same thing though. what am i forgetting?

---

### Post by bhe on 2007-11-05
> **ge5239 said:**
> followed the guide, which have helped me previously, but this time i got; 
rtorrent: error while loading shared libraries: libtorrent.so.10: cannot open shared object file: No such file or directory

..and from whatever i understood from the info, i did install everything. 
this is the latest unstable version of rtorrent, 
    * libtorrent-0.11.9.tar.gz
    * rtorrent-0.7.9.tar.gz 

*.8 gave same thing though. what am i forgetting?

I'm having the same problem.
A couple of months ago, I installed an older version, and that worked perfectly.
But libtorrent 0.11.8 and rtorrent 0.7.8 give me the mentioned error.

Anybody have a clue about what is going wrong?

EDIT:
I found the solution.
Add the following line to /etc/ld.so.conf
include /usr/local/lib

Run ldconfig

rtorrent will run fine now!

---

### Post by airtonix on 2007-11-10
didnt work for me

---

### Post by shplog on 2007-11-14
didn't work for me either.

---

### Post by DCM36 on 2007-11-15
bhe's solution worked for me on a fresh install of gusty.. i used compile instructions from [here]("http://code.google.com/p/ntorrent/wiki/QuickStart")

---

### Post by okej01 on 2007-11-15
I used this howto and all worked fantastically

[http://www.howtoforge.com/compiling_rtorrent_from_svn_on_ubuntu_gutsy_gibbon]("http://www.howtoforge.com/compiling_rtorrent_from_svn_on_ubuntu_gutsy_gibbon")

This user guide was very helpful:

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/")

---

### Post by Lividity on 2007-11-22
> **bhe said:**
> 
I found the solution.
Add the following line to /etc/ld.so.conf
include /usr/local/lib

Run ldconfig

rtorrent will run fine now!

Thanks bhe Your solution worked perfectly. 

I was receiving the following error:

rtorrent: error while loading shared libraries: libtorrent.so.10: cannot open shared object file: No such file or directory

# To solve this problem from the terminal typed:

sudo nano  /etc/ld.so.conf

# Then pasted the following text:

include /usr/local/lib

# Then I saved the file I edited. I fired up the terminal and typed: 

sudo ldconfig

# Then I typed:

rtorrent 

and everything is running just fine

In rtorrent 0.8.4 libtorrent 0.12.4 this solution stopped working for me. I instead used:

./autogen.sh && ./configure --libdir=/usr/local/lib && make

---

### Post by ghostlines on 2007-12-09
I am trying to compile it but i get this error:
                aclocal...
                aclocal not found
Though I am trying to install it on an ubuntu server, feisty fawn 64bit to be exact. The apt-get version worked great but that doesn't have encryption it's an old version.

Does anyone no how to solve this?
Any help will be certainly appreciated.

---

### Post by ghostlines on 2007-12-09
the problem was i needed to install automake, i did have autoconf and some other auto's i think but not automake. now i'm getting further

---

### Post by magnismo on 2008-02-20
thank you for a great guide and it worked like a charm. i just used the newest stable release of rtorrent and libtorrent. very very nice.

version rtorrent 0.79, libtorrent 0.11.9 and by the way i used it on debian aswell samething accept the  sudo part

---

### Post by Adam590 on 2008-03-10
***EDITED***

Had the outdated versions from the Feisty repos until I got the hang of it, then I wanted to update.

I used Synaptic to remove rtorrent and libtorrent.

Built rtorrent 0.7.9 and libtorrent 0.11.9 as per the directions here, and rtorrent fired right up - it even used the rtorrent.rc file from my previous install for its settings. 

Only one issue: I had some completed and partially downloaded files that do show up, but rtorrent wants to start downloading them all over again from zero. How do I get it to recognize the existing files and parts of files?

Thanks,
Adam



**EDIT:** 

Nevermind - the second time I started it the hashing worked fine and recognized my files, yay!   \\:D/

---

### Post by teddybar on 2008-03-27
i try make and it show erros: 

```
make[3]: Entering directory `/home/admin/rtorrent-0.7.9/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -O2 -Wall -g -DDEBUG -I/usr/local/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -MT command_download.o -MD -MP -MF ".deps/command_download.Tpo" -c -o command_download.o command_download.cc; \
        then mv -f ".deps/command_download.Tpo" ".deps/command_download.Po"; else rm -f ".deps/command_download.Tpo"; exit 1; fi
command_download.cc: In function 'void initialize_command_download()':
command_download.cc:395: error: 'is_pex_active' is not a member of 'torrent::Download'
command_download.cc:471: error: 'size_pex' is not a member of 'torrent::Download'
command_download.cc:472: error: 'max_size_pex' is not a member of 'torrent::Download'
make[3]: *** [command_download.o] Error 1
make[3]: Leaving directory `/home/admin/rtorrent-0.7.9/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/admin/rtorrent-0.7.9/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/admin/rtorrent-0.7.9'
make: *** [all] Error 2
```

---

### Post by flokason on 2008-04-22
At first, I got the ncurses error, but I followed the HOWTO and got ./configure to work.

But when I do make, I get this:




```
download.cc:66: error: no matching function for call to &#8216;torrent::TrackerList::TrackerList(torrent::TrackerList*)&#8217;
/usr/local/include/torrent/tracker_list.h:145: note: candidates are: torrent::TrackerList::TrackerList(const torrent::TrackerList&)
/usr/local/include/torrent/tracker_list.h:81: note:                 torrent::TrackerList::TrackerList(torrent::TrackerManager*)
download.cc: In member function &#8216;void core::Download::enable_udp_trackers(bool)&#8217;:
download.cc:88: error: conversion from &#8216;torrent::TrackerList*&#8217; to non-scalar type &#8216;torrent::TrackerList&#8217; requested
download.cc:91: error: &#8216;class torrent::TrackerList&#8217; has no member named &#8216;get&#8217;
download.cc:93: error: &#8216;class torrent::TrackerList&#8217; has no member named &#8216;get&#8217;
download.cc:95: error: &#8216;class torrent::TrackerList&#8217; has no member named &#8216;get&#8217;
make[3]: *** [download.o] Error 1
make[3]: Leaving directory `/home/arnar/rtorrent-0.7.9/src/core'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/arnar/rtorrent-0.7.9/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/arnar/rtorrent-0.7.9'
make: *** [all] Error 2

```

any ideas?

EDIT*
I found out I was using libtorrent12.1 which is unstable, I put 11.9 in and it worked

rtorrent is up and running, but I get this error in rtorrent:
```
torrent: symbol lookup error: rtorrent: undefined symbol: _ZN7torrent8Download15set_pex_enabledEb
```

I get the feeling like the libtorrent 12.1 is the reason, because I didnt remove it, I just configure/make/sudo make install libtorrent 11.9

So I want to uninstall rtorrent and the libtorrents, so I can reinstall them correctly.

But How do I uninstall rtorrent and libtorrents?


edit:
I just did a clean install of the new ubuntu, so Idont have this problem anymore

---

### Post by Kalden on 2008-04-27
Hi,

I tried to install rtorrent 0.8.0 and libtorrent 0.12.0

I did the following steps : 
After installing the dependencies
```
sudo apt-get remove rtorrent libtorrent10
```
```
wget http://libtorrent.rakshasa.no/downloads/libtorrent-0.12.0.tar.gz
tar xf libtorrent-0.12.0.tar.gz
cd libtorrent-0.12.0/
./configure
make
sudo make install
```
```
wget http://libtorrent.rakshasa.no/downloads/rtorrent-0.8.0.tar.gz
tar xf rtorrent-0.8.0.tar.gz
cd rtorrent-0.8.0/
./configure
make
sudo make install
```

When I want to start rtorrent I get this message : 
error while loading shared libraries: libtorrent.so.11: cannot open shared object file: No such file or directory

How can I solve this ?

---

### Post by hyper_ch on 2008-05-05
for compiling rtorrent from svn on gutsy and hardy you can use my little howto that I made a long time ago. It's tested up to revision 1057

[http://www.howtoforge.com/compiling_rtorrent_from_svn_on_ubuntu_gutsy_gibbon](http://www.howtoforge.com/compiling_rtorrent_from_svn_on_ubuntu_gutsy_gibbon)

---

### Post by karmik on 2008-06-24
[screen](http://www.gnu.org/software/screen/) is your friend :) (man screen :P)
I use it on my homeserver, works great. Too bad it doesn't support teredo and other niffy things, but eh you can't complain what you don't provide for yourself.

---

### Post by verymagicalguy on 2008-07-26
> **Kalden said:**
> 

When I want to start rtorrent I get this message : 
error while loading shared libraries: libtorrent.so.11: cannot open shared object file: No such file or directory

How can I solve this ?

```
sudo ldconfig
```

This solved the problem for me.

Great guide! It works great for rtorrent-0.8.2 and libtorrent-0.12.2! Thanks!

---

### Post by Kalden on 2008-07-26
> **verymagicalguy said:**
> ```
sudo ldconfig
```

This solved the problem for me.

Great guide! It works great for rtorrent-0.8.2 and libtorrent-0.12.2! Thanks!

Thanks, I'll try that.

Kalden

---

### Post by ercdvs on 2008-11-10
Gonna bump this up a bit.
using the latest rtorrent from apt-get ..

has anyone has an issue with memory usage?

from a fresh boot, the process takes 10mb off the top, and every 1 minute seems to grab another 10mb or so.

quiting rtorrent recovers the initial 10mb usage, but the ebbed away memory is still gone, until a reboot.

anybody else seeing this?

---

### Post by hyper_ch on 2008-11-10
it's the way linux uses ram... why free it if it's not needed by something else.. unused ram = wasted ram...

btw, I'd suggest to use rtorrent from svn :)

---

