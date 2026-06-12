---
title: "New to VLC and still learning Ubuntu"
date: 2019-03-14
forum: New to Ubuntu
---

### Post by harfin on 2019-03-14
I am unable to play DVD's on my HP Laptop (running bionic beaver) and I am lost trying to understand the language used on help seekers' previous threads. 

When I open VLC media player and insert the DVD into the laptop's internal DVD /CD drive I get:-
[HTML]Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
[/HTML]

Can someone please help in simple language please what I need to do

Alan

---

### Post by yancek on 2019-03-14
What is on the DVD?  Music, home movie, commercial video ...?

---

### Post by harfin on 2019-03-14
It's a DVD bought in the UK from a reputable store and is  the  movie "Paddington 2".

Alan

---

### Post by oldrocker99 on 2019-03-14
I've never done anything but put the disk in the player, and VLC comes up with the disk menu. If not, the disk will show on the desktop. Right-click and choose "Open with VLC," and you should be okay.

---

### Post by harfin on 2019-03-14
Alas I have tried that several times, all to no avail!

The disk is clearly shown on the desktop, and when I request "open" a VLC window appears with two items
VIDEO_TS
AUDIO_TS

If I select VIDEO_TS, it then shows a list of files and if I select all it comes back with:
[HTML]Your input can't be opened:
VLC is unable to open the MRL 'file:///media/harfin/PADDINGTON_2/VIDEO_TS/VTS_01_0.VOB'. Check the log for details.
Your input can't be opened:
VLC is unable to open the MRL 'file:///media/harfin/PADDINGTON_2/VIDEO_TS/VTS_03_0.VOB'. Check the log for details.
[COLOR=#000000]
[/COLOR]
[/HTML] 

Grrrrrrr

---

### Post by monkeybrain20122 on 2019-03-14
How did you install vlc? If it is a snap (installed via the Software Store) then apparently it has some difficulties accessing external media (may include DVD drive) because of sandboxing. If that is the case remove it from the software store and install the .deb with apt
```
sudo apt install vlc
``` and see if it helps.

---

### Post by harfin on 2019-03-15
Sorry, but no it doesnt. 

I did as you said, but the DVD still does not play.  

Just to cross check, I tried a couple of other shop-bought DVD's, and it's the same story. Insert the DVD,The DVD icon pops up on the desktop, but clicking it although it opens VLC the DVD just will not play except for an instantaneous nano-seconds of a buzz then all is quiet.

I don't as a norm buy DVD videos, except for the odd item that I wish to save for posterity. 

I should add that I haven't utilised the facility of playing DVD's on the laptop since I installed Bionic Beaver a few months back. Is that significanT?

Alan

---

### Post by ajgreeny on 2019-03-15
As this is a commercially purchased DVD it is most likely the DVD is encrypted and you probably still need libdvdcss installed.

See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) for all the details and how to do it.

---

### Post by Holger_Gehrke on 2019-03-15
Thank you for reminding me to check whether DVD-playback works ... I set this machine up 2 years ago and had no need of it in all that time. Of course it didn't work. What was missing in my case was the library for CSS (content scrambling system) decoding. Commercial DVDs are partially encrypted. This is both a (half-hearted) attempt at copy protection and a way to make producers of DVD-players pay for a license from the DVD-consortium, so they'll get a key to decrypt the discs. The conditions of that license make it very difficult to write an open source DVD player that has a legit key, because you can't hide the key if your source-code is openly available. Getting and installing the library from videolan.org (makers of vlc) is quite easy. First you need to add their repository to your software sources. Execute this in a terminal 
```

echo 'deb https://download.videolan.org/pub/debian/stable/ /'|sudo tee /etc/apt/sources.list.d/vlc-dvdcss.list
```
Than get the repository signing key and add it to the keys known to the package system
```

wget -O - https://download.videolan.org/pub/debian/videolan-apt.asc | sudo apt-key add -
```
Now update the lists of available packages and install the library
```

sudo apt upgrade
sudo apt install libdvdcss2

```
Two problems with this:
[LIST=1]
[*]If you've installed vlc as a snap, then it can't use the library because snaps are isolated to a certain degree from the rest of the system. 
[*]Depending on where you live, libdvdcss might be illegal, comparable to owning lock picks or specialized tools for breaking and entering. 
[/LIST]
 
Holger

---

### Post by harfin on 2019-03-15
Hi [COLOR=#000000]Holger_Gehrke[/COLOR]
Thanks for that input.

After an earlier posting, I uninstalled VLC  from the Ubuntu software centre, and installed it with "[COLOR=#000000][FONT=&quot]sudo apt install vlc" from the terminal.

I have sighted  the index as you advised, but I am unsure what "the key" looks like that I need to install.  If the key is a string of numbers, then is it, for example, the number "[/FONT][/COLOR][COLOR=#000000]44462" [/COLOR][COLOR=#000000][FONT=&quot]from one item in the index, such as "[/FONT][/COLOR][libdvdcss2_1.2.13-0_amd64.deb]("https://download.videolan.org/pub/debian/stable/libdvdcss2_1.2.13-0_amd64.deb")[COLOR=#000000]                      05-Sep-2013 15:20               44462"?[/COLOR]
[COLOR=#000000][/COLOR]

Secondly which one should I choose of the items on that list (nine in all)!

Alan

---

### Post by flyn633 on 2019-03-15
Does it contain any SW data on it? or is it corrupted?

---

### Post by harfin on 2019-03-16
On entering "sudo apt install libdvdcss2" in the terminal, the following is shown :
> sudo apt install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libdvd-pkg' instead of 'libdvdcss2'
The following additional packages will be installed:
  autoconf automake autopoint autotools-dev build-essential debhelper
  dh-autoreconf dh-strip-nondeterminism dpkg-dev fakeroot g++ g++-7 gcc gcc-7
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libarchive-cpio-perl libasan4 libatomic1 libc-dev-bin libc6-dev libcilkrts5
  libfakeroot libfile-stripnondeterminism-perl libgcc-7-dev libitm1 liblsan0
  libltdl-dev libmail-sendmail-perl libmpx2 libquadmath0 libsigsegv2
  libstdc++-7-dev libsys-hostname-long-perl libtool libtsan0 libubsan0
  linux-libc-dev m4 make manpages-dev po-debconf
Suggested packages:
  autoconf-archive gnu-standards autoconf-doc dh-make dwz debian-keyring
  g++-multilib g++-7-multilib gcc-7-doc libstdc++6-7-dbg gcc-multilib flex
  bison gcc-doc gcc-7-multilib gcc-7-locales libgcc1-dbg libgomp1-dbg
  libitm1-dbg libatomic1-dbg libasan4-dbg liblsan0-dbg libtsan0-dbg
  libubsan0-dbg libcilkrts5-dbg libmpx2-dbg libquadmath0-dbg glibc-doc
  libtool-doc libstdc++-7-doc gfortran | fortran95-compiler gcj-jdk m4-doc
  make-doc libmail-box-perl
The following NEW packages will be installed
  autoconf automake autopoint autotools-dev build-essential debhelper
  dh-autoreconf dh-strip-nondeterminism dpkg-dev fakeroot g++ g++-7 gcc gcc-7
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libarchive-cpio-perl libasan4 libatomic1 libc-dev-bin libc6-dev libcilkrts5
  libdvd-pkg libfakeroot libfile-stripnondeterminism-perl libgcc-7-dev libitm1
  liblsan0 libltdl-dev libmail-sendmail-perl libmpx2 libquadmath0 libsigsegv2
  libstdc++-7-dev libsys-hostname-long-perl libtool libtsan0 libubsan0
  linux-libc-dev m4 make manpages-dev po-debconf
0 to upgrade, 44 to newly install, 0 to remove and 0 not to upgrade.
Need to get 29.9 MB of archives.
After this operation, 126 MB of additional disk space will be used.
Do you want to continue? [Y/n] ^[[1;2B
Is this what you would expect?

Regards
Alan

---

### Post by Holger_Gehrke on 2019-03-16
Hello, Harfin!

Regarding your post #10, the three code-blocks in my post (#9) all contain terminal commands you were supposed to enter as is. The text before each block explains what they do. The first block adds a new repository to apt, the second block downloads the key for that repository and gives it to apt so apt can verify the signatures of the package and the last block updates the package lists and installs the needed library.

Regarding your post #12, no, this is not at all what I expected. I didn't even know libdvd-pkg exists. It should work, but it takes the long way around to achieve the same thing - it installs a complete set of development tools, downloads the source code for libdvdcss2 and compiles and installs that. As you can tell from the output, it installs about 126 MB of tools to get a library that's less then 200 kb. If one has all these tools installed anyway, than its a nice idea. If one just wants to watch a movie it's overkill. 'libdvd-pkg' has an entry in the field 'Provides:' set to 'libdvdcss2'; so if 'libdvdcss2' can't be found as a package in the repositories, apt will offer this package. If you follow the instructions, there will be a package 'libdvdcss2' in the repositories known to apt and apt will install that and not offer to install 'libdvd-pkg'

Holger

---

### Post by harfin on 2019-03-16
Hi Holger

Well, the new package has fixed the problem! DVD videos now up and running!  Thankyou so much for your advice and input!

Alan aka Harfin

---

### Post by ajgreeny on 2019-03-16
It was all made very clear in the link that I gave in post #8
> Installing libdvdcss

Legal warning: Check with your local laws to make sure usage of libdvdcss2 would be legal in your area.

Ubuntu 15.10 and newer

From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss.

    Install the libdvd-pkg package (no need to add third party repositories) via Synaptic or command line: 

sudo apt install libdvd-pkg && sudo dpkg-reconfigure libdvd-pkg

    Follow libdvd-pkg's instructions to let it download, compile, and install libdvdcss.  so I am surprised you did not just follow that info.

---

### Post by harfin on 2019-03-16
Thanks for your input ajgreeny.

Alan

---

### Post by harfin on 2019-03-17
Further to the resolution of being able to play DVD video discs, this morning I attempted to see if there were any updates for the laptop (running "sudo apt update in the terminal) and the following details were shown after it started to compile the update list:
> W: GPG error: [https://download.videolan.org/pub/debian/stable](https://download.videolan.org/pub/debian/stable)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6BCA5E4DB84288D9
E: The repository 'https://download.videolan.org/pub/debian/stable  Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

I knew that there are updates from the software updater tool, so I used that to the ensure that updates were installed.

 Seems that the issue revolves around videolan 

Any advice / suggestions / recommendations ?

---

### Post by oldos2er on 2019-03-17
Install the missing key. ```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 6BCA5E4DB84288D9
```

---

### Post by harfin on 2019-03-17
Thanks. Just entered "[COLOR=#000000][FONT=&quot]sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 6BCA5E4DB84288D9".
Now rebooting, as when I rebooted 30 mins ago, I could only get back on in safe mode.
Thanks
Alan

[/FONT][/COLOR]

---

### Post by MukeeWrench on 2019-09-16
Tried as you said but my Ubuntu 18.04 won't accept wget -0 - as valid. There's an alphabet of letters but letter o or zero. Thanks for the attempt.

---

### Post by mc4man on 2019-09-17
> **MukeeWrench said:**
> Tried as you said but my Ubuntu 18.04 won't accept wget -0 - as valid. There's an alphabet of letters but letter o or zero. Thanks for the attempt.

Those instructions you attempted are a poor choice, the better method is linked in  post 8

---

