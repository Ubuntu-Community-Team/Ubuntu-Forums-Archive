---
title: "HOWTO: Download Ubuntu ISOs from multiple mirrors at once"
date: 2006-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by antini on 2006-08-29
1. Install [aria2]("http://aria2.sourceforge.net") download utility. It's command line and supports bittorrent as well as [metalink]("http://www.metalinker.org"). Metalinks list mirrors, p2p, & checksums for a fast and easy download.     

2. Visit [Metalink @ Packages Resources]("http://metalink.packages.ro/"), [Ubuntu section]("http://download.packages.ro/metalink/ubuntu/").

3. From a terminal: aria2c *URL*

---

### Post by antini on 2006-09-05
Here's a good [metalink]("http://www.metalinker.org") overview:

> Metalink makes complex download pages obsolete by replacing long lists of download mirrors and BitTorrent trackers with a single .metalink file. As you might have already guessed, a .metalink file is a file that tells a download manager all the different ways it can download a file. The file itself takes the form of an open XML standard that can list an unlimited number of HTTP and FTP sources as well as BitTorrent trackers and ed2k and magnet links.
([http://www.downloadsquad.com/2006/08/28/metalinks-integrated-bittorrent-http-and-ftp-downloads/](http://www.downloadsquad.com/2006/08/28/metalinks-integrated-bittorrent-http-and-ftp-downloads/))

It usually results in really fast and automatically verified downloads.

---

### Post by TwoWordz on 2006-09-05
If you want to download ubuntu iso from multiple mirrors at once, you can use bittorrent. 

:D

keep it simple.

TW

---

### Post by antini on 2006-09-07
BitTorrent uses multiple PEERS at once. This is great and uses users bandwidth. But, not all places allow BT downloads. Sometimes they're blocked.

Metalink allows you to use whatever is available, whether it is BitTorrent, ed2k, magnet links, or mirror (http/ftp) servers.

---

### Post by antini on 2006-09-21
Anyone interested in packaging [aria2]("http://aria2.sourceforge.net") for Ubuntu? It's in Debian [unstable]("http://packages.debian.org/unstable/net/aria2") and [testing]("http://packages.debian.org/testing/net/aria2").

---

### Post by phizz on 2006-09-28
this is wicked. Everyone says 'use bittorrent for downloading isos.' I would if my isp didnt packetshape torrent traffic to death. Thanks!

---

### Post by Josh1 on 2006-09-28
I used reget for 5.10 (got 10 ubuntu 6.06 cd's in the mail for me and friends who wanted to use ubuntu).

---

### Post by antini on 2006-09-28
> **phizz said:**
> this is wicked. Everyone says 'use bittorrent for downloading isos.' I would if my isp didnt packetshape torrent traffic to death. Thanks!

Thanks phizz! It's super easy and usually super fast. Hopefully somebody will take the debian package & add it to the Ubuntu repository so people can install it easier. Lots of distributions are using this as the preferred way to transfer their ISOs...maybe Ubuntu will catch on.

---

### Post by antini on 2006-10-02
aria2 Ubuntu packages are at [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=aria2](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=aria2)

Then try some [.metalinks]("http://www.metalinker.org/samples.html") out...

---

### Post by jdong on 2006-10-02
Please don't do something like this on release day... it might make your download speed look wonderful but puts unnecessary stress on the servers :). Even if you spread your load on multiple mirrors, you're likely preventing someone else from getting their hands on a copy of Ubuntu.

---

### Post by Josh1 on 2006-10-02
> **jdong said:**
> Please don't do something like this on release day... it might make your download speed look wonderful but puts unnecessary stress on the servers :). Even if you spread your load on multiple mirrors, you're likely preventing someone else from getting their hands on a copy of Ubuntu.

If 50,000 people want to download ubuntu right now, and each use 10 connections, that will easily clog the server down.
But since there is loads of mirrors for ubuntu (there is even one that runs on WAIX, lol) you could put one connection per mirror..

---

### Post by antini on 2006-10-31
As always, [Metalinks]("http://www.metalinker.org") are available for new versions of Ubuntu at [http://download.packages.ro/metalink/ubuntu/](http://download.packages.ro/metalink/ubuntu/) as soon as they hit the mirrors.

The newly released Metalink tools (command line, [http://prog.infosnel.nl/metalinks/](http://prog.infosnel.nl/metalinks/)) can be used to generate Metalinks. It scans files and adds their checksums and mirrors to a Metalink.

---

### Post by antini on 2006-11-21
Linux.com has a good article explaining Metalinks at titled [Downloading bliss with Metalink]("http://www.linux.com/article.pl?sid=06/11/01/1641247"):

> Getting popular software off the Internet can sometimes be a struggle, even with all the mirrors and BitTorrent Samaritans out there. When the Fedora project released Fedora Core 6 last month, for instance, even several dozen mirrors weren't enough to serve everyone, and torrent speeds weren't good enough because of a scarcity of seeders. But thanks to Metalink I was able to sleep while my FC6 ISOs were downloading.

Metalink is an open standard that claims to make downloading easier, faster, and more reliable by helping users extract the last drop of juice out of their connection. But Metalink isn't your run-of-the-mill download accelerator. It is in fact a framework for use by other download clients, and bundles traditional HTTP and FTP methods of downloading files along with BitTorrent.

The Metalink standard replaces static URLs with a .metalink file, which is a simple XML file. The file in turn contains locations of all the mirrors of the application you want to download. In addition to HTTP and FTP mirrors and rsync, Metalink supports several P2P methods as well, including BitTorrent, ed2k, and magnet links. For example, the OpenOffice.org metalink contains links to more than 50 HTTP and FTP servers and a torrent.

If I were using a regular hyperlink to download OpenOffice.org and the server went down midway through the transfer, I would be left with an incomplete transfer that could either be resumed or not depending on the download client. But with Metalink, if one server goes down, the client software simply jumps to another mirror and resumes downloading from that point. In effect, this increases reliability, as all listed servers would need to be down for the file to be unavailable.

Files downloaded with metalinks are automatically verified. Metalink supports both MD5SUM and SHA1SUM checksums as well as PGP signatures, which are embedded in the .metalink file itself. Checksums are unique for every file, like a fingerprint. If there's an error in transfer, or if someone has maliciously replaced a good file with a bad one, the checksums won't match. If that happened with another file transfer method, you'd have to download the file again from another mirror. With Metalink, if the application you are downloading has a torrent, Metalink can use a torrent's partial file or chunk checksums to verify mirror downloads as well. If only a small chunk of a download has errors, Metalink just re-downloads that part instead of the whole file.

---

### Post by Ziox on 2006-12-03
What is the advantage of metalink over bittorrent? and what is a good program to use for ubuntu?

---

### Post by antini on 2006-12-03
> **Ziox said:**
> What is the advantage of metalink over bittorrent? and what is a good program to use for ubuntu?

Metalink can use bittorrent, to supplement mirror downloads. In some places, p2p can't be used - like schools, businesses, and some ISPs. In places like that, regular downloads aren't blocked, so Metalink clients will skip p2p and use mirrors. There are also other features like OS, language, and location download filtering. Depending on the mirrors, in normal use Metalink downloads will be much faster.

[aria2]("http://aria2.sourceforge.net") is in the feisty repos. 'sudo apt-get install aria2' should work.

You might be able to download the source and compile it for edgy.  
Something like the following should work:

```
sudo -s
echo 'deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse' >> /etc/apt/sources.list
apt-get update
cd /tmp
apt-get source aria2
apt-get build-dep aria2
cd aria2-*
debuild -uc -us
cd ..
dpkg -i aria2*.deb
rm -rf aria2*
exit
```

---

### Post by elektronaut on 2006-12-07
In case you get 'command not found' for 'debuild', it's in the devscripts package:```
sudo aptitude install devscripts

```

---

### Post by antini on 2006-12-10
Thanks for the help.

Metalinks contributed to the distribution of [openSUSE 10.2]("http://en.opensuse.org/Released_Version#Metalink")...

---

### Post by smartbei on 2007-01-05
I am hacing a problem using aria2/metalinks. the download proceeds well, and for some reason this is the only way i can get speeds that are practical for downloading a dvd iso. On torrents I get really low speeds (max 5KB/2, avg 1.5KB/s)...

when the download finishes it checks the file and always says 'checksum failed'. Still, i have done this twice now, and each time independantly verified that the md5sum doesn't match up. Still, it takes a long time to download and I wonder how much the fact that it doesn't match actually has to do with anything...

I am downloading a DVD iso for SUSE (it is supposed to work better on my hardware) - what do you suggest?

---

### Post by antini on 2007-01-05
> **smartbei said:**
> I am hacing a problem using aria2/metalinks. the download proceeds well, and for some reason this is the only way i can get speeds that are practical for downloading a dvd iso. On torrents I get really low speeds (max 5KB/2, avg 1.5KB/s)...

when the download finishes it checks the file and always says 'checksum failed'. Still, i have done this twice now, and each time independantly verified that the md5sum doesn't match up. Still, it takes a long time to download and I wonder how much the fact that it doesn't match actually has to do with anything...

I am downloading a DVD iso for SUSE (it is supposed to work better on my hardware) - what do you 
suggest?

My guess is that you are getting errors in the transfer due to errors in your connection or one of the mirrors is serving up bad data (more likely the first).

The current version of aria2 doesn't support the advanced error correction that metalink allows (just the speed).

Since you have already downloaded the ISO, there are probably just a few small errors in the whole file, which causes the checksum to fail. You can use a torrent and another torrent client (**don't use aria2**) and it will scan the file and fix errors. Or you can use rsync, see the bottom of [http://en.opensuse.org/Metalinks](http://en.opensuse.org/Metalinks)

> This presupposes that you were downloading openSUSE-10.2-GM-DVD-i386.iso via metalink, and at some point (probably the end) you got an error. Use rsync like this to download any missing chunks:

cd /directory/ofthe/iso
rsync -avvP rsync://mirrors.kernel.org/opensuse/distribution/10.2/iso/dvd/openSUSE-10.2-GM-DVD-i386.iso .

Note: we can just use a dot (".") at the end here since we simply want to continue the ISO with the same filename, in the current directory. 

I know these extra steps are annoying, sorry. Hopefully the next version of aria2 supports the features that will automate this.

---

### Post by smartbei on 2007-01-06
Thanks for the quick reply. I tried using the said rsync package but I keep getting the following error for the mirror they used:
```
$ rsync -avvP rsync://mirrors.kernel.org/opensuse/distribution/10.2/iso/dvd/openSUSE-10.2-GM-DVD-i386.iso .
opening tcp connection to mirrors.kernel.org port 873
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: error in rsync protocol data stream (code 12) at io.c(463) [receiver=2.6.8]

```
And a different one for another I tried:
```
$ rsync -avvP rsync://sunsite.informatik.rwth-aachen.de/pub/linux/opensuse/distribution/10.2/iso/dvd/openSUSE-10.2-GM-DVD-i386.iso .
opening tcp connection to sunsite.informatik.rwth-aachen.de port 873
rsync: failed to connect to sunsite.informatik.rwth-aachen.de: Connection refused (111)
rsync error: error in socket IO (code 10) at clientserver.c(107) [receiver=2.6.8]

```

I checked the router and I think I have it set up so port 873 is open - though I am not sure as to how to test this.

I also tried bittorent and opened the torrent in Azureus, which, after checking, said that the file is 77.9% complete, explaining the wrong md5sum. However, because my download speed is so low, that would still take forever to make up with azureus. Any ideas what the error is?

EDIT: I made my computer a temporary DeMilitarized Zone for testing and I see that rsync works now. Apparently I was still blocking a neccessary port.

---

### Post by antini on 2007-01-06
> **smartbei said:**
> EDIT: I made my computer a temporary DeMilitarized Zone for testing and I see that rsync works now. Apparently I was still blocking a neccessary port.

EXCELLENT, glad you got it working. rsync probably won't be as fast as the metalink download, but it's a good way to finish the download and have it verified, if the torrent was really slow.

Once aria2 supports some of the advanced error correction features of metalink, this shouldn't be a problem. or aria2 could support rsync so this step could be automatic, but that might be harder to add.

---

### Post by antini on 2007-02-05
There are now updated .metalinks for ubuntu, kubuntu, and edubuntu.

[http://download.packages.ro/metalink/ubuntu/](http://download.packages.ro/metalink/ubuntu/)
[http://download.packages.ro/metalink/kubuntu/](http://download.packages.ro/metalink/kubuntu/)
[http://download.packages.ro/metalink/edubuntu/](http://download.packages.ro/metalink/edubuntu/)

---

### Post by antini on 2007-07-23
aria2 now supports repairing corrupted downloads with metalinks that contain chunk checksums - which [http://download.packages.ro/metalink/ubuntu/](http://download.packages.ro/metalink/ubuntu/) and elsewhere include.

metalink support (ftp/http, file selection, whole file verification) has been added to DownThemAll! 1.0 Beta, a Firefox Add-on at [http://www.downthemall.net/main/install-it/downthemall-10-beta/](http://www.downthemall.net/main/install-it/downthemall-10-beta/)

Here's what metalinks listing multiple files look like in DTA...
[CENTER][IMG]http://code.downthemall.net/maierman/metaselect4.png[/IMG][/CENTER]

& KGet for KDE 4.0 has also added metalink support to SVN at
[http://websvn.kde.org/trunk/KDE/kdenetwork/kget/](http://websvn.kde.org/trunk/KDE/kdenetwork/kget/)

---

### Post by antini on 2007-11-13
metalinks for all the recent Ubuntu releases can be found at [http://www.metalinker.org/samples/ubuntu/](http://www.metalinker.org/samples/ubuntu/)

---

### Post by antini on 2008-01-15
KGet 2.0, part of KDE 4.0, now supports **[metalinks]("http://www.metalinker.org")**.

---

### Post by teledyn on 2008-01-25
the raphink site appears to be gone, and the current apt-get install aria2 fetches and installs version 0.11.0, which is quite old, and it doesn't work in Gutsy Ubuntu 7.10 :(

is there some trick to making this happen?  I also tried downloading the source code, installing the dev libs for ares and it STILL just sits there until it times out even with a simple http:// url!  A search on the forums here didn't find any reports, so is it possible there's just something wrong with my overall ubuntu config?  It's a pretty straight-out-of-the-box install of 7.06 that was upgraded to 7.10, nothing fancy.  is Aria2 trying to do something funky with ports and maybe hits my ISP's firewall?  I don't see any need for that for a simple HTTP transfer, but I tried

[COLOR="DeepSkyBlue"]$ aria2c [http://ubuntu.media.mit.edu/ubuntu-releases/gutsy/ubuntu-7.10-desktop-i386.iso](http://ubuntu.media.mit.edu/ubuntu-releases/gutsy/ubuntu-7.10-desktop-i386.iso) [http://ftp.belnet.be/mirror/ubuntu.com/releases/gutsy/ubuntu-7.10-desktop-i386.iso](http://ftp.belnet.be/mirror/ubuntu.com/releases/gutsy/ubuntu-7.10-desktop-i386.iso)  [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/gutsy/ubuntu-7.10-desktop-i386.iso](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/gutsy/ubuntu-7.10-desktop-i386.iso)

[/COLOR]and all I get are timeouts, whether it's one, two or three urls in that list :(

---

### Post by teledyn on 2008-01-25
btw, it is illogical to assume that downloading from three servers would deny other people from downloading from those servers: With 3 URLs, you are tying up each server for only 1/3 of the time, and in practical results, most often transfers run into snags and the bitrate will vary, whereas the multiple-server download will interleave the gaps so you can disconnect from the servers even faster.  Since HTTP is stateless, unlike FTP, you do not consume a connection to any one server for the full length of time, only for the period of the current fetch, and if the software is smart it will do range-requests anyway; if you use multi-URLs with aria2 (if it works) each of your connections is relatively short lived and thus isn't it *friendlier* to the server and to other users to fetch even multiple connections to the same server?

---

### Post by antini on 2008-01-25
> **teledyn said:**
> the raphink site appears to be gone, and the current apt-get install aria2 fetches and installs version 0.11.0, which is quite old, and it doesn't work in Gutsy Ubuntu 7.10 :(

is there some trick to making this happen?  I also tried downloading the source code, installing the dev libs for ares and it STILL just sits there until it times out even with a simple http:// url!  A search on the forums here didn't find any reports, so is it possible there's just something wrong with my overall ubuntu config?  It's a pretty straight-out-of-the-box install of 7.06 that was upgraded to 7.10, nothing fancy.  is Aria2 trying to do something funky with ports and maybe hits my ISP's firewall?  I don't see any need for that for a simple HTTP transfer, but I tried

[COLOR="DeepSkyBlue"]$ aria2c [http://ubuntu.media.mit.edu/ubuntu-releases/gutsy/ubuntu-7.10-desktop-i386.iso](http://ubuntu.media.mit.edu/ubuntu-releases/gutsy/ubuntu-7.10-desktop-i386.iso) [http://ftp.belnet.be/mirror/ubuntu.com/releases/gutsy/ubuntu-7.10-desktop-i386.iso](http://ftp.belnet.be/mirror/ubuntu.com/releases/gutsy/ubuntu-7.10-desktop-i386.iso)  [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/gutsy/ubuntu-7.10-desktop-i386.iso](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/gutsy/ubuntu-7.10-desktop-i386.iso)

[/COLOR]and all I get are timeouts, whether it's one, two or three urls in that list :(

I suppose you could test the same URL w/ curl or wget. if they have problems, then it's your config. if they don't, its aria2.

aria2 won't use weird ports on just http downloads.

you also might want to try the "-l logfile" option to save a log, that might shed some light on your problem. you could post it here or report the bug on SF for aria2. what about your system? is it x86_64?

let us know what you find.

---

### Post by antini on 2008-01-25
> **teledyn said:**
> btw, it is illogical to assume that downloading from three servers would deny other people from downloading from those servers: With 3 URLs, you are tying up each server for only 1/3 of the time, and in practical results, most often transfers run into snags and the bitrate will vary, whereas the multiple-server download will interleave the gaps so you can disconnect from the servers even faster.  Since HTTP is stateless, unlike FTP, you do not consume a connection to any one server for the full length of time, only for the period of the current fetch, and if the software is smart it will do range-requests anyway; if you use multi-URLs with aria2 (if it works) each of your connections is relatively short lived and thus isn't it *friendlier* to the server and to other users to fetch even multiple connections to the same server?

I've seen one server admin complain, but most don't seem to mind.

using metalinks, you can make downloads more efficient by using local mirrors & giving servers priority. a dynamic mirror "observer" like Bouncer or mirror manager could create up to date metalinks depending on server load & do some really cool stuff.

---

### Post by antini on 2008-02-29
[DownThemAll]("http://www.downthemall.net/main/install-it/downthemall-10/") 1.0 final is out, with very nice [metalink]("http://www.metalinker.org/") support.

---

### Post by antini on 2008-04-25
official metalinks are provided for the new releases:

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)
[http://releases.ubuntu.com/kubuntu/8.04/](http://releases.ubuntu.com/kubuntu/8.04/) 

[https://help.ubuntu.com/community/Metalink](https://help.ubuntu.com/community/Metalink) has some info on metalink downloads.

---

