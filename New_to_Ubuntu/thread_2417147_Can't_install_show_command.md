---
title: "Can't install show command"
date: 2019-04-21
forum: New to Ubuntu
---

### Post by uknownprior on 2019-04-21
I'm a complete newbie to Linux and  I'm having problems installing the show command; I've installed Ubuntu on 64 bit Windows machine.  When I type show, I get the following: 

```
sarah@LAPTOP-SHTK4QRP:/mnt/c/Users/sarah/Downloads$ show
```


Command 'show' not found, but can be installed with:


```
sudo apt install mailutils-mh
sudo apt install mmh
sudo apt install nmh
```

I've tried installing each of the above commands; both mailutils-mh and mmh appear to be correctly installed.  The dpkg --status info for each of the three packages is below. Any help would be very much appreciated. Thanks so much! 

```
sarah@LAPTOP-SHTK4QRP:/mnt/c/Users/sarah/Downloads$ dpkg --status mmh
Package: mmh
Status: install ok installed
Priority: optional
Section: mail
Installed-Size: 3582
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.3-3
Replaces: mh
Provides: mail-reader, mh
Depends: file, libc6 (>= 2.14), libtinfo5 (>= 6)
Conflicts: mh
Conffiles:
 /etc/mmh/components caed07636d5cd7620566e2a90d6f7464
 /etc/mmh/digestcomps 1ecabc206f446b69e35581d4062c2cba
 /etc/mmh/distcomps c51e21c15d56b41b114b450b5007a755
 /etc/mmh/forwcomps caed07636d5cd7620566e2a90d6f7464
 /etc/mmh/mhl.body deb6a367bdd98a429aab44ed89ee2f03
 /etc/mmh/mhl.format 548bf665f6d3243586d09b1e7974191a
 /etc/mmh/mhl.forward 2a0c2cd5e4eb9c8b4cbb823fb107daf0
 /etc/mmh/mhl.headers 2d6741d9567396c2aeb6872384325b71
 /etc/mmh/mhl.reply 0632d5576b475d236555fa9c16870877
 /etc/mmh/mhn.defaults bc1fcfcac82914494ef80f289cdf7a4f
 /etc/mmh/rcvdistcomps 02f34a5037aa4fb46e7ade09663b2961
 /etc/mmh/rcvdistcomps.outbox 790db1e0d443064f67a342d4c15addd2
 /etc/mmh/replcomps 61da18b2fdb03393ae81e786119a6456
 /etc/mmh/replgroupcomps 34e374ecc22261d8fc23d2efcf2dacd7
 /etc/mmh/scan.MMDDYY 36c3ba2da7ae45a943dd41b7d56afef0
 /etc/mmh/scan.YYYYMMDD 394aca6d310a97e926da0e556a70570a
 /etc/mmh/scan.default 8f0aa1a21c6a5b45495918341b187369
 /etc/mmh/scan.mailx acc810838e4361e6d91bb9b1b9084802
 /etc/mmh/scan.meillo e4a466090f63c9ac58e89938eb4d6dd2
 /etc/mmh/scan.nmh 042c918916f299068809fd43e05bf826
 /etc/mmh/scan.nomime 6272f86fd829b8bb04c9b663b8fd5a93
 /etc/mmh/scan.size 76e66062fa217b031cba69819af6671f
 /etc/mmh/scan.time fbf263aec304af649f35b50ab0ab4c05
 /etc/mmh/scan.timely 829a299f6bbcd5094fce557cb5fa2b1a
 /etc/mmh/scan.unseen 4812174e73ad3184d80954ea3a267bbd
Description: set of electronic mail handling programs
 This is the mmh mail user agent (reader/sender), a command-line based mail
 reader that is powerful and extensible.  mmh is an excellent choice for
 people who receive and process a lot of mail.
 .
 Unlike most mail user agents, mmh is not a single program, rather it is a
 set of programs that are run from the shell.  This allows the user to
 utilize the full power of the Unix shell in coordination with mmh.
 .
 Mmh is a modified version of the electronic mail handling system nmh.
 Nmh (new MH) itself was originally based on the package MH-6.8.3, and
 was intended to be a (mostly) compatible drop-in replacement for MH.
 In contrast, mmh is not intended to be a drop-in replacement for nmh,
 rather mmh breaks compatibility to nmh in order to modernize and
 simplify it.
Original-Maintainer: Dmitry Bogatov <KAction@gnu.org>
Homepage: [http://marmaro.de/prog/mmh/](http://marmaro.de/prog/mmh/)
sarah@LAPTOP-SHTK4QRP:/mnt/c/Users/sarah/Downloads$ show -mailutils dmh
```


Command 'show' not found, but can be installed with:


```
sudo apt install mailutils-mh
sudo apt install mmh
sudo apt install nmh

```

```
sarah@LAPTOP-SHTK4QRP:/mnt/c/Users/sarah/Downloads$ show
```


Command 'show' not found, but can be installed with:


```
sudo apt install mailutils-mh
sudo apt install mmh
sudo apt install nmh
```


```
sarah@LAPTOP-SHTK4QRP:/mnt/c/Users/sarah/Downloads$ dpkg --status mmh
Package: mmh
Status: install ok installed
Priority: optional
Section: mail
Installed-Size: 3582
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.3-3
Replaces: mh
Provides: mail-reader, mh
Depends: file, libc6 (>= 2.14), libtinfo5 (>= 6)
Conflicts: mh
Conffiles:
 /etc/mmh/components caed07636d5cd7620566e2a90d6f7464
 /etc/mmh/digestcomps 1ecabc206f446b69e35581d4062c2cba
 /etc/mmh/distcomps c51e21c15d56b41b114b450b5007a755
 /etc/mmh/forwcomps caed07636d5cd7620566e2a90d6f7464
 /etc/mmh/mhl.body deb6a367bdd98a429aab44ed89ee2f03
 /etc/mmh/mhl.format 548bf665f6d3243586d09b1e7974191a
 /etc/mmh/mhl.forward 2a0c2cd5e4eb9c8b4cbb823fb107daf0
 /etc/mmh/mhl.headers 2d6741d9567396c2aeb6872384325b71
 /etc/mmh/mhl.reply 0632d5576b475d236555fa9c16870877
 /etc/mmh/mhn.defaults bc1fcfcac82914494ef80f289cdf7a4f
 /etc/mmh/rcvdistcomps 02f34a5037aa4fb46e7ade09663b2961
 /etc/mmh/rcvdistcomps.outbox 790db1e0d443064f67a342d4c15addd2
 /etc/mmh/replcomps 61da18b2fdb03393ae81e786119a6456
 /etc/mmh/replgroupcomps 34e374ecc22261d8fc23d2efcf2dacd7
 /etc/mmh/scan.MMDDYY 36c3ba2da7ae45a943dd41b7d56afef0
 /etc/mmh/scan.YYYYMMDD 394aca6d310a97e926da0e556a70570a
 /etc/mmh/scan.default 8f0aa1a21c6a5b45495918341b187369
 /etc/mmh/scan.mailx acc810838e4361e6d91bb9b1b9084802
 /etc/mmh/scan.meillo e4a466090f63c9ac58e89938eb4d6dd2
 /etc/mmh/scan.nmh 042c918916f299068809fd43e05bf826
 /etc/mmh/scan.nomime 6272f86fd829b8bb04c9b663b8fd5a93
 /etc/mmh/scan.size 76e66062fa217b031cba69819af6671f
 /etc/mmh/scan.time fbf263aec304af649f35b50ab0ab4c05
 /etc/mmh/scan.timely 829a299f6bbcd5094fce557cb5fa2b1a
 /etc/mmh/scan.unseen 4812174e73ad3184d80954ea3a267bbd
Description: set of electronic mail handling programs
 This is the mmh mail user agent (reader/sender), a command-line based mail
 reader that is powerful and extensible.  mmh is an excellent choice for
 people who receive and process a lot of mail.
 .
 Unlike most mail user agents, mmh is not a single program, rather it is a
 set of programs that are run from the shell.  This allows the user to
 utilize the full power of the Unix shell in coordination with mmh.
 .
 Mmh is a modified version of the electronic mail handling system nmh.
 Nmh (new MH) itself was originally based on the package MH-6.8.3, and
 was intended to be a (mostly) compatible drop-in replacement for MH.
 In contrast, mmh is not intended to be a drop-in replacement for nmh,
 rather mmh breaks compatibility to nmh in order to modernize and
 simplify it.
Original-Maintainer: Dmitry Bogatov <KAction@gnu.org>
Homepage: [http://marmaro.de/prog/mmh/](http://marmaro.de/prog/mmh/)

Package: nmh
Status: deinstall ok config-files
Priority: optional
Section: mail
Installed-Size: 8353
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.7.1~RC3-1build1
Config-Version: 1.7.1~RC3-1build1
Replaces: mh
Provides: mail-reader, mh
Depends: libc6 (>= 2.15), libcurl4 (>= 7.16.2), libdb5.3, liblockfile1 (>= 1.0), libsasl2-2, libssl1.1 (>= 1.1.0), libtinfo5 (>= 6), netbase (>= 3.16-1), mime-support
Recommends: default-mta | mail-transport-agent
Suggests: exmh, mh-e, mh-book, par, libmime-tools-perl, libmailtools-perl
Conflicts: mh
Conffiles:
 /etc/nmh/MailAliases ae4986a0ade4529044af1a61f9e1a65b
 /etc/nmh/bash_completion_nmh 434ad70e82f5de723c50844ba805be1d
 /etc/nmh/components 66698f0336087e65a4951965673792a6
 /etc/nmh/digestcomps 0dd0031144c396ff7badb4df74ed1263
 /etc/nmh/distcomps 574acfe3657e159f2250f134f7eac495
 /etc/nmh/forwcomps b8f22e8603c843848a37169a02baed40
 /etc/nmh/mhical.12hour 941c6dae59d42aa541b8d3d6bf4acf78
 /etc/nmh/mhical.24hour fd398fc4316340ea45418e7044de4889
 /etc/nmh/mhl.body deb6a367bdd98a429aab44ed89ee2f03
 /etc/nmh/mhl.digest b0f5c8218d42516deb86fe99b5187324
 /etc/nmh/mhl.format 4286bead1c5f09aa070733830bb6fa59
 /etc/nmh/mhl.forward 1388b48bae0f85195a3d5083e851d56d
 /etc/nmh/mhl.headers 9f1a3578114e903059ce34e0d853c980
 /etc/nmh/mhl.reply 9a3001e21b814c62b81f68fd183512a2
 /etc/nmh/mhl.replywithoutbody fecf0671ed42678457a8bad1a6d2db1b
 /etc/nmh/mhn.defaults 4f4a240d24d651c5655288c4e6bdb18a
 /etc/nmh/mhshow.marker be8b83b743e0e991b539fb3d4775a3ca
 /etc/nmh/mts.conf 8ed8c2a7b730e11195f533b75c560a1f
 /etc/nmh/rcvdistcomps 8883a2fc5acc36bc5640dac8c2b923c3
 /etc/nmh/rcvdistcomps.outbox bd583c31c73b1ad473a563de4896731b
 /etc/nmh/replcomps a4aeb8d34fc89d141afb23983cdb874a
 /etc/nmh/replgroupcomps 183f61567bb84ad31781933f2b24a4ac
 /etc/nmh/scan.MMDDYY 8594df7f3c80441ba1151801f5477a85
 /etc/nmh/scan.YYYYMMDD eac8e08e1aa1bcd7a8d1f251d8cd7dda
 /etc/nmh/scan.curses 1a957d6717c72627602b914d4e7bbcde
 /etc/nmh/scan.default 85ef315655b128b952e1352ced2e177b
 /etc/nmh/scan.highlighted 8aa1ba3edf2492fe7b2242d8f391102e
 /etc/nmh/scan.mailx 59dcfde86eebaa35aff5beb092032da5
 /etc/nmh/scan.nomime 462a46aba6cabfa4d471f8638c34e97f
 /etc/nmh/scan.size 50dd5d8ee3c180f9457991ae07eb7109
 /etc/nmh/scan.time b31fbdef706eebe355027c9550e1ea76
 /etc/nmh/scan.timely 37cf6a7dee2b086e54ecbb0e71d6d586
 /etc/nmh/scan.unseen fd75c585fc6bf6cd12655238f66f127e
Description: set of electronic mail handling programs
 This is the nmh mail user agent (reader/sender), a command-line based mail
 reader that is powerful and extensible.  nmh is an excellent choice for
 people who receive and process a lot of mail.
 .
 Unlike most mail user agents, nmh is not a single program, rather it is a
 set of programs that are run from the shell.  This allows the user to
 utilize the full power of the Unix shell in coordination with nmh.  Various
 front-ends are available, such as mh-e (an emacs mode), xmh, and exmh (X11
 clients).
 .
 nmh was originally based on MH version 6.8.3, and is intended to be a
 (mostly) compatible drop-in replacement for MH.
Original-Maintainer: Alexander Zangerl <az@debian.org>

Package: mailutils-mh
Status: install ok installed
Priority: optional
Section: mail
Installed-Size: 5111
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mailutils
Version: 1:3.4-1
Provides: mail-reader
Depends: mailutils-common (= 1:3.4-1), guile-2.0-libs, libc6 (>= 2.14), libmailutils5, libreadline7 (>= 6.0), libtinfo5 (>= 6)
Suggests: mailutils, mh-e
Conffiles:
 /etc/emacs/site-start.d/50mailutils-mh.el 9d5b57603ba036ebf75ceb88cf619501
Description: GNU mailutils-based MH utilities
 GNU Mailutils is a rich and powerful protocol-independent mail framework.
 It contains a series of useful mail libraries, clients, and servers.
 .
 These are the GNU mailutils MH utilities. It is an implementation of MH, a
 collection of small shell programs to read and handle mail in a very flexible
 way.
Original-Maintainer: Jordi Mallach <jordi@debian.org>
```

---

### Post by monkeybrain20122 on 2019-04-21
What is the 'show' command?

---

### Post by uknownprior on 2019-04-21
I'm using it as part of a bioinformatics project (MUMmer); as best I can tell, it should be installed with mmh/nmh/ or mailutils -mh; but it's not working for me. A thread was posted [here]("https://ubuntuforums.org/showthread.php?t=2203646"), but as best I can tell the issue was never resolved.

---

### Post by TheFu on 2019-04-21
> **uknownprior said:**
> I'm using it as part of a bioinformatics project (MUMmer); as best I can tell, it should be installed with mmh/nmh/ or mailutils -mh; but it's not working for me. A thread was posted [here]("https://ubuntuforums.org/showthread.php?t=2203646"), but as best I can tell the issue was never resolved.

I've never heard of 'show' before either, but I've only been on Unix 26 yrs.  More to learn, I suppose.

In that other link, Sandy found the 'show' program is installed outside the normal PATH for any Unix/Linux system. This must be for a specific reason.

Try running it with **/usr/bin/mh/show** - the entire, exact, command in bold.

If you need to learn about directories and PATH, that is something I teach to my day-1 beginning Linux classes.  It is a very basic thing to understand.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a no-hassle, Linux book that will teach the basics that all Unix/Linux users need to know.

---

