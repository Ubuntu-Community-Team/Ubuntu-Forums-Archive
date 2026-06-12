---
title: "How do I see/run installed software? It's missing..."
date: 2015-10-07
forum: New to Ubuntu
---

### Post by Salty-san on 2015-10-07
If it's from the software center then it works and is visible in the right location in Start or through folder browsing in applications. But if I install some stuff from sites because that's only where I could find it then it is just nowhere to be seen on the surface. I am iliterate in terms of terminal, sooo is there something I can do to find them or whatever?

Case in point I tried installing mksub, from a topic here even, and then what? Also, what is PPA? I also tried installing YUMI from website, got a package install window with details and everything, worked fine, and nowhere in sight..Checked some pathing button there, said lintian was not available. Wtf is lintian? I installed it anyway, then it gave some details or something in said window but I still couldn't see it.

Now I'm not sure if it's a limitation of Lubuntu/Live disk or if I am missing key features (like whatever lintian was) or if it's just normal, but I would really like to be able to install software from more than just the center ;/...I'm on live USB Lubuntu version 15.04.

---

### Post by yancek on 2015-10-07
You can generally find applications by simply typing the name in the Search bar of the Dash, the Ubuntu logo in the upper left of the Desktop.   Doing that for 'mkusb' will show the icon for it.  Click on it and it opens.  If you haven't use it before, I'd suggest reading a tutorial on it, see the link below.  You can also open it from the terminal.  If you simply type mkusb in a terminal you will get the output below which tells you what to type:

```
sudo -H /usr/sbin/mkusb 
``` 

Doing an online search for "what is ppa ubuntu" will produce the following explanation.

> A **Personal Package Archive** (**PPA**) is a  special software repository for uploading source packages to be built  and published as an APT repository by Launchpad. While the term is used  exclusively within **Ubuntu**, Launchpad host Canonical envisions adoption beyond the **Ubuntu** community.

mkusb tutorial:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

If you look at the file name for the yumi download, you will see that it has an ".exe" extension which means it is windows only software as is pendrivelinux/universal usb installer and won't run on Linux.  The download button on there site shows that clearly.

**[COLOR=#800000]YUMI-2.0.1.8.exe for windows[/COLOR]**

If you are looking for an application, probably the easiest way to find it is from the Search box in the Dash.

---

### Post by oldos2er on 2015-10-07
PPA = Personal Package Archive; it's a [repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") run by a private person or persons.

```
apt-cache show lintian
``` says lintian ```

....dissects Debian packages and reports bugs and policy
 violations. It contains automated checks for many aspects of Debian
 policy as well as some checks for common errors.
``` Don't know if that helps you or not.

> Case in point I tried installing mksub, from a topic here even, and then what? Is [this]("http://www.inside-r.org/packages/cran/seas/docs/mksub") what you're referring to?

> it gave some details or something in said window but I still couldn't see it. It would really help if you could copy/paste error messages, or provide a screenshot of them.

---

### Post by Salty-san on 2015-10-08
> **yancek said:**
> You can generally find applications by simply typing the name in the Search bar of the Dash, the Ubuntu logo in the upper left of the Desktop.   Doing that for 'mkusb' will show the icon for it.  Click on it and it opens.  If you haven't use it before, I'd suggest reading a tutorial on it, see the link below.  You can also open it from the terminal.  If you simply type mkusb in a terminal you will get the output below which tells you what to type:

If you are looking for an application, probably the easiest way to find it is from the Search box in the Dash.

Lubuntu doesn't have bars on the top/side of the desktop, it's at the bottom and looks+has a Start button like in Windows. But it's very rudimentally done. There is no Search. There is only predetermined categories like Internet, Graphics, Sound&Video, and so on where things go if I use the Software center (makes a new one for Games), and the System Tools and Preference separately and Run and Logout. If you search via folders and such you get the same things only (and I used to see them there at least if not elsewhere). But there are some things that are cut off and that I can't seem to access just from system folders, like where the Wallpapers for desktop are stored and other places until there.

I guess it's a limitation of the GUI, being just more so surface based and segregated from terminal, as a trade off from being a very lightweight, low spec distro. 

Funny enough it's more like in the link in oldos2er's sign, about needing both GUI and commands, so my call to ask was right on.

> If you look at the file name for the yumi download, you will see that it  has an ".exe" extension which means it is windows only software as is  pendrivelinux/universal usb installer and won't run on Linux.  The  download button on there site shows that clearly.

**[COLOR=#800000]YUMI-2.0.1.8.exe for windows[/COLOR]**

Lol. Actually if you scroll just a wee bit lower there is the Ubuntu and Debian based download links. I *did* say that it opened the package install window and that it ran fine, and where I also got the lintian install command. ;p...But thanks anyway.

> Case in point I tried installing mksub, from a topic here even, and then what?                             

Is [this]("http://www.inside-r.org/packages/cran/seas/docs/mksub") what you're referring to?

Actually meant topic here on forums, first I got link to this one from a site: [http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073) ...gave me what I needed to install it first.

But thanks for those 2 links guys, will be reading more on it in any case and post updates.

> It would really help if you could copy/paste error messages, or provide a screenshot of them.

Derp, I even had it opened all day and a while after posting this...that Terminal window. Posted this late so I couldn't think well. I guess I expected a reply first. But I can recreate my exact steps, and will post it now...

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

lubuntu@lubuntu:~$ sudo add-apt-repository ppa:mkusb/ppa  # 
 
 More info: https://launchpad.net/~mkusb/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpkw1td7kw/secring.gpg' created
gpg: keyring `/tmp/tmpkw1td7kw/pubring.gpg' created
gpg: requesting key 54B8C8AC from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpkw1td7kw/trustdb.gpg: trustdb created
gpg: key 54B8C8AC: public key "Launchpad PPA for MKUSB" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
lubuntu@lubuntu:~$ sudo apt-get update
Ign cdrom://Lubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422) vivid InRelease
Ign cdrom://Lubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422) vivid/main Translation-en_US
Ign cdrom://Lubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422) vivid/main Translation-en
Ign cdrom://Lubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422) vivid/multiverse Translation-en_US
Ign cdrom://Lubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422) vivid/multiverse Translation-en
Ign cdrom://Lubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422) vivid/restricted Translation-en_US
Ign cdrom://Lubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422) vivid/restricted Translation-en
Ign cdrom://Lubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422) vivid/universe Translation-en_US
Ign cdrom://Lubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422) vivid/universe Translation-en
Ign http://ppa.launchpad.net vivid InRelease                                   
Get:1 http://security.ubuntu.com vivid-security InRelease [64.4 kB]            
Get:2 http://ppa.launchpad.net vivid Release.gpg [836 B]                       
Get:3 http://ppa.launchpad.net vivid Release [15.1 kB]                         
Get:4 http://security.ubuntu.com vivid-security/main amd64 Packages [119 kB]
Get:5 http://archive.ubuntu.com vivid InRelease [218 kB]                       
Get:6 http://ppa.launchpad.net vivid/main amd64 Packages [662 B]               
Get:7 http://ppa.launchpad.net vivid/main Translation-en [809 B]               
Get:8 http://security.ubuntu.com vivid-security/restricted amd64 Packages [10.4 kB]
Get:9 http://security.ubuntu.com vivid-security/universe amd64 Packages [57.1 kB]
Get:10 http://security.ubuntu.com vivid-security/multiverse amd64 Packages [5,195 B]
Get:11 http://security.ubuntu.com vivid-security/main Translation-en [63.4 kB] 
Get:12 http://security.ubuntu.com vivid-security/multiverse Translation-en [2,246 B]
Get:13 http://security.ubuntu.com vivid-security/restricted Translation-en [2,607 B]
Get:14 http://security.ubuntu.com vivid-security/universe Translation-en [35.3 kB]
Get:15 http://archive.ubuntu.com vivid-updates InRelease [64.4 kB]        
Get:16 http://archive.ubuntu.com vivid/main amd64 Packages [1,364 kB]
Get:17 http://archive.ubuntu.com vivid/restricted amd64 Packages [15.4 kB]
Get:18 http://archive.ubuntu.com vivid/universe amd64 Packages [6,485 kB]
Get:19 http://archive.ubuntu.com vivid/multiverse amd64 Packages [134 kB]      
Get:20 http://archive.ubuntu.com vivid/main Translation-en [793 kB]            
Get:21 http://archive.ubuntu.com vivid/multiverse Translation-en [103 kB]      
Get:22 http://archive.ubuntu.com vivid/restricted Translation-en [4,228 B]     
Get:23 http://archive.ubuntu.com vivid/universe Translation-en [4,456 kB]      
Get:24 http://archive.ubuntu.com vivid-updates/main amd64 Packages [209 kB]    
Get:25 http://archive.ubuntu.com vivid-updates/restricted amd64 Packages [13.1 kB]
Get:26 http://archive.ubuntu.com vivid-updates/universe amd64 Packages [111 kB]
Get:27 http://archive.ubuntu.com vivid-updates/multiverse amd64 Packages [5,195 B]
Get:28 http://archive.ubuntu.com vivid-updates/main Translation-en [102 kB]    
Get:29 http://archive.ubuntu.com vivid-updates/multiverse Translation-en [2,246 B]
Get:30 http://archive.ubuntu.com vivid-updates/restricted Translation-en [2,969 B]
Get:31 http://archive.ubuntu.com vivid-updates/universe Translation-en [65.5 kB]
Fetched 14.5 MB in 16s (866 kB/s)                                              
Reading package lists... Done
lubuntu@lubuntu:~$ sudo apt-get install mkusb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  pv wmctrl
Suggested packages:
  doc-base
The following NEW packages will be installed:
  mkusb pv wmctrl
0 upgraded, 3 newly installed, 0 to remove and 183 not upgraded.
Need to get 793 kB of archives.
After this operation, 1,135 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/mkusb/ppa/ubuntu/ vivid/main mkusb all 10.0.6-1ubuntu1 [726 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ vivid/universe pv amd64 1.5.7-2 [44.9 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ vivid/universe wmctrl amd64 1.07-7 [21.8 kB]
Fetched 793 kB in 0s (1,170 kB/s)
Selecting previously unselected package mkusb.
(Reading database ... 108394 files and directories currently installed.)
Preparing to unpack .../mkusb_10.0.6-1ubuntu1_all.deb ...
Unpacking mkusb (10.0.6-1ubuntu1) ...
Selecting previously unselected package pv.
Preparing to unpack .../archives/pv_1.5.7-2_amd64.deb ...
Unpacking pv (1.5.7-2) ...
Selecting previously unselected package wmctrl.
Preparing to unpack .../wmctrl_1.07-7_amd64.deb ...
Unpacking wmctrl (1.07-7) ...
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Setting up mkusb (10.0.6-1ubuntu1) ...
Setting up pv (1.5.7-2) ...
Setting up wmctrl (1.07-7) ...
lubuntu@lubuntu:~$ sudo apt-get install lintian
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  diffstat gettext hardening-includes intltool-debian libapt-pkg-perl
  libarchive-zip-perl libasprintf-dev libauthen-sasl-perl
  libclass-accessor-perl libclone-perl libdigest-hmac-perl libdpkg-perl
  libemail-valid-perl libfile-basedir-perl libfile-fcntllock-perl
  libgettextpo-dev libgettextpo0 libgomp1 libio-pty-perl
  libio-socket-inet6-perl libio-string-perl libipc-run-perl
  liblist-moreutils-perl libmailtools-perl libnet-dns-perl
  libnet-domain-tld-perl libnet-ip-perl libnet-smtp-ssl-perl
  libparse-debianchangelog-perl libperlio-gzip-perl libsocket6-perl
  libsub-name-perl libtext-levenshtein-perl libunistring0 make patchutils
  t1utils
Suggested packages:
  gettext-doc libgssapi-perl debian-keyring gcc c-compiler
  libhtml-template-perl libxml-simple-perl binutils-multiarch dpkg-dev
  libtext-template-perl libyaml-perl make-doc
The following NEW packages will be installed:
  diffstat gettext hardening-includes intltool-debian libapt-pkg-perl
  libarchive-zip-perl libasprintf-dev libauthen-sasl-perl
  libclass-accessor-perl libclone-perl libdigest-hmac-perl libdpkg-perl
  libemail-valid-perl libfile-basedir-perl libfile-fcntllock-perl
  libgettextpo-dev libgettextpo0 libgomp1 libio-pty-perl
  libio-socket-inet6-perl libio-string-perl libipc-run-perl
  liblist-moreutils-perl libmailtools-perl libnet-dns-perl
  libnet-domain-tld-perl libnet-ip-perl libnet-smtp-ssl-perl
  libparse-debianchangelog-perl libperlio-gzip-perl libsocket6-perl
  libsub-name-perl libtext-levenshtein-perl libunistring0 lintian make
  patchutils t1utils
0 upgraded, 38 newly installed, 0 to remove and 183 not upgraded.
Need to get 3,175 kB/3,591 kB of archives.
After this operation, 16.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ vivid/main libunistring0 amd64 0.9.3-5.2ubuntu1 [279 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ vivid/main libgettextpo0 amd64 0.19.2-2ubuntu1 [111 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ vivid/main diffstat amd64 1.59-1 [22.3 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ vivid/main gettext amd64 0.19.2-2ubuntu1 [851 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ vivid/main intltool-debian all 0.35.0+20060710.1 [31.6 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ vivid/main libapt-pkg-perl amd64 0.1.29build2 [76.2 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ vivid/main libarchive-zip-perl all 1.39-1 [87.6 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ vivid/main libasprintf-dev amd64 0.19.2-2ubuntu1 [4,588 B]
Get:9 http://archive.ubuntu.com/ubuntu/ vivid/main libsub-name-perl amd64 0.12-1 [11.2 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ vivid/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:11 http://archive.ubuntu.com/ubuntu/ vivid/main libclone-perl amd64 0.37-1build1 [11.3 kB]
Get:12 http://archive.ubuntu.com/ubuntu/ vivid/main libdigest-hmac-perl all 1.03+dfsg-1 [12.1 kB]
Get:13 http://archive.ubuntu.com/ubuntu/ vivid/main libnet-smtp-ssl-perl all 1.01-3 [5,948 B]
Get:14 http://archive.ubuntu.com/ubuntu/ vivid/main libmailtools-perl all 2.13-1 [82.6 kB]
Get:15 http://archive.ubuntu.com/ubuntu/ vivid/main libsocket6-perl amd64 0.25-1build1 [23.7 kB]
Get:16 http://archive.ubuntu.com/ubuntu/ vivid/main libio-socket-inet6-perl all 2.72-1 [13.8 kB]
Get:17 http://archive.ubuntu.com/ubuntu/ vivid/main libnet-ip-perl all 1.26-1 [31.5 kB]
Get:18 http://archive.ubuntu.com/ubuntu/ vivid/main libnet-dns-perl amd64 0.81-2 [302 kB]
Get:19 http://archive.ubuntu.com/ubuntu/ vivid/main libnet-domain-tld-perl all 1.72-1 [13.7 kB]
Get:20 http://archive.ubuntu.com/ubuntu/ vivid/main libemail-valid-perl all 1.195-1 [16.6 kB]
Get:21 http://archive.ubuntu.com/ubuntu/ vivid/main libfile-basedir-perl all 0.03-1fakesync1 [10.5 kB]
Get:22 http://archive.ubuntu.com/ubuntu/ vivid/main libgettextpo-dev amd64 0.19.2-2ubuntu1 [127 kB]
Get:23 http://archive.ubuntu.com/ubuntu/ vivid/main libio-pty-perl amd64 1:1.08-1build5 [32.3 kB]
Get:24 http://archive.ubuntu.com/ubuntu/ vivid/main libio-string-perl all 1.08-3 [11.1 kB]
Get:25 http://archive.ubuntu.com/ubuntu/ vivid/main libipc-run-perl all 0.92-1 [101 kB]
Get:26 http://archive.ubuntu.com/ubuntu/ vivid/main liblist-moreutils-perl amd64 0.33-2build1 [41.0 kB]
Get:27 http://archive.ubuntu.com/ubuntu/ vivid/main libparse-debianchangelog-perl all 1.2.0-1.1 [49.9 kB]
Get:28 http://archive.ubuntu.com/ubuntu/ vivid/main libperlio-gzip-perl amd64 0.18-3build1 [15.0 kB]
Get:29 http://archive.ubuntu.com/ubuntu/ vivid/main libtext-levenshtein-perl all 0.11-1 [9,348 B]
Get:30 http://archive.ubuntu.com/ubuntu/ vivid/main hardening-includes all 2.7ubuntu1 [13.7 kB]
Get:31 http://archive.ubuntu.com/ubuntu/ vivid/main patchutils amd64 0.3.3-1 [68.2 kB]
Get:32 http://archive.ubuntu.com/ubuntu/ vivid/main t1utils amd64 1.38-4 [52.5 kB]
Get:33 http://archive.ubuntu.com/ubuntu/ vivid/main lintian all 2.5.30+deb8u3ubuntu1 [581 kB]
Get:34 http://archive.ubuntu.com/ubuntu/ vivid/main libauthen-sasl-perl all 2.1600-1 [48.7 kB]
Fetched 3,175 kB in 8s (375 kB/s)                                              
Extracting templates from packages: 100%
Selecting previously unselected package libunistring0:amd64.
(Reading database ... 108428 files and directories currently installed.)
Preparing to unpack .../libunistring0_0.9.3-5.2ubuntu1_amd64.deb ...
Unpacking libunistring0:amd64 (0.9.3-5.2ubuntu1) ...
Selecting previously unselected package libgettextpo0:amd64.
Preparing to unpack .../libgettextpo0_0.19.2-2ubuntu1_amd64.deb ...
Unpacking libgettextpo0:amd64 (0.19.2-2ubuntu1) ...
Selecting previously unselected package libgomp1:amd64.
Preparing to unpack .../libgomp1_4.9.2-10ubuntu13_amd64.deb ...
Unpacking libgomp1:amd64 (4.9.2-10ubuntu13) ...
Selecting previously unselected package diffstat.
Preparing to unpack .../diffstat_1.59-1_amd64.deb ...
Unpacking diffstat (1.59-1) ...
Selecting previously unselected package gettext.
Preparing to unpack .../gettext_0.19.2-2ubuntu1_amd64.deb ...
Unpacking gettext (0.19.2-2ubuntu1) ...
Selecting previously unselected package intltool-debian.
Preparing to unpack .../intltool-debian_0.35.0+20060710.1_all.deb ...
Unpacking intltool-debian (0.35.0+20060710.1) ...
Selecting previously unselected package libapt-pkg-perl.
Preparing to unpack .../libapt-pkg-perl_0.1.29build2_amd64.deb ...
Unpacking libapt-pkg-perl (0.1.29build2) ...
Selecting previously unselected package libarchive-zip-perl.
Preparing to unpack .../libarchive-zip-perl_1.39-1_all.deb ...
Unpacking libarchive-zip-perl (1.39-1) ...
Selecting previously unselected package libasprintf-dev:amd64.
Preparing to unpack .../libasprintf-dev_0.19.2-2ubuntu1_amd64.deb ...
Unpacking libasprintf-dev:amd64 (0.19.2-2ubuntu1) ...
Selecting previously unselected package libsub-name-perl.
Preparing to unpack .../libsub-name-perl_0.12-1_amd64.deb ...
Unpacking libsub-name-perl (0.12-1) ...
Selecting previously unselected package libclass-accessor-perl.
Preparing to unpack .../libclass-accessor-perl_0.34-1_all.deb ...
Unpacking libclass-accessor-perl (0.34-1) ...
Selecting previously unselected package libclone-perl.
Preparing to unpack .../libclone-perl_0.37-1build1_amd64.deb ...
Unpacking libclone-perl (0.37-1build1) ...
Selecting previously unselected package libdigest-hmac-perl.
Preparing to unpack .../libdigest-hmac-perl_1.03+dfsg-1_all.deb ...
Unpacking libdigest-hmac-perl (1.03+dfsg-1) ...
Selecting previously unselected package libdpkg-perl.
Preparing to unpack .../libdpkg-perl_1.17.25ubuntu1_all.deb ...
Unpacking libdpkg-perl (1.17.25ubuntu1) ...
Selecting previously unselected package libnet-smtp-ssl-perl.
Preparing to unpack .../libnet-smtp-ssl-perl_1.01-3_all.deb ...
Unpacking libnet-smtp-ssl-perl (1.01-3) ...
Selecting previously unselected package libmailtools-perl.
Preparing to unpack .../libmailtools-perl_2.13-1_all.deb ...
Unpacking libmailtools-perl (2.13-1) ...
Selecting previously unselected package libsocket6-perl.
Preparing to unpack .../libsocket6-perl_0.25-1build1_amd64.deb ...
Unpacking libsocket6-perl (0.25-1build1) ...
Selecting previously unselected package libio-socket-inet6-perl.
Preparing to unpack .../libio-socket-inet6-perl_2.72-1_all.deb ...
Unpacking libio-socket-inet6-perl (2.72-1) ...
Selecting previously unselected package libnet-ip-perl.
Preparing to unpack .../libnet-ip-perl_1.26-1_all.deb ...
Unpacking libnet-ip-perl (1.26-1) ...
Selecting previously unselected package libnet-dns-perl.
Preparing to unpack .../libnet-dns-perl_0.81-2_amd64.deb ...
Unpacking libnet-dns-perl (0.81-2) ...
Selecting previously unselected package libnet-domain-tld-perl.
Preparing to unpack .../libnet-domain-tld-perl_1.72-1_all.deb ...
Unpacking libnet-domain-tld-perl (1.72-1) ...
Selecting previously unselected package libemail-valid-perl.
Preparing to unpack .../libemail-valid-perl_1.195-1_all.deb ...
Unpacking libemail-valid-perl (1.195-1) ...
Selecting previously unselected package libfile-basedir-perl.
Preparing to unpack .../libfile-basedir-perl_0.03-1fakesync1_all.deb ...
Unpacking libfile-basedir-perl (0.03-1fakesync1) ...
Selecting previously unselected package libfile-fcntllock-perl.
Preparing to unpack .../libfile-fcntllock-perl_0.22-1build1_amd64.deb ...
Unpacking libfile-fcntllock-perl (0.22-1build1) ...
Selecting previously unselected package libgettextpo-dev:amd64.
Preparing to unpack .../libgettextpo-dev_0.19.2-2ubuntu1_amd64.deb ...
Unpacking libgettextpo-dev:amd64 (0.19.2-2ubuntu1) ...
Selecting previously unselected package libio-pty-perl.
Preparing to unpack .../libio-pty-perl_1%3a1.08-1build5_amd64.deb ...
Unpacking libio-pty-perl (1:1.08-1build5) ...
Selecting previously unselected package libio-string-perl.
Preparing to unpack .../libio-string-perl_1.08-3_all.deb ...
Unpacking libio-string-perl (1.08-3) ...
Selecting previously unselected package libipc-run-perl.
Preparing to unpack .../libipc-run-perl_0.92-1_all.deb ...
Unpacking libipc-run-perl (0.92-1) ...
Selecting previously unselected package liblist-moreutils-perl.
Preparing to unpack .../liblist-moreutils-perl_0.33-2build1_amd64.deb ...
Unpacking liblist-moreutils-perl (0.33-2build1) ...
Selecting previously unselected package libparse-debianchangelog-perl.
Preparing to unpack .../libparse-debianchangelog-perl_1.2.0-1.1_all.deb ...
Unpacking libparse-debianchangelog-perl (1.2.0-1.1) ...
Selecting previously unselected package libperlio-gzip-perl.
Preparing to unpack .../libperlio-gzip-perl_0.18-3build1_amd64.deb ...
Unpacking libperlio-gzip-perl (0.18-3build1) ...
Selecting previously unselected package libtext-levenshtein-perl.
Preparing to unpack .../libtext-levenshtein-perl_0.11-1_all.deb ...
Unpacking libtext-levenshtein-perl (0.11-1) ...
Selecting previously unselected package make.
Preparing to unpack .../make_4.0-8.1_amd64.deb ...
Unpacking make (4.0-8.1) ...
Selecting previously unselected package hardening-includes.
Preparing to unpack .../hardening-includes_2.7ubuntu1_all.deb ...
Unpacking hardening-includes (2.7ubuntu1) ...
Selecting previously unselected package patchutils.
Preparing to unpack .../patchutils_0.3.3-1_amd64.deb ...
Unpacking patchutils (0.3.3-1) ...
Selecting previously unselected package t1utils.
Preparing to unpack .../t1utils_1.38-4_amd64.deb ...
Unpacking t1utils (1.38-4) ...
Selecting previously unselected package lintian.
Preparing to unpack .../lintian_2.5.30+deb8u3ubuntu1_all.deb ...
Unpacking lintian (2.5.30+deb8u3ubuntu1) ...
Selecting previously unselected package libauthen-sasl-perl.
Preparing to unpack .../libauthen-sasl-perl_2.1600-1_all.deb ...
Unpacking libauthen-sasl-perl (2.1600-1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for install-info (5.2.0.dfsg.1-6) ...
Setting up libunistring0:amd64 (0.9.3-5.2ubuntu1) ...
Setting up libgettextpo0:amd64 (0.19.2-2ubuntu1) ...
Setting up libgomp1:amd64 (4.9.2-10ubuntu13) ...
Setting up diffstat (1.59-1) ...
Setting up gettext (0.19.2-2ubuntu1) ...
Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up libapt-pkg-perl (0.1.29build2) ...
Setting up libarchive-zip-perl (1.39-1) ...
Setting up libasprintf-dev:amd64 (0.19.2-2ubuntu1) ...
Setting up libsub-name-perl (0.12-1) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libclone-perl (0.37-1build1) ...
Setting up libdigest-hmac-perl (1.03+dfsg-1) ...
Setting up libdpkg-perl (1.17.25ubuntu1) ...
Setting up libnet-smtp-ssl-perl (1.01-3) ...
Setting up libmailtools-perl (2.13-1) ...
Setting up libsocket6-perl (0.25-1build1) ...
Setting up libio-socket-inet6-perl (2.72-1) ...
Setting up libnet-ip-perl (1.26-1) ...
Setting up libnet-dns-perl (0.81-2) ...
Setting up libnet-domain-tld-perl (1.72-1) ...
Setting up libemail-valid-perl (1.195-1) ...
Setting up libfile-basedir-perl (0.03-1fakesync1) ...
Setting up libfile-fcntllock-perl (0.22-1build1) ...
Setting up libgettextpo-dev:amd64 (0.19.2-2ubuntu1) ...
Setting up libio-pty-perl (1:1.08-1build5) ...
Setting up libio-string-perl (1.08-3) ...
Setting up libipc-run-perl (0.92-1) ...
Setting up liblist-moreutils-perl (0.33-2build1) ...
Setting up libparse-debianchangelog-perl (1.2.0-1.1) ...
Setting up libperlio-gzip-perl (0.18-3build1) ...
Setting up libtext-levenshtein-perl (0.11-1) ...
Setting up make (4.0-8.1) ...
Setting up hardening-includes (2.7ubuntu1) ...
Setting up patchutils (0.3.3-1) ...
Setting up t1utils (1.38-4) ...
Setting up lintian (2.5.30+deb8u3ubuntu1) ...
Setting up libauthen-sasl-perl (2.1600-1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
lubuntu@lubuntu:~$ 


```

There's also this lintian output for Yumi which looks like problem...

```
W: yumi: latest-debian-changelog-entry-without-new-version
W: yumi: copyright-without-copyright-notice
E: yumi: description-starts-with-package-name
W: yumi: extended-description-line-too-long
W: yumi: binary-without-manpage usr/bin/YUMI.gambas
W: yumi: desktop-entry-lacks-main-category usr/share/applications/yumi.desktop
W: yumi: menu-command-not-in-package usr/share/menu/yumi:4 usr/bin/yumi.gambas
E: yumi: menu-icon-not-in-xpm-format usr/share/pixmaps/yumi.png

```

---

### Post by Geoffrey_Arndt on 2015-10-08
Just checking on something you wrote in your first post:  

"I would really like to be able to install software from more than just the center ;/...I'm on live USB Lubuntu version 15.04."

If you are running a live Lubuntu version off cd/dvd/flash-stick, did you create the live version with "persistence"?

As far as I've seen, software installation is very problematic on a live OS (even with persistence "over-time").   Installs only persist for the live session, unless you've customized the iso.

Insofar as installing from other than official repos (including PPA's) . . . generally not recommended.   Results in less security, stability, and potential upgrade issues (requires deactivation of all PPA's for instance).

Sorry if you've already taken care of these items.    Also, I've always preferred the gui interface options you get in Xubuntu or Mate versus Lubuntu (but that's 100% up to individual).

---

