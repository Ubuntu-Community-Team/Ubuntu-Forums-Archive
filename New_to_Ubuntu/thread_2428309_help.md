---
title: "help"
date: 2019-10-02
forum: New to Ubuntu
---

### Post by fiza92 on 2019-10-02
Hi,

Sorry for posting help first. The server wouldn't let me post so I had to update and check if it worked.

Just a little bit of background first. I am new to ubuntu. I've used  it briefly in the past in a virtualized environment. I've officially switched  over to ubuntu now and am running into quite a few errors.

1. Ubuntu terminal won't open! I downloaded terminator and that works  but the original gnome terminal won't and I want to fix this bug. I  pressed Alt+F2 and entered gnome-terminal on xterm and it tells me  command not found. What do I do?

All I have done since I got this pc is download python 3.6. This one  comes with python2.7 already downloaded. I tried a bunch of things to  get python 3.6 to open because it was giving me errors. I'm not sure if  that switched symlink (and I am not entirely sure what that is or how to  switch it although I have tried with the use of different codes on  different forums here).

2. I get a stop sign at the top left hand of the screen with the notice, "A problem occurred when checking for updates." [Someone else]("https://ubuntuforums.org/showthread.php?t=2365720") was running into the same issues so I did the following based on that:

```
 sudo apt autoremove 
```

```

sudo apt update
sh: 1: /usr/lib/cnf-update-db: not found
Reading package lists... Done
E: Problem executing scripts APT::Update::razz:ost-Invoke-Success  'if /usr/bin/test -w /var/lib/command-not-found/ -a -e  /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'

```
```
sudo apt full-upgrade

Errors were encountered while processing:
 /tmp/apt-dpkg-install-j3Rg2C/11-ibus_1.5.17-3ubuntu5.2_amd64.deb
 /tmp/apt-dpkg-install-j3Rg2C/12-gir1.2-ibus-1.0_1.5.17-3ubuntu5.2_amd64.deb
 /tmp/apt-dpkg-install-j3Rg2C/39-python3-uno_1%3a6.0.7-0ubuntu0.18.04.10_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

NOTE: I also get a bunch of dkpg errors!


Then I tried ```
uname -a:

Linux fiza 4.15.0-62-generic #69-Ubuntu SMP Wed Sep 4 20:55:53 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```
Then I tried ```
lsb_release -a:
bash: /usr/bin/lsb_release: /usr/bin/python3: bad interpreter: No such file or directory

```

Following the above to [this new thread]("https://ubuntuforums.org/showthread.php?t=2365934").

I tried ```
 dpkg --audit distro-info-data 
``` which gave me nothing.

I tried ```
locate distro-info
``` and got:

```
/usr/share/distro-info
/usr/share/distro-info/debian.csv
/usr/share/distro-info/ubuntu.csv
/usr/share/doc/distro-info-data
/usr/share/doc/python3-distro-info
/usr/share/doc/distro-info-data/README.Debian
/usr/share/doc/distro-info-data/changelog.gz
/usr/share/doc/distro-info-data/copyright
/usr/share/doc/python3-distro-info/changelog.gz
/usr/share/doc/python3-distro-info/copyright
/var/lib/dpkg/info/distro-info-data.list
/var/lib/dpkg/info/distro-info-data.md5sums
/var/lib/dpkg/info/python3-distro-info.list
/var/lib/dpkg/info/python3-distro-info.md5sums
/var/lib/dpkg/info/python3-distro-info.postinst
/var/lib/dpkg/info/python3-distro-info.prerm
```

Then I tried ```
sudo apt-get install --reinstall distro-infor-data
``` and got :

```
Errors were encountered while processing:
 /var/cache/apt/archives/ibus_1.5.17-3ubuntu5.2_amd64.deb
 /var/cache/apt/archives/gir1.2-ibus-1.0_1.5.17-3ubuntu5.2_amd64.deb
 /var/cache/apt/archives/python3-uno_1%3a6.0.7-0ubuntu0.18.04.10_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Basically, I am at a loss. Please help!

UPDATE: I re-tried: 

```
 dpkg --audit distro-info-data 
dpkg: error: unable to open lock file /var/lib/dpkg/lock for testing: Permission denied

```

---

### Post by howefield on 2019-10-02
Duplicate thread closed.

---

