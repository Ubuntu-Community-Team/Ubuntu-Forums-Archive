---
title: "Seamonkey wants updating"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by roblinux on 2008-08-15
Every time I open seamonkey  (I use it only to look at hotmail account)....it gives a message about needing updating to 1.1.11 from 1.1.9

Will Ubuntu do this at some point or should I do something??

Thanks

Rob

---

### Post by jualin on 2008-08-15
Go to System, Administration, Synaptic Package Manager and then look for the "seamonkey" package and check the version that you have and the latest version that the repositories have.

---

### Post by jualin on 2008-08-15
I checked myself and the latest version found on the repositories is the 1.1.9. If you want to update it to 1.1.11 then download it using the seamonkey website, and [follow this instructions]("http://www.seamonkey-project.org/releases/seamonkey1.1.11/installation#linux") to install it. Good luck!

---

### Post by Too Late on 2008-08-15
Isn't there an automatic upgrade feature somewhere in menus in Seamonkey? If there is, that will probably work only when you've started the program with the sudo command (in terminal, type sudo seamonkey).

---

### Post by oldsoundguy on 2008-08-15
I use the Mozilla stuff FROM the Mozilla site not the package manager.  Repositories do not have the updates for them. (I am using the latest FireFox & Thunderbird in GUTSY .. updates to that are not available!!)

To update (example) open terminal and type:

gksudo seamonkey & 

and hit enter.
the program will open, only it is NOT the one you set up .. it is an updater in disguise.  Under the help tab you will see that the UPDATE is now operational.  Click on it and follow the directions.  Once completed, close the program.  When you re-open it, it will be updated and will have everything you have put into it!

---

### Post by roblinux on 2008-08-17
Thanks....I don't see an update option in the menus and am not confident with tarballs.

Will stick to the old one for now.

Thanks for replies !!

Rob

---

### Post by jualin on 2008-08-17
> **roblinux said:**
> Thanks....I don't see an update option in the menus and am not confident with tarballs.

Will stick to the old one for now.

Thanks for replies !!

Rob

[This link ]("http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually") will help you feel comfortable with tarballs, after you take a look at it is not that hard. Hope this helps!

---

### Post by n4p1 on 2008-09-07
The newest version is in intrepid release:
seamonkey-browser_1.1.11+nobinonly-0ubuntu1_i386.deb

But when I install it in hardy heron there is some errors:
```
root@ibmt23:/home/napi# dpkg -i seamonkey-browser_1.1.11+nobinonly-0ubuntu1_i386.deb
Selecting previously deselected package seamonkey-browser.
(Reading database ... 115115 files and directories currently installed.)
Unpacking seamonkey-browser (from seamonkey-browser_1.1.11+nobinonly-0ubuntu1_i3                                             86.deb) ...
dpkg: dependency problems prevent configuration of seamonkey-browser:
 seamonkey-browser depends on libgtk2.0-0 (>= 2.13.3); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu4.
 seamonkey-browser depends on libhunspell-1.2-0 (>= 1.2.4); however:
  Package libhunspell-1.2-0 is not installed.
 seamonkey-browser depends on libpango1.0-0 (>= 1.21.3); however:
  Version of libpango1.0-0 on system is 1.20.5-0ubuntu1.
dpkg: error processing seamonkey-browser (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 seamonkey-browser
```
after that seamonkey (v1.1.11) works great but when I wanna install something via apt-get, its tell me everytime about seamonkey dependencies and exit..
```
root@ibmt23:/home/napi# apt-get install openssh-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  openssh-server: Depends: openssh-blacklist but it is not going to be installed
  seamonkey-browser: Depends: libgtk2.0-0 (>= 2.13.3) but 2.12.9-3ubuntu4 is to be installed
                     Depends: libhunspell-1.2-0 (>= 1.2.4) but it is not installable
                     Depends: libpango1.0-0 (>= 1.21.3) but 1.20.5-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

When I do:
```
root@ibmt23:/home/napi# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  seamonkey-browser
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 29.6MB disk space will be freed.
Do you want to continue [Y/n]?
```
apt-get tryin remove my seamonkey...

How to fix that? I wanna use seamonkey 1.1.11 from inrepid and apt-get.

**EDIT:[SIZE="6"][/SIZE]**
I found solution. Just edit dependencies in seamonkey(...).deb
Step by step:
**How to install Seamonkey 1.1.11 from itrepid in hardy heron.**

Do it at your own risk!

1. Download:
wget [http://ubuntu.osuosl.org/ubuntu/pool/universe/s/seamonkey/seamonkey-browser_1.1.11+nobinonly-0ubuntu1_i386.deb](http://ubuntu.osuosl.org/ubuntu/pool/universe/s/seamonkey/seamonkey-browser_1.1.11+nobinonly-0ubuntu1_i386.deb)
2. Install
dpkg -i seamonkey-browser_1.1.11+nobinonly-0ubuntu1_i386.deb
Now you will see some errors about missing dependencies, if you can, install newest version via apt-get. If you see this:
```
  seamonkey-browser: Depends: libgtk2.0-0 (>= 2.13.3) but 2.12.9-3ubuntu4 is to be installed
                     Depends: libhunspell-1.2-0 (>= 1.2.4) but it is not installable
                     Depends: libpango1.0-0 (>= 1.21.3) but 1.20.5-0ubuntu1 is to be installed
```
ignore that.
3. Try run seamonkey and see if everything works ok (Applications->Internet->Seamonkey)
4. If everything is ok do: 
apt-get remove seamonkey
5. We will now change some lines in dep file. Create seamonkey.sh:
pico seamonkey.sh:
```
#!/bin/bash

EDITOR=gedit

if [[ -z "$1" ]]; then
  echo "Syntax: $0 debfile"
  exit 1
fi

DEBFILE="$1"
TMPDIR=`mktemp -d /tmp/deb.XXXXXXXXXX` || exit 1
OUTPUT=`basename "$DEBFILE" .deb`.modfied.deb

if [[ -e "$OUTPUT" ]]; then
  echo "$OUTPUT exists."
  rm -r "$TMPDIR"
  exit 1
fi

dpkg-deb -x "$DEBFILE" "$TMPDIR"
dpkg-deb --control "$DEBFILE" "$TMPDIR"/DEBIAN

if [[ ! -e "$TMPDIR"/DEBIAN/control ]]; then
  echo DEBIAN/control not found.

  rm -r "$TMPDIR"
  exit 1
fi

CONTROL="$TMPDIR"/DEBIAN/control

MOD=`stat -c "%y" "$CONTROL"`
$EDITOR "$CONTROL"
if [[ "$MOD" == `stat -c "%y" "$CONTROL"` ]]; then
  echo Not modfied.
else
  echo Building new deb...
  dpkg -b "$TMPDIR" "$OUTPUT"
fi

rm -r "$TMPDIR"
```
[code taken from here](http://ubuntuforums.org/showthread.php?t=636724)
6. Save it, do:
chmod +x seamonkey.sh
and run:
./seamonkey.sh seamonkey-browser_1.1.11+nobinonly-0ubuntu1_i386.deb
wait a sec, you will see control file from deb, now edit Depends line. Search for:
- libgtk2.0-0 (>= 2.13.3), and change to: libgtk2.0-0 (>= 2.12.8)
- libhunspell-1.2-0 (>= 1.2.4), and change to: libhunspell-1.1-0 (>= 1.1.0)
- libpango1.0-0 (>= 1.21.3), and change to: libpango1.0-0 (>= 1.20.5)
Close text editor and now modified deb would be created.
7. dpkg -i seamonkey-browser_1.1.11+nobinonly-0ubuntu1_i386.modified.deb
and voila, we have now working seamonkey v1.1.11 in hardy heron.

---

