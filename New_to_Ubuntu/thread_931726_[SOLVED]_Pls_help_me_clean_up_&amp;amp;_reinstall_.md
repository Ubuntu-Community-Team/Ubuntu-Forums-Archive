---
title: "[SOLVED] Pls help me clean up &amp;amp; reinstall Firefox!!!"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by iClouseau88 on 2008-09-27
Ubuntu Hardy 8.0.4.1

/usr/lib has firefox and firefox-3.0.3 directories and files.  

Profile safely backed upto /home before.

/opt lost firefox folder (I deleted it with the hope I could reinstall ff!)

Now when I type gksudo firefox or gksudo firefox-3.0.3, or click on the FF icon nothing happens.

Synaptic package manager still shows firefox and firefox-3.0.3 as installed.

SOS!!!

---

### Post by perlluver on 2008-09-27
> **iClouseau88 said:**
> Ubuntu Hardy 8.0.4.1

/usr/lib has firefox and firefox-3.0.3 directories and files.  

Profile safely backed upto /home before.

/opt lost firefox folder (I deleted it with the hope I could reinstall ff!)

Now when I type gksudo firefox or gksudo firefox-3.0.3, or click on the FF icon nothing happens.

Synaptic package manager still shows firefox and firefox-3.0.3 as installed.

SOS!!!

Try ```
sudo apt-get --purge remove firefox
``` then ```
sudo apt-get install firefox-3.0
``` hoping this works for you.  If not let us know.

---

### Post by iClouseau88 on 2008-09-27
hoe1@hoe1-laptop:~$ gksudo firefox
hoe1@hoe1-laptop:~$ gksudo firefox-3.0
exec: 118:                                                                                                                                                                                                                                                     /usr/lib/firefox-3.0.3/firefox-3.0: not found
                                                                                                                                                                                                                 hoe1@hoe1-laptop:~$ 


Still no go!

---

### Post by starcannon on 2008-09-27
if your looking for the firefox executable link look in /usr/bin

If you need to reinstall firefox then open {System>Administration>Synaptic Package>Manager}: Search [firefox] and click the box next to the firefox you want to reinstall, choose reinstall from the menu that pops up, click Apply, and click Apply again. This works on all applications that have been installed using Ubuntu's package management system.

I'm not sure whats going on with your system, but I will give you this advice concerning what you said in your post:
>  Now when I type gksudo firefox or gksudo firefox-3.0.3, or click on the FF icon nothing happens.While there may be some reason to run firefox as superuser, I can not think of a good one.  

GL

---

### Post by perlluver on 2008-09-27
> **iClouseau88 said:**
> hoe1@hoe1-laptop:~$ gksudo firefox
hoe1@hoe1-laptop:~$ gksudo firefox-3.0
exec: 118:                                                                                                                                                                                                                                                     /usr/lib/firefox-3.0.3/firefox-3.0: not found
                                                                                                                                                                                                                 hoe1@hoe1-laptop:~$ 


Still no go!

Any reason you are trying to run it as root?  Just type firefox in the terminal and see if there are any errors.

---

### Post by Xiong Chiamiov on 2008-09-27
> **starcannon said:**
> 
While there may be some reason to run firefox as superuser, I can not think of a good one.  


Agreed.  You should probably tell us the underlying problem so we can fix *that* instead.

---

### Post by kansasnoob on 2008-09-27
What exactly is (or was) Firefox doing wrong?

---

### Post by kansasnoob on 2008-09-27
> **Xiong Chiamiov said:**
> Agreed.  You should probably tell us the underlying problem so we can fix *that* instead.

Agreed, I didn't bother to read all replies first, my bad:oops:

---

### Post by iClouseau88 on 2008-09-28
Hi everyone,

I started out using Firefox when I first installed a dual boot XP-Ubuntu 6.06.  Over the years I updated firefox by waiting to get Ubuntu updated or upgraded first.  However in the last year or two partly because there were frequent updates of Firefox, partly because I jumped the gun when I see a HOWTO in Ubuntuzilla or Ubuntuweblogs.  The short answer is there's no consistent procedure on my part to update Firefox and clean upafterwards.  So the more I follow the forums the more I messed up.

Right now Synaptic Package Manager shows that firefox(meta package) and firefox-3.0.3 are installed.  I even reinstalled these two using Synaptic.  However when I either click on the FF icon or use gksudo firefox-3.0.3 nothing happens in the terminal.  Previously when I did not loose Gnome display, depending on what I chose to do either of the following happens:

1) Clicking on the FF icon gives FF2.0.0.14, despite updating to 2.0.0.17
2) gksudo firefox-3.0 gives FF 3.0.1

I hope you understand more of the situation I am in now.  I would very much appreciate your help.

OK. I am trying to type firefox in the terminal.  Here's what happens:

hoe1@hoe1-laptop:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
hoe1@hoe1-laptop:~$ sudo apt-get install firefox-3.0
[sudo] password for hoe1: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

(I then closed Synaptic Pkg manager)

hoe1@hoe1-laptop:~$ sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hoe1@hoe1-laptop:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found

---

### Post by Xiong Chiamiov on 2008-09-28
First, make sure that the firefox2 package isn't installed.  I don't know what it's called specifically, but a search for firefox should find it.

But more importantly, **why are you running firefox as root**?  If you're just wanting to run an application in terminal, you don't have to use gksudo.

---

### Post by iClouseau88 on 2008-09-28
Hi,

There's a lock symbol besides FF2.0 in Synaptic so I couldn't even delete it (FF2.0.0.14).  The last time I use gksudo because it was an instruction from either Ubuntugeek or Ubuntuweblog, I can't remember which but it worked.

---

### Post by aysiu on 2008-09-28
My guess is that /usr/bin is set to go to /opt/firefox/firefox

Seeing as how you deleted /opt/firefox, it is now pointing to nothing, which is why Firefox won't launch.

Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and post the output back here? ```
ls -l /usr/bin/firefox
ls -l /opt
dpkg -s firefox-2
dpkg -s firefox-3.0
dpkg -s firefox
ls -l /usr/lib/firefox*
```

---

### Post by iClouseau88 on 2008-09-28
Here's the output after pasting the commands suggested by Aysiu:

hoe1@hoe1-laptop:~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2008-04-25 21:32 /usr/bin/firefox -> /opt/firefox/firefox
hoe1@hoe1-laptop:~$ ls -l /opt
total 8
drwxr-xr-x 13 root root 4096 2008-02-26 20:04 thunderbird
drwxr-xr-x  4 hoe1 hoe1 4096 2008-03-19 00:37 wicd
hoe1@hoe1-laptop:~$ dpkg -s firefox-2
Package: firefox-2
Status: purge ok not-installed
Priority: optional
Section: web
hoe1@hoe1-laptop:~$ dpkg -s firefox-3.0
Package: firefox-3.0
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 3408
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: i386
Version: 3.0.3+build1+nobinonly-0ubuntu2~fta1~hardy
Replaces: firefox (<< 3), firefox-granparadiso, firefox-libthai, firefox-trunk
Provides: firefox-libthai, www-browser
Depends: debianutils (>= 1.16), firefox-3.0-branding | abrowser-3.0-branding, fontconfig, libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.6.0), libgcc1 (>= 1:4.1.1-21), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.12.0), libnspr4-0d (>= 4.7.1+1.9-0ubuntu5~), libpango1.0-0 (>= 1.20.5), libstdc++6 (>= 4.1.1-21), psmisc, xulrunner-1.9 (>= 1.9.0.1)
Recommends: ubufox
Suggests: firefox-3.0-gnome-support (= 3.0.3+build1+nobinonly-0ubuntu2~fta1~hardy), latex-xft-fonts, libthai0
Conflicts: firefox (<< 3), firefox-granparadiso (<< 3.0~alpha8-0), firefox-libthai, firefox-trunk (<< 3.0~a8~cvs20070914t1713-0)
Conffiles:
 /etc/firefox-3.0/pref/firefox.js 6f52c7983d5ecdc9d3b953863bbebca2
 /etc/firefox-3.0/profile/mimeTypes.rdf 69cdcb7e0209f2e9d29000ee1c0ee2f0
 /etc/firefox-3.0/profile/prefs.js 99940ecd258d83b3355ab06fca0ffddb
 /etc/firefox-3.0/profile/localstore.rdf ea03cc19c2a3f622fa557cd8ea9da6eb
 /etc/firefox-3.0/profile/chrome/userContent-example.css d3765c7d2de5626529195007f4b7144a
 /etc/firefox-3.0/profile/chrome/userChrome-example.css 4788fdaa51b0a238cb21f5c2877ef06d
 /etc/firefox-3.0/profile/bookmarks.html 5268a062e398d7c991f16155159088a3
 /etc/firefox-3.0/firefoxrc 8a85ef440bb82bd19fdea6c15d1b05b8 obsolete
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
 .
 Install this firefox package too, if you want to be automatically upgraded to
 new major firefox versions in the future.
hoe1@hoe1-laptop:~$ dpkg -s firefox
Package: firefox
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 124
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: all
Source: firefox-3.0
Version: 3.0.3+build1+nobinonly-0ubuntu2~fta1~hardy
Depends: firefox-3.0, firefox-3.0-branding
Description: meta package for the popular mozilla web browser
 Firefox 3 is the next major release of the standalone Mozilla browser; it is
 written in the XUL language and designed to be lightweight and cross-platform.
 .
 This is a meta package that will point to the latest firefox package in ubuntu.
 Don't remove this if you want to receive automatic major version upgrades for
 this package in future.
hoe1@hoe1-laptop:~$ ls -l /usr/lib/firefox*

---

### Post by Xiong Chiamiov on 2008-09-28
> **iClouseau88 said:**
> Hi,

There's a lock symbol besides FF2.0 in Synaptic so I couldn't even delete it (FF2.0.0.14).  The last time I use gksudo because it was an instruction from either Ubuntugeek or Ubuntuweblog, I can't remember which but it worked.
Don't run things as root unless you have a good reason to.  This is not a good reason.

Secondly, let's see if we can get firefox all removed.  If I remember my apt-get syntax,
```

sudo apt-get remove --purge *firefox*

```

---

### Post by aysiu on 2008-09-28
> **iClouseau88 said:**
> Here's the output after pasting the commands suggested by Aysiu:

hoe1@hoe1-laptop:~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2008-04-25 21:32 /usr/bin/firefox -> /opt/firefox/firefox
hoe1@hoe1-laptop:~$ ls -l /opt
total 8
drwxr-xr-x 13 root root 4096 2008-02-26 20:04 thunderbird
drwxr-xr-x  4 hoe1 hoe1 4096 2008-03-19 00:37 wicd
 As I suspected, /usr/bin/firefox is still pointing to /opt/firefox/firefox, but /opt/firefox no longer exists.

So paste these commands into the terminal, and you should be fine: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo apt-get install --reinstall firefox
```

---

### Post by iClouseau88 on 2008-09-28
hoe1@hoe1-laptop:~$ sudo rm /usr/bin/firefox
rm: cannot remove `/usr/bin/firefox': No such file or directory
hoe1@hoe1-laptop:~$ sudo dpkg-divert --rename --remove /usr/bin/firefox
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
hoe1@hoe1-laptop:~$ sudo apt-get install --reinstall firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/68.3kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  firefox
Install these packages without verification [y/N]? y
(Reading database ... 165798 files and directories currently installed.)
Preparing to replace firefox 3.0.3+build1+nobinonly-0ubuntu2~fta1~hardy (using .../firefox_3.0.3+build1+nobinonly-0ubuntu2~fta1~hardy_all.deb) ...
Unpacking replacement firefox ...
Setting up firefox (3.0.3+build1+nobinonly-0ubuntu2~fta1~hardy) ...
hoe1@hoe1-laptop:~$

---

### Post by iClouseau88 on 2008-09-28
aysiu,

I can't thank you enough for your help and patience.  I just got FF3.0.3 with everything back like it was before.

---

